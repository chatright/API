# Chat Right
## The Ultimate AI Chatbot and Assistant for Republicans, Conservatives and Christians

**Documentation for the Chat Right API for Developers.** 

*NOTE: The API is not available to the public yet.*

# Chat Right API Documentation

The Chat Right API allows you to integrate the power of the Chat Right's Abraham language model into your applications, products, or services. With the Chat Right API, you can interact with the language model to generate human-like text responses, answer questions, assist with tasks, and much more.

This document will guide you through the various aspects of working with the Chat Right API, including authentication, making API requests, and understanding the response format. Let's get started!

## API Authentication

To use the Chat Right API, you need an API key. Please contact the Chat Right team or refer to the Chat Right website to obtain your API key. Once you have your API key, you need to include it in the headers of your API requests using the following format:

```
Authorization: Bearer YOUR_API_KEY
```

## Making API Requests

The Chat Right API provides a single endpoint for interacting with the Abraham language model. The endpoint URL is:

```
https://www.chatright.app/action/completions/v/1
```

To make an API request, send a POST request to the endpoint URL mentioned above. The request body should be in JSON format and include the following parameters:

- **prompt** (required): The input text or prompt for the language model. This text provides context and instructions for generating the desired response.
- **max_tokens** (optional): The maximum number of tokens the generated response should contain. By default, this value is set to 512. Adjusting this parameter can control the length of the generated response.
- **temperature** (optional): The temperature parameter determines the randomness of the generated output. Higher values (e.g., 0.8) produce more random responses, while lower values (e.g., 0.2) generate more focused and deterministic responses. The default value is 0.8.
- **stop_sequence** (optional): The stop sequence is an optional string that can be used to indicate when the generated response should end. If included, the model will stop generating text once the stop sequence is encountered.

Here's an example of a minimal API request:

```json
POST /action/completions/v/1
Host: www.chatright.app
Authorization: Bearer YOUR_API_KEY
Content-Type: application/json

{
  "prompt": "Hello,",
  "max_tokens": 64
}
```

## API Response

The API response will be in JSON format and will contain the generated output from the language model. The response will include the following fields:

- **id**: The unique identifier of the API request.
- **object**: The object type, which is always set to "text_completion".
- **created**: The timestamp indicating when the API request was created.
- **model**: The version and details of the Chat Right's Abraham language model.
- **choices**: An array containing the generated completion(s). Each choice has the following fields:
  - **text**: The generated text response.
  - **finish_reason**: The reason why the response generation ended. Common values include "stop_sequence", "max_tokens", and "temperature".
  - **index**: The index of the generated completion in the response.
  - **logprobs**: Log probabilities assigned to each token in the generated completion.

Here's an example of a sample API response:

```json
{
  "id": "unique-request-id",
  "object": "text_completion",
  "created": 1657864938,
  "model": "abraham-1.0",
  "choices": [
    {
      "text": "Hello, how can I assist you today?",
      "finish_reason": "stop_sequence",
      "index": 0,
      "logprobs": null
    }
  ]
}
```

## Error Handling

If there is an error with your API request, the server will respond with an appropriate HTTP status code along with an error message in the response body. Common error codes include:

- **400 Bad Request**: Indicates a problem with the request parameters or JSON format.
- **401 Unauthorized**: Indicates an authentication failure due to an invalid API key.
- **429 Too Many Requests**: Indicates that you have exceeded your API rate limit.

Please refer to the HTTP status code and the error message in the response to troubleshoot and resolve any issues with your API requests.

## That's it!

Congratulations! You are now equipped with the necessary information to integrate the Chat Right API into your applications. Experiment with different prompts, parameters, and techniques to make the most of the Chat Right's Abraham language model. If you have any questions or need further assistance, please reach out to the Chat Right team.

Happy coding!
