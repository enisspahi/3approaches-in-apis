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

# Pairs

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

# Communication Issues between Pairs

<div class="flex justify-center items-center h-full">
<img src="/ibet.png" class="m-5 h-80 p-2 rounded bg-white" />
</div>

---
layout: center
---

# Find a common language

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

# OpenAPI Specification

<br>
<br>

- Technology agnostic standard to describe Rest APIs
- Formerly Swagger, OpenAPI as of version 3
- Written as JSON or YAML
- Great tooling for code and documentation generation
- [https://openapi.tools/](https://openapi.tools/)

---
clicks: 5
---

# OpenAPI Specification

<div grid="~ cols-2 gap-4">

<div>

```yaml {all|1|2-4|5-6|7-22|23-}  {maxHeight:'400px'} 
openapi: 3.0.3
info:
  title: Recipes API
  ...
servers:
- url: http://localhost:8080
paths:
  /recipes:
    get:
      summary: List all recipes
      ...
      responses:
        ...
        "200":
          description: OK
          content:
            'application/json':
              schema:
                type: array
                items:
                  $ref: '#/components/schemas/Recipe'
        ...
components:
  schemas:
    Recipe:
      type: object
      ...
```
</div>

<div class="p-3">

<v-clicks at="0">

- **Openapi:** Spec Version
- **Info:** General API information as metadata
- **Servers:** Connectivity information about target servers
- **Paths:** Paths to the endpoints with their expected request, response and errors. 
- **Components:** Holds the schemas for the request, response and errors for referencing

</v-clicks>

</div>

</div>


---

# AsyncAPI Specification

<br>
<br>

- Technology agnostic standard to describe message-driven APIs​
- An adaptation of the OpenAPI specification
- Written as JSON or YAML
- Protocols: AMQP, HTTP, JMS, Kafka, but not only
- [https://www.asyncapi.com/tools](https://www.asyncapi.com/tools)


---
clicks: 5
---

# AsyncAPI Specification

<div grid="~ cols-2 gap-4">

<div>

```yaml {all|1|2-4|6-10|12-24|26-}  {maxHeight:'400px'} 
asyncapi: 2.0.0
info:
  title: Ping Service
  ...

servers:
  localhost:
    url: localhost:9092
    protocol: kafka
    protocolVersion: '1.0.0'

channels:
  ping.topic:
    description: Kafka topic for ping messages
    publish:
      operationId: pingSent
      message:
        $ref : '#/components/messages/Ping'
  pong.topic:
    description: Kafka topic for pong messages
    subscribe:
      operationId: pongReceived
      message:
        $ref : '#/components/messages/Pong'      

components:
  messages:
    Ping:
      name: Ping
      ...
      payload:
        $ref: '#/components/schemas/PingPayload'
    Pong:
      name: Pong
      ...
      payload:
        $ref: '#/components/schemas/PongPayload'

  schemas:
    PingPayload:
      type: object
      ...
    PongPayload:
      type: object       
      ...
```
</div>

<div class="p-3">

<v-clicks at="0">

- **Asyncapi:** Spec Version
- **Info:** Metadata information about the API
- **Servers:** Connectivity information about servers (i.e. Kafka brokers)
- **Channels:** Messages exchange between provider and consumer
- **Components:** Defines the reusable objects such as schemas or messages which could be referenced.

</v-clicks>

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
layout: center
---

# Development Process

<div class="flex justify-center items-center h-full">
<img src="/nicolascage_pedropascal.gif" class="m-5 h-80 p-2 rounded bg-white" />
</div>

---

# Let's build an API - Recipes Demo

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

<br>

<div class="flex justify-center h-full">
<img src="/api-code-first.drawio.png" class="m-5 h-70 p-2 rounded bg-white" />
</div>

---

# API Development - Code First

Communicate API specification once coding has been done

<br>

| **Advantages** | **Disadvantages** |
| ------------- |-------------|
| Focus on coding | Late communication with the consumer |
| Flexibility to change the API design | Does not enable development in parallel      |
|  | Annotations      |

---

# API Development - API First

Communicate API specification before coding. Prioritizes API design over implementation.

<br>

<div class="flex justify-center h-full">
<img src="/api-api-first.drawio.png" class="m-5 h-70 p-2 rounded bg-white" />
</div>

---

# API Development - API First

Communicate API specification before coding. Prioritizes API design over implementation.

<br>

| **Advantages** | **Disadvantages** |
| ------------- |-------------|
| Early communication with the consumer | Less flexibility to change the API design |
| Documentation thought ahead | Sometimes bureaucratic for providers |
| Enables development in parallel |  |

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

# Recap

|     |     |
| --- | --- |
| When to use Code first? | Provider initially focuses on coding speed <br> Flexibility to change the design |
| When to use API first? | API design over implementation <br> Early communication with the consumer → Documentation <br> Utilize code generation <br> Large number of consumers |
| When to use Consumer first? | Provider should conform to consumer needs <br> API consumer and provider test their applications independently <br> To sync provider and consumer deployments <br> Small number of consumers |
| When to mix & match? | When API first alone is not sufficient to match consumer needs |

---
layout: center
---

# Are same approaches applicable to AsyncAPI?

<div v-click="1" class="flex justify-center items-center">

- Inspired by OpenAPI
- Code First and API First
- Pact Messaging support
- [https://www.asyncapi.com/tools](https://www.asyncapi.com/tools)

</div>

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
