          # Описание
          Репозиторий Data-Source-API-Analyst-Test (public) создан c целью продемонстрировать понимание работы REST API, извлечения данных и применения подходов к устранению неполадок("Homework assignment for Data Source API Analyst role.").
          
          # Цели 
          1. Исследовать GitHub API для извлечения данных о публичных репозиториях, коммитах и содержимом.
          2. Подготовить и протестировать отчеты на основе требований клиента.
          3. Создать документацию о порядке и результатах работы.
          
          # Требования клиента
          - Поиск публичных репозиториев.
          - Получение информации о коммитах.
          - Извлечение содержимого репозиториев.
          
          # Дополнительные требования
          Фильтрация репозиториев по требованиям указанным в техническом задании (client requirements).
              Клиент заинтересован в современных трендах с использованием и применением самого популярного языка программирования в области науки о данных и считает, что развитие языка программирования в последние годы тесно переплетается с искусственным интелектом, в связи с чем
              - "Клиент требует актуальные публичные репозитории, количество подписчиков более 20000"
              - "Клиент требует фильтровать коммиты по языку Python, по типу организация,название организации содержит GPT".
              - "Клиент требует отобрать коммиты самого популярного репозитория"
          
          # Структура репозитория
          - Content: файлы, связанные с документацией API, кодом для аутентификации и извлечения данных, руководством по устранению неполадок (auth process, data extraction,rate limits, handling errors, pagination, troubleshooting guide).
          - Postman_сollection: коллекция Postman для тестирования API.
          
          # Использование
          1. перейти на документацию Github API REST (https://docs.github.com/en/rest)
          2. Найти необходимые конечные точки (endpoints) с учетом ТЗ (client requirements):
          - поиск репозиториев: /search/repositories
          - получение коммитов: /repos/{owner}/{repo}/commits
                
          3. Учесть пагинацию, ограничения по запросам к источнику данных и их количество
          4. Получить токен и настроить аутентификацию с помощью токена GitHub.
          (template GITHUB_TOKEN: <token>)
          5. Определить метод GET, переменную  url = https://api.github.com, заголовки, параметры по ТЗ
          Заголовки
          - Authorization: Bearer <token> (для авторизации)
          - X-GitHub-Api-Version: 2022-11-28 (для указания версии)
          - Accept: application/vnd.github+json (для формата данных)
          
	Дополнительные параметры
	- Python
	- 2024
	- public
	- organization	

          (template https://api.github.com/search/repositories?q=language:python&….)
          
          6. Открыть Google colab (https://colab.research.google.com/)
          - создать новый notebook
          - импортировать необходимые библиотеки для Python (requests).
          - сформировать запрос с параметрами
	template: 
	import requests
	response = requests.get(url+'/search/repositories?	q=language:python', headers={'Authorization': f'Bearer {any_token}'})

	if response.status_code == 200:
    		data = response.json()
    		print(data)
	else:
    		print(f'Error: {response.status_code}')
           
          7. Использовать коллекцию Postman для тестирования API.
          - установить/открыть Postman
          - создать коллекцию запросов Github_API_TEST
          	- GET {{url}}/search/repositories
                   - GET {{url}}/repos/{owner}/{repo}/commits
          
          # Результаты
          - Экспортированная коллекция Postman в формате '.json'.
          - Скачанный Jupyter notebook в формате '.ipynb'.
