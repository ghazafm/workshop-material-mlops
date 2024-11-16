Here’s an updated **README.md** file to match your scenario, where MLflow is run directly in a Docker container:

---

# MLflow Logging Example

This project demonstrates how to run an MLflow server using Docker and perform simple logging with MLflow through a Python script or Jupyter Notebook. You can log parameters, metrics, and artifacts and explore the results in the MLflow UI.

---

## Prerequisites

1. **Docker** installed on your system.
2. Basic familiarity with MLflow (optional).

---

## Getting Started

### Step 1: Build the Docker Image

1. Clone or download this repository to your local machine.
2. Open a terminal and navigate to the project directory.
3. Build the Docker image using the following command:
   ```bash
   docker build -t mlflow-server .
   ```

### Step 2: Run the MLflow Server in a Container

Start the MLflow server using the following command:
```bash
docker run -it --rm -p 5000:5000 -h 0.0.0.0 mlflow-server
```

- `run`: Command to run docker image.
- `-it`: Run your container interactively.
- `-rm`: Auto remove container after you turn off it.
- `-p 5000:5000`: Maps port 5000 from the container to your machine for the MLflow UI.
- `-h 0.0.0.0`: Maps ip 0.0.0.0 (default) for the container service.
- `0mlflow-server`: Your image name.

After running this command, the MLflow server will be accessible at `http://127.0.0.1:5000`.

---

### Step 3: Perform Logging

To log parameters, metrics, and artifacts:

1. Run the provided Python script or Jupyter Notebook (`notebook_mlflow.ipynb`).
2. The script will connect to the MLflow server running at `http://127.0.0.1:5000`.
3. The logs will be recorded and can be viewed in the MLflow UI.

---

### Step 4: Explore the MLflow UI

1. Open a web browser and navigate to:
   ```
   http://127.0.0.1:5000
   ```
2. You will see all the logged experiments, parameters, metrics, and artifacts.

---

## Key Features

- **Log Parameters**: Such as learning rate, batch size, etc.
- **Log Metrics**: Such as training accuracy, test accuracy, etc.
- **Log Artifacts**: Such as model files or metadata.

---

## Example Python Script

The following Python script demonstrates how to log data to the MLflow server:

```python
import mlflow

def train_and_log_model():
    # Example parameters
    learning_rate = 0.01
    epochs = 10

    # Example metrics
    train_accuracy = 0.95
    test_accuracy = 0.90

    # Start an MLflow run
    with mlflow.start_run():
        # Log parameters
        mlflow.log_param("learning_rate", learning_rate)
        mlflow.log_param("epochs", epochs)

        # Log metrics
        mlflow.log_metric("train_accuracy", train_accuracy)
        mlflow.log_metric("test_accuracy", test_accuracy)

        # Log a simple text artifact
        with open("example_artifact.txt", "w") as f:
            f.write("This is an example artifact!")
        mlflow.log_artifact("example_artifact.txt")

        print("Logging complete. Check the MLflow UI for results.")

if __name__ == "__main__":
    train_and_log_model()
```

---

## Troubleshooting

- **Cannot Access MLflow UI**: Ensure the container is running and port 5000 is available.
- **Logging Issues**: Verify that the Python script is pointing to the correct tracking URI (`http://127.0.0.1:5000`).

---

Enjoy experimenting with MLflow! 🚀

---