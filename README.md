
# Javascript Interpreting Twitch Bot

## Mission

To collaboratively write a Twitch IRC Bot in NodeJS that is capable of interpreting javascript in the Twitch chat. 

## Instructions

Clone this repository to your computer. Create a code branch using `git branch yourbranchhere`. Commit code to your branch until you have a feasible solution for the bounty. Push your branch to GitHub and create a pull request on github.com. I will do a code review with you, and we'll merge your code into the main branch.

Once all bounties are complete, the Twitch Bot will be ready to deploy!

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
    - Write a `exportSession` function that creates/updates local files based on a given Twitch username
        - Create a folder named by the twitch username, if it doesn't already exists
        - Create a script.js file in that folder, if it doesn't already exist
            - Grab the Array of js expressions the Twitch user has entered so far.
            - Write those expressions as lines of JS in script.js
        - Create a README.md file in that folder, if it doesn't already exist
            - Write lines of text to this file that provide instructions on how to run the script.js file

- :hourglass: Bounty #8 (easy, and involves coordinating with Adam)
    - Build out the logic within the "if message is !code" block
        - Use the `exportSession` function from Bounty #7
        - Reply in the Twitch chat with a GitHub url where the user can access their code
            - Ask me about what GitHub url to use, I'll write another program that auto-pushes these exported sessions to GitHub

- :hourglass: Bounty #9 (due diligence)
    - Update this README with better, more useful information. 
    - Emulate the README formatting of other popular Github repositories

    


