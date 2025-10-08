Great use cases! Let’s break down how to build both projects using **Django REST Framework (DRF)** and **djangorestframework-simplejwt** for secure, scalable APIs with role-based access.

---

## 🛒 **Online Shopping Platform**
**Users:** Admin, Customer, Seller  
**Core Features:**
- Product listing and management (by sellers)
- Order placement and tracking (by customers)
- Admin dashboard for user and product oversight

### 🔧 Setup Strategy
1. **Install DRF and SimpleJWT**
   ```bash
   pip install djangorestframework djangorestframework-simplejwt
   ```

2. **Configure JWT in `settings.py`**
   ```python
   REST_FRAMEWORK = {
       'DEFAULT_AUTHENTICATION_CLASSES': (
           'rest_framework_simplejwt.authentication.JWTAuthentication',
       ),
   }
   ```

3. **Define User Roles**
   Extend Django’s `AbstractUser` or use a `Profile` model with a `role` field:
   ```python
   class CustomUser(AbstractUser):
       ROLE_CHOICES = (
           ('admin', 'Admin'),
           ('customer', 'Customer'),
           ('seller', 'Seller'),
       )
       role = models.CharField(max_length=10, choices=ROLE_CHOICES)
   ```

4. **Create Role-Based Permissions**
   Use custom permissions to restrict access:
   ```python
   class IsSeller(BasePermission):
       def has_permission(self, request, view):
           return request.user.role == 'seller'
   ```

5. **Secure Endpoints**
   Apply permissions to views:
   ```python
   class ProductCreateView(CreateAPIView):
       permission_classes = [IsAuthenticated, IsSeller]
       ...
   ```

6. **Token Authentication**
   Use JWT for login:
   ```python
   from rest_framework_simplejwt.views import TokenObtainPairView, TokenRefreshView
   ```

---

## 🎓 **Academic Institution Website**
**Users:** Admin, Translator  
**Core Features:**
- Admin uploads documents
- Translators access and submit translations
- Role-based access to document types

### 🔧 Setup Strategy
1. **Same JWT and DRF setup as above**

2. **User Model**
   ```python
   class CustomUser(AbstractUser):
       ROLE_CHOICES = (
           ('admin', 'Admin'),
           ('translator', 'Translator'),
       )
       role = models.CharField(max_length=10, choices=ROLE_CHOICES)
   ```

3. **Permissions**
   ```python
   class IsTranslator(BasePermission):
       def has_permission(self, request, view):
           return request.user.role == 'translator'
   ```

4. **Views**
   - Admin-only document upload
   - Translator-only document access and submission

---

## 🔐 JWT Token Flow
- **Login:** Users get access and refresh tokens
- **Access Token:** Short-lived, used for API calls
- **Refresh Token:** Long-lived, used to renew access token

---

## 🧠 Tips
- Use **ViewSets** and **Routers** for cleaner URL management
- Add **Swagger or DRF Spectacular** for API documentation
- Consider **Token Blacklisting** if you need logout functionality

---

Would you like a sample folder structure or code snippets for one of these projects?
