# SonarQube

AIM: Scan Python scripts for vulnerabilities, bugs, and other traits using SonarQube

***What is SonarQube:***

SonarQube is an automatic code review tool to detect bugs, vulnerabilities, and code smells in your code. It can integrate with your existing workflow to enable continuous code inspection across your project branches and pull requests.

SonarQube is a Code Quality Assurance tool that collects and analyzes source code and provides reports for the code quality of your project. It combines static and dynamic analysis tools and enables quality to be measured continually over time. Everything from minor styling choices to design errors are inspected and evaluated by SonarQube. This provides users with a rich searchable history of the code to analyze where the code is messing up and determine whether or not it is styling issues, code defeats, code duplication, lack of test coverage, or excessively complex code. 

SonarQube also ensures code reliability, Application security, and reduces technical debt by making your code base clean and maintainable. SonarQube also provides support for 27 different languages, including C, C++, Java, JavaScript, PHP, GO, Python, and much more. SonarQube also provides CI/CD integration and gives feedback during code review with branch analysis and pull request decoration.

![picture1](https://github.com/roshnii20/SonarQube/blob/main/pictures/Picture1.png)

1.	The SonarQube server running the following processes:
   o	a web server that serves the SonarQube user interface.
   o	a search server based on Elasticsearch.
   o	the compute engine in charge of processing code analysis reports and saving them in the SonarQube database.
2.	The database to store the following:
   o	Metrics and issues for code quality and security generated during code scans.
   o	The SonarQube instance configuration.
3.	One or more scanners running on your build or continuous integration servers to analyze projects.


Virtual Machine requirements and prerequisites:

•	3CPU, 8GB RAM
•	Java
•	Docker

SonarQube has a dependency on Java, so we need that installed. 
It also needs a database to store analysis results. By default, it uses H2 database, which is fine for lighter and non-critical workloads. But for critical workloads, it is recommended to use databases like PostgreSQL, MySQL etc. 
Here in this lab, we are using the default H2 database.  
We will install SonarQube using Docker so we need that installed too.


PART 1: SonarQube installation

STEP 1: Install Java using the following command:
sudo apt-get install openjdk-11-jdk

Verify: java -version
![picture2](https://github.com/roshnii20/SonarQube/blob/main/pictures/Picture2.png)

STEP 2: Install Docker and adding user to docker group

sudo apt-get update

sudo apt-get install \
    apt-transport-https \
    ca-certificates \
    curl \
    gnupg \
    lsb-release

curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /usr/share/keyrings/docker-archive-keyring.gpg

echo \
  "deb [arch=amd64 signed-by=/usr/share/keyrings/docker-archive-keyring.gpg] https://download.docker.com/linux/ubuntu \
  $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null


sudo apt-get update

sudo apt-get install docker-ce docker-ce-cli containerd.io

![picture3](https://github.com/roshnii20/SonarQube/blob/main/pictures/Picture3.png)

We will add our user to Docker group so that we don’t have to use sudo everytime

sudo usermod -aG docker $USER

Logout and log back in for the changes to take place

STEP 3: Installing SonarQube using Docker

docker run -d --name sonarqube -p 9000:9000 sonarqube

SonarQube runs on port 9000
![picture4](https://github.com/roshnii20/SonarQube/blob/main/pictures/Picture4.png)

Verify the container is running:
![picture5](https://github.com/roshnii20/SonarQube/blob/main/pictures/Picture5.png)

