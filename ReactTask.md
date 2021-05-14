### React task

Create a website for task boards management.

As a user you can register with email and password and create a board or open an existing one. 
When the user setups a board user may specify its name and the users, who have access to it (by email). If one of the users with such email doesn’t exist, throw a validation error.
The board is divided into three columns: “TODO”, “In Progress”, “Done”.
Each member of the board can add a task via “+” button in todo column and drag and drop all existing tasks in the different columns. 

Frontend technologies:

React: [Course](https://scrimba.com/learn/learnreact)

Redux: [Tutorial](https://www.valentinog.com/blog/redux/)

Typescript: [Handbook](https://www.typescriptlang.org/docs/handbook), [React with Typescript docs](https://www.typescriptlang.org/docs/handbook/react.html)

Backend technoligies - 
One framework for choice:
Express, Koa, Nest.js

Additional tasks:
(If another user is on the scrum board in the different browser, he sees the changes without a reload. Use websocket protocol for it)
