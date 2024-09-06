# Configuration Repository

## Overview
This repository stores the **configuration files** (`YAML` format) for different environments of the microservices architecture. The configurations are used by the **Spring Cloud Config Server** to provide environment-specific properties to microservices like `HotelService`, `RatingService`, `UserService`, and more.

## Files

### 1. **application.yml**
This is the default configuration file that applies when no specific environment profile is active. It contains common properties shared across all environments.

### 2. **application-dev.yml**
This file contains configuration specific to the **development environment**. When the `dev` profile is active, this file's settings will override those in `application.yml`.

### 3. **application-prod.yml**
This file contains configuration specific to the **production environment**. When the `prod` profile is active, this file's settings will override those in `application.yml`.

## Usage

### How it works with the Config Server:
- The **Spring Cloud Config Server** reads these configuration files and serves them to microservices based on their active profile.
- Microservices fetch configurations dynamically based on their environment using the following URL pattern:
```bash
http://{config-server-url}/{application-name}/{profile}/{label}
```

For example, to fetch application-dev.yml for the hotelservice, the URL would be:
```bash
http://localhost:8888/hotelservice/dev/main
```

### Active Profiles:
**Default Profile:** application.yml
**Development Profile** application-dev.yml
**Production Profile:** application-prod.yml

### How to Update
## Clone the repository:

```bash
git clone https://github.com/chandrakanthrck/config-repo.git
```
**Edit the YAML files:** Make changes to the respective application.yml, application-dev.yml, or application-prod.yml based on the environment.

**Commit and Push:**
```bash
git add .
git commit -m "Update configuration"
git push origin main
```

### Important Notes
- Ensure that sensitive data like passwords, API keys, etc., are not exposed in these files. Consider using **encrypted values** or **environment variables** for sensitive information.
- The configuration repository works in tandem with the **Spring Cloud Config Server** to provide environment-specific configurations to microservices.

### License
This project is licensed under the MIT License.
