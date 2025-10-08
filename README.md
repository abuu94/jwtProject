# jwtProject
Boiler Plate for Authorisation and Authentication


**Django REST Framework (DRF) is the core toolkit for building REST APIs in Django, while djangorestframework-simplejwt is an add-on specifically for handling JWT-based authentication within DRF.**

Here’s a breakdown of their roles and differences:

---

### 🧰 **Django REST Framework (DRF)**
**Purpose:**  
DRF is a powerful and flexible toolkit for building Web APIs in Django.

**Key Features:**
- **Serialization:** Converts Django models to JSON and vice versa.
- **Viewsets and Routers:** Simplifies URL routing and view logic.
- **Authentication & Permissions:** Built-in support for basic, session, and token authentication.
- **Browsable API:** Automatically generates a user-friendly web interface for testing endpoints.

**Use Case:**  
You use DRF when you want to expose your Django models and business logic as RESTful APIs. It’s the foundation for any API work in Django.

---

### 🔐 **djangorestframework-simplejwt**
**Purpose:**  
This is a plugin for DRF that adds support for **JSON Web Token (JWT)** authentication.

**Key Features:**
- **Access and Refresh Tokens:** Issues short-lived access tokens and long-lived refresh tokens.
- **Stateless Authentication:** No need to store tokens in the database.
- **Custom Claims:** Allows embedding user data in the token payload.
- **Token Blacklisting (optional):** Can revoke tokens if needed.

**Use Case:**  
Use this when you want secure, scalable, stateless authentication for your DRF APIs—especially useful for mobile apps or single-page applications (SPAs) like React or Angular.

---

### 🔍 **Key Differences**
| Feature | Django REST Framework | djangorestframework-simplejwt |
|--------|------------------------|-------------------------------|
| Scope | Full API toolkit | JWT authentication plugin |
| Authentication | Basic, Session, Token | JWT (Access + Refresh) |
| Token Storage | Server-side (for TokenAuth) | Client-side (stateless) |
| Use Alone? | Yes | No, requires DRF |
| Ideal For | Building APIs | Securing APIs with JWT |

Sources: 

---

If you're building an API and need secure login/logout with token-based access, you'd use **DRF** as your base and **simplejwt** to handle authentication. Want help setting them up together?
