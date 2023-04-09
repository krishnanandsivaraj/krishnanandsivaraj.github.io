---
title: Some Learnings on types
author: Krishnanand Sivaraj
date: 2023-04-09 00:55:00 +0800
categories: [typescript, refactoring]
tags: [typescript]
pin: false
---

## Playing with custom types

Apart from the primitive types offered by types, we have the flexibility to create our own types in TS.  While it has its benefits I found out few concepts that will better our usage.

**Use custom types wisely with optional and never types**
While developing applications that use Typescript it is mostly essential to perform database queries or parse external api.
> The result of these operations are either a success or an error.

```typescript
function getApiResponse() : Response | null {
		try {
			// code block to call an api and get response
			return response;
		} catch (ex) {
			// throw exception or log exception
		}
}
```
The above is just an example.  While it is certain that we pass the response on success, sometimes a) the response might be empty or b) throws an error that results in no response.  Here is a simple way to refactor this scenario

```typescript
type Response {
		status: '200' | '400' | '204',
		data?: object,
		error?: object
	}

let response: Response;
function getApiResponse() : Response {
		try {
			
			response.data = // code block to call an api and get response
			response.status = response.data ? 204 : 200;
		} catch (ex) {
			// throw or log exception
		}
		return response;
}
```

In the above snippet we have a strong validation for the status codes.  Even thought the example above has improved, we can still refactor such scenarios like this

```
type Response {
	status: '200' | '204',
	data: object
} | {
	status: '400' | '500' | '404',
	error: object
}


let response: Response;
function getApiResponse() : Response {
		try {
			
			response.data = // code block to call an api and get response
			response.status = response.data ? 204 : 200;
		} catch (ex) {
			// throw or log exception
		}
		return response;
}
```

or this can also be like below with `never` type.  **never** prevents us from using improper usage of types.

```typescript
type Response {
	status: '200' | '204',
	data: object,
	error: never
} | {
	status: '400' | '500' | '404',
	error: object,
	data: never
}


let response: Response;
function getApiResponse() : Response {
		try {
			
			response.data = // code block to call an api and get response
			response.status = response.data ? 204 : 200;
		} catch (ex) {
			// throw or log exception
		}
		return response;
}
```



