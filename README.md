👋 Java Maven Build Job In Jenkins - Project

This is a simple Java application that prints a welcome message. It's designed to help you learn how to build Java projects with **Maven**, automate builds using **Jenkins**, and integrate CI/CD with **GitHub Actions**.

📌 Project Goals

- ✅ Build a basic Java app using Maven
- ✅ Set up a Jenkins Freestyle project to build the app
- ✅ Set up GitHub Actions to automate Maven builds on push

📁 Project Structure

hello-java-maven/ 
├── src/ 
│ └── main/ 
│ └── java/ 
│ └── HelloWorld.java 
├── pom.xml 
└── README.md


🧪 HelloWorld.java

java
public class HelloWorld {
    public static void main(String[] args) {
        System.out.println("Hello, Jenkins + Maven!");
    }
}


⚙️ Maven Build Instructions
Make sure you have Java and Maven installed. Then, run:
mvn clean package
This will compile the app and generate a JAR file in the target/ directory.

🤖 Jenkins CI Setup
Install Jenkins (locally or using Docker).
Configure Maven under Manage Jenkins → Global Tool Configuration.
Create a Freestyle Job:
Source: Local or GitHub repo
Build step: Invoke top-level Maven targets
Goals: clean package
Run the job — you should see BUILD SUCCESS 🎉

🔁 GitHub Actions CI/CD
This repo includes a GitHub Actions workflow that runs on every push:

.github/workflows/maven.yml:

name: Java CI with Maven

on:
  push:
    branches: [ main ]
  pull_request:
    branches: [ main ]

jobs:
  build:
    runs-on: ubuntu-latest
    steps:
      - name: Checkout code
        uses: actions/checkout@v4

      - name: Set up JDK 17
        uses: actions/setup-java@v4
        with:
          distribution: 'temurin'
          java-version: '17'

      - name: Build with Maven
        run: mvn clean package
You can monitor builds under the Actions tab of your repo.

📦 Build Output
After a successful build, you'll find the .jar file at:
target/hello-1.0.jar
Run it with : java -jar target/hello-1.0.jar

![Ubuntu Instance ](https://github.com/user-attachments/assets/0aca25b3-d60e-43ae-ae19-ca765cfcb32d)
![Job](https://github.com/user-attachments/assets/35eb3bfa-83ef-45e7-89cc-e43d7ac38d23)
![console output](https://github.com/user-attachments/assets/c807d6ba-7721-450e-b133-d8ecbdaab3bd)
![Build success](https://github.com/user-attachments/assets/5d73efd4-a84c-4560-9c30-66eb0993f244)
![Github Actions ](https://github.com/user-attachments/assets/86c54054-25c3-4d87-a7bc-0f91f91d32fd)

📃 License
This project is open-source under the MIT License.

🙌 Credits
Built as part of a CI/CD learning exercise using:
☕ Java
🧰 Maven
🔧 Jenkins
⚙️ GitHub Actions

Happy Building! 🚀

