CREATE DATABASE RetailStoreDB;

USE RetailStoreDB;

# SKAPAR KUND TABELE 
CREATE TABLE Customers (
    customer_id INT AUTO_INCREMENT PRIMARY KEY,
    first_name VARCHAR(50) NOT NULL,
    last_name VARCHAR(50) NOT NULL,
    email VARCHAR(100) NOT NULL UNIQUE,
    phone VARCHAR(15) UNIQUE,
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);
# SKAPAR PRODUKT TABELL 
CREATE TABLE Products (
    product_id INT AUTO_INCREMENT PRIMARY KEY,
    name VARCHAR(100) NOT NULL,
    category ENUM('Electronics', 'Clothing', 'Home', 'Beauty', 'Sports') NOT NULL,
    price DECIMAL(10,2) NOT NULL CHECK (price > 0),
    stock_quantity INT NOT NULL CHECK (stock_quantity >= 0)
);
# SKAPAR ORDER TABELL 
CREATE TABLE Orders (
    order_id INT AUTO_INCREMENT PRIMARY KEY,
    customer_id INT NOT NULL,
    order_date DATETIME DEFAULT CURRENT_TIMESTAMP,
    status ENUM('Pending', 'Shipped', 'Delivered', 'Cancelled') DEFAULT 'Pending',
    FOREIGN KEY (customer_id) REFERENCES Customers(customer_id)
);
# SKAPAR ORDERDETALJ TABELL 
CREATE TABLE OrderDetails (
    order_detail_id INT AUTO_INCREMENT PRIMARY KEY,
    order_id INT NOT NULL,
    product_id INT NOT NULL,
    quantity INT NOT NULL CHECK (quantity > 0),
    subtotal DECIMAL(10,2) NOT NULL CHECK (subtotal >= 0),
    FOREIGN KEY (order_id) REFERENCES Orders(order_id),
    FOREIGN KEY (product_id) REFERENCES Products(product_id)
);
# LÄGGER TILL KUNDER 
INSERT INTO Customers (first_name, last_name, email, phone, created_at) VALUES
('John', 'Doe', 'john.doe@email.com', '1234567890', '2024-01-05 10:00:00'),
('Jane', 'Smith', 'jane.smith@email.com', '0987654321', '2024-01-06 14:20:00'),
('Alice', 'Johnson', 'alice.johnson@email.com', '1122334455', '2024-01-07 09:15:00'),
('Bob', 'Brown', 'bob.brown@email.com', '2233445566', '2024-01-08 11:45:00'),
('Charlie', 'Davis', 'charlie.davis@email.com', '3344556677', '2024-01-09 16:30:00');

# Lägger till produkter 
INSERT INTO Products (name, category, price, stock_quantity) VALUES
('Laptop', 'Electronics', 999.99, 50),
('Smartphone', 'Electronics', 599.99, 100),
('T-Shirt', 'Clothing', 19.99, 200),
('Headphones', 'Electronics', 89.99, 150),
('Blender', 'Home', 49.99, 75);

#lägger till ordrar 
INSERT INTO Orders (customer_id, order_date, status) VALUES
(1, '2024-01-05 10:00:00', 'Shipped'),
(2, '2024-01-06 14:20:00', 'Delivered'),
(3, '2024-01-07 09:15:00', 'Pending'),
(4, '2024-01-08 11:45:00', 'Pending'),
(5, '2024-01-09 16:30:00', 'Shipped');

#Lägger till orderdetaljer 
INSERT INTO OrderDetails (order_id, product_id, quantity, subtotal) VALUES
(1, 1, 1, 999.99),
(1, 3, 2, 39.98),
(2, 2, 1, 599.99),
(3, 4, 1, 89.99),
(4, 5, 2, 99.98);





