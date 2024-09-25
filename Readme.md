# Mission 3

## Part 0,1,2

[Link to video] 
Ссылка на видео: https://disk.yandex.ru/i/um81pcnCOUzd8A
Ссылки endpoint url: 
1) https://qwjcps.buildship.run/me
2) https://qwjcps.buildship.run/message


## Part 3

``` sql 1 получить список юзернеймов пользователей
SELECT username 
FROM users;
```

``` sql 2 получить кол-во отправленных сообщений каждым пользователем: username - number of sent messages
SELECT u.username, COUNT(m.id) AS sent_messages 
FROM users u 
LEFT JOIN messages m ON u.id = m.from 
GROUP BY u.username;
```

``` sql 3 Получить пользователя с самым большим кол-вом полученных сообщений и само количество username - number of received messages
Copy code
SELECT u.username, COUNT(m.id) AS received_messages 
FROM users u LEFT JOIN messages m ON u.id = m.to 
GROUP BY u.username 
ORDER BY received_messages 
DESC LIMIT 1;
```

``` sql 4 Получить среднее кол-во сообщений, отправленное каждым пользователем
SELECT AVG(sent_message_count) AS avg_sent_messages 
FROM ( SELECT COUNT(m.id) AS sent_message_count FROM users u 
LEFT JOIN messages m ON u.id = m.from 
GROUP BY u.id ) 
AS user_sent_messages;
```

