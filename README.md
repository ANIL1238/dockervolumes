Here is your complete **Docker Volume-based Todo App project** in **Git-ready code format** — you can directly copy this into your GitHub repository.

---

## ✅ `todo-app` — GitHub Repository Code

### 📁 Folder Structure:

```
todo-app/
├── Dockerfile
├── index.html
└── README.md
```

---

### 📄 `Dockerfile`

```Dockerfile
# Use a lightweight Nginx image
FROM nginx:alpine

# Copy static HTML into nginx's default site directory
COPY index.html /usr/share/nginx/html/index.html

# Create directory for volume data
RUN mkdir -p /app/data

# Set working directory to match volume mount
WORKDIR /app/data
```

---

### 📄 `index.html`

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
  <title>Todo App</title>
</head>
<body>
  <h1>🚀 Welcome to My Todo App</h1>
  <p>This app uses Docker volumes to persist data!</p>
</body>
</html>
```

---

### 📄 `README.md`

```markdown
# 🐳 Docker Volume Example: Todo App

This project demonstrates using **Docker Volumes** to persist data across container restarts.

---

## 📁 Folder Structure

```

todo-app/
├── Dockerfile       # Builds a simple nginx-based container
├── index.html       # Static webpage served by nginx
└── README.md        # Documentation

````

---

## 🚀 Steps to Run

### Step 1: Clone the Repo

```bash
git clone https://github.com/YOUR_USERNAME/todo-app.git
cd todo-app
````

---

### Step 2: Create a Docker Volume

```bash
docker volume create todo_data
```

---

### Step 3: Build Docker Image

```bash
docker build -t testapp .
```

---

### Step 4: Run Container With Volume

```bash
docker run -d -p 8080:80 -v todo_data:/app/data --name todo_container testapp
```

---

## ✅ Verify It’s Working

### Open in browser:

```
http://YOUR_PUBLIC_IP:8080
```

### Save a file into the volume:

```bash
docker exec -it todo_container sh
echo "Hello from volume!" > /app/data/hello.txt
exit
```

### Check the volume from another container:

```bash
docker run -it --rm -v todo_data:/data alpine sh
cat /data/hello.txt
```

✅ You should see:

```
Hello from volume!
```

---

## 📂 Where is data stored on host?

```
/var/lib/docker/volumes/todo_data/_data/
```

Even if the container is deleted, this data will remain.

---

## 🧹 Clean Up

```bash
docker stop todo_container
docker rm todo_container
docker volume rm todo_data
```

---

## 🔁 Summary

* **Volume:** Persists data across container lifecycles.
* **Safe:** Keeps your app logic and data storage separate.
* **Flexible:** Share volumes across containers.

---

🧠 Happy Learning! – *Built with Nginx + Docker Volumes*

````

---

### 📦 One-Line Shell Script to Generate Files (Optional)
If you want to create all files quickly on your server:
```bash
mkdir -p todo-app && cd todo-app && \
echo 'FROM nginx:alpine\nCOPY index.html /usr/share/nginx/html/index.html\nRUN mkdir -p /app/data\nWORKDIR /app/data' > Dockerfile && \
echo '<!DOCTYPE html><html><head><title>Todo App</title></head><body><h1>🚀 Welcome to My Todo App</h1><p>This app uses Docker volumes to persist data!</p></body></html>' > index.html && \
touch README.md
````

Then paste the full `README.md` content from above into the `README.md` file manually.

---

Let me know if you'd like this zipped, pushed to GitHub, or if you want to extend it with a real backend (like Node.js or Python Flask).
