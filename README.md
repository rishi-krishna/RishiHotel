# hotel.com


Enterprise-level hotel booking simulation app built with Angular, Spring Boot, SQL, MongoDB, and Redis


📦 hotel.com – Microservices Overview
This project follows a microservices architecture where each service is independently deployable, scalable, and responsible for a specific business capability. All services communicate via REST APIs and are orchestrated through Spring Cloud Gateway and Eureka Discovery.

### 🔐 1. auth-service: [hotel-auth-service]
Purpose: Handles authentication and user management.
#### Responsibilities:
  1) User registration and login
  2) JWT token generation and validation
  3) Role-based access control (Guest, Admin, Hotel Staff)
  4) Token blacklist for logout
  5) Password encryption (BCrypt)
Database: PostgreSQL
Tech Stack: Spring Boot, Spring Security, JWT, Spring Data JPA


### 🏨 2. hotel-service: [hotel-hotel-service]
Purpose: Manages hotels and room inventory.
#### Responsibilities:
  1) CRUD operations for hotels and rooms
  2) Store room types, amenities, prices
  3) Admin-only endpoints for managing listings
  4) Expose room availability for booking-service
Database: PostgreSQL
Tech Stack: Spring Boot, Spring Data JPA, Hibernate


### 📆 3. booking-service: [hotel-booking-service]
Purpose: Handles room reservations and booking logic.
#### Responsibilities:
  1) Book, cancel, and modify reservations
  2) Check room availability before booking
  3) Enforce booking rules (date validation, conflict resolution)
  4) Store historical bookings
Database: PostgreSQL
Tech Stack: Spring Boot, Spring Data JPA, REST


### 👤 4. user-profile-service: [hotel-user-profile-service]
Purpose: Manages user-specific preferences and history.
#### Responsibilities:
  1) Store user preferences like favorite hotels, cities, filters
  2) Save user search history
  3) Show personalized recommendations
Database: MongoDB
Tech Stack: Spring Boot, Spring Data MongoDB

### 📣 5. notification-service: [hotel-notification-service]
Purpose: Sends notifications related to bookings and alerts.
#### Responsibilities:
  1) Send booking confirmation emails
  2) Send check-in reminders
  3) Send promotional or system alerts (optional SMS/email)
  4) Retry failed notifications
Database: MongoDB
Tech Stack: Spring Boot, Spring Scheduler, Spring Mail, RabbitMQ/Kafka-ready


### 🌐 6. gateway-service: [hotel-gateway-service]
Purpose: Acts as a single entry point for all microservices.
#### Responsibilities:
  1) Route incoming HTTP requests to appropriate microservices
  2) Handle CORS, security headers, and rate limiting
  3) Optionally authenticate tokens at gateway level
  4) Provide failover and retry logic
Database: None
Tech Stack: Spring Cloud Gateway


### 📡 7. discovery-server: [hotel-discovery-server]
Purpose: Service discovery and registry using Eureka.
#### Responsibilities:
  1) Register all microservices
  2) Maintain availability map of services
  3) Allow dynamic load-balanced routing between services
Database: None
Tech Stack: Spring Cloud Netflix Eureka


### ⚙️ 8. config-server: [hotel-config-server]
Purpose: Centralized configuration for all services.
#### Responsibilities:
  1) Load all application.yml configs from a Git repository
  2) Provide configuration to services at runtime
  3) Allow runtime updates and refresh scopes
Database: None
Tech Stack: Spring Cloud Config Server

### 9. frontend: [hotel-frontend]
purpose: FrontEnd UI of RishiHotel
#### Responsibilities:
  1) main UI of the hotel
  2) UI includes all components of the hotel
Database: None
Tech Stack: Angular, typescript, HTML, CSS

### 🧠 Why Microservices?
Modularity: Each service focuses on a single business capability
Scalability: Services like booking or auth can scale independently
Resilience: One failing service won’t bring down the whole app
Deployability: Easier CI/CD pipelines, small independent releases
Tech Flexibility: Easier to introduce new tech stacks in isolated areas





