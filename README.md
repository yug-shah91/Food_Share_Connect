🌱 FoodShare Connect

A food donation platform connecting donors, recipients, and admins — built as a B.Tech VI Sem mini project at Medicaps University, Indore.

Stack: Plain HTML/CSS/JS frontend + Spring Boot 3.2 REST API backend with JWT auth, role-based access control, and H2 in-memory database.

👥 Team
NameRoleYash Veer SinghBackend + IntegrationYug ShahFrontend UIYatharth GuptaAdmin Dashboard + Testing

📸 Features

Donor — Submit food donations with AI-powered freshness scoring
Recipient — Browse active listings, filter by category/freshness, claim pickups
Admin — Real-time dashboard with platform stats, user activity, and prediction log
JWT Authentication — Stateless, role-based access (DONOR / RECIPIENT / ADMIN)
Freshness AI — Score (0–99) computed server-side from food category + storage condition


🗂️ Project Structure
foodshare/
├── frontend/
│   ├── index.html          ← Single-page app shell + all role views
│   ├── style.css           ← Full UI stylesheet
│   └── app.js              ← All JS: auth, API calls, rendering
│
└── foodshare-backend/      ← Spring Boot project
    ├── pom.xml
    └── src/main/java/com/foodshare/
        ├── FoodShareApplication.java
        ├── config/
        │   ├── SecurityConfig.java         ← JWT filter chain + CORS
        │   ├── DataSeeder.java             ← Seeds 3 demo users on startup
        │   └── GlobalExceptionHandler.java ← Centralised error responses
        ├── security/
        │   ├── JwtUtils.java               ← Token generation & validation
        │   ├── JwtAuthFilter.java          ← OncePerRequestFilter
        │   └── UserDetailsServiceImpl.java
        ├── entity/
        │   ├── User.java                   ← id, username, password, fullName, role
        │   └── Donation.java               ← Full donation model + enums
        ├── repository/
        │   ├── UserRepository.java
        │   └── DonationRepository.java
        ├── dto/
        │   ├── AuthDTOs.java               ← LoginRequest / LoginResponse / RegisterRequest
        │   ├── DonationDTOs.java           ← CreateRequest / DonationResponse
        │   └── AdminStatsDTO.java          ← Dashboard stats
        ├── service/
        │   ├── AuthService.java
        │   ├── DonationService.java
        │   ├── AdminService.java
        │   └── FreshnessService.java       ← Freshness score + risk logic
        └── controller/
            ├── AuthController.java
            ├── DonationController.java
            └── AdminController.java
