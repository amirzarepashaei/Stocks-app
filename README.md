# T-Mobile Coding Challenge

### Important! Read this First !

Do **not** submit a pull request to this repository.  You PR wil be rejected and your submission ignored.
To be safe **do not Fork** this repository, if you do you will be tempted to create a PR.

To _properly_ submit a coding challenge you must:

1. Create a blank (empty) repo in the public git service of your choice ( github, gitlab, bitbucket )
2. Clone this repo to your local workstation
3. Reset the remote origin to point to your newly created empty repo
4. Push the master branch up to your repo

5. make necessary changes
6. push changes to your origin
7. send address of your copy to t-mobile.

We will review your copy online before and during your interview.


# Stocks coding challenge

## How to run the application

There are two apps: `stocks` and `stocks-api`.

- `stocks` is the front-end. It uses Angular 7 and Material. You can run this using `yarn serve:stocks`
- `stocks-api` uses Hapi and has a very minimal implementation. You can start the API server with `yarn serve:stocks-api`

A proxy has been set up in `stocks` to proxy calls to `locahost:3333` which is the port that the Hapi server listens on.

> You need to register for a token here: https://iexcloud.io/cloud-login#/register/ Use this token in the `environment.ts` file for the `stocks` app.

> The charting library is the Google charts API: https://developers.google.com/chart/

## Problem statement

[Original problem statement](https://github.com/tmobile/developer-kata/blob/master/puzzles/web-api/stock-broker.md)

### Task 1

Please provide a short code review of the base `master` branch:

#### Task 1-A
1. What is done well?
- I really like the app piping system. The architecture is implemented pretty well. It is organised.

- The implementation of services to fetch data from API and the state manangement is implemented well too.

- Material library is used, which is pretty common practice these days as Google recommends. However, I cannot say this is done well because usage of the libraries is easy but on the otherside dependencies are growing. I would prefer to have lower dependencies on production level applications.

- This appliation is made with Angular 7 and NGRX library. However, using Angular-redux might be a better choice over NGRX.

2. What would you change?
- As it is in the tasks list, I would add accessibility feature to have a universal design.

- Usage of css grid system would be nice in order to have a responsive website. (PS. I donnot like using libraries like Bootstrap - tho I have used it a lot before - but as we have built-in CSS grid system it would be an advantage to use it).

- It is also good to take advantage of CSS pre-processors such as less or alternative.

- Usually in production-level applications, as there might be network delay, the data might show up with delay. It would be beneficial to add some basic animations like a spinner to show the user a process is happening, hence increasing user experience by showing a meaningful action and reducing headache for end users. 


3. Are there any code smells or problematic implementations?
- After using my own API key and using [Redux DevTools Chrome Extension](https://github.com/zalmoxisus/redux-devtools-extension) I can see that data is retrieved but clicking the button is not showing any data. My assumption is that somewhere the data is passed incorrectly which needs to be fixed.

> Make a PR to fix at least one of the issues that you identify

#### Task 1-B

[Accessability](https://www.w3.org/WAI/GL/WCAG20/) is an important feature of all public facing websites.  

> Make a PR to add accessability features to the web application


### Task 2

```
Business requirement: As a user I should be able to type into
the symbol field and make a valid time-frame selection so that
the graph is refreshed automatically without needing to click a button.
```

_**Make a PR from the branch `feat_stock_typeahead` to `master` and provide a code review on this PR**_

> Add comments to the PR. Focus on all items that you can see - this is a hypothetical example but let's treat it as a critical application. Then present these changes as another commit on the PR.

### Task 3

```
Business requirement: As a user I want to choose custom dates
so that I can view the trends within a specific period of time.
```

_**Implement this feature and make a PR from the branch `feat_custom_dates` to `master`.**_

> Use the material date-picker component

> We need two date-pickers: "from" and "to". The date-pickers should not allow selection of dates after the current day. "to" cannot be before "from" (selecting an invalid range should make both dates the same value)

### Task 4

```
Technical requirement: the server `stocks-api` should be used as a proxy
to make calls. Calls should be cached in memory to avoid querying for the
same data. If a query is not in cache we should call-through to the API.
```

_**Implement the solution and make a PR from the branch `feat_proxy_server` to `master`**_

> It is important to get the implementation working before trying to organize and clean it up.
