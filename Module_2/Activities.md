# Module 2 Activities: Agentic Patterns and Custom API Integration

In this module we will work more with tools and agentic workflows, bringing in the very power HTTP Request node for making calls to REST APIs.

## Module 2, Activity 1: A Very Basic HTTP Request

We will begin with a trivial workflow that is designed to send a GET request to a REST API endpoint.  This particular endpoint will require no authentication or credentials and just return a basic JSON payload.

So let's start with a manual trigger and add to it an "HTTP Request" node, as shown in this workflow:

<img src="./pics/cat_facts.jpg" width="300">

When you add the HTTP Request node, n8n will bring up the following screen:

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

## Module 2, Activity 2: HTTP Requests as a Tool

Now we are going to make this a little more complicated.  We are going to create a weather chatbot that will use the HTTP Request as a tool rather than a separate node.  For this activity, you will need to create an API key from Visual Crossing as described in the onboarding document.

### Create The Workflow

We are going to begin by creating a basic chatbot workflow like we did in Module 1.  It should look like this:

<img src="./pics/basic_chatbot_http_req.jpg" width="600">

We are now going to populate this step by step.

First, let's configure the agent.  We want to update the system message a bit to provide some basic instructions.  Our goal will be for the agent to read from the user's message what location they are referring to and then go get the current weather for that location.  Provide the following to the system message:

```
You are a helpful weather assistant. When a user asks about weather for a location, use the Get Current Weather tool to fetch the current conditions. Extract the location from the user's message and format it appropriately (e.g., "Denver,CO" or "London,UK"). Present the weather information in a friendly, conversational way.
```

It is important that we have included in the system prompt examples of how to format the data since the Visual Crossing API has requirements of no space in between the city and state/country.  Providing examples of behavior you want is called **few-shot prompting** and is a very good habit to adopt!

### Configure the HTTP Request Tool

Let's start at the top of the tool, as shown here:

<img src="./pics/top_http_req.jpg" width="600">

Notice that we start with a tool description, which tells the agent what this particular tool does.  Keep these descriptive but concise.  Next, we see that we are using the GET method.  After that, we pass it a URL.  This is where things get a little complicated.  We need to get the location from the agent.  If we look at the input panel on the left in the "From AI" section, we can see that the agent populated a variable called "location."  It is used to populate the URL.  However, there is a bit of code being used here to do so, namely:

```
{{ $fromAI('location', 'The location to get weather for (e.g., Breckenridge,CO)', 'string') }}
```

`$fromAI()` is a special function used when the HTTP Request node is connected as a tool to an AI agent.  It tells the agent that it needs to supply this value when calling the tool.  `location` is the parameter name that the AI will reference internally.  `The location to get weather for (e.g., Breckenridge,CO)` is a description that helps the AI understand what value it should provide.  This acts as instructions for the agent.  Finally, `string` specifies the data type the AI should return.

Let's dive a bit deeper into the next part of the HTTP Request configuration by considering what the URL would look like if we wanted to cURL this information.  If I wanted to get the weather for my home town of Breckenridge, CO, I would use the following URL:

```
https://weather.visualcrossing.com/VisualCrossingWebServices/rest/services/timeline/breckenridge%2C%20co?unitGroup=us&key=SUYJUM8ETPPD2BAXGRHDX23M5&contentType=json&include=current
```

Let's briefly review REST API's and what this actually means.  We start with the base URL, which, in this case, is:

```
https://weather.visualcrossing.com/VisualCrossingWebServices/rest/services/timeline/breckenridge%2C%20co
```

From here, the `?` indicates that query parameters are now coming.  `&` signals the start of a new query parameter.  So we have a query parameter called `unitGroup` which has a value of `us`.  We also have our `key` passed right in the URL along with `contentType`.  `include=current` tells this particular API to be sure to include the current measurement in addition to the historical ones.  We will use all of these (except `contentType`, which is defaulted) in our HTTP Request Tool.

So let's scroll down in that node to see what else we can configure.  Here is what we see:

<img src="./pics/bottom_http_req.jpg" width="600">

First, we have authentication set to none.  In general, it is best practice to save authentication information in credentials.  However, in this simple case we can see from the URL that the `key` is passed as a query example, so we will start with this approach.  We turn on "Send Query Parameters" and then set each of them by their name and value.  

Once this is configured, you are now ready to run this basic chatbot.  Ask what the weather is like in your home town and watch it at work!

###  Setting the Credentials Outside of Query Parameters

As stated above, it is generally preferrable to set the credentials outside of the workflow itself in the credential manager.  So let's adjust the above workflow and do that.

Let's start by detaching that HTTP Request Tool from the workflow by hitting the trash icon on the arrow connecting the agent to the tool.  Next, create a new HTTP Request Tool and copy in the values for the description in URL from the original one.  

Now, we are going to add authentication.  We know that this particular API wants Query Authentication since the URL was taking it as a query parameter.  So choose "Generic Credential Type" from the dropdown as shown:

<img src="./pics/query_auth1.jpg" width="300">

Next, select "Query Auth" from the dropdown:

<img src="./pics/query_auth2.jpg" width="300">

Then, it will ask you to select which Query Auth you would like to choose, which lists any available from your credentials.  We will be creating a new one, so select "Create new credential."  Here you will get the following screen:

<img src="./pics/query_auth3.jpg" width="300">

Be sure to give this credential a unique name ("Weather Query Auth" in this case).  Then, we know it wants the query parameter called `key` and we copy the actual value of that key into the box.  Then hit save, which saves it to your credentials, allowing you to use it for all future workflows.

Wire this new tool into your workflow and confirm it works as before.