import json
from itertools import count

with open("orders_july_2023.json", "r") as my_file:
    orders = json.load(my_file)

max_price = 0
max_order = ''
for order_num, orders_data in orders.items():
    price = orders_data['price']
    if price > max_price:
        max_order = order_num
        max_price = price
print(f'Номер заказа с самой большой стоимостью: {max_order}, стоимость заказа: {max_price}')

max_quantity = 0
max_order = ''
for order_num, orders_data in orders.items():
    quantity = orders_data['quantity']
    if quantity > max_quantity:
        max_order = order_num
        max_quantity = quantity
print(f'Номер заказа с самым большим количеством товаров: {max_order}, количество товаров: {max_quantity}')

max_quantity = 0
max_date = ''
for order_num, orders_data in orders.items():
    date = orders_data['date']
    if date > max_date:
        max_date = date
        len(orders_data)
print(f'В этот день в июле: {max_date}, было сделано больше всего заказов, а именно {len(orders_data)}')

max_order = 0
user_dict = {}
for order_num, orders_data in orders.items():
    user_id = orders_data['user_id']
    user_dict[user_id] = user_dict.get(user_id, 0) + 1
    orders_2 = user_dict.get(user_id)
    if orders_2 > max_order:
        max_orders = orders_2
print(f'Самое большое количество заказов сделал пользователь: {user_id}, количество заказов: {max_orders}')

max_price = 0
user_dict = {}
for order_num, orders_data in orders.items():
    user_id = orders_data['user_id']
    user_dict[user_id] = user_dict.get(user_id, 0) + 1
    orders_2 = user_dict.get(user_id)
    if orders_2 > max_price:
        max_price = price
print(f'У данного пользователя: {user_id}, самая большая суммарная стоимость заказа, стоимость заказа: {max_price}')

price_sum = 0
price_count = 0
for order_num, orders_data in orders.items():
    price_sum += orders_data['price']
    price_count = len(orders)
print(f'Средняя стоимость заказа: {price_sum//price_count}')

sum_all = 0
count = 0
for order, data in orders.items():
    sum_all += data['price']
    count += data['quantity']
print(f'Средняя стоимость товаров: {sum_all/count:.3}')
