---
title: 'Three approaches in API Development'
layout: two-cols
theme: seriph
author: Enis Spahi
presenter: true
---

<br>
<br>
<br>
<br>
<br>
<br>

# **Three approaches in API Development**
<br>

### Enis Spahi

::right::

<img src="/background2.png" class="rounded-lg w-80 border-2 border-gray-400 abs-tr mt-0 mr-0 opacity-90"/>

---

<br>
<br>
<br>

# About me

Consultant Architect at OpenValue

<div class="my-10 flex flex-col gap-y-4">
  <div class="flex items-center">
    <ri-mail-send-line class="mr-2"/>
    <a href="mailto:enis@openvalue.de" target="_blank">enis@openvalue.de</a>
  </div>
  <div class="flex items-center">
    <ri-github-fill class="mr-2"/>
    <a href="https://github.com/enisspahi" target="_blank">enisspahi</a>
  </div>
  <div class="flex items-center">
    <ri-linkedin-fill class="mr-2"/>
    <a href="https://www.linkedin.com/in/enisspahi/" target="_blank">enisspahi</a>
  </div> 
</div>

<img src="https://gravatar.com/avatar/9c891fc2c3c17bb8cc0ecd7848e144a7?s=300" class="rounded-full w-40 border-2 border-gray-400 abs-tr mt-35 mr-35"/>

---
clicks: 2
---

# APIs

<div grid="~ cols-2 gap-10">

<div>

<br>
<br>
<br>

## "An application programming interface (API) is a way for two or more computer programs to communicate with each other."​

Source: Wikipedia, "API"​

</div>

<div>

<br>
<br>
<br>

![Local Image](/api-machine-to-machine.drawio.png)

<arrow v-click="1" x1="550" y1="370" x2="550" y2="290" color="#564" width="2" arrowSize="1" />
<arrow v-click="1" x1="900" y1="370" x2="900" y2="290" color="#564" width="2" arrowSize="1" />

<br>
<br>
<div grid="~ cols-2 grid-rows-3">

<div v-click="1" color="#564">

**Consumer**

</div>

<div v-click="1" class="right-0 flex justify-end"  color="#564">

**Provider**

</div>


<div v-click="[1, 2]" class="abs-tr mt-100 mr-100">
<AutoFitText :max="50" :min="50" modelValue="🙂"/>
</div>

<div v-click="[1, 2]" class="abs-tr mt-100 mr-15">
<AutoFitText :max="50" :min="50" modelValue="🙂"/>
</div>

<div v-click="2" class="abs-tr mt-100 mr-80">
<AutoFitText :max="50" :min="50" modelValue="🙂🤦‍♀️😱😡"/>
</div>

<div v-click="2" class="abs-tr mt-100 mr-15">
<AutoFitText :max="50" :min="50" modelValue="🤯🤔"/>
</div>

</div>

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
  - Publicly available (i.e.. Geo-Location services, LLMs)​
  - Communication at scale: Many Consumers ↔ 1 Provider

---

# Statistics

Obstacles to consuming APIs

<div class="flex justify-center">
<img src="/postman_soar_obstacles.png" class="m-5 h-70 p-2 rounded bg-white" />
</div>

<div class="flex justify-center">
Source: Postman, "2023 State of the API Report"​​​
</div>



---
layout: statement
---

# Let's build an API


---

# Use Case: What should I cook?

<div grid="~ cols-2 gap-2" m="-t-2">

<div>

#### Consumer 🙂

</div>

<div>

#### Provider 🙂

</div>

<div class="max-h-95 overflow-auto">

<img src="/client-ui.png" class="h-61 rounded border-2 border-gray-400" />

<img src="/client-ui-response.png" class="h-131 rounded border-2 border-gray-400" />

</div>

<div>


```shell
curl 'http://localhost:8080/recipes?title=Pumpkin&nutritionFacts=LOW_CALORIE'
```

```json {all}{maxHeight:'335px'} 
[
    {
        "title": "Pumpkin Soup",
        "ingredients": [
            {
                "name": "Pumpkin",
                "quantity": 1000.0,
                "unit": "grams"
            },
            {
                "name": "Onion",
                "quantity": 1.0,
                "unit": "unit"
            },
            {
                "name": "Vegetable broth",
                "quantity": 750.0,
                "unit": "ml"
            },
            {
                "name": "Cream",
                "quantity": 100.0,
                "unit": "ml"
            },
            {
                "name": "Nutmeg",
                "quantity": 1.0,
                "unit": "gram"
            },
            {
                "name": "Salt",
                "quantity": 1.0,
                "unit": "tablespoon"
            }
        ],
        "preparationTime": 15,
        "cookingTime": 30,
        "servings": 4,
        "instructions": [
            "Sauté onion until translucent.",
            "Add pumpkin cubes, vegetable broth, and salt, bring to a boil.",
            "Simmer until pumpkin is tender.",
            "Blend until smooth, stir in cream and nutmeg.",
            "Heat through and serve."
        ],
        "nutritionFacts": [
            "LOW_CALORIE",
            "CARBS"
        ]
    }
]
```

</div>


</div>

---
layout: statement
---

# Find a common language

---

# OpenAPI Specification

<div class="grid grid-cols-2 md:grid-cols-[2fr_3fr] gap-0">

<div>
<br>
<br>
<br>

<img src="/openapi.webp" class="m-5 h-25 p-2 rounded bg-white" />
</div>


<div>
<br>
<br>
<br>

- Technology agnostic standard to describe Rest APIs
- Formerly Swagger, OpenAPI as of version 3
- Written as JSON or YAML
- Great tooling for code and documentation generation
- [https://openapi.tools/](https://openapi.tools/)
</div>

</div>

---
clicks: 5
---

# OpenAPI Specification

<div grid="~ cols-2 gap-4">

<div>

```yaml {all|1|2-4|5-6|7-22|23-}{maxHeight:'400px'} 
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

# 3 Approaches


---
layout: statement
---

<div class="flex justify-center items-center h-full">

# 1. Code First
</div>

<div class="flex justify-center items-center h-full">
<br>
<br>
<img src="/typing_jim_carrey.gif" class="m-5 h-60 p-2 rounded bg-white" />
</div>

---

# 1. Code First

Communicate API specification once coding has been done

<br>

<div class="flex justify-center h-full">
<img src="/api-code-first.drawio.png" class="m-5 h-70 p-2 rounded bg-white" />
</div>

---

# 1. Code First

Communicate API specification once coding has been done

<div grid="~ cols-2 gap-10">

<div>

<br>

**Advantages:**
- Focus on coding
- Flexibility to change the API design
- Documentation generation
- Client code generation

</div>

<div>

<br>

<div v-click="1">

**Disadvantages:**
- Late communication with the consumer
- Does not enable development in parallel
- Annotations
</div>

</div>

</div>

---
layout: statement
---

<div class="flex justify-center items-center h-full">

# 2. API First
</div>

<div class="flex justify-center items-center h-full">
<br>
<br>
<img src="/tethered_cap.png" class="m-5 h-70 p-2 rounded bg-white" />
<!-- https://packagingeurope.com/features/whats-the-problem-with-tethered-bottle-caps/12336.article -->
</div>


---

# 2. API First

Communicate API specification before coding. Prioritizes API design over implementation.

<br>

<div class="flex justify-center h-full">
<img src="/api-api-first.drawio.png" class="m-5 h-70 p-2 rounded bg-white" />
</div>

---

# 2. API First

Communicate API specification before coding. Prioritizes API design over implementation.

<div grid="~ cols-2 gap-10">

<div>

<br>

**Advantages:**
- Early communication with the consumer
- Enables development in parallel
- Documentation thought ahead
- Client and server code generation

</div>

<div>

<br>

<div v-click="1">

**Disadvantages:**
- Less flexibility to change the API design
- Sometimes bureaucratic for providers
- Requires Integration Testing
- "Can I deploy?" challenge
</div>

</div>

</div>

---
layout: statement
---

<div class="flex justify-center items-center h-full">

# 3. Consumer First
</div>

<div class="flex justify-center items-center h-full">
<br>
<br>
<img src="https://media0.giphy.com/media/v1.Y2lkPTc5MGI3NjExenc3bnk2ZnUyaDRyNjRrNzlhYThsOHhiY3JkejBoZDlhM3U5ODRjcCZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/e4RDR0vxGRBbifJUGe/giphy.gif" class="m-5 h-80 p-2 rounded bg-white" />
</div>

---

# 3. Consumer First

Consumer dictates the expected API behavior to the provider.

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

<img src="/api-consumer-contracts.drawio.png" class="h-50 rounded bg-white" />

</div>

</div>

---

# 3. Consumer First

Consumer dictates the expected API behavior to the provider.

<div grid="~ cols-2 gap-10">

<div>

<br>

**Advantages:**
- Test Driven API Development
- Independent consumer and provider testing
- "Can I deploy?" challenge solved

</div>

<div>

<br>

<div v-click="1">

**Disadvantages:**
- Conflicting expections of multiple consumers
</div>

</div>

</div>

---
layout: statement
---

# The right methodology?

---

# The right methodology?

|     |     |
| --- | --- |
| When to use Code first? | Provider initially focuses on coding speed <br> Flexibility to change the design |
| When to use API first? | API design over implementation <br> Early communication with the consumer → Documentation <br> Utilize code generation <br> Large number of consumers <br> Published Language |
| When to use Consumer first? | Provider should conform to consumer needs <br> API consumer and provider test their applications independently <br> To sync provider and consumer deployments <br> Small number of consumers |
| When to mix & match? | Best of both worlds |

---
layout: statement
---

# Message-driven APIs?

---


# AsyncAPI Specification

<div class="grid grid-cols-2 md:grid-cols-[2fr_3fr] gap-0">

<div>
<br>
<br>
<br>

<img src="/asyncapi.png" class="m-5 h-25 p-2 rounded bg-white" />
</div>


<div>
<br>
<br>
<br>

- Technology agnostic standard to describe message-driven APIs​
- An adaptation of the OpenAPI specification
- Written as JSON or YAML
- Protocols: AMQP, HTTP, JMS, Kafka, but not only
- [https://www.asyncapi.com/tools](https://www.asyncapi.com/tools)
</div>

</div>


---
clicks: 5
---

# AsyncAPI Specification

<div grid="~ cols-2 gap-4">

<div>

```yaml {all|1|2-4|6-10|12-24|26-}{maxHeight:'400px'} 
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
  outgoing.ping:
    description: Kafka topic for ping messages
    publish:
      operationId: pingSent
      message:
        $ref : '#/components/messages/Ping'
  incoming.pong:
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
layout: center
---

# Thank you for your attention!

<br>

<div class="flex justify-center items-center">
<img src="/qr.png" class="flex h-50" />
</div>
<div class="flex justify-center items-center">

[https://github.com/enisspahi/3approaches-in-apis](https://github.com/enisspahi/3approaches-in-apis)
</div>



