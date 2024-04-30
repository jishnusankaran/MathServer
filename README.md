# Ex.05 Design a Website for Server Side Processing
## Date:3.4.2024 

## AIM:
To design a website to find surface area of a Right Cylinder in server side.

## FORMULA:
Surface Area = 2Πrh + 2Πr<sup>2</sup>
<br>r --> Radius of Right Cylinder
<br>h --> Height of Right Cylinder

## DESIGN STEPS:

### Step 1:
Clone the repository from GitHub.

### Step 2:
Create Django Admin project.

### Step 3:
Create a New App under the Django Admin project.

### Step 4:
Create python programs for views and urls to perform server side processing.

### Step 5:
Create a HTML file to implement form based input and output.

### Step 6:
Publish the website in the given URL.

## PROGRAM :
```
<!DOCTYPE html>
<html>
<head>
<title>Surface Of Area Right Cylinder</title>
<style type="text/css">
body {
    background-color: #CCCCFF;
}
.edge {
    width: 100%;
    padding-top: 50px; 
    text-align: center; 
}
.box {
    display: inline-block; 
    border: 2px ridge #800000; 
    width: 400px; 
    min-height: 200px; 
    font-size: 25px;
    background-color: #40E0D0;
    padding: 20px; 
}
.formelt {
    color: #DE3163;
    text-align: center;
    margin-top: 7px;
    margin-bottom: 6px;
}
h1 {
    color: black;
    text-align: center;
    padding-top: 20px;
}
</style>
</head>
<body>
  <div class="edge">
    <div class="box">
      <h3>JISHNUPRIYAN S(212223240061)</h3>
      <h1>Surface Of Area Right Cylinder</h1>
      <form method="POST">
        {% csrf_token %}
        <div class="formelt">
          Radius : <input type="text" name="radius" value="{{ r }}" required>(in m)<br/>
        </div>
        <div class="formelt">
          Height : <input type="text" name="height" value="{{ h }}" required>(in m)<br/>
        </div>
        <div class="formelt">
          <input type="submit" value="Calculate"></input><br/>
        </div>
        <div class="formelt">
          Area : <input type="text" name="surfacearea" value="{{ surfacearea }}" readonly>m<sup>2</sup><br/>
        </div>
      </form>
    </div>
  </div>
</body>
</html>
```
## urls.py
```
from django.contrib import admin
from django.urls import path
from mathapp import views
urlpatterns = [
    path('admin/', admin.site.urls),
    path('surfacearea/',views.surfacearea,name="surfacearea"),
    path('',views.surfacearea,name="surfacearearoot")
]
```

## views.py
```
from django.shortcuts import render
def surfacearea(request):
    context={}
    context['surfacearea'] = "0"
    context['r'] = "0"
    context['h'] = "0"
    if request.method == 'POST':
        print("POST method is used")
        r = request.POST.get('radius','0')
        h = request.POST.get('height','0')
        print('request=',request)
        print('radius=',r)
        print('height=',h)
        surfacearea = 2*3.14*int(r)*int(h) + 2*3.14*int(r)*int(r)
        context['surfacearea'] = surfacearea
        context['r'] = r
        context['h'] = h
        print('Area=',surfacearea)
    return render(request,'mathapp/math.html',context)
```
## SERVER SIDE PROCESSING:
![alt text](<Screenshot 2024-04-05 041517.png>)

## HOMEPAGE:
![alt text](<Screenshot 2024-04-05 041502.png>)

## RESULT:
The program for performing server side processing is completed successfully.
