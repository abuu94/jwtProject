## If admin faile to be created via createsuperuser then use shell
from shop.models import CustomUser
admin = CustomUser.objects.get(username='your_admin_username')
admin.role = 'admin'
admin.save()
