# Weekly Meal Planner - a work in progress
http://linserv1.cims.nyu.edu:31247/

## Overview
Planning meals for the week is a pain, especially figuring out what groceries you need to buy. There's nothing worse than finding a nice easy recipe online but discovering that it's for a serving size of 12 people, then having to spend 9 years figure out how much to scale the recipe down--on the one hand, you don't want to eat the same thing day in and day out, on the other hand, you don't want to spend all that time cooking all that food for just 1 meal. Once you figure out you want to eat the dish only 3 times, now you have to figure out what else to cook and repeat the whole process.

Weekly Meal Planner is a web app that generates an weekly eating plan and a overall shopping list for the week for the user who wants fresh homecooked food but also diversity. Users register and log in before being prompted to enter either links to recipes or manual entry of ingredients. Users can cross out what they have in their pantry already, and then select when during the week they plan to eat each dish, as well as how many people would be eating. It then takes this information and generates a shopping list and the user entered meal plan.

## Data Model
The application will store Users and Weeks. Users contain an array of references to Week objects, and Week contains multiple embedded dishes, which in turn contain multiple embedded ingredients.

Sample User:
```javascript
{
  username: "john123",
  hash: , // a password hash
  weeks: // an array of references to all Week objects
}
```
Sample Week:
```javascript
{
  weekStart: '11/01/2018',
  weekEnd: '11/08/2018',
  dishes: 
  [
    {
      name: "instant ramen",
      serves: 1,
      ingredients:
      [
        {
          name: "instant ramen",
          amt: "1 unit",
          have: false
        },
        {
          name: "hot water",
          amt: "2.5 cups",
          have: true
        }
      ]
    }
  ],
  plan: 
  [
    [{'num':1, 'breakfast':[], 'lunch':[], 'dinner':[dishes[0]]], //monday -> dinner of instant ramen
    [{'num':2, 'breakfast':[], 'lunch':[], 'dinner':[]], 
    [{'num':3, 'breakfast':[], 'lunch':[], 'dinner':[]],
    [{'num':4, 'breakfast':[], 'lunch':[], 'dinner':[]],
    [{'num':5, 'breakfast':[], 'lunch':[], 'dinner':[]],
    [{'num':6, 'breakfast':[], 'lunch':[], 'dinner':[]],
    [{'num':7, 'breakfast':[], 'lunch':[], 'dinner':[]]
  ]
}
```  
## [Schema Draft](src/db.js)

## Wireframes

/ - homepage to view current calendar, view previous calendars, and add dish

![home](documentation/home.png)

/dishes - page to add an existing dish to calendar

![dishes](documentation/dishes.png)

/adddish - page to add a new dish to the week

![adddish](documentation/adddish.png)


## Site map

![sitemap](documentation/site-map.png)

## Use Cases
non-registered users can:
  - register a new account

registered users can:
  - log in to existing account
  - view current week of meals
  - create new week
  - edit existing week
  - add dishes and their ingredients either manually or via link
  - assign dishes to meals throughout the week
  
- unit testing with Jasmine
- Bootstrap
- request + cheerio for recipe parsing
