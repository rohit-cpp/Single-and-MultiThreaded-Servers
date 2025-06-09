# 🧵 Java Socket Server Performance Test: Single Thread vs Multi-thread vs Thread Pool

This project is a hands-on demonstration of different Java server concurrency models using sockets:

- ✅ **Single-threaded Server**
- ❌ **Multi-threaded Server**
- ✅ **Thread Pool Server**

All implementations were tested using **Apache JMeter** under high request loads (up to 10,000 requests per minute). Performance results are included with screenshots.

---

## ⚙️ Technologies

- Java 8+
- Apache JMeter
- Java Networking (Sockets)
- Java Concurrency (Threads, ExecutorService)

---

## 🚀 Server Types

### 1. 🔹 Single-threaded Server

- Handles **one client at a time**
- Good for simple or controlled environments
- Efficient at low traffic

**✅ Test Result:** 
- Able to handle **10,000 requests/min** successfully.

📸 Screenshot
![Screenshot 2025-06-09 142644](https://github.com/user-attachments/assets/3784bd54-c84d-4537-8ee3-51745a68cfa1)

https://github.com/user-attachments/assets/d3952ec1-54f2-49b6-afe4-24e00c9c00bb

---

### 2. ❌ Multi-threaded Server (New Thread per Client)

- Spawns a new thread for each client connection
- Under high load, **system runs out of resources**

**❌ Test Result:**
- Fails completely at 10,000 RPM
- No successful requests

📸 Screenshot
![Screenshot 2025-06-09 144111](https://github.com/user-attachments/assets/34217dd5-2524-44fa-965b-4a57a65c8a08)

https://github.com/user-attachments/assets/ac1423e0-2f0b-40e7-bad8-a20feb223666

---

### 3. ✅ Thread Pool Server

- Uses `Executors.newFixedThreadPool()`
- Limits the number of threads
- Handles high load **efficiently** and **safely**

**✅ Test Result:** 
- Smooth performance under high load
- 100% success rate with 10,000+ RPM

📸 Screenshot
![Screenshot 2025-06-09 145159](https://github.com/user-attachments/assets/223ed6a8-6e30-4056-a386-4b04245c744d)

https://github.com/user-attachments/assets/fe254b62-dd88-400d-a9ab-780b160621c4

---

## 🧪 JMeter Load Testing

**Test Config:**
- 10,000 requests per minute
- 100 concurrent threads
- 1-minute ramp-up

**Metrics Tracked:**
- % Success
- Avg. Response Time

| Server Type       | Success Rate | Notes                                   |
|-------------------|--------------|-----------------------------------------|
| Single Thread      | ✅ 100%      | Processes one request at a time         |
| Multi Thread       | ❌ 0%        | Crashed due to thread exhaustion        |
| Thread Pool (10)   | ✅ 100%      | Efficient concurrency + resource control|

---

## 💻 How to Run

### 🔧 Compile All Java Files

```bash
javac Server.java Client.java

🧵 Run Single Thread Server
cd single_thread
java Server

🔁 Run Multi Thread Server
cd multi_thread
java Server

🧠 Run Thread Pool Server
cd thread_pool
java Server

