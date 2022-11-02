## RequestForListOfCats-HTTP
### Description
<a href ="https://raw.githubusercontent.com/netology-code/jd-homeworks/master/http/task1/cats">There is</a> a list of facts about cats. Our task is to make a request to this resource and filter out the facts that no one voted for (the upvotes field).
The format of each entry is as follows:
```json
{
  "id": "5b4910ae0508220014ccfe91",
  "text": "Кошки могуть создавать более 100 разных звуков, тогда как собаки только около 10.",
  "type": "cat",
  "user": "Alex Petrov",
  "upvotes": null
},
```
```text
id - уникальный идентификатор записи
text - сообщение
type - тип животного
user - имя пользователя
upvotes - голоса
```
We need to:
1. Read the entire list and return only those facts for which the upvotes field is not `null'

### Realization
1. Looked at the <a href ="https://raw.githubusercontent.com/netology-code/jd-homeworks/master/http/task1/cats">data</a>
2. Created a `maven`project and add to ```pom.xml``` httpclient library:
```text
<dependency>
   <groupId>org.apache.httpcomponents</groupId>
   <artifactId>httpclient</artifactId>
   <version>4.5.12</version>
</dependency>
```
3. Created httpClient:
```text
CloseableHttpClient httpClient = HttpClientBuilder.create()
    .setDefaultRequestConfig(RequestConfig.custom()
        .setConnectTimeout(5000)    // максимальное время ожидание подключения к серверу
        .setSocketTimeout(30000)    // максимальное время ожидания получения данных
        .setRedirectsEnabled(false) // возможность следовать редиректу в ответе
        .build())
    .build();
```
4. Added the request object ```HttpGet request = new HttpGet("https://raw.githubusercontent.com/netology-code/jd-homeworks/master/http/task1/cats")``` and
called the remote service `CloseableHttpResponse response = httpClient.execute(request)`;
5. Added to pom.xml library for working with json
```text
<dependency>
   <groupId>com.fasterxml.jackson.core</groupId>
   <artifactId>jackson-databind</artifactId>
   <version>2.11.1</version>
</dependency>
```
6. Created a class into which I converted the json response from the server;
7. Converted json to a list of java objects;
8. Filtered the list - using the stream api, using the method ;
9. Displayed the result on the screen.
