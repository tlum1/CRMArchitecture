# Authorization REST API

POST /register

{
    email, phone, name, role
}

Response:
- 201, {id}
- 400
- 500

{
    error_message: $message
}

POST /login

{
    login,
    password
}

Response:
- 200, {token, expiration}
- 400
- 500

{
    error_message: $message
}

# User REST API

## Example of getting user data from table MoneyFlowBudget, for other strctures the same.

GET /MoneyFlowBudget

Header:
- x-auth-token: $token

- 200
- 401 (access denied)
- 500
- 400

{
    MoneyFlowBudget: [
        {
            id: 1,
            moneyflowbudget: {
                name
            },
            timestamp,
            items: [
                {
                    name, FromDate, ToDate, Project, Currency, Description
                }
            ]
        }
    ],

    page_index: 0,
    page_count: 10
}



GET /MoneyFlowBudget/${id}

Header:
- x-auth-token: $token

- 200
- 401 (access denied)
- 500
- 400

{
    MoneyFlowBudget: [
        {
            id: 1,
            moneyflowbudget: {
                name
            },
            timestamp,
            items: [
                {
                    name, FromDate, ToDate, Project, Currency, Description
                }
            ]
        }
    ],

}


GraphQL


POST /MoneyFlowBudget

{
    Name,
    User,
    FromDate,
    ToDate,
    Project,
    Currency,
    Description
}

Response:

OK
{
  id
}

---



RabbitMQ queue schema (logitics)

- Queue (producer, consumer)
- Fanout (?)
- 1 queue - 1 data type (model)
- EMAIL_SENDING_QUEUE, EMAIL_SENDING_QUEUE_V2
- RabbitMQ cookbook, RabbitMQ best practices