

##  go-sensordb-svc

### Description

**GoSensorDBSvc** is a non-volatile, in-memory database service written in Go. It leverages Go's powerful concurrency features to manage sensor data efficiently. This project includes a RESTful API to store and retrieve sensor data, making it suitable for high-performance and concurrent data processing applications.

### Features

1. **In-Memory Database**: Designed using Go's map data structure for fast data access.
2. **Concurrency Management**: Implements locking mechanisms to ensure safe concurrent writes.
3. **Channel-Based Data Processing**: Uses Go channels and goroutines to handle data asynchronously.
4. **RESTful API**: Provides endpoints for storing and retrieving sensor data.

### Endpoints

- **POST /api/v1/data**
  - **Description**: Stores sensor data in the in-memory database.
  - **Payload**:
    ```json
    {
      "sensorId": "sd2",
      "data": "anyData"
    }
    ```
  - **Workflow**:
    1. Data is pushed to a channel.
    2. Goroutines read data from the channel and write it into the in-memory database.

- **GET /api/v1/getSensorData**
  - **Description**: Retrieves all stored sensor data.
  - **Response**: Returns a list of all sensor data stored in the database.

### Installation

1. Clone the repository:
   ```sh
   git clone https://github.com/yourusername/GoSensorDBSvc.git
   cd GoSensorDBSvc
   ```

2. Build the project:
   ```sh
   go build
   ```

3. Run the service:
   ```sh
   ./GoSensorDBSvc
   ```

### Usage

- **Store Data**: Use `curl` or any HTTP client to send a POST request to `/api/v1/data` with the required payload.
  ```sh
  curl -X POST http://localhost:8080/api/v1/data -d '{"sensorId":"sd2", "data":"anyData"}' -H "Content-Type: application/json"
  ```

- **Retrieve Data**: Use `curl` or any HTTP client to send a GET request to `/api/v1/getSensorData`.
  ```sh
  curl http://localhost:8080/api/v1/getSensorData
  ```

### Contributing

1. Fork the repository.
2. Create a new branch (`git checkout -b feature-branch`).
3. Make your changes.
4. Commit your changes (`git commit -am 'Add new feature'`).
5. Push to the branch (`git push origin feature-branch`).
6. Create a new Pull Request.



Feel free to adjust the URLs and any other details to fit your specific repository setup.
