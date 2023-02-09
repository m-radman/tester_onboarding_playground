# Part 1 appendix-a: Run Postman tests in Jenkins

This lecture is `apendix-a` sequel to [`Part 1`](./Part1.md) lecture.   

## Run Postman tests in Jenkins

### 🎯 Our goals

- Learn **how to configure Jenkins job** to run Postman collection via Newman CLI

### ✍️ One BIG `TODO`

**Watch *[Run Postman Collections in Jenkins with Newman](https://www.youtube.com/watch?v=iS7HPNswv-8)* YouTube video** (_👨‍🏫 `Valentin Despa` -- :hourglass: ~2h)_

## Conceptual Asides

### ✋ Conceptual Asides `TODO` List ✍️

- `CA-1` let’s demystify 🔎 what is Newman ? 👉 **command-line tool** that is responsible to **run Postman collections** (command-line collection runner) [see here](https://learning.postman.com/docs/running-collections/using-newman-cli/command-line-integration-with-newman/)
- `CA-2` let’s demystify 🔎 how to install and use Newman ? 👉 Newman is an **npm package**, you can find it [here](https://www.npmjs.com/package/newman) in npm public registry and `newman`'s code lives in GitHub repo [here](https://github.com/postmanlabs/newman)
    
    ```bash
    # install newman cli 
    npm install -g newman
    
    # run collection from json file 
    newman run my_collections/my_collection.json
    
    # run collection from public url 
    newman run https://www.getpostman.com/collections/631643-f695cab7-6878-eb55-7943-ad88e1ccfd65-JsLv
    ```
    
    📌 all command-line options documented in [README.md in GitHub](https://github.com/postmanlabs/newman#command-line-options) 
    
- `CA-3` let’s demystify 🔎 what is Jenkins ? 👉 Jenkins is a self-contained, open source **automation server**
- `CA-4` let’s demystify 🔎 what is Jenkins used for ? 👉 Jenkins can be used **to automate all sorts of tasks** related to building, testing, and delivering or deploying software applications
- `CA-5` let’s demystify 🔎 can Jenkins be installed to run on my machine ? how ? 👉 Yes, Jenkins can be run as standalone server by any machine with a Java Runtime Environment (JRE) installed 📌 see [How to install Jenkins on Windows](https://www.jenkins.io/doc/book/installing/windows/)

### Links & Readings

#### Additional tutorials

    🚵 [⚠️ Skip this for now] Jenkins official tutorial → [Getting Started with Jenkins Guided Tour](https://www.jenkins.io/doc/pipeline/tour/getting-started/)


:point_left: [go back to main page](../README.md)