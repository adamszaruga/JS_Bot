
# Javascript Interpreting Twitch Bot

## Mission

To collaboratively write a Twitch IRC Bot in NodeJS that is capable of interpreting javascript in the Twitch chat. 

## Instructions

Clone this repository to your computer. Create a code branch using `git branch yourbranchhere`. Commit code to your branch until you have a feasible solution for the bounty. Push your branch to GitHub and create a pull request on github.com. I will do a code review with you, and we'll merge your code into the main branch.

Once all bounties are complete, the Twitch Bot will be ready to deploy!

## Gameplan

The below pseudo-code roughly describes how our twitch bot should behave:

```
Javascript Interpereting Twitch Bot

Goal: Write a twitch bot that will let viewers run javascript in the chat

Global Variables - 
	userExpressionMap - An Object that maps twitch user names to an Array of Javascript Expressions

When a Twitch viewer writes a message in chat:

	First, parse the message to see if it's valid JavaScript
		
	if the message is valid JS:

		Add the message to the Array in userExpressionMap for the given twitch user

		Use safe-eval to evaluate all the expressions in the array, in order

			If an expression creates/uses variables, update safe-eval's context object
			
			Pass the context object to the next safe-eval call

		TwitchBot responds with the last evaluated value from safe-eval
		
	else if the message is the !undo command:

		Pop last element from the Array in userExpressionMap for the given twitch user

	else if the message is the !code command:

		If it doesn't exist already, create a folder for that user

		Create a script.js file in that folder

		Create a README.md file in that folder

		Find the expression Array for the given Twitch User and write it to the script.js file

		Write a neatly formatted set of instructions for running the code in README.md

		Trigger a push to GitHub

		TwitchBot responds with a link to the code we just published
```

## Bounties

- :hourglass: Bounty #1 (easy)
    - Remove all the irrelevant boilerplate code from the example twitch bot code.

- :hourglass: Bounty #2 (mostly straightforward)
    - Set up the main if-else logic within the 'chat' event callback

- :hourglass: Bounty #3 (easy)
    - Define a global variable that we'll use to map Twitch usernames to an array of JS messages (strings)

- :hourglass: Bounty #4 (kind of involved)
    - Write a `parseMessage` function that interprets a chat message and categorizes 
        - if the message begins with a `!undo` or `!code`, return `'UNDO'` and `'CODE'` respectively
        - if the message is executable javascript, return `'JS'`
            - use safe-eval to determine if the message is JS
        - Otherwise, don't return anything (or return `undefined`)

- :hourglass: Bounty #5 (pretty tough)
    - Build out the logic within the "if message is javascript" block
        - Grab the Array of js expressions the Twitch user has entered so far
        - Loop through the expression Array
            - Use safe-eval to run the current expression
            - If the current expression begins with a variable declaration or assignment, create/update a `context` Object to pass into the next safe-eval call
        - Try to run the message with safe-eval, passing in the final `context` object
            - If it throws an error, reply in the Twitch chat with the error message. 
            - If it returns a value, reply in the Twitch chat with that value.toString()
            - Use `@username` to tag the person who typed the Javascript.
        

- :hourglass: Bounty #6 (not too bad)
    - Build out the logic within the "if message is !undo" block
        - Grab the Array of js expressions the Twitch user has entered so far.
        - If the array exists and isn't empty, remove the last element

- :hourglass: Bounty #7 (involves learning new things in NodeJS)
    - Write a `exportSession` function that creates a Github Gist based on a given Twitch username
        - Use the Github API to create a new Gist
            - The Gist should contain the code in the twitch user's expression Array
            - Include a comment block at the top that explains how to run the javascript code
        - Return a url to the gist

- :hourglass: Bounty #8 (involves getting carried by Bounty #7  )
    - Build out the logic within the "if message is !code" block
        - Use the `exportSession` function from Bounty #7
        - Reply in the Twitch chat with a link to the user's generated Github Gist
        - Use `@username` to tag the person who typed the !code command
            

- :hourglass: Bounty #9 (due diligence)
    - Update this README with better, more useful information. 
    - Emulate the README formatting of other popular Github repositories

    


