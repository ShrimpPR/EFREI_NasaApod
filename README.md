# 🚀 Astronomy Picture of the Day (APOD)
## 📌 Getting Started

### Follow these steps to set up and run the project:
## 1️⃣ Clone the Repository
```bash
git clone https://github.com/ShrimpPR/EFREI_NasaApod.git
```

## 2️⃣ Open the Project

Use your preferred IDE or terminal to navigate into the project directory.
## 3️⃣ Configure the Application

Rename the `application.properties.example` file to `application.properties` and update the following values:

### Database Configuration
```
spring.datasource.url=jdbc:mysql://localhost:3306/apod  
spring.datasource.username=REPLACE_WITH_YOUR_DB_USERNAME  
spring.datasource.password=REPLACE_WITH_YOUR_DB_PASSWORD
```

### Security Configuration
```
jwt.secret=REPLACE_WITH_YOUR_OWN_JWT_SECRET
```

### API Configuration
```
api.key=REPLACE_WITH_YOUR_OWN_API_KEY
```

## 4️⃣ Set Up the Database

Start your MySQL server and create a schema named apod.
## 5️⃣ Run the Application

Launch the application using your preferred method.
## 📖 API Documentation
### 🛠 Roles & Permissions

    ADMIN → Full CRUD access to APODs in the database

        Endpoint: /apod/(the method you want to use)

    USER → Fetches the picture of the day

        Endpoint: /api

    SCRAPER → Scrapes and stores the APOD in the database

        Endpoint: /api/scrapping

## 🔬 API Testing

You can test the API using different tools like Postman or Bruno. Here are some examples of how to test the API using Bruno.

POST {{connectionPath}}/user/login
Body: `{
    "username": "user1",
    "password": "password"
}`

GET {{connectionPath}}/api -> For users only

To store the authentication token after login or registration, add this Post-Request Script in Bruno:

You will also need to add an Auth Bearer Token in the Authorization tab of each requests beside the login and the registration.

```
var jsonData = res.getBody();
bru.setEnvVar("userToken", jsonData.token);
```

You can do the same but using Postman

```
var jsonData = pm.response.json();
pm.environment.set("userToken", jsonData.token);
```
Also, create an environment variable named userToken in the collection settings.