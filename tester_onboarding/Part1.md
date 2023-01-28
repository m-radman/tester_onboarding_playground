# Part 1: API Testing with Postman

### 📫 Final version of collection.json → [ATTACH HERE]

**Before we get started**

- [ ]  `step1` Go to [https://www.postman.com/](https://www.postman.com/) and create an account or login with Google account (it’s free)
- [ ]  `step2` Download and install `Postman Desktop App` [https://www.postman.com/downloads/](https://www.postman.com/downloads/)
- [ ]  `step3` (optional at this point) Download and Install NodeJS [https://nodejs.org/en/download/](https://nodejs.org/en/download/) *(LTS Long Term Supported version is ok)*
- [ ]  `step4` 🎉 you are all set!

### API Testing with Postman

<aside>
🎯 Our goals

- Learn how to do API Testing using Postman
- Gain some basic understanding of certain concepts such as JSON, API, RESTful API, Client Server communication over HTTP, etc
</aside>

<aside>
✍️ **One BIG `TODO`: Take [Postman Beginner's Course on API Testing](https://www.youtube.com/watch?v=VywxIQ2ZXw4) course 2h 1.5M views ([GitHub repo](https://github.com/vdespa/introduction-to-postman-course) of the course)**

- follow along with the instructor / code in parallel
    - consult `[Postman Learning Center](https://learning.postman.com/docs/getting-started/introduction/)`  pages whenever you feel like you want to know more or double check something (some links are also provided below👇)
    - whenever you are faced with new terminology / unknown concept we want to **stop and DEMYSTIFY it**
        - we want to: **`stop` 🖐️🛑 → `ask questions` → `find answers` (in attached video or blog post) → `move on` with the course**
    - make notes during the process (*not mandatory, recommended*)
</aside>

### Conceptual Asides

*Every now and then we will want to stop and demystify some term that we don’t know about.*

> ✋🛑 We will call these occasions **conceptual asides**
> 

> ℹ️  Simply we will stop and ask questions that help us understand term/concept we never heard of before, term/concept that sounds overly complex but actually becomes simple once we answered few questions.
> 
- The questions we want to ask ourselves
    
    → what is it ? (could be a tool, library, an idea, standard way to do something, etc)
    
    → where is it used ? 
    
    → who uses it ? 
    
    → how we could use it ?  
    
    → what problem it solves for us ? 
    
    → etc 
    

<aside>
✋ C**onceptual Asides`TODO`** ✍️

- `CA-1` let’s demystify 🔎 how client and server talk with each other ? 👉 let’s jump to quick lesson [here](https://www.udemy.com/course/understand-nodejs/learn/lecture/3466030#overview)
- `CA-2` let’s demystify 🔎 what are TCP/IP protocols used for? 👉 let’s jump to quick lesson [here](https://www.udemy.com/course/understand-nodejs/learn/lecture/3632880#overview)
- `CA-3` let’s demystify 🔎 addresses and ports / how program knows to which computer to send a message over HTTP? 👉 let’s jump to quick lesson  [here](https://www.udemy.com/course/understand-nodejs/learn/lecture/3632882#overview)
- `CA-4` let’s demystify 🔎 what is HTTP ? 👉 let’s jump to quick lesson [here](https://www.udemy.com/course/understand-nodejs/learn/lecture/3632884#overview)
- `CA-5` let’s demystify 🔎 what is JSON ? 👉 let’s jump to quick lesson [here](https://www.udemy.com/course/understand-nodejs/learn/lecture/3488912#overview)
    
        → about *Objects and Object Literals in JavaScript* learn [here](https://www.udemy.com/course/understand-javascript/learn/lecture/2237512#overview) 
    
        → about *JSON and Object Literals* in JavaScript learn [here](https://www.udemy.com/course/understand-javascript/learn/lecture/2237518#overview) 
    
- `CA-6` let’s demystify 🔎 what is API ? and what is ENDPOINT? 👉 let’s jump to quick lesson [here](https://www.udemy.com/course/understand-nodejs/learn/lecture/3632896#overview)
- `CA-7` let’s demystify 🔎 what it means that API is RESTful API ? 👉 let’s jump to quick lesson [here](https://www.udemy.com/course/understand-nodejs/learn/lecture/3658452#overview)
- `CA-8` let’s demystify 🔎 what is CLI ? 👉 let’s jump to quick lesson [here](https://www.udemy.com/course/understand-nodejs/learn/lecture/3453082#overview)

… (more to come here)

 

*Udemy account* → `ivacizmas@gmail.com` / `UcimoProgramiranje2022`  

</aside>

### Links & Readings

📌 `[Postman Learning Center](https://learning.postman.com/docs/getting-started/introduction/)` 

 📙 [How to SEND you first REQUEST from Postman](https://learning.postman.com/docs/getting-started/sending-the-first-request/) 

 📙 [How to create a COLLECTION in Postman](https://learning.postman.com/docs/getting-started/creating-the-first-collection/) 

 📙 [How to EXPORT collection from Postman](https://learning.postman.com/docs/getting-started/importing-and-exporting-data/#exporting-collections) 

 📙 [How to use VARIABLES in Postman](https://learning.postman.com/docs/sending-requests/variables/)

 📙 [How to manage ENVIRONMENTS in Postman](https://learning.postman.com/docs/sending-requests/managing-environments/) 

 📙 [How to write SCRIPTS in Postman](https://learning.postman.com/docs/writing-scripts/intro-to-scripts/) 

📌 [learn about pre-request scripts](https://learning.postman.com/docs/writing-scripts/pre-request-scripts/) *(useful to “setup test environment” before sending a request)*

📌 [learn how to write tests](https://learning.postman.com/docs/writing-scripts/test-scripts/) ie checks that are meant to check the response 

🔬[check out some examples here](https://learning.postman.com/docs/writing-scripts/script-references/test-examples/) 

[📙 How to RUN COLLECTION of requests manually in Postman](https://learning.postman.com/docs/running-collections/intro-to-collection-runs/)

📙 [How to RUN COLLECTION of requests using Newman](https://learning.postman.com/docs/running-collections/using-newman-cli/command-line-integration-with-newman/) **`TODO`** ✍️

👆Go through [these steps](https://learning.postman.com/docs/running-collections/using-newman-cli/installing-running-newman/) to `npm install -g newman` on your machine and attempt to run a collection locally (from command line from your machine; note that before doing that you will have to export collection in json format)