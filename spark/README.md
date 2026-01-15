
# 🔥 Spark 4.0.1 – Docker Environment  
A lightweight Docker-based environment for running **Apache Spark 4.0.1**, **PySpark**, and **JupyterLab** locally.

This project allows you to:

- Build a reproducible Spark environment  
- Run Spark & PySpark interactively  
- Launch JupyterLab in your browser  
- Enter the container and explore files inside  
- Extend the image with Python libraries (Jupyter, boto3, etc.)

---

## 📁 Project Structure

```
.
├── Dockerfile
├── README.md
└── (optional spark configs, notebooks, scripts)
```

---

# 🚀 Getting Started

## ✅ 1. Build the Docker Image

Run the following command inside the project directory (where the Dockerfile is):

```bash
docker build . -t spark-4.0.1
```

This will create a Docker image named **spark-4.0.1**.

---

## ✅ 2. Run the Container (Default Mode)

Start the container normally using:

```bash
docker run spark-4.0.1
```

This uses the default `CMD` from your Dockerfile.

---

## ✅ 3. Run JupyterLab in Your Local Browser  
If your Dockerfile starts JupyterLab, you must expose port **8888**:

```bash
docker run -it -p 8888:8888 spark-4.0.1:latest
```

Then open your browser:

```
http://localhost:8888
```

---

## ✅ 4. Access the Container Shell (bash)

To explore files, inspect Spark installation, debug configs, etc.:

```bash
docker run -it --entrypoint bash spark-4.0.1:latest
```

---

# 🧪 Example: Starting PySpark Manually

Once inside the container:

```bash
pyspark
```

Or:

```bash
$SPARK_HOME/bin/pyspark
```

---

# 🧰 Troubleshooting

### ❗ Port 8888 already in use
If you see:
```
Bind for 0.0.0.0:8888 failed: port is already allocated
```
Run:

```bash
docker run -it -p 9999:8888 spark-4.0.1:latest
```

Then open:
```
http://localhost:9999
```

---

### ❗ Container networking error
```bash
docker ps
docker stop <container_id>
docker rm <container_id>
```

---

### ❗ Jupyter fails to run as root
Already handled in Dockerfile using `--allow-root`.

---

### ❗ Spark logs too verbose
Inside a notebook:

```python
spark.sparkContext.setLogLevel("ERROR")
```

---

# 🧱 Notes for Windows / WSL2 Users

- Use **WSL2** for best performance  
- Ensure Docker Desktop → *Use WSL2 backend* is enabled 

---

# 🛠 Customize the Docker Image

Add Python packages by editing your Dockerfile:

```dockerfile
RUN pip install jupyterlab notebook boto3 pandas pyarrow
```

Rebuild:

```bash
docker build . -t spark-4.0.1
```

---

# 🤝 Contributing
Feel free to open issues or PRs.

---

# 📜 License
Open-source. Use freely.
