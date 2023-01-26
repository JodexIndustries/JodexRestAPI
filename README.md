Простой RestAPI для взаимодействия с сервером.

## /api/server
```JSON
{
  "serverOnline":"1",
  "playerList":"_Jodex__",
  "serverUptime":"1h 27s", 
  "worldTimeStatus":"Night",
  "serverTPS":"*20.0"
}
```
## /api/player/NICKNAME
```JSON
{
  "kills":"0",
  "timeDays":"0",
  "timeSeconds":"51",
  "balance":"0.0",
  "mobKills":"2",
  "success":true,
  "timeHours":"6",
  "deaths":"1",
  "timeMinutes":"43"
}

```
## NodeJS Примеры
Пример использования PlayerRequest (node-fetch)

```js
  let url = `http://localhost:8080/api/player/NICKNAME`
  let response;
  try {
  response = await fetch(url, { method: "Get" });
  } catch (err) {
    return console.log('Api сервер не отвечает');
  }
  const json = await response.json();
  //Выводим информацию о игроке в json формате
  console.log(json)
```

 Пример использования PostRequest (node-fetch)
```
  let url = `http://localhost:8080/api/server/command`
  let response;
  const params = new URLSearchParams();
  params.append('command', "Сообщение broadcast");
  try {
     response = await fetch(url, {method: 'POST', body: params});
     //отправляем broadcast сообщение на сервер
    } catch (err) {
    return console.log('Api сервер не отвечает');
  }
```
