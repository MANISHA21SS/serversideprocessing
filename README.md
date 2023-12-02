# Design a Website for Server Side Processing

## AIM:
To design a website to perform mathematical calculations in server side.

## DESIGN STEPS:

### Step 1:
clone the repository from github.
### Step 2:
create django admin project.
### Step 3:
create a new app.
### Step 4:
create a python programs for views and urls.
### Step 5:
create a HTML file of forms.
### Step 6:
Publish the website in the given URL.
## PROGRAM
~~~
math.html
<html>
<head>
<meta charset='utf-8'>
<meta http-equiv='X-UA-Compatible' content='IE=edge'>
<title>Area of prism</title>
<meta name='viewport' content='width=device-width, initial-scale=1'>
<style type="text/css">
body 
{
background-color:cyan;
}
.edge {
width: 1080px;
margin-left: auto;
margin-right: auto;
padding-top: 200px;
padding-left: 300px;
}
.box {
display:block;
border: Thick dashed lime;
width: 500px;
min-height: 300px;
font-size: 20px;
background-color: purple;
}
.formelt{
color: Red;
text-align: center;
margin-top: 5px;
margin-bottom: 5px;
}
h1
{
color: yellow;
text-align: center;
padding-top: 20px;
}
</style>
</head>
<body>
<div class="edge">
<div class="box">
<h1>Area of a prism</h1>
<form method="POST">
{% csrf_token %}
<div class="formelt">
side : <input type="text" name="side" value="{{s}}"></input>(in 
m)<br/>
</div>
<div class="formelt">
height : <input type="text" name="height" value="{{h}}">
</input>(in m)<br/>
</div>
<div class="formelt">
<input type="submit" value="Calculate"></input><br/>
</div>
<div class="formelt">
Area : <input type="text" name="area" value="{{area}}">
</input>m<sup>2</sup><br/>
</div>
</form>
</div>
</div>
</body>
</html>
views.py:

from django.shortcuts import render
def rectarea(request):
    context={}
    context['area'] = "0"
    context['l'] = "0"
    context['b'] = "0"
    if request.method == 'POST':
        print("POST method is used")
        l = request.POST.get('length','0')
        b = request.POST.get('breadth','0')
        print('request=',request)
        print('Length=',l)
        print('Breadth=',b)
        area = int(l) * int(b)
        context['area'] = area
        context['l'] = l
        context['b'] = b
        print('Area=',area)
    return render(request,'myapp/math.html',context)

urls.py:

from django.contrib import admin
from django.urls import path
from myapp import views
urlpatterns = [
    path('admin/', admin.site.urls),
    path('areaofrectangle/',views.rectarea,name="areaofrectangle"),
    path('',views.rectarea,name="areaofrectangleroot")
]
~~~
## OUTPUT:
![Screenshot (71)](https://github.com/MANISHA21SS/serversideprocessing/assets/147474298/231bfccd-139c-4563-a82f-e9c176758f10)

### Home Page:
![Screenshot (72)](https://github.com/MANISHA21SS/serversideprocessing/assets/147474298/506405d6-50c1-4599-a1d6-40242074d01f)

## Result:
The program for server side processing is completed successfully.
