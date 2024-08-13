# Food Ordering System
This project implements a distributed food ordering system using Kafka as the central data pipeline. The system components are divided into multiple backends that handle different aspects of the order lifecycle.

## Architecture Overview
- Food Ordering Client: The frontend interface where customers place their food orders.
- Orders Backend: Handles incoming orders from the Food Ordering Client and publishes order details to the Kafka topic order_details.
- Kafka (Data Pipeline): A central messaging system that facilitates communication between different components of the system. It includes:
   - order_details topic: Receives new order details from the Orders Backend.
   - order_confirmed topic: Used by other services to confirm and process orders.
- Transactions Backend: Listens to the order_details topic, processes transactions, and publishes confirmed orders to the order_confirmed topic.
- Analytics Backend: Consumes messages from the order_confirmed topic to update and monitor real-time analytics such as total orders and revenue.
- Email Backend: Reads from the order_confirmed topic to send confirmation emails to customers after their orders are processed.

## Project Structure
- orders_backend.py: Handles order intake and publishes to Kafka.
- transactions_backend.py: Processes transactions and confirms orders.
- analytics_backend.py: Tracks real-time metrics.
- email_backend.py: Sends email confirmations.

## Project Diagram 
![img](https://github.com/user-attachments/assets/627044b0-9626-4907-810e-e6abb057448f)
