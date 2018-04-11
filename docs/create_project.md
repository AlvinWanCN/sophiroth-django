

## How to create a django project.

### step 1:   prepare a directory

You will create a project at this directory D:\gitcenter\

```cmd
D:
cd gitcenter

```

### step2: create a django project

now we create a django project and named djangotest

```cmd
django-admin startproject djangotest
```

### step3: enter the project directory and startup service


```cmd
cd djangotest
python manage.py runserver 0.0.0.0:8080
```


##### 不指定IP和端口

直接在第三步中，如果不指定ip和端口，直接执行 python manage.py runserver， 则是默认使用127.0.0.1和8080端口，执行IP和端口后，则用我们执行的。

### step4: visit django web

after step3 done, you can visit the django web now.

url:   localhost:8080





