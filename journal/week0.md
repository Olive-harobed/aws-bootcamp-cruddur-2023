# Week 0 — Billing and Architecture

## Conceptual diagram using Lucid Charts
![image](https://user-images.githubusercontent.com/79452458/230979812-7d4918f2-ac6f-449e-866a-f262874569a9.png)
![Cruddr conceptual diagram](https://lucid.app/lucidchart/882e70c1-9f93-467d-9dc8-257d9efd194e/edit?view_items=vskMEq663eXG&invitationId=inv_c395a0d7-f3f9-47e5-8f26-8ab75c5a3c3d "Cruddr conceptual diagram")

## Logical diagram using Lucid Charts
![image](https://user-images.githubusercontent.com/79452458/230980563-0c049ab8-223d-4d8f-befd-9b4cbfd52455.png)
![Cruddr logical diagram](https://lucid.app/lucidchart/52fba20f-12ee-4d5d-835e-d3a8cf4b7787/edit?viewport_loc=-2109%2C-130%2C3192%2C1641%2C0_0&invitationId=inv_07e20d1c-d4a9-4487-98ab-7695ca161cfd "Cruddr logical diagram")

## Installed AWS CLI

## Create Billing Alarm
The budget was created using the alarm.json in the aws/json folder and running the following command:
``aws sns create-topic --name billing-alarm``
This creates sns topic arn as output.

``aws sns subscribe \
    --topic-arn="output of the previous command" \
    --protocol=email \
    --notification-endpoint="dewgodswill@gmail.com
``
![image](https://user-images.githubusercontent.com/79452458/230982674-336899d1-832d-45c9-a9b3-5a34913f04a4.png)

## Create a Budget
The budget was created using the budget.json and notifications-with-subscribers.json in the aws/json folder and running the following command:

``aws budgets create-budget \
    --account-id XXXXXXXXXXXXX \
    --budget file://aws/json/budget.json \
    --notifications-with-subscribers file://aws/json/notifications-with-subscribers.json
``    
![image](https://user-images.githubusercontent.com/79452458/230982249-ad1da6b8-2606-4290-ab5d-f9552a2109de.png)
