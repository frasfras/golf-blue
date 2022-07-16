# golf-blue
sustainability in golf a golf-related app idea using airtable stepzen

<h2>Getting Started</h2>

Step by step 

<h2>Building  From source github</h2>
git clone https://github.com/frasfras/golf-blue.git

cd golf-blue

npm install

npm run serve

app running at 
Local:   http://localhost:8081/

<h3> Stepzen CLI - Create GraphQL Api </h3>

cd documents &&  mkdir stepdoc

after login ,import REST api  in terminal :

stepzen import curl  https://api.airtable.com/v0/appneKtre6Ux4ESiq/waterplan   -H "Authorization: Bearer apikey" --query-name queryWaterplan --query-type Airtable

stepzen import graphql  

endpoint url:  https://api.baseql.com/airtable/graphql/appneKtre6Ux4E

header:'Content-Type': 'application/json'

Your API url is  https://shima.stepzen.net/api/airtable/__graphql


<h3> Vue CLI - Creating the Project </h3>

  setting up a vue App

 npm install -g @vue/cli

 vue create app-name

 select 'Manually . . '   then select  Router and Vuex

 and Choose Vue. version 3

 say Yes to Use History mode

  On Lint  choose Eslint plus prettier , Lint on save

  On place the config , select dedicated files or package,json

  saves preset as no.

  cd app-name

  npm run serve
