# JavaLoginShowcase 🚀
This repository contains a sample login page implemented in Java for practicing Java deployment techniques. It includes a stylish and functional login UI, designed to help you understand how to deploy and manage a Java-based web application. 💻✨

![alt text](image.png)

## Features:
- User-friendly login interface 🖥️
- Responsive design 📱
- Sample code for deploying Java web applications 📦

## Purpose:
This project is a hands-on example for developers looking to practice deploying Java applications. It’s perfect for learning deployment strategies, UI design, and Java web development. 🎓🔧

## Branding:
Made with Love by **DevOps Insiders** ❤️. We are passionate about delivering high-quality solutions and resources for the DevOps community. 🌟

## Prerequisites:
Before you begin, ensure you have met the following requirements:

- **Java Development Kit (JDK)**: Ensure you have JDK 8 or higher installed. You can download it from [Oracle's website](https://www.oracle.com/java/technologies/javase-jdk11-downloads.html) or use OpenJDK. ☕
- **Maven**: Apache Maven is used for building the project. Download and install Maven from [Maven's official website](https://maven.apache.org/download.cgi). 📦
- **Apache Tomcat**: A web server and servlet container for deploying the WAR file. Download it from [Apache Tomcat's website](https://tomcat.apache.org/download-90.cgi). 🖥️
- **Git**: Required for cloning the repository. Install Git from [Git's official website](https://git-scm.com/downloads). 🧩

## Getting Started:
1. **Clone the Repository**:
   ```bash
   git clone https://github.com/your-username/JavaLoginShowcase.git
   ```
2. **Navigate to the Project Directory**:
   ```bash
   cd JavaLoginShowcase
   ```

## Deployment Instructions:
1. **Build the Project**:
   - Use Maven to clean and package the application into a WAR file:
     ```bash
     mvn clean package
     ```
   - This command will generate a WAR file in the `target` directory (e.g., `target/JavaLoginShowcase.war`). 📦

2. **Deploy to Tomcat**:
   - Copy the WAR file to the Tomcat `webapps` directory:
     ```bash
     cp target/JavaLoginShowcase.war $TOMCAT_HOME/webapps/
     ```
   - Restart the Tomcat server to deploy the WAR file:
     ```bash
     $TOMCAT_HOME/bin/shutdown.sh
     $TOMCAT_HOME/bin/startup.sh
     ```

3. **Access the Application**:
   - Once deployed, access the application through your web browser at:
     ```
     http://localhost:8080/JavaLoginShowcase
     ```

## Contributing:
Feel free to contribute by submitting issues or pull requests. We welcome any improvements or suggestions! 🤝

## License:
This project is licensed under the Apache License - see the [LICENSE](LICENSE) file for details. 📜

**DevOps Insiders** is committed to enhancing the DevOps community with valuable resources and examples. Follow us for more tools and insights! 🌟

### Emojis Reference:
- **🚀**: Represents the project being a showcase or launch.
- **💻✨**: Emphasizes the modern and functional nature of the login UI.
- **🖥️** and **📱**: Indicate the types of interfaces and design considerations.
- **🎓🔧**: Suggests learning and hands-on practice.
- **❤️** and **🌟**: Show love and commitment to quality from the DevOps Insiders community.
- **☕**: Represents Java.
- **📦**: Denotes Maven and deployment.
- **🧩**: Indicates Git.
- **🤝**: Encourages contributions.
- **📜**: Represents licensing.


==========================================================================

Awesome 🎉
Since it’s working, here is a **clean, copy-paste-ready Day 5 NOTES VERSION** you can **write down or save**.
This is **exactly how you should explain + do it again without help**.

---

# ✅ **Day 5 – Manual Java WAR Deployment on Windows 11 (Tomcat)**

![Image](https://i.sstatic.net/zX4Ig.png)

![Image](https://media.geeksforgeeks.org/wp-content/uploads/20240612170604/Maven-Build-Life-Cycle.png)

![Image](https://www3.ntu.edu.sg/home/ehchua/programming/howto/images/TomcatArchitecture.png)

![Image](https://logicmonitor.com/wp-content/uploads/2023/09/apache_tomcat_request_handling-1024x573.jpg)

---

## 🔹 1. Prerequisites (One-time Setup)

### Install

* **JDK 11 or 17**
* **Maven**
* **Git**
* **Apache Tomcat 9 (ZIP)**

Extract Tomcat to:

```
D:\Devops software\apache-tomcat-9.0.113
```

---

## 🔹 2. Set Environment Variable (IMPORTANT)

Open **PowerShell (Admin)** and run:

```powershell
setx CATALINA_HOME "D:\Devops software\apache-tomcat-9.0.113"
```

Close PowerShell → Open a **new** one.

Verify:

```powershell
$env:CATALINA_HOME
```

---

## 🔹 3. Start Tomcat

```powershell
& "$env:CATALINA_HOME\bin\startup.bat"
```

Verify in browser:

```
http://localhost:8080
```

✔ Apache Tomcat home page should open

---

## 🔹 4. Clone Java Application

```powershell
git clone https://github.com/your-username/JavaLoginShowcase.git
cd JavaLoginShowcase
```

---

## 🔹 5. Build WAR File Using Maven

```powershell
mvn clean package
```

WAR generated at:

```
target\JavaLoginShowcase-1.0.0.war
```

---

## 🔹 6. Rename WAR (Context Path Control)

```powershell
Rename-Item target\JavaLoginShowcase-1.0.0.war JavaLoginShowcase.war
```

Why?
👉 WAR name = application URL path in Tomcat

---

## 🔹 7. Deploy WAR to Tomcat

```powershell
Copy-Item target\JavaLoginShowcase.war `
"$env:CATALINA_HOME\webapps\" -Force
```

Tomcat auto-deploys the WAR.

(Optional restart)

```powershell
& "$env:CATALINA_HOME\bin\shutdown.bat"
& "$env:CATALINA_HOME\bin\startup.bat"
```

---

## 🔹 8. Access the Application

Open browser:

```
http://localhost:8080/JavaLoginShowcase
```

✔ Frontend loads successfully

---

## 🔹 9. Stop Tomcat (When Done)

```powershell
& "$env:CATALINA_HOME\bin\shutdown.bat"
```

---

# 🧠 **IMPORTANT CONCEPTS (Interview Notes)**

### PowerShell vs CMD

| Shell      | Syntax     |
| ---------- | ---------- |
| CMD        | `%VAR%`    |
| PowerShell | `$env:VAR` |

---

### TOMCAT_HOME vs CATALINA_HOME

* `CATALINA_HOME` → **Required by Tomcat on Windows**
* `TOMCAT_HOME` → Informal (often Linux)

---

### WAR Context Path Rule

```
JavaLoginShowcase.war → /JavaLoginShowcase
JavaLoginShowcase-1.0.0.war → /JavaLoginShowcase-1.0.0
```

---

