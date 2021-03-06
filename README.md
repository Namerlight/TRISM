# Trism - A Catalogue of Educational Materials

#### Project for CSE299 - Junior Design
#### Section 17
#### Faculty: SAS3 

## Group Members:

| | |
|-|-|
| Shadab Hafiz Choudhury | Sarah Suad |
| 1631335042 | 1632282642 |
| shadab.choudhury@northsouth.edu | sarah.suad@northsouth.edu
| | |

## Table of Contents

1. [Project Description](https://github.com/Namerlight/TRISM/#1-Project)
2. [Packages and Libraries](https://github.com/Namerlight/TRISM/#2-Packages-and-Libraries-Used)
3. [Setup Instructions](https://github.com/Namerlight/TRISM/#3-Setup-Instructions)
4. [Project Goals](https://github.com/Namerlight/TRISM/#4-Project-Goals)
5. [Features of the Project](https://github.com/Namerlight/TRISM/#5-Features-of-the-Project)
6. [Features not Implemented](https://github.com/Namerlight/TRISM/#6-Features-not-Implemented)
7. [Possible Future Updates](https://github.com/Namerlight/TRISM/#7-Possible-Future-Updates)
8. [Business Plan](https://github.com/Namerlight/TRISM/#8-Business-Plan)


## 1. Project 

Trism is a catalogue of educational materials that takes inspiration from websites such as IMDB, Goodreads, MyAnimeList or PCPartPicker and lets people compile their own lists of educational materials such as books, videos, online courses and websites, etc. Each list is saved individually and can be used for personal reference or shared with others.

Currently, the website is a work in progress and is being hosted on Google Firebase at the following link:

### [Trism](https://trism-def99.firebaseapp.com/)

## 2. Packages and Libraries Used

- NPM
- NodeJS
- Google Firebase CLI
- Materialize CSS

## 3. Setup Instructions

1. Download and install NodeJS from their [website](https://nodejs.org/en/).
2. Make sure NPM is installed during the NodeJS installation process.
3. Install the Google Firebase CLI
```npm install -g firebase-tools```
After that, log in to your google account, using ```firebase login```
4. If it is necessary to install Materialize CSS, use
```npm install materialize-css@next```
5. In order to run the web page locally, use
```firebase serve```
The default location is https://localhost:5000/
In order to apply changes to online-hosted version, use
```firebase deploy```


## 4. Project Goals
The goal of this project was to create a web app that contains lists of instructional materials. Since this list is hosted online, anyone can access it from any device. This would allow, for instance, teachers to make the list just once, and then share it with students whenever necessary.

## 5. Features of the Project

Features that were implemented in the project include:

#### Interactive Front-End Website
The website is hosted on Google Firebase and used as a front end for the user to visit and interact with, located at [Trism](https://trism-def99.firebaseapp.com/). It is divided into four sections: the landing page, the profile page, the lists and the library. The first four sections were completed and all implemented, while the latter is currently a placebo for possible future development.

The website was created in HTML, CSS and Javascript.  We used Materialize CSS as a CSS framework. The initial setup of the website was based off one of MaterializeCSS's given templates.

#### Back-End Firestore Database
For the needs of a flexible, high speed database suitable for working with in javascript, Firebase Firestore was used. As this database uses the same platform as our web hosting, the integration process was simplified. 

The database is divided into an Users table and a Lists table. The Users table is used for user authentication, registration and logging in, while the lists table contains the names of a list, the owner of the list and a nested table containing the list itself. As the Database is a noSQL DB, it exists entirely as JSON files with no need for SQL.

#### Lists
Users can compile lists of resources they find online and add it to their 'My Lists' tab, found on the user's profile page. Each list is saved into the database using a unique ID. Information such as the name of the resource, resource type, URL and review is taken from the user and added to the database when the 'Add' button is pressed. Users can view and edit compiled lists after they have been created. A unique URL is generated for each list which can be used to develop a 'Share List' feature, in the future.

We used a Materialize modal and forms to build the menu/form for adding a new list in HTML+CSS. Using JS, we added a script in the 'listdb.js' file that reads the input info and uses one of Firebase's built-in functions to update the database. Upon creation of a list, the list name is passed from the 'Profile' page to the 'My Lists' page using a unique URL. The URL of each list can be found on the 'My Lists' tab of the 'Profile' page. In order to update and retrieve data from the database a firebase reference is used. Retrieving data from the database requires the database to be queried using the database reference. A database snapshot is then taken using firebase's built-in function. Each document retrieved from the database, is passed to a 'sortList' function which then sorts data into their respective columns in the HTML table. 

#### User Registration and Log-In
Users can create an account. At this stage, only the email address, password, and a confirming password are needed. Once the user has created an account, they will be automatically logged in. If they already have an account, they can log in with the Log In button, or log out.

Both registration and login forms are placed in modals which can be opened from the navbar at the top. Firebase's built-in authentication functions are used to create and log users in. Logged in users' info can be accessed through firebase's built-in credentials.

#### User Transactions/Subscriptions
In order to gain access to additional features and services, users have the option to subscribe to the website. If the user chooses to subscribe, the date of subscription is saved to the database and a unique ID for each subscription is generated. The unique ID along with date of subscription, can be viewed on the subscriptions tab of the user's profile page. Further development of this feature would allow users to upgrade their account and access exclusive features.

When an user subscribes, the JS script reads their credentials, records the timestamp, then adds those two to a Subscription table in the database. In order to update and retrieve data from the database a firebase reference is used. Retrieving data from the database requires the database to be queried using the database reference. A database snapshot is then taken using firebase's built-in function. Each document retrieved from the database, is passed to a 'sortList' function which then sorts data into their respective columns in the HTML table. Firebase's auto ID feature allows each document to have a unique ID. This ID is used as the transaction/subscription ID. 

## 6. Features not Implemented

Features that could not be implemented due to various restrictions in time, skills or technology include:

#### Web-Scraping from user-entered URLs
While originally planned, webscraping could not be carried out for several reasons. Firstly, webscraping the titles of books from a given URL from Amazon is not possible due to Amazon's bot protection. Using Browser User Agents to bypass it did not work. To carry out webscraping would have required using the AWS API, which is a premium feature. Similar protections existed for other websites such as Udemy, making the webscraping feature highly inconsistent.

#### Tagging and User Suggestions System
As a lot of time was dedicated into setting up the adding-to-lists function, we were unable to actually set up a list of examples in advance. This meant there was no data set to work off to build a suggestions system (which would use simple graphical machine learning models like linear and multivar regression).

#### Deletion of resources from compiled lists
In Firebase, deletion requires additional checks. Due to a lack of time, we did not implement the ability to actually delete an item from a list.

## 7. Possible Future Updates

In addition to all the features not implemented that could be worked on in the future, there are several other future plans:
* Changing Hosting Plan to a different provider or a higher tier of Firebase from the Free Tier.
* Implementing a proper payment system for users who want to donate or recieve additional 'subscriber-only' privileges. We could use a proper payment portal such as Google Pay, Credit Cards or various E-Wallets.
* A Mobile Application that would allow users to take advantage of this website's features in an optimized app (as opposed to the mobile version of a browser page) while on the go.

## 8. Business Plan

We expect there will be lot of traffic from students, teachers and everyone who goes on the internet for academic and learning purposes. Therefore, monetizing the website through advertisements should be straightforward. High traffic would ensure a relatively high number of views and clicks, making it an attractive prospect for those looking to sponsor the website.

Additionally, this website can operate on a subscriber-only model. New users would recieve a 3-month period of free trial, following which they would have to subscribe to the website. Subscription fees can be kept low, ranging from $5-$10 annually depending on userbase demographics. If the subscriber model is too restrictive, we can switch to a freemium model where users can use the website forever but with limitations such as plenty of advertisements or a limit on the number of lists they can create.



