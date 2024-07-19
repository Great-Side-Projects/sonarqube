<a name="readme-top"></a>


[![MIT License][license-shield]][license-url]
[![LinkedIn][linkedin-shield]][linkedin-url]


<!-- PROJECT LOGO -->
<br />
<div align="center">
  <a href="https://www.keycloak.org/">
    <img src="https://assets-eu-01.kc-usercontent.com:443/b1ac63b6-1e65-01f4-6f38-e97c0e9214a1/12e3974b-220d-4cde-8f17-2ff9fa9d9c27/SonarQube_Logo.svg" alt="Logo" width="400" height="">
  </a>

  <h3 align="center">Sonarqube</h3>

  <p align="center">
    SonarQube is an open-source platform developed by SonarSource for continuous inspection of code quality to perform automatic reviews with static analysis of code to detect bugs, code smells, and security vulnerabilities on 20+ programming languages.
    <br />
    <a href="https://docs.sonarsource.com/sonarqube/latest/"><strong>Explore the docs »</strong></a>
    <br />
    <br />
    <a href="http://20.64.115.37:9000/">View Demo</a>
    ·
    <a href="https://github.com/Great-Side-Projects/sonarqube/issues">Report Bug</a>
    ·
    <a href="https://github.com/Great-Side-Projects/sonarqube/issues/new">Request Feature</a>
  </p>
</div>



<!-- TABLE OF CONTENTS -->
<details>
  <summary>Table of Contents</summary>
  <ol>
    <li>
      <a href="#about-the-project">About The Project</a>
      <ul>
        <li><a href="#built-with">Built With</a></li>
        <li><a href="#Architecture-design">Architecture design</a></li>
        <li><a href="#Architecture-diagram">Architecture diagram</a></li>
     </ul>
    </li>
    <li>
      <a href="#getting-started">Getting Started</a>
      <ul>
        <li><a href="#prerequisites">Prerequisites</a></li>
        <li><a href="#installation">Installation</a></li>
      </ul>
    </li>
    <li><a href="#usage">Usage</a></li>
    <li><a href="#roadmap">Roadmap</a></li>
    <li><a href="#contributing">Contributing</a></li>
    <li><a href="#license">License</a></li>
    <li><a href="#contact">Contact</a></li>
    <li><a href="#acknowledgments">Acknowledgments</a></li>
  </ol>
</details>

<!-- ABOUT THE PROJECT -->
## About The Project

[![Product Name Screen Shot][product-screenshot-UI]](http://20.64.115.37:9000/)

How to deploy Sonarqube on an Azure VM or localhost with Docker. 

<p align="right">(<a href="#readme-top">back to top</a>)</p>


### Built With

This project is built with the following technologies:


* [![Docker][DockerImage]](https://www.docker.com/)
* [![VM][AzureVM]](https://azure.microsoft.com/es-es/services/virtual-machines/)
* [![PostgreSQL][PostgreSQL]](https://www.postgresql.org/)

### Architecture design

The architecture design is based in Azure cloud services, the project is deployed in Azure VM, the database is Azure SQL Database, the CI/CD is GitHub Actions.

<p align="right">(<a href="#readme-top">back to top</a>)</p>

### Architecture diagram
[![Architecture diagram][architecture-diagram]](http://20.64.115.37:9000)

<p align="right">(<a href="#readme-top">back to top</a>)</p>


<!-- GETTING STARTED -->
## Getting Started

Here you can find the steps to run the project in your local environment to explore the Sonarqube proyect. 

### Prerequisites

This is an example of how to list things you need to use the software and how to install them.

You need to have a database created in PostgreSQL, for example "sonaqube" see https://docs.sonarsource.com/sonarqube/latest/setup-and-upgrade/install-the-server/installing-the-database/.
#### Note: the first time you run the project, the database will be created automatically and take more time to start the Sonarqube server. 

* Docker
* PostgresSQL database
* ***Sudo privileges in your local environment or VM (mandatory for docker installation)

### Installation
0. ***Increase the vm.max_map_count kernel setting to at least 262144. See https://www.elastic.co/guide/en/elasticsearch/reference/current/vm-max-map-count.html
    ```sh
    #temp solution
    sudo sysctl -w vm.max_map_count=262144
    
    #permanent solution
    sudo nano /etc/sysctl.conf
    #add the following line in the last line
    vm.max_map_count=262144
    #save and exit
    sudo sysctl -p
    ```

1. Clone the repo
   ```sh
   git clone https://github.com/Great-Side-Projects/keycloak.git
   ```
2. Go to the root folder of the project
   ```sh
   cd sonarqube
   ``` 
3.  find a docker file "Dockerfilelocal"  and set the environment variables in the dockerfile. root folder of the project
    ```dockerfile
    ENV SONAR_JDBC_MAXACTIVE=5 \
        SONAR_JDBC_MAXIDLE=2 \
        SONAR_JDBC_MINIDLE=1 \
        SONAR_JDBC_MAXWAIT=5000 \
        SONAR_JDBC_URL=jdbc:postgresql://localhost/sonarqube \ # change localhost for the ip of your database
        SONAR_JDBC_USERNAME=sonarqube \ # change for your username
        SONAR_JDBC_PASSWORD=sonarqube # change for your password
    ```

4. Create image and run with docker. root folder of the project 
 
   ```sh
    docker build -t sonarqube:latest -f Dockerfilelocal .
    docker run -p 9000:9000 sonarqube:latest
   ```
5. Open your browser and go to `http://localhost:9000/` to see the UI of the Sonarqube. the first time you run the project, the database will be created automatically and take more time to start the Sonarqube server. 
6. Login with the default credentials: user: admin, password: admin. the first time you log in, you will be asked to change the password.  
7. Enjoy!

<p align="right">(<a href="#readme-top">back to top</a>)</p>

<!-- USAGE EXAMPLES -->
## Usage

### Easy way:
Go to `http://localhost:9000/` and you can see the UI to manage the Sonarqube server.


<p align="right">(<a href="#readme-top">back to top</a>)</p>


<!-- ROADMAP -->
## Roadmap

- [x] Implement Docker for deployment
- [x] Implement Azure SQL Database for data storage
- [x] Implement Azure VM for deployment
- [x] Implement CI/CD with GitHub Actions
- [ ] Implement Azure Kubernetes Service for deployment


See the [open issues](https://github.com/Great-Side-Projects/sonarqube/issues) for a full list of proposed features (and known issues).

<p align="right">(<a href="#readme-top">back to top</a>)</p>

<!-- CONTRIBUTING -->
## Contributing

Contributions are what make the open source community such an amazing place to learn, inspire, and create. Any contributions you make are **greatly appreciated**.

If you have a suggestion that would make this better, please fork the repo and create a pull request. You can also simply open an issue with the tag "enhancement".
Don't forget to give the project a star! Thanks again!

1. Fork the Project
2. Create your Feature Branch (`git checkout -b feature/AmazingFeature`)
3. Commit your Changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to the "develop" Branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

<p align="right">(<a href="#readme-top">back to top</a>)</p>


<!-- LICENSE -->
## License

Distributed under the MIT License. See `LICENSE.txt` for more information.

<p align="right">(<a href="#readme-top">back to top</a>)</p>

<!-- CONTACT -->
## Contact

Angel Morales - [LinkedIn](https://www.linkedin.com/in/angelmoralesb/) - angelmoralesb@gmail.com

Project Link: [https://github.com/Great-Side-Projects/sonarqube](https://github.com/Great-Side-Projects/sonarqube)

<p align="right">(<a href="#readme-top">back to top</a>)</p>



<!-- ACKNOWLEDGMENTS -->
## Acknowledgments

* [Sonar Server Guides](https://www.keycloak.org/guides#server)
* [Choose an Open Source License](https://choosealicense.com)
* [Docker](https://www.docker.com/)
* [GitHub Actions](https://docs.github.com/es/actions)
* [Azure Virtual Machines](https://azure.microsoft.com/es-es/services/virtual-machines/)
* [Azure SQL Database PostgreSQL](https://azure.microsoft.com/es-es/products/postgresql)
* [Sonarqube](https://www.sonarqube.org/)
* [Sonnar Docker](https://docs.sonarsource.com/sonarqube/latest/setup-and-upgrade/install-the-server/installing-sonarqube-from-docker/)

 
<p align="right">(<a href="#readme-top">back to top</a>)</p>


<!-- MARKDOWN LINKS & IMAGES -->
<!-- https://www.markdownguide.org/basic-syntax/#reference-style-links -->
[contributors-shield]: https://img.shields.io/github/contributors/othneildrew/Best-README-Template.svg?style=for-the-badge
[contributors-url]: https://github.com/Great-Side-Projects/sonarqube/graphs/contributors
[forks-shield]: https://img.shields.io/github/forks/othneildrew/Best-README-Template.svg?style=for-the-badge
[forks-url]: https://github.com/Great-Side-Projects/sonarqube/forks
[stars-shield]: https://img.shields.io/github/stars/othneildrew/Best-README-Template.svg?style=for-the-badge
[stars-url]: https://github.com/Great-Side-Projects/sonarqube/stargazers
[issues-shield]: https://img.shields.io/github/issues/othneildrew/
[issues-url]: https://github.com/Great-Side-Projects/sonarqube/issues
[license-shield]: https://img.shields.io/github/license/othneildrew/Best-README-Template.svg?style=for-the-badge
[license-url]: https://github.com/Great-Side-Projects/quickshortapi/blob/main/LICENSE
[linkedin-shield]: https://img.shields.io/badge/-LinkedIn-black.svg?style=for-the-badge&logo=linkedin&colorB=555
[linkedin-url]: https://www.linkedin.com/in/angelmoralesb/
[product-screenshot-UI]: images/screenshotUI.png
[DockerImage]: https://img.shields.io/badge/Docker-0db7ed?style=for-the-badge&logo=docker&logoColor=white
logo=microsoft-azure&logoColor=white
[PostgreSQL]: https://img.shields.io/badge/PostgreSQL-336791?style=for-the-badge&logo=postgresql&logoColor=white
[architecture-diagram]: images/Sonarqube-Architecture-Design.drawio.png
[AzureVM]: https://img.shields.io/badge/Azure%20VM-0089D6?style=for-the-badge&logo=microsoft-azure&logoColor=white