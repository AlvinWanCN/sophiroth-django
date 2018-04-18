
##

将sophiroth应用里的User模块加入到admin里去，使得我们可以通过admin管理它。

```bash
# vim sophiroth/admin.py

from django.contrib import admin
from sophiroth.models import *
# Register your models here.


class UserAdmin(admin.ModelAdmin):
    list_display = ['username','email']
    search_fields = ['user']

admin.site.register(User,UserAdmin)
```