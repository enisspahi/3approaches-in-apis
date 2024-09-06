---
title: 'Three approaches in API Development'
layout: center
theme: seriph
---

<img src="/OpenValue Square.jpg" class="m-5 h-70 p-2 rounded bg-white" />

---
layout: intro
---

# Three approaches in API Development

<br>

Enis Spahi (@enisspahi)

---
layout: statement
---

# API


<br>
<br>
<br>

## "An application programming interface (API) is a way for two or more computer programs to communicate with each other."​

Source: Wikipedia, "API"​


---

# Relationships

<div grid="~ cols-2 grid-rows-2 gap-5" >

<div class="row-span-1 col-span-2 flex justify-center h-full">
<img src="/api-client-server.drawio.png" class="m-5 h-50 p-2 rounded bg-white" />
</div>

<div class="flex justify-center items-center">
<AutoFitText :max="50" :min="50" modelValue="🙂"/>
</div>

<div class="flex justify-center items-center">
<AutoFitText :max="50" :min="50" modelValue="🙂"/>
</div>


</div>

---

# Boundaries

<br>

- Private​ APIs
  - Provider and consumer are developers in the same team or same organisation​

<br>

- Partner Facing​ APIs
  - Serving partners (i.e.: Payment Service Providers)​
  - Provider and consumer might not communicate directly

<br>

- Public APIs
  - Publicly available (i.e.. Geo-Location services)​
  - Communication at scale: Many Consumers ↔ 1 Provider

---

# Statistics

Top 3 Obstacles to consuming APIs


<div grid="~ cols-2 gap-4">

<div>

<br>

<br>

- Lack of documentation​
- Difficulty in discovering APIs​
- Lack of time​
</div>

<div>

![Obstacles](/postman_soar_obstacles.png)
Source: Postman, "2023 State of the API Report"​​​
</div>


</div>

---

# API Communication

<div grid="~ cols-2 grid-rows-2 gap-5" >

<div class="row-span-1 col-span-2 flex justify-center h-full">
<img src="/api-client-server.drawio.png" class="m-5 h-50 p-2 rounded bg-white" />
</div>

<div class="flex justify-center items-center">
<AutoFitText :max="50" :min="50" modelValue="🙂"/>
<AutoFitText :max="50" :min="50" modelValue="🤦‍♀️"/>
<AutoFitText :max="50" :min="50" modelValue="😱"/>
<AutoFitText :max="50" :min="50" modelValue="😡"/>
</div>

<div class="flex justify-center items-center">
<AutoFitText :max="50" :min="50" modelValue="🤯"/>
<AutoFitText :max="80" :min="50" modelValue="🤔"/>
</div>


</div>

---
layout: center
---

# Enhancing Communication

<div class="flex justify-center items-center h-full">
<img src="/ibet.png" class="m-5 h-80 p-2 rounded bg-white" />
</div>


---
layout: center
---

# Speak common language
<!-- Speak common language -->

<br>

<div grid="~ cols-1 grid-rows-2 gap-2" >

<div class="flex justify-center h-full">
<img src="/openapi.webp" class="m-5 h-20 p-2 rounded bg-white" />
</div>

<div class="flex justify-center h-full">
<img src="/asyncapi.png" class="m-5 h-20 p-2 rounded bg-white" />
</div>

</div>


---

# Standardized API Communication

<br>
<br>
<br>

<div grid="~ cols-2 gap-10">

<div>

<img src="/api-human2human.drawio.png" class="m-5 h-60 p-2 rounded bg-white" />

</div>

<div>

<br>


- Common Language for API discovery
  - OpenAPI/Swagger for REST APIs
  - AsyncAPI for message-driven APIs
- Foundation for tooling
  - Code generation
  - Documentation
- Community

</div>

</div>

<!-- API Spec define the functions and the expected results of an API -->

---
layout: statement
---

# Development Process
Let's build an API


---

# Recipes API

<div grid="~ cols-2 gap-2" m="-t-2">

<div>

#### Client

</div>

<div>

#### Server

</div>

<div class="max-h-87 overflow-auto">

<img src="/client-ui.png" class="h-60 rounded border-2 border-gray-400" />

<img src="/client-ui-response.png" class="h-130 rounded border-2 border-gray-400" />

</div>

<div class="max-h-87 overflow-auto">

<img src="/swagger-ui.png" />

<img src="/swagger-ui2.png" />

</div>


</div>



---

# API Development - Code First

Communicate API specification once coding has been done

<div grid="~ cols-2 gap-10">

<div>

<br>

<div v-click="1">

- **Advantages:**
  - Focus on coding
  - Flexibility to change the API design

</div>

<div v-click="2">

- **Disadvantages:**
  - Late communication with the consumer
  - Does not enable development in parallel
  - Annotations
</div>

</div>

<div>

<br>
<br>

<img src="/api-code-first.drawio.png" class="h-50 rounded bg-white" />

</div>

</div>

---

# API Development - API First

Communicate API specification before coding. Prioritizes API design over implementation.

<div grid="~ cols-2 gap-10">

<div>

<br>

<div v-click="1">

- **Advantages:**
  - Early communication with the consumer
  - Documentation thought ahead
  - Enables development in parallel

</div>

<div v-click="2">

- **Disadvantages:**
  - Less flexibility to change the API design
  - Sometimes bureaucratic for providers
</div>

</div>

<div>

<br>
<br>

<img src="/api-api-first.drawio.png" class="h-54 rounded bg-white" />

</div>

</div>

---

# API Development - Consumer First

Consumer dictates the expected API behavior to the provider

<div grid="~ cols-2 gap-10">

<div>

<br>

<div v-click="1">

**Pact:** A Code-first consumer contract testing tool that enables consumer driven API development.

</div>


<div v-click="2">

**Process:**
- Consumer produces a pact
- Provider verifies it's API implementation
- Server / Client deployments synced

</div>

</div>

<div>

<br>
<br>

<img src="/image.png" class="h-50 rounded bg-white" />

</div>

</div>

---

# Summary

|     |     |
| --- | --- |
| When to use Code first? | Provider initially focuses on coding speed <br> Flexibility to change the design |
| When to use API first? | API design over implementation <br> Early communication with the consumer → Documentation <br> Utilize code generation <br> Large number of consumers |
| When to use Consumer first? | Provider should conform to consumer needs <br> API consumer and provider test their applications independently <br> To sync provider and consumer deployments <br> Small number of consumers |
| When to mix & match? | When API first alone is not sufficient to match consumer needs |


---
layout: statement
---

## **OpenValue Blog**

[https://openvalue.blog/posts/2023/11/25/communicating_our_apis_part1/](https://openvalue.blog/posts/2023/11/25/communicating_our_apis_part1/)

[https://openvalue.blog/posts/2023/11/26/communicating_our_apis_part2/](https://openvalue.blog/posts/2023/11/26/communicating_our_apis_part2/)

## **Code Samples**

[https://github.com/enisspahi/code-first-api-example](https://github.com/enisspahi/code-first-api-example)

[https://github.com/enisspahi/contract-first-api-example](https://github.com/enisspahi/contract-first-api-example)

[https://github.com/enisspahi/consumer-first-api-example](https://github.com/enisspahi/consumer-first-api-example)

---
layout: statement
---

# Q&A
