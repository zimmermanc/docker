<!--
docker-compose implementation
-->



<!-- Task to write dockerfile and compose yml -->





<br />
<p align="center">
  <a href="https://github.com/zimmermanc/docker">
  </a>

  <h3 align="center">Protected Container</h3>

  <p align="center">
  Implementation includes 2 running containers. Authentication Proxy and Content Web server
  </p>
</p>



<!-- TABLE OF CONTENTS -->
<details open="open">
  <summary>Table of Contents</summary>
  <ol>
    <li>
      <a href="#about-the-project">About The Task</a>
      <ul>
        <li><a href="#built-with">Built With</a></li>
      </ul>
    </li>
    <li>
      <a href="#getting-started">Getting Started</a>
      <ul>
        <li><a href="#deployment">Deployment</a></li>
      </ul>
    </li>
    <li><a href="#files">Files</a></li>
    <li><a href="#contact">Contact</a></li>
  </ol>
</details>



<!-- ABOUT THE PROJECT -->
## About The Task

Implementation includes 2 running containers. Authentication Proxy and Content Web server. Restriction of access to the content server is done by restricting all external traffic to this container. Requests reach the proxy server and are evaluated before being sent by reverse proxy to the content server. All requests that are not pointed directly at the protected content return 404, this includes all HTTP traffic.


Key Config items:
* Access Key URL is required to obtain data. Default: mysupersecretaccesskey
* Basic Auth is configured within the proxy server Dockerfile by using openssl. Default: zimmermanc / secretpass



### Built With

* [Docker-compose](https://docs.docker.com/compose/)
* [Docker](https://docker.com)
* [vim](https://www.vim.org/)
* [OpenSSL](https://openssl.org)
* [nginx](https://nginx.com)



<!-- GETTING STARTED -->
## Getting Started

A docker and docker-compose implementation will be required to deploy these containers. Documentation for your architecture is available at https://docs.docker.com/compose/install/ and here https://docs.docker.com/get-docker/


### Deployment 

1. Install docker and docker-compose with links above
2. Build images
   ```sh
   docker-compose build
   ```
3. Run containers
   ```sh
   docker-compose up -d
   ```
4. Verify containers are running
   ```sh
   docker ps
   ```
5. View content
   ```sh
   curl -k https://localhost/mysupersecretaccesskey/index.htm
   ```



<!-- Files -->
## Files

```bash
.
├── docker-compose.yml - Networking and Build configuration
├── proxy
│   ├── Dockerfile - Installs useful utilities and copies nginx config Files, configures SSL certificates. **This is also where the Basic Auth password is set**
│   └── conf.d
│       ├── default.conf - Disables HTTP traffic
│       └── ssl.conf - Sets nginx SSL configuration and reverse proxy config. **This is also where the url access string is set**
├── tree.txt
└── web
    ├── Dockerfile - Installs useful utilities and copies nginx config Files
    ├── conf.d
    │   └── default.conf - Defines location of protected content and set root
    └── content
        └── index.htm - protected content
```




<!-- LICENSE -->
## License

Distributed under the MIT License. See `LICENSE` for more information.



<!-- CONTACT -->
## Contact

Chris Zimmerman - [@chrisszimmerman](https://twitter.com/chrisszimmerman - czimmerman@paloaltonetworks.com

Project Link: [https://github.com/zimmermanc/docker](https://github.com/zimmermanc/docker)







