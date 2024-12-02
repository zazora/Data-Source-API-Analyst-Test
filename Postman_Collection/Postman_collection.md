запросы в Postman
- создать коллекцию  Data-Source-API-Analyst-Test
- создать переменные в коллекции:
url = https://api.github.com
token=******

- создать запросы searchRepositories, searchCommits, соответственно
             - GET {{url}}/search/repositories
-в первом запросе
установить параметр q=GPT+in:name+language:Python+followers:>20000
итоговый запрос {{url}}/search/repositories?q=GPT+in:name+language:Python+followers:>20000&sort=stars&order=desc&per_page=10
установить дополнительные параметры sort:stars & order:desc
во вкладке scripts/Post-response прописать java script код для получения тела запроса и извлечения данных в переменные "owner" и "repo" для добавления из в переменные коллекции и включения во второй запрос
let data= pm.response.json()['items'];
pm.collectionVariables.set("repo", data[0]["name"]);
pm.collectionVariables.set("owner", data[0].owner.login);

              - GET {{url}}/repos/{{owner}}/{{repo}}/commits
-в обоих запросах установить параметр per_page 10
-запустить коллекцию
