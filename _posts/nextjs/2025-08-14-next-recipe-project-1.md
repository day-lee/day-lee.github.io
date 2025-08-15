---
title:  "[Next.js] Overview of the recipe project"
excerpt: ""
share: false
categories:
  - nextjs

toc: true
toc_sticky: true
published: true
 
date: 2025-08-14
last_modified_at: 2025-08-14
---

## Goal

Solve the never-ending question of life: **what to eat today?**

## User story

As a recipe project user,

- I want to view, search, and filter a list of recipes

    so that I can browse ideas for today’s meal.
    
- I want to add, edit, and delete recipes
    
    so that I can maintain a collection of my favorite recipes.
    
- I want to add up to three recipes to the meal planner.
    
    so that I can plan my meals for the day.
    
- I want to pick a random recipe
    
    so that I can receive recommendations.
    

(TBC)
- I want to calculate the measurement for multiple people. 
- I want to switch the view from my own recipe project list to shared list so that I can get a new ideas.
- I want to add others recipe into my recipe project so I can check it later.
- I want to add categories such as favourite, cuisine, main ingredients category within my recipe project.
- I want to have ingredient filter so I can choose multiple ingredients that I currently have at home.

## User scenario

- I usually cook for Lunch and Dinner.
- I usually cook for myself one portion for lunch, and two portions for dinner for me and my partner.
- When I choose what to eat for the day, I think of the cuisine first and available ingredients.
- or it can be depending on supermarket offer. if pork is on sale, I just buy one and think of the menu later.
- I mainly make Korean, Western, Chinese, Vietnamese, Thai cuisines.
- I choose the menu on the day, or the day before if I really have a craving for the food.
- For main ingredients, I buy whole chicken, chicken thigh, chicken wings, pork belly, pork shoulder, minced pork, minced beef, fishes, prawns, hamburgers, sausages, eggs, tofu…
- I get the menu ideas while watching tv shows, blog etc. I usually search for the recipe on youtube.
- I usually just choose the top video on the list. The taste of my food is not consistent. I am experimenting my style yet.
- After I made food, if I tried to cook it again as I remembered, I tend to miss certain steps. I want to write down the **tips on somewhere.** → note
- Sometimes, when we have no specific ideas and doesn’t have any ingredients at home, It’s hard to think of what to eat for the day. → ramdom pick

---

## UI

### Main

- recipe list
- search
- hashtag filter
- plan a meal button

### Detail
- recipe detail
- recipe form
- random pick
- meal planner

### Side bar

- create recipe
- meal planner
- random pick
- about

---

## Features

### CRUD

- CRUD recipe
- Like, favourite
- add hashtag: key ingredients, time(roughly within 30 min, 60 mins), type(korean, western)

### Search
- by key ingredient, category

### Filter
- by key ingredient, category

### Meal planning sticky card
- jira sticky style vertical recipe movable card
- challenge: how to reset the data everyday? cronjob?
- future: meal record history

### Random menu choice

(TBC)

### Admin page

### Authentication
- Multiple users can own their recipe project
- select to be public or private
- data structure scalable?
- https://youtu.be/thysQ_FSWfQ?si=YCvmon9bMaifA19g

### Pagination or infinite scrolling

### Measurement conversion
- Selection of 1-10 pax

---

## Tech stacks
- Next.js
- Typescript
- Jest, playwright
- Tailwind
- Supabase 
- Postgresql

