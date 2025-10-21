# Ex.05 Design a Website for Server Side Processing
## Date:12-10-2025

## AIM:
 To design a website to calculate the power of a lamp filament in an incandescent bulb in the server side. 


## FORMULA:
P = I<sup>2</sup>R
<br> P --> Power (in watts)
<br> I --> Intensity
<br> R --> Resistance

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
bmi.html:
<html>
    <head>
        <title>BMI Calculator</title>
        <style>
            
            form{
                text-align: center;
                margin-top: 13%;
                margin-left: 36%;
                width: 350px;
                /* border: 5px solid rgb(9, 5, 1); */
                padding: 2%;
                border-radius: 15px;
                box-shadow: 0 4px 12px rgba(0, 0, 0, 0.2);
                background-color: white;
            }
            label{
                font-size: 18px;
                font-weight: bold;
            }
            div{
                margin: 10px;
            }
            input{
                width: 200px;
                height: 25px;
                border-radius: 5px;
                border: 1px solid gray;
                padding: 5px;
            }
        </style>
    </head>
    <body style="background-color: rgb(210, 215, 215);">
        <form method="post">
            <h1 style="color: rgb(57, 2, 160)">BMI Calculator</h1>
          {% csrf_token %}
            <div>
                <label>Height (cm):</label>
                <input type="text" name="height">
            </div>
            
            <div>
                <label>Weight (kg):</label>
                <input type="text" name="weight"><br>
            </div>
            
            <div>
                <button type="submit">Calculate</button>
            </div>
             
            <div>
                {% if BMI %}
                <h3>Your BMI is: {{ BMI }}</h3>
                {% endif %}
            </div>
            
            
        </form>      
    </body>
</html>

views.py:
from django.shortcuts import render

def calculate_bmi(request):
    bmi = None

    if request.method == "POST":
        try:
            height_cm = float(request.POST.get("height"))
            weight_kg = float(request.POST.get("weight"))
            height_m = height_cm / 100  # convert cm to meters
            
            bmi = weight_kg / (height_m * height_m)

            print(f"Calculated BMI: {bmi:.2f}")  # Output to console

        except (TypeError, ValueError, ZeroDivisionError):
            bmi = None

    return render(request, "server_side_processing/bmi.html", {"BMI": bmi})

urls.py:
from django.urls import path
from . import views 
urlpatterns = [
    path('', views.calculate_bmi, name='bmi'),
]
```

## OUTPUT:
![alt text](<Screenshot 2025-10-21 180848.png>) ![alt text](<Screenshot 2025-10-21 181109.png>) ![alt text](<Screenshot 2025-10-21 181123.png>) ![alt text](<Screenshot 2025-10-21 181159.png>)


## RESULT:
The program for performing server side processing is completed successfully.
