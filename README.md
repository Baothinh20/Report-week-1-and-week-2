# Báo cáo tuần 1 và 2

## Người viết: Trần Bảo Thịnh
## Thông tin liên lạc:

  - Số điện thoại:0362993732
  - Gmail: tranbaothinh.2001@gmail.com
  - Github: https://github.com/Baothinh20

## Mục lục:
### I. Công việc được giao:
### II. Tiến trình công việc:
#### 1. Tổng quan:
#### 2. Cài đặt và thiết lập app Django cơ bản:
#### 3. Bổ sung:
#### 4. Debug:( Hiện tại các Debug em đã sửa được )
### III.Tài liệu tham khảo

-----

### I. Công việc được giao:

  - Tìm hiểu về Python Framework.
    - Cài đặt Python.
    - Cài đặt Pycharm
  - Tìm hiểu về Django:
    - Cài đặt Django theo hướng dẫn trên web https://docs.djangoproject.com/en/4.0/intro/install/.
    - Tìm hiểu về cách tạo 1 app cơ bản và có các tính năng (tạo poll để vote).
  - Tìm hiểu về Netbox:
    - Đọc sơ qua tài liệu trên git https://github.com/netbox-community/netbox.
  
### II. Tiến trình công việc:

  1. Tổng quan:
   - Python Framework là các đoạn code đã được viết sẵn, một bộ khung và các thư viện lập trình được đóng gói.
   - Django là Python Back-end framework tốt nhất vào những năm 2021 tới hiện tại.

   ![alt text](https://github.com/Baothinh20/Report/blob/main/image/Django.png?raw=true)
   
   - Điểm nổi bật chính:
      - Rất nhiều thư viện có sẵn.
      - Hệ thống xác nhận thông tin người dùng có sẵn.
      - Cơ sở dữ liệu hướng đối tượng giúp lưu trữ và phục hồi dữ liệu.
      - Trình quản lý admin tự động giúp sửa, thêm và xóa các tính năng.
      - Hệ thống cache mạnh mẽ.
      - 
   - Sơ qua về Netbox:
       
       ![alt text](https://github.com/Baothinh20/Report/blob/main/image/netbox.png?raw=true)
    
      - NetBox là một công cụ mô hình hóa tài nguyên cơ sở hạ tầng (IRM) được thiết kế để trao quyền tự động hóa mạng, được sử dụng bởi hàng nghìn tổ chức trên khắp           thế giới.
      - Vô số thành phần cơ sở hạ tầng có thể được mô hình hóa trong NetBox.
      - Ngoài các mô hình và chức năng tích hợp sẵn, NetBox có thể được tùy chỉnh và mở rộng theo nhiều cách.
      - NetBox cũng có API REST hoàn chỉnh cũng như API GraphQL.
      - NetBox là một ứng dụng web dựa trên Django Python với cơ sở dữ liệu PostgreSQL.
      - NetBox app stack.
      
      ![alt text](https://github.com/Baothinh20/Report/blob/main/image/netbox_app.png?raw=true)
      
  2. Cài đặt và thiết lập app Django cơ bản: (Step-by-step)
   - Cài đặt Pycharm theo web https://niithanoi.edu.vn/huong-dan-cai-dat-va-su-dung-pycharm-ide-trong-lap-trinh-python.html
   - Cài đặt Python 3.10 theo web https://www.python.org/downloads/release/python-3105/
   - Kiểm tra version để xem có chạy ổn định không:
    
    >py -m django --version

   - Tạo project:
      
    >django-admin startproject mysite
      
   - Các file đã đc tạo:

   ```bash
   mysite/
    manage.py
    mysite/
        __init__.py
        settings.py
        urls.py
        asgi.py
        wsgi.py
   ```
   - Ghi chú:
      - Thư mục gốc mysite/ ngoài cùng là container của project.
      - Thư mục mysite/ bên trong là package Python thực tế cho project
      - mysite/ __ init __ .py: là một file rỗng để đánh dấu đây là package của Python.
      - mysite/settings.py: Cài đặt/ cấu hình cho project này.
      - mysite/urls.py: Các khai báo URL cho project này, đóng vai trò làm router để hướng dẫn các request đến file xử lý phù hợp.
      - mysite/asgi.py và mysite/wsgi.py: file cấu hình cho server

    >py manage.py runserver
   
   - Tạo Poll app:
   
    >py manage.py startapp polls

   - Các file đã được tạo:
   
   ```bash
   mysite/
    manage.py
    mysite/
        __init__.py
        settings.py
        urls.py
        asgi.py
        wsgi.py
   ```
   
   - Tạo view cơ bản như web https://docs.djangoproject.com/en/4.0/intro/tutorial01/#writing-your-first-django-app-part-1
   - Ta cần điều hướng để có thể gọi view này -> chỉnh url
   - Để load được poll/urls.py vào trong mysite/urls.py thì ta phải thông qua lệnh “include“, muốn sử dụng được lệnh include thì bạn phải import nó từ packages “urls”
   
   - Thư mục mysite/urls.py hiện tại:
   ```bash
   from django.contrib import admin
   from django.urls import include, path

   urlpatterns = [
   path('polls/', include('polls.urls')),
   path('admin/', admin.site.urls),
   ]
   ```
   
   - Thiết lập cơ sở dữ liệu
      - Mở file mysite/settings.py.
      - Theo mặc định, cấu hình sử dụng SQLite.

         ```bash
          DATABASES = {
             'default': {
                 'ENGINE': 'django.db.backends.sqlite3',
                'NAME': BASE_DIR / 'db.sqlite3',
             }
          }
          ```
     
      - Nếu muốn sử dụng cơ sở dữ liệu khác, thay đổi từ khóa:
       - ENGINE -> 'django.db.backends.sqlite3', 'django.db.backends.postgresql', 'django.db.backends.mysql', or 'django.db.backends.oracle' etc.
       - NAME : Tên cơ sở dữ liệu

   - Nếu không sử dụng SQLite làm cơ sở dữ liệu của mình, các cài đặt bổ sung như USER, PASSWORDvà HOST phải được thêm vào.
   - INSTALLED_APPS chứa tên của tất cả các ứng dụng Django được kích hoạt trong phiên bản Django này.
       - django.contrib.admin- Trang web quản trị.
       - django.contrib.auth- Một hệ thống xác thực.
       - django.contrib.contenttypes- Một khung cho các loại nội dung.
       - django.contrib.sessions- Một khung phiên.
       - django.contrib.messages- Một khung nhắn tin.
       - django.contrib.staticfiles- Một khung để quản lý các tệp tĩnh.
   - Lệnh migrate sẽ tạo các cơ sở dữ liệu cần thiết dựa trên co sở dữ liệu ở mysite/settings.py
   - Tạo model:
       - Tạo model trong polls/models.py
       - Với poll app chỉ cần 2 model Question and Choice
       - Thư mục sau khi sửa
          ```bash
          from django.db import models

          class Question(models.Model):
              question_text = models.CharField(max_length=200)
              pub_date = models.DateTimeField('date published')


          class Choice(models.Model):
              question = models.ForeignKey(Question, on_delete=models.CASCADE)
              choice_text = models.CharField(max_length=200)
              votes = models.IntegerField(default=0)
          ```
       - Mỗi mô hình được đại diện bởi một lớp phân lớp con django.db.models.Model. Mỗi mô hình có một số biến lớp, mỗi biến đại diện cho một trường cơ sở dữ liệu            trong mô hình.
       - Mỗi trường được đại diện bởi một thể hiện của một lớp Field
      
   - Kích hoạt model:
       - Thêm 'polls.apps.PollsConfig' vào mysite/settings.py để đưa ứng dụng vào project
       - Thư mục sau khi sửa
          ```bash
          INSTALLED_APPS = [
              'polls.apps.PollsConfig',
              'django.contrib.admin',
              'django.contrib.auth',
              'django.contrib.contenttypes',
              'django.contrib.sessions',
              'django.contrib.messages',
              'django.contrib.staticfiles',
          ]
          ```
        - Chạy lệnh:
          ```bash
          python manage.py makemigrations polls
          ```
        - Xuất hiện những dòng lệnh:
          ```bash
          Migrations for 'polls':
          polls/migrations/0001_initial.py
              - Create model Question
              - Create model Choice
          ```
       - Khi chạy lệnh makemigrations tức là ta đang thực hiện một số thay đổi trong model và các thay đổi đấy lưu ở dạng migration ( phần này em không hiểu lắm )
       - Lệnh sqlmigrate lấy tên migration và trả về SQL mà migration chạy.( Ở đây sử dụng PostgreSQL )
          ```bash
          py manage.py sqlmigrate polls 0001
          ```
       - Chạy lệnh migrate để tạo các model trong cơ sở dữ liệu
       - Note: Run python manage.py makemigrations to create migrations for those changes. Run python manage.py migrate to apply those changes to the database.
   - Cài đặt API:

          ```
          py manage.py shell
          
          >>> from polls.models import Choice, Question  # Import the model classes we just wrote.

          # No questions are in the system yet.
          >>> Question.objects.all()
          <QuerySet []>

          # Create a new Question.
          # Support for time zones is enabled in the default settings file, so
          # Django expects a datetime with tzinfo for pub_date. Use timezone.now()
          # instead of datetime.datetime.now() and it will do the right thing.
          >>> from django.utils import timezone
          >>> q = Question(question_text="What's new?", pub_date=timezone.now())

          # Save the object into the database. You have to call save() explicitly.
          >>> q.save()

          # Now it has an ID.
          >>> q.id
          1

          # Access model field values via Python attributes.
          >>> q.question_text
          "What's new?"
          >>> q.pub_date
          datetime.datetime(2012, 2, 26, 13, 0, 0, 775217, tzinfo=<UTC>)

          # Change values by changing the attributes, then calling save().
          >>> q.question_text = "What's up?"
          >>> q.save()

          # objects.all() displays all the questions in the database.
          >>> Question.objects.all()
          <QuerySet [<Question: Question object (1)>]>
          ```
       - Sửa file polls/models.py:
       
          ```bash
          from django.db import models

          class Question(models.Model):
              # ...
              def __str__(self):
                  return self.question_text
              def was_published_recently(self):
                  return self.pub_date >= timezone.now() - datetime.timedelta(days=1)

          class Choice(models.Model):
              # ...
              def __str__(self):
                  return self.choice_text
           ```
       - Lưu thay đổi:

          ```bash
          >>> from polls.models import Choice, Question

          # Make sure our __str__() addition worked.
          >>> Question.objects.all()
          <QuerySet [<Question: What's up?>]>

          # Django provides a rich database lookup API that's entirely driven by
          # keyword arguments.
          >>> Question.objects.filter(id=1)
          <QuerySet [<Question: What's up?>]>
          >>> Question.objects.filter(question_text__startswith='What')
          <QuerySet [<Question: What's up?>]>

          # Get the question that was published this year.
          >>> from django.utils import timezone
          >>> current_year = timezone.now().year
          >>> Question.objects.get(pub_date__year=current_year)
          <Question: What's up?>

          # Request an ID that doesn't exist, this will raise an exception.
          >>> Question.objects.get(id=2)
          Traceback (most recent call last):
              ...
          DoesNotExist: Question matching query does not exist.

          # Lookup by a primary key is the most common case, so Django provides a
          # shortcut for primary-key exact lookups.
          # The following is identical to Question.objects.get(id=1).
          >>> Question.objects.get(pk=1)
          <Question: What's up?>

          # Make sure our custom method worked.
          >>> q = Question.objects.get(pk=1)
          >>> q.was_published_recently()
          True

          # Give the Question a couple of Choices. The create call constructs a new
          # Choice object, does the INSERT statement, adds the choice to the set
          # of available choices and returns the new Choice object. Django creates
          # a set to hold the "other side" of a ForeignKey relation
          # (e.g. a question's choice) which can be accessed via the API.
          >>> q = Question.objects.get(pk=1)

          # Display any choices from the related object set -- none so far.
          >>> q.choice_set.all()
          <QuerySet []>

          # Create three choices.
          >>> q.choice_set.create(choice_text='Not much', votes=0)
          <Choice: Not much>
          >>> q.choice_set.create(choice_text='The sky', votes=0)
          <Choice: The sky>
          >>> c = q.choice_set.create(choice_text='Just hacking again', votes=0)

          # Choice objects have API access to their related Question objects.
          >>> c.question
          <Question: What's up?>

          # And vice versa: Question objects get access to Choice objects.
          >>> q.choice_set.all()
          <QuerySet [<Choice: Not much>, <Choice: The sky>, <Choice: Just hacking again>]>
          >>> q.choice_set.count()
          3

          # The API automatically follows relationships as far as you need.
          # Use double underscores to separate relationships.
          # This works as many levels deep as you want; there's no limit.
          # Find all Choices for any question whose pub_date is in this year
          # (reusing the 'current_year' variable we created above).
          >>> Choice.objects.filter(question__pub_date__year=current_year)
          <QuerySet [<Choice: Not much>, <Choice: The sky>, <Choice: Just hacking again>]>

          # Let's delete one of the choices. Use delete() for that.
          >>> c = q.choice_set.filter(choice_text__startswith='Just hacking')
          >>> c.delete()
           ```
   - Chỉnh sửa giao diện và thêm đường dẫn:
     - Sửa file  polls/views.py:

          ```bash
          def detail(request, question_id):
              return HttpResponse("You're looking at question %s." % question_id)

          def results(request, question_id):
              response = "You're looking at the results of question %s."
              return HttpResponse(response % question_id)

          def vote(request, question_id):
              return HttpResponse("You're voting on question %s." % question_id)
           ```
           
     - Sửa file  polls/url.py:

           ```bash
            from django.urls import path

            from . import views
            urlpatterns = [
                # ex: /polls/
                path('', views.index, name='index'),
                # ex: /polls/5/
                path('<int:question_id>/', views.detail, name='detail'),
                # ex: /polls/5/results/
                path('<int:question_id>/results/', views.results, name='results'),
                # ex: /polls/5/vote/
                path('<int:question_id>/vote/', views.vote, name='vote'),
            ]
           ```
           
     - Mỗi view chịu trách nghiệm cho việc trả về HttpResponse khi việc kết nối hoàn tất hoặc trả về  Http404 khi xuất hiện lỗi.

     - Sửa file  polls/view.py:

           ```bash
           Phần này em chưa hiểu kĩ ạ. Hình như chỉ để hiện pub_date khi thay đổi question.
            from django.http import HttpResponse

            from .models import Question


            def index(request):
                latest_question_list = Question.objects.order_by('-pub_date')[:5]
                output = ', '.join([q.question_text for q in latest_question_list])
                return HttpResponse(output)

           # Leave the rest of the views (detail, results, vote) unchanged
           ```
     - Đặt Template:

           ```bash
            {% if latest_question_list %}
                <ul>
                {% for question in latest_question_list %}
                    <li><a href="{% url 'polls:detail' question.id %}">{{ question.question_text }}</a></li>
                {% endfor %}
                </ul>
            {% else %}
                <p>No polls are available.</p>
            {% endif %}
           ```
           
     - Update index view:

           ```bash
            from django.http import HttpResponse
            from django.template import loader

            from .models import Question


            def index(request):
                latest_question_list = Question.objects.order_by('-pub_date')[:5]
                template = loader.get_template('polls/index.html')
                context = {
                    'latest_question_list': latest_question_list,
                }
                return HttpResponse(template.render(context, request))
           ```
     - Hiển thị Http404:
     - Chỉnh sửa file: polls/view.py
           ```bash
            from django.http import Http404
            from django.shortcuts import render

            from .models import Question
            # ...
            def detail(request, question_id):
                try:
                    question = Question.objects.get(pk=question_id)
                except Question.DoesNotExist:
                    raise Http404("Question does not exist")
                return render(request, 'polls/detail.html', {'question': question})
           ```

     - Tạo polls/template/polls/detail.html template:
           ```bash
            from django.urls import path

            from . import views

            app_name = 'polls'
            urlpatterns = [
                path('', views.index, name='index'),
                path('<int:question_id>/', views.detail, name='detail'),
                path('<int:question_id>/results/', views.results, name='results'),
                path('<int:question_id>/vote/', views.vote, name='vote'),
            ]
           ```

   - Tối giản hóa code (Ở đây em áp dụng các cách tối giản của tutorial04) : 
        https://docs.djangoproject.com/en/4.0/intro/tutorial04/

   - Tạo các Test cho app của mình: 
        https://docs.djangoproject.com/en/4.0/intro/tutorial05/

   - Sử dụng Css để làm đẹp web : 
        https://docs.djangoproject.com/en/4.0/intro/tutorial06/
        
   - Chỉnh sửa mẫu admin : 

           ```bash
              from django.contrib import admin

              # Register your models here.
              from django.contrib import admin

              from .models import Choice,Question

              class ChoiceInline(admin.TabularInline):
                  model = Choice
                  extra = 3


              class QuestionAdmin(admin.ModelAdmin):
                  fieldsets = [
                      (None,               {'fields': ['question_text']}),
                      ('Date information', {'fields': ['pub_date'], 'classes': ['collapse']}),
                  ]
                  inlines = [ChoiceInline]
                  list_display = ('question_text', 'pub_date', 'was_published_recently')
                  list_filter = ['pub_date']
                  search_fields = ['question_text']

              admin.site.register(Question, QuestionAdmin)
           ```
           
  3. Bổ sung:

   - Cài netbox trên ubuntu (20.04). https://docs.netbox.dev/en/stable/installation/
      - Vì quá trình cài không có lỗi nên các bước làm em làm giống tutorial và em đã cài các phần mềm PostgreSQL Database, Redis, Gunicorn, HTTP Server Setup (Apache)       để hỗ trợ cho netbox.
   - Tìm hiểu thêm về cách phát triển netbox: https://docs.netbox.dev/en/stable/development/
   - Tạo thêm nhánh Storage và thêm các tính năng như hiển thị model, add, delete, etc. 
    
### III.Tài liệu tham khảo
  - https://topdev.vn/blog/framework-la-gi/.
  - https://niithanoi.edu.vn/huong-dan-cai-dat-va-su-dung-pycharm-ide-trong-lap-trinh-python.html
  - https://www.jetbrains.com/help/pycharm/installation-guide.html#silent
  - https://t3h.edu.vn/tin-tuc/top-framework-python-hoan-hao-danh-cho-lap-trinh-vien.
  - https://www.python.org/downloads/release/python-3105/
  - https://vn.got-it.ai/blog/python-back-end-framework#:~:text=Python%20Back%2Dend%20framework%20l%C3%A0,v%C3%A0%20c%C3%B4ng%20d%E1%BB%A5ng%20kh%C3%A1c%20nhau.
  - https://docs.djangoproject.com/en/4.0/intro/install/.
  - https://docs.djangoproject.com/en/4.0/intro/tutorial01/#writing-your-first-django-app-part-1 to part 7.
  - https://docs.djangoproject.com/en/4.0/intro/reusable-apps/.
  - https://github.com/netbox-community/netbox.
  - https://docs.netbox.dev/en/stable/
  - https://computingforgeeks.com/install-and-configure-netbox-ipam-dcim-tool-on-ubuntu/.
  - https://computingforgeeks.com/installing-postgresql-database-server-on-ubuntu/.
  - https://news.cloud365.vn/tag/netbox/
  - Extra:
    - https://howkteam.vn/course/upload-file-trong-lap-trinh-website-voi-python/tao-mot-web-app-va-xu-ly-khi-nguoi-dung-yeu-cau-truy-cap-trong-python-django-1517.
  - Demo:
    - https://demo.netbox.dev/.
