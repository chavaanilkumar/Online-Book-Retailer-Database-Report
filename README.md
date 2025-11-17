Online Book Retailer Database
This project is a normalized relational database designed to simulate the data management system for an Online Book Retailer. Developed as a comprehensive SQL solution, its primary goal is to efficiently manage customer, product inventory, and transaction information.

The database was populated with realistic, randomly generated data, exceeding the minimum requirements with 1201 total orders.

***Features
Customer Management: Stores and uniquely identifies customer records.

Product Inventory: Tracks book details, including price and optional ratings.

Order Tracking: Records individual transactions, linking customers to products and logging the purchase quantity and timestamp.

Enforced Integrity: Uses UNIQUE, NOT NULL, and CHECK constraints to maintain high data quality and prevent illogical entries.

GDPR Compliance Support: Designed with Data Minimization and Right to Erasure principles in mind.

*** Technologies
Database Management System: SQLite

Data Generation Script: Python (using the sqlite3 and Faker library with UK locale en_GB)

*** Database Schema
The database employs a three-table normalized schema. | Table | Primary Key (PK) | Foreign Key (FK) | Key Columns | | :--- | :--- | :--- | :--- | | Customers | customer_id | - | customer_name, customer_email (UNIQUE, NOT NULL), customer_country | | Products | product_id | - | product_name, product_price, product_rating (allows NULL) | | Orders | order_id | customer_id, product_id | order_quantity (CHECK > 0), order_timestamp |

Constraints and Integrity Highlights
Uniqueness: customer_email is enforced as UNIQUE and NOT NULL for reliable customer identification.

Business Logic: A CHECK(order_quantity > 0) constraint prevents the recording of orders with illogical or zero quantities.

Realism: The product_rating column was intentionally set to NULL for approximately 50% of the products, mimicking the real-world scenario where not all products receive a review.

*** Ethical and Data Privacy Discussion
In the design and data generation for this database, ethical considerations for data handling were a priority:

Data Minimization: The database avoids storing highly sensitive Personally Identifiable Information (PII) like complete home addresses or payment details. It focuses only on the minimum required information (name and email) for order processing.

Segregation: PII (in the Customers table) is separated from the behavioral transaction data (in the Orders table) to allow for analysis with an added layer of privacy.

Right to Erasure (GDPR): The customer_id foreign key in the Orders table is configured with an ON DELETE CASCADE action. This directly supports a "right to be forgotten" implementation, as deleting a customer record automatically removes all their associated transaction history, ensuring complete data removal upon request.

***Getting Started
The database creation script and generation methodology are fully documented in the provided Colab notebook.

Code Appendix Link: https://colab.research.google.com/drive/1LEPiLj2hxiNWhyXosfw6LLrEr1CPkq5p#scrollTo=OmegoidIY_s8
