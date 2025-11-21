# Module 2 Activities: Agentic Patterns and Custom API Integration

In this module we will work more with tools and agentic workflows, bringing in the very power HTTP Request node for making calls to REST APIs.

## Module 2, Activity 1: A Very Basic HTTP Request

We will begin with a trivial workflow that is designed to send a GET request to a REST API endpoint.  This particular endpoint will require no authentication or credentials and just return a basic JSON payload.

So let's start with a manual trigger and add to it an "HTTP Request" node, which will bring up the following screen:

<img src="./pics/http_request_blank.jpg" width="300">

Right now we are going to keep this as simple as possible.  So we just need a URL for our GET request.  Let's use `https://catfact.ninja/fact`.  If you put that in the URL box and click the red "Execute step" button, you will see the returned payload.  It varies each time you execute the request, but (in JSON format) the output should look something like this:

```json

[
    {
        "fact": "At 4 weeks, it is important to play with kittens so that they do not develope a fear of people.",
        "length": 95
    }
]
```

Congratulations!  You have just made your first API request from n8n!


