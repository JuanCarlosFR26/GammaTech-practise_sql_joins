# Soluciones de los ejercicios

## Ejercicio 1
SELECT color, SUM(quantity) AS total_quantity
FROM shirts s
INNER JOIN bills  b
ON b.product_id = s.shirt_id
GROUP BY color;
## Ejercicio 2
SELECT color, SUM(quantity) AS total_quantity, SUM(quantity * price) AS total_price
FROM shirts
INNER JOIN bills ON bills.product_id = shirts.shirt_id GROUP BY color;

## Ejercicio 3
SELECT name, SUM(quantity) AS total_sales
FROM dealers d
INNER JOIN bills b
ON b.dealer_id = d.dealer_id
GROUP BY name;


## Ejercicio 4
SELECT name, SUM(quantity) AS total_sales, SUM(quantity * price) AS total_price
FROM dealers d
INNER JOIN bills b
ON b.dealer_id = d.dealer_id
INNER JOIN shirts s
ON b.product_id = s.shirt_id
GROUP BY name;


## Ejercicio 5
SELECT name, SUM(quantity) AS total_sales, SUM(quantity * price) AS total_price
FROM dealers d
INNER JOIN bills b
ON b.dealer_id = d.dealer_id
INNER JOIN shirts s
ON b.product_id = s.shirt_id
WHERE name = 'Blondy Lacelett'
GROUP BY name;

## Ejercicio 6
SELECT d.name, SUM(quantity) AS total_sales, SUM(quantity * price) AS total_profits
FROM departments d
INNER JOIN dealers
ON d.department_id = dealers.department_id
INNER JOIN bills b
ON b.dealer_id = dealers.dealer_id
INNER JOIN shirts s
ON s.shirt_id = b.product_id
GROUP BY d.name;

## Ejercicio 7
SELECT d.name, SUM(quantity) AS total_sales, SUM(quantity * price) AS total_profits
FROM departments d
INNER JOIN dealers 
ON d.department_id = dealers.department_id
INNER JOIN bills b
ON b.dealer_id = dealers.dealer_id
INNER JOIN shirts s
ON s.shirt_id = b.product_id
WHERE b.date >= '2023-06-01' AND b.date <= '2023-06-15'
GROUP BY d.name;

## Ejercicio 8
SELECT color, SUM(quantity) AS total_sales, price
FROM shirts s
INNER JOIN bills b
ON s.shirt_id = b.product_id
WHERE b.date <= '2023-06-30' AND b.date >= '2023-06-21'
GROUP BY color, price;


## Ejercicio 9
SELECT color, SUM(quantity) AS total_sales, d.name
FROM shirts s
INNER JOIN bills b
ON s.shirt_id = b.product_id
INNER JOIN dealers
ON dealers.dealer_id = b.dealer_id
INNER JOIN departments d
ON d.department_id = dealers.department_id
WHERE d.name = 'North'
GROUP BY color, d.name;

## Ejercicio 10
SELECT d.name department_name, COUNT(bill_id)
FROM bills b
INNER JOIN dealers 
ON dealers.dealer_id = b.dealer_id
INNER JOIN departments d
ON d.department_id = dealers.department_id
WHERE d.name = 'South'
GROUP BY d.name;