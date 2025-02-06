Dockerized Web Scraper with MySQL Integration using Python

📌 Project Overview

This project demonstrates how to build a Dockerized web scraper using Python that extracts movie quotes from a website and stores them in a MySQL database running in a separate Docker container. The setup ensures seamless communication between containers using a custom Docker network with the bridge driver.

🚀 Features

Web Scraping: Uses requests and BeautifulSoup to extract movie quotes from a website.

MySQL Integration: Stores scraped data in a Dockerized MySQL database.

Containerized Environment: Runs both the scraper and MySQL database in separate Docker containers.

🛠️ Prerequisites

Ensure you have the following installed before running the project:

Docker installed on your machine.

Basic understanding of Docker and Python.

Python dependencies:

requests

BeautifulSoup4

mysql-connector-python

📂 Project Structure

├── scraper.py        # Python script to scrape and store data
├── Dockerfile        # Docker configuration for the scraper
├── requirements.txt  # Python dependencies
├── docker-compose.yml # Docker Compose setup (optional)
└── README.md         # Project documentation

⚙️ Setting Up the MySQL Database Container

Run the following command to create a MySQL container:

docker run -d --name mysql-container -e MYSQL_ROOT_PASSWORD=redhat -e MYSQL_DATABASE=scraper_db -p 3306:3306 mysql:latest

Access the MySQL container:

docker exec -it mysql-container mysql -u root -predhat

Create the quotes table:

USE scraper_db;

CREATE TABLE quotes (
    id INT AUTO_INCREMENT PRIMARY KEY,
    text TEXT NOT NULL,
    author VARCHAR(255) NOT NULL
);

🔧 Running the Web Scraper

Build the Docker Image for the Scraper:

docker build -t scraper-image .

Run the Scraper in a Container:

docker run --rm --name scraper-container --network=bridge scraper-image

🏗️ Using Docker Compose (Optional)

To simplify container management, use Docker Compose:

Start the services:

docker-compose up -d

Stop the services:

docker-compose down

🎯 Conclusion

This project provides a fully containerized web scraping solution using Docker and MySQL. It enables efficient data extraction and storage while maintaining a modular and scalable architecture.




