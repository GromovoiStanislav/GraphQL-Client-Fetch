# GraphQL client fetch - example

```
// Замените URL на ваш эндпоинт GraphQL
const graphqlEndpoint = 'https://example.com/graphql';

// GraphQL запрос
const graphqlQuery = `
  query {
    // Ваши запрашиваемые поля
    users {
      id
      name
      email
    }
  }
`;

// Опции запроса
const requestOptions = {
  method: 'POST',
  headers: {
    'Content-Type': 'application/json',
    // Дополнительные заголовки, если необходимо
    // Например, авторизационный токен
    // 'Authorization': 'Bearer YOUR_TOKEN',
  },
  body: JSON.stringify({ query: graphqlQuery }),
};

// Выполнение запроса
fetch(graphqlEndpoint, requestOptions)
  .then(response => response.json())
  .then(data => {
    // Обработка ответа от сервера
    console.log(data);
  })
  .catch(error => {
    console.error('Ошибка при выполнении запроса:', error);
  });
```

```
// Замените URL на ваш эндпоинт GraphQL
const graphqlEndpoint = 'https://example.com/graphql';

// GraphQL запрос с переменными
const graphqlQuery = `
  query getUser($userId: ID!) {
    user(id: $userId) {
      id
      name
      email
    }
  }
`;

// Переменные для запроса
const variables = {
  userId: '12345', // Замените на значение ID, которое хотите запросить
};

// Опции запроса
const requestOptions = {
  method: 'POST',
  headers: {
    'Content-Type': 'application/json',
    // Дополнительные заголовки, если необходимо
    // Например, авторизационный токен
    // 'Authorization': 'Bearer YOUR_TOKEN',
  },
  body: JSON.stringify({
    query: graphqlQuery,
    variables: variables,
  }),
};

// Выполнение запроса
fetch(graphqlEndpoint, requestOptions)
  .then(response => response.json())
  .then(data => {
    // Обработка ответа от сервера
    console.log(data);
  })
  .catch(error => {
    console.error('Ошибка при выполнении запроса:', error);
  });
```
