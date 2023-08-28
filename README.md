# Kafka Notify - A Golang Project for Learning

Kafka Notify is a basic project designed to help you learn the fundamentals of the Go programming language while working with Apache Kafka for event notification. This project aims to provide a simple yet practical example of how to produce and consume messages using Kafka in a Go application.

## Table of Contents

- [Introduction](#introduction)
- [Features](#features)
- [Getting Started](#getting-started)
  - [Prerequisites](#prerequisites)
  - [Installation](#installation)
- [Tools](#tools)
- [Usage](#usage)
  - [Configuration](#configuration)
  - [Producing Messages](#producing-messages)
  - [Consuming Messages](#consuming-messages)
- [Contributing](#contributing)
- [License](#license)

## Introduction

Kafka Notify is designed for those who are new to both the Go programming language and Apache Kafka. This project walks you through the process of setting up a simple messaging system using Kafka, where producers can send messages and consumers can receive and process those messages. By following this project, you'll gain hands-on experience with Go's syntax, Kafka's concepts, and the integration between the two.

## Features

- **Basic Kafka Interaction:** Learn how to set up a connection to a Kafka broker, create a topic, and send/receive messages.
- **Producer Implementation:** Understand how to create a Kafka message producer in Go to publish messages to a topic.
- **Consumer Implementation:** Learn how to create a Kafka message consumer in Go to subscribe to a topic and process incoming messages.
- **Configuration:** Explore how to configure Kafka connection parameters and project settings.
- **Serialization:** Gain insights into message serialization and deserialization using JSON.
- **Error Handling:** Learn about basic error handling strategies in Go.

## Getting Started

### Prerequisites

To get started with Kafka Notify, ensure you have the following installed:

- Go (1.14 or higher)
- Apache Kafka (2.0 or higher) - [Download and Installation Guide](https://kafka.apache.org/downloads)

### Installation

1. Clone this repository to your local machine:

   ```bash
   git clone https://github.com/buzzcoode/kafka-notify.git
  ```

2. Navigate to the project directory:
  ```bash
    cd kafka-notify
  ```
3. Install the required Go dependencies:
  ```bash
    go mod download
  ```

## Tools

This project uses the following tools:

- [Golang](https://golang.org/) for backend development
- [Go-Gin](https://github.com/gin-gonic/gin) for route management
- [Kafka](https://kafka.apache.org/) for event notification

## Usage

1. Start the producer

Open up a terminal, move into the **kafka-notify** directory, and run the producer with the following command:

```bash
  go run cmd/producer/producer.go
```

2. Start the consumer

Open up a second terminal window, navigate to the **kafka-notify** directory, and start the consumer by running:

```bash
  go run cmd/consumer/consumer.go
``` 

3. Sending notifications
With both producer and consumer running, you can simulate sending notifications. Open up a third terminal and use the below **curl** commands to send notifications:

### User 1 (Fernando) receives a notification from User 2 (Júlia):

```bash
  curl -X POST http://localhost:8080/send \
-d "fromID=2&toID=1&message=Júlia started following you."
```
### User 2 (Júlia) receives a notification from User 1 (Fernando):

```bash
  curl -X POST http://localhost:8080/send \
-d "fromID=1&toID=2&message=Fernando mentioned you in a comment: 'Great seeing you yesterday, @Fernando!'"
``` 
### User 1 (Fernando) receives a notification from User 4 (Dedaldino):

```bash
  curl -X POST http://localhost:8080/send \
-d "fromID=4&toID=1&message=Dedaldino liked your post: 'Drink more water!'"
``` 

4. Retrieving notifications

Finally, you can fetch the notifications of a specific user. You can use the below curl commands to fetch notifications:

### Retrieving notifications for User 1 (Fernando):

```bash
  curl http://localhost:8081/notifications/1
```

### Output:
```json
  {"notifications": [{"from": {"id": 2, "name": "Júlia"}, "to": {"id": 1, "name": "Fernando"}, "message": "Júlia started following you."}]}
  {"notifications": [{"from": {"id": 4, "name": "Dedaldino"}, "to": {"id": 1, "name": "Fernando"}, "message": "Dedaldino liked your post: 'Drink more water!'"}]}
```
## Contributing

Contributions to Kafka Notify are welcome! Feel free to open issues or submit pull requests for improvements or fixes. Please follow the existing coding style and guidelines.

---

## License

Kafka Notify is open-source software licensed under the MIT License.