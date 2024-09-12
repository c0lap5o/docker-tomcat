# Dockerized Tomcat Server

This project provides a Docker setup for deploying a Tomcat server with custom configurations.

## Prerequisites

- Docker
- Docker Compose

## Quick Start

1. Clone this repository:
   ```
   git clone https://github.com/yourusername/docker-tomcat.git
   cd docker-tomcat
   ```

2. Change the `.env` file in the project root and set the `HTTP_PORT` variable:
   ```
   HTTP_PORT="8080:8080"
   ```

3. Build and start the container:
   ```
   docker-compose up -d
   ```

4. Access Tomcat at `http://localhost:8080`

## Configuration

- `Dockerfile-tomcat`: Defines the Tomcat server image
- `docker-compose.yml`: Orchestrates the Tomcat service
- `config/context.xml`: Custom context configuration for Tomcat manager
- `config/tomcat-users.xml`: Defines Tomcat users and roles

## Customization

To deploy your web application:

1. Place your WAR file in the project directory
2. Uncomment and modify the following line in `docker-compose.yml`:
   ```yaml
   - ./yourapp.war:/usr/local/tomcat/webapps/yourapp.war
   ```

## Stopping the Server

To stop and remove the containers:

```
docker-compose down
```

## Contributing

Pull requests are welcome. For major changes, please open an issue first to discuss what you would like to change.

## License

MIT License

Copyright (c) 2024 c0lap5o

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.
