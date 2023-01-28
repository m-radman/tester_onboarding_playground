# Part 2: API Testing with SuperTest

## GitHub Repo → https://github.com/ivaaaa/supertest-playground

### Before we get started

- [ ]  `step0` Make sure you have Git as well as NodeJS (`npm` comes with it) installed on your system
    
    ![Screenshot 2023-01-04 at 18.08.28.png](./assets/part2/Part2_1.png)
    
    *If you don’t have NodeJS installed don’t panic, just go to [https://nodejs.org/en/](https://nodejs.org/en/) to download and install LTS version of NodeJS on your system.* 
    
- [ ]  `step1` Clone GitHub repo ‣, this is going to be our code repository for `Part 2`
    
    ```bash
    git clone git@github.com:ivaaaa/supertest-playground.git
    cd supertest-playground 
    
    # NOTE: please do checkout develop branch 
    # commit and push your changes to develop branch 
    # once you are happy we will create a PR (Pull Request)
    # to REVIEW and then MERGE your changes from develop to master 
    git checkout develop 
    
    npm install
    ```
    
- [ ]  `step2` Make sure you have access to [Simple Books API](https://github.com/vdespa/introduction-to-postman-course/blob/main/simple-books-api.md)  endpoints from Postman
- [ ]  `step3` Check out `supertest`’s  [README.md](https://github.com/ladjs/supertest#readme)
    
    👉 **Why we need** SuperTest? **Which problem it solves** for us? 
    
    → It will provide us with **high-level abstraction for testing HTTP** 
    
    `note#1` “testing HTTP” just means testing APIs, tests that send HTTP request and expect HTTP response in return
    
    `note#2` ”high-level abstraction” means this 👇
    
    Our tests **don’t** **need** to **know `how` to** send an HTTP request (although they do need it sent). By deciding to use SuperTest we are deciding that we are going to delegate the responsibility of sending requests over HTTP to `supertest`. Or, in other words, **we will use `supertest` to send HTTP requests** over network for us.
    
    👉 **What** is SuperTest **based on**? → “HTTP assertions made easy via **SuperAgent**”  (*SuperAgent - Small progressive **client-side HTTP request library**)
    
    `[supertest` on npm](https://www.npmjs.com/package/supertest) & `[superagent` on npm](https://www.npmjs.com/package/superagent)  documentation available [here](https://ladjs.github.io/superagent/) 
    
- [ ]  `step4` 🎉 you are all set!

### API Testing with SuperTest

#### 🎯 Our goal

- Learn **how to design, write and run API tests** **using SuperTest** library

#### 👀 `PHASE 1` **Get to know the thing under test**

Before we get into writing tests, let’s first analyse the functionality of our “application under test”. 

In other words, we want to look into the [API documentation](https://github.com/vdespa/introduction-to-postman-course/blob/main/simple-books-api.md) that describes **`which endpoints of Simple Books are exposed and how to use them`** 

We should: 
- get familiar with all of the endpoints (8 endpoints + 1 endpoint we need for authentication purposes)
- detect the resources which Simple Books service is responsible of (we have 2 resources - `book` and `order` )
- think about which [status codes](https://www.w3.org/Protocols/HTTP/HTRESP.html) could be returned by each of the endpoints
    - 400 Bad Request - valid / failure response for POST / PUT request (when `body` you sent in HTTP request is not what web service code expects)
    - 200 OK - valid / success response for GET request
    - 201 OK - valid / success response for POST / PUT request
    - 404 Not Found - resource not found, valid GET response if the requested resource does not exist (example: there is no book with given bookId)
    - 500 Internal Server Error - an error occurred but web service code did not count on that type of error - this is not smth that you would ever expect to happen
    
[📚 Simple Books API](https://github.com/vdespa/introduction-to-postman-course/blob/main/simple-books-api.md) implements following endpoints

  ```
  GET `/status`  grab status of the web service 
  ```

  ---

  ```
  GET `/books`  list books 
  GET `/books/:bookId` get book details by it’s id 
  ```
  ---

  ```
  POST `/orders`  create new order record `requires authentication`
  GET `/orders`  get all orders `requires authentication`
  GET `/orders/:orderId` get order by it’s id  `requires authentication`
  PATCH `/orders/:orderId` update existing order  `requires authentication`
  DELETE `/orders/:orderId` delete order with given id  `requires authentication`
  ```

  ---

  ```
  POST `/api-clients/` register your API client so that you can authenticate yourself
  ```

#### 💻 `PHASE 2` **Walk-through the steps of setting up the `supertest-playground` code project from scratch**

📌 Here is where I am writing down the steps I did to setup `supertest-playground` code base. Feel free to create a GitHub repo of your own and repeat these steps yourself (recommended ⚠️🙏).

- `Step1` create an empty repository in GitHub and run `git clone` to clone the repo to your machine 

- `Step2` create an `npm` package 

  ```jsx
  cd my_projects/supertest_playground
  npm init 
  ```

  - We are actually converting the project folder into an `npm` package by running `init` command. As a result `package.json` file will be created. Folder with `package.json` file is considered to be an `npm` package by definition.

- `Step3` install `[supertest](https://github.com/ladjs/supertest)` and save it to our dev dependencies 

  ```jsx
  npm install supertest --save-dev
  ```

     - As a result our `package.json` file should be updated - `supertest` should be added to `"devDependencies"` . `**TODO**` Quick read about what package.json is - see [geeksforgeeks](https://www.geeksforgeeks.org/node-js-package-json/) article.

     - `package-lock.json` file will be generated automatically by `npm` (node’s package manager). `**TODO**`Quick read about what package-lock.json is all about - see [geeksforgeeks](https://www.geeksforgeeks.org/difference-between-package-json-and-package-lock-json-files/) article.

- `Step4`  install `[jest](https://github.com/facebook/jest)`  (The Javascript Testing Framework) and save it to our dev dependencies

  ```jsx
  npm install jest --save-dev 
  ```

  - Please note link to [Jest documentation](https://jestjs.io/docs/getting-started) 📌

- `Step5` add `test` and `test:watch` scripts to [npm scripts](https://docs.npmjs.com/cli/v9/using-npm/scripts) in `package.json` 

  ```jsx
  // package.json
  {
    "name": "supertest-playground",
    "version": "1.0.0",
    ...
    "scripts": {
      "test": "jest",
      "test:watch": "jest --watch"
    }
  }
  ```

  - Note how `test` script only runs/executes/starts `jest` test runner. While `test:watch` script also starts `jest` test runner but in watch mode. `**TODO`** Read about [**how to Run jest from command line](https://jestjs.io/docs/cli#running-from-the-command-line).** 

- `Step6` in order to *start tests* we will `(1)` go to command line (MacOS Terminal / Linux Shell / GitBash etc) and `(2)` run one of the two `npm scripts`:   

  ```jsx
  npm run test 
  npm run test:watch
  ```

- `Step7` in the root of the project create a folder named `tests` with subfolders `books` `orders` and `status`

  - Note that this is where our test files are going to live :) Also note that all of our test files will be named as following `*.test.js` This is so that jest runner automatically recognises which files to run. Jest will run all files that match certain pattern such as `*.test.js` or `*.spec.js` - see [here](https://jestjs.io/docs/configuration#testregex-string--arraystring). Check out all the [command line options](https://jestjs.io/docs/cli) you can pass to `jest` CLI tool.

#### ✍️ `PHASE 3` **Exercises**

**`TODO`** Your task is to implement test cases in 5 test files marked with TODO as shown on screenshot below 👇 

  ```jsx
  books/get_single_book.test.js
  orders/submit_order.test.js
  orders/update_order.test.js
  orders/get_order.test.js
  orders/delete_order.test.js
  ```

![Screenshot 2023-01-05 at 23.40.14.png](./assets/part2/Part2_2.png)

Some of the tests are already implemented - to give an example to learn from. 

  ```jsx
  status/get_status.test.js
  books/get_list_of_books.test.js
  orders/get_orders.test.js
  ```

❗IMPORTANT → You can always use JavaScript `console.log` to debug test execution. Or you can search the internet to find a way to setup the Node debugger in `vscode` to work with jest ([check out this gist](https://gist.github.com/jherax/231b2dda7f9cce20e13f4590594fdb70) + [read about what `.vscode/launch.json` file is all about](https://code.visualstudio.com/docs/editor/debugging#_launch-configurations)).

### Conceptual Asides 
#### ✋ Conceptual Asides`TODO` ✍️

- `CA-M`  let’s demystify 🔎 why we need APIs? → what is RPC (RPC stands for Remote Procedure Call, procedure = function) ? 👉let’s jump to a quick lesson by `Valentin Despa` 🧑‍🏫 [here](https://www.youtube.com/watch?v=MdaGuP6-bKs)

*Udemy account* → `ivacizmas@gmail.com` / `UcimoProgramiranje2022`  

### Links & Readings

. . . 
