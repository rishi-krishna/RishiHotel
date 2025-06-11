# hotel.com

PRODUCTION READY CODE BRANCH

Enterprise-level hotel booking simulation app built with Angular, Spring Boot, SQL, MongoDB, and Redis


📦 hotel.com – Microservices Overview
This project follows a microservices architecture where each service is independently deployable, scalable, and responsible for a specific business capability. All services communicate via REST APIs and are orchestrated through Spring Cloud Gateway and Eureka Discovery.

### 🔐 1. auth-service: 
Purpose: Handles authentication and user management.
Responsibilities:
User registration and login
JWT token generation and validation
Role-based access control (Guest, Admin, Hotel Staff)
Token blacklist for logout
Password encryption (BCrypt)
Database: PostgreSQL
Tech Stack: Spring Boot, Spring Security, JWT, Spring Data JPA


🏨 2. hotel-service
Purpose: Manages hotels and room inventory.
Responsibilities:
CRUD operations for hotels and rooms
Store room types, amenities, prices
Admin-only endpoints for managing listings
Expose room availability for booking-service
Database: PostgreSQL
Tech Stack: Spring Boot, Spring Data JPA, Hibernate


📆 3. booking-service
Purpose: Handles room reservations and booking logic.
Responsibilities:
Book, cancel, and modify reservations
Check room availability before booking
Enforce booking rules (date validation, conflict resolution)
Store historical bookings
Database: PostgreSQL
Tech Stack: Spring Boot, Spring Data JPA, REST


👤 4. user-profile-service
Purpose: Manages user-specific preferences and history.
Responsibilities:
Store user preferences like favorite hotels, cities, filters
Save user search history
Show personalized recommendations
Database: MongoDB
Tech Stack: Spring Boot, Spring Data MongoDB

📣 5. notification-service
Purpose: Sends notifications related to bookings and alerts.
Responsibilities:
Send booking confirmation emails
Send check-in reminders
Send promotional or system alerts (optional SMS/email)
Retry failed notifications
Database: MongoDB
Tech Stack: Spring Boot, Spring Scheduler, Spring Mail, RabbitMQ/Kafka-ready


🌐 6. gateway-service
Purpose: Acts as a single entry point for all microservices.
Responsibilities:
Route incoming HTTP requests to appropriate microservices
Handle CORS, security headers, and rate limiting
Optionally authenticate tokens at gateway level
Provide failover and retry logic
Database: None
Tech Stack: Spring Cloud Gateway


📡 7. discovery-server
Purpose: Service discovery and registry using Eureka.
Responsibilities:
Register all microservices
Maintain availability map of services
Allow dynamic load-balanced routing between services
Database: None
Tech Stack: Spring Cloud Netflix Eureka


⚙️ 8. config-server
Purpose: Centralized configuration for all services.
Responsibilities:
Load all application.yml configs from a Git repository
Provide configuration to services at runtime
Allow runtime updates and refresh scopes
Database: None
Tech Stack: Spring Cloud Config Server

🧠 Why Microservices?
Modularity: Each service focuses on a single business capability
Scalability: Services like booking or auth can scale independently
Resilience: One failing service won’t bring down the whole app
Deployability: Easier CI/CD pipelines, small independent releases
Tech Flexibility: Easier to introduce new tech stacks in isolated areas





