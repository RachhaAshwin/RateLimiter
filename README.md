# RateLimiter
A rate limiter is a mechanism that is used to control the rate at which a user or an application can access an API or a service. In simpler terms, it limits the number of requests that can be made in a given time interval.

The implementation consists of several files and directories:

main.go is the main entry point for the program, it initializes a new gin router and calls a function to initialize the routes for the application.

middleware/middleware.go is the middleware code for the gin router that implements the rate limiter functionality. It uses a token bucket algorithm to limit the number of requests made by a user or an application. The GetClientIdentifier function is used to generate a unique identifier for each request and is used as a key to lookup the token bucket. The RateLimit function is called for each incoming request and checks if the request is allowed or not based on the rules defined in rules/rules.go.

bucket/tokenBucket.go contains the implementation of the token bucket algorithm used by the middleware to rate limit incoming requests.

rules/rules.go contains the configuration for the rate limiter. The rules define the maximum number of tokens and the rate at which the tokens are refilled.

init.go contains the implementation for initializing the token bucket map used by the middleware to store the token bucket for each unique identifier.

The basic idea is that when a request comes in, the middleware generates a unique identifier for that request and uses it to look up the token bucket. The token bucket is then checked to see if the request can be allowed or not. If the bucket has enough tokens, the request is allowed and the tokens are deducted from the bucket. If the bucket does not have enough tokens, the request is rejected with a "Too Many Requests" error message.

This rate limiter can be used to prevent abuse of an API or a service by limiting the number of requests that can be made in a given time interval.
