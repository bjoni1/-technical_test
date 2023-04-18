# Technical test

## Introduction

Fabien just came back from a meeting with an incubator and told them we have a platform “up and running” to monitor people's activities and control the budget for their startups !

All others developers are busy and we need you to deliver the app for tomorrow.
Some bugs are left and we need you to fix those. Don't spend to much time on it.

We need you to follow these steps to understand the app and to fix the bug : 
 - Sign up to the app
 - Create at least 2 others users on people page ( not with signup ) 
 - Edit these profiles and add aditional information 
 - Create a project
 - Input some information about the project
 - Input some activities to track your work in the good project
  
Then, see what happens in the app and fix the bug you found doing that.

## Then
Time to be creative, and efficient. Do what you think would be the best for your product under a short period.

### The goal is to fix at least 3 bugs and implement 1 quick win feature than could help us sell the platform

## Setup api

- cd api
- Run `npm i`
- Run `npm run dev`

## Setup app

- cd app
- Run `npm i`
- Run `npm run dev`

## Finally

Send us the project and answer to those simple questions : 
- What bugs did you find ? How did you solve these and why ? 
- Which feature did you develop and why ? 
- Do you have any feedback about the code / architecture of the project and what was the difficulty you encountered while doing it ? 

____________________________________________________________________________________________________________________
## Run the project
- I changed the frontend port to 3000
- You can run both the api and app components using npm start
## Bugs
- In the singup.js file , the input for the password field wasnt working properly.The problem was that the type of the input wasnt specified -> type="password"

- When i try to update a user information i noticed that i couldnt change the Name field.So i deleted the disabled property of the name input in user/view.js

- When i tried creating a user, i noticed that the form was sending name instead of username so i corrected it in user/list.js

- When i wanted to update the information of a user, i saw that in the Update button was used the onChange hook and thus didnt work. So i changed it to onClick and it works fine

- In the api/controller/user , in the get method by id, i changed from this     const data = await UserObject.find({ _id: req.params.id });
 to this     const data = await UserObject.findOne({ _id: req.params.id });
because i dont want to return an array but a single object

- I removed the disabled property on Name of project input in app/scenes/project/edit

- I fixed the searchbar in the project component

- I created a filter in the project list to see the active and inactive projects
- I found the=at the projectName was displayed as undefined in the scenes/activity.As to fix this issue i simply replaced e.project with e.projectName

## Feature

The only feature i could add for now was the role feature where u have an admin and a user.
The admin would have access to all of the program's feature but the user would have access to a limited number of them.

Here are the steps i followed to do this :

- I added a role attribute to the user model in the API and also in the postUser controller
- I added the role="Admin" in the registration form so that when a new user is registered they will be 'admin' and have access to all the feature. 
This isnt the best practice but only to visaully see the difference in admin and user.

- I added the role="User" in the user addition form.This way the admin can create normal users with limited access.

- I limited the access to the user section, monetary information of projects, and modify project section for the role "Users"

- I also have hidden from the role="Users" the project modifcation feature and deletion feature in activities.
