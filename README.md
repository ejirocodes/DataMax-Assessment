# DataMax frontend Assessment

## Project setup
```
yarn install
```

### Compiles and hot-reloads for development
```
yarn serve
```

### Compiles and minifies for production
```
yarn build
```

### Lints and fixes files
```
yarn lint
```


# How I approached the challenge
## Passively Solving the problem
When I got the email of the technical assessment., within 10 mins, I already mapped out the approach I was going to take in implementing the prototype as well as the technologies and framework to use.

## Actual Implementation
The first thing I did after meticulously going through the assessment instructions was to check out the [Ice and Fire](https://anapioficeandfire.com/Documentation)  API and study how it works. It was a piece of cake because all it required for me to get all books and paginate the data.

The codebase on [GitHub](https://github.com/ejirocodes/DataMax-Assessment) is properly documented with the steps taken to solve the problem

## Error handling
In a case where an error occur, I gracefully handle the situation by displaying a helpful message to the user. Also, if any HTTP error occurs, the user is notified of the error via a toast component and also allow for the user to reload the page by clicking on the try again button (see image below)

![Error toast](./src/assets/error.png)

## Technologies and Framework used
The project was bootstrapped with Vue.js and I choose the Vuetify UI component library because it literally gives me exactly what I needed to build this prototype rapidly.
The built-in JavaScript fetch API was used for API calls in favour of Axios or jQuery to reduce bundle size and improve performance. The prototype was hosted on Netlify because it makes deploying frontend apps fast and it also has a built-in continuous integration system.

## Below are links to the prototype
### View the prototype on [Netlify](https://data-max-assessment-ejiro-asiuwhu.netlify.app)

### View source code on [GitHub](https://github.com/ejirocodes/DataMax-Assessment)
