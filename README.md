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

<h2> Stepzen CLI - Create GraphQL Api </h2>

cd documents &&  mkdir stepdoc

after login ,import REST api  in terminal :

stepzen import curl  https://api.airtable.com/v0/appneKtre6Ux4ESiq/waterplan   -H "Authorization: Bearer apikey" --query-name queryWaterplan --query-type Airtable

stepzen import graphql  

endpoint url:  https://api.baseql.com/airtable/graphql/appneKtre6Ux4E

header:'Content-Type': 'application/json'

Your API url is  https://shima.stepzen.net/api/airtable/__graphql

Type  stepzen start
![Screen Shot 2022-07-16 at 9 14 40 PM](https://user-images.githubusercontent.com/65541080/179356030-f666f9a9-323b-4a4a-b783-e224b2c40ef2.png)


<h2> Vue CLI - Creating the Project </h2>

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
