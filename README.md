# Trying to integrate django-react 

## 1. create Virtual Envivronment & run shell 

### Install virtual environment
       pip install pipenv

### Create python virtual environment 
      pipenv install 

### Install django inside virtual environment
      pipenv install django


### start virtual enviroment 
      run shell


## 2. create react app(e.g : reactapp)
### create react app and downloads essential files to run react using npm
      npx create-react-app reactapp
      
### change directory inside reactapp than start npm 
      cd reactapp && npm start

### create reactapp for production here we can see than we do have a build folder for production inside build.we can see static files which consists css,js and different static files.

      npm run build



## 3. create django project(e.g : myproject)

### create django project
      django-admin start project myproject 
 

### 3.1 In setting.py of myproject

#### Add template path to react build. 
     os.path.join(BASE_DIR, 'reactapp/build'), 

#### TEMPLATES :arrow_right: DIRS :warning:

    TEMPLATES = [
        {
            'BACKEND': 'django.template.backends.django.DjangoTemplates',
            'DIRS': [
                os.path.join(BASE_DIR, 'reactapp/build'),
            ],

            'APP_DIRS': True,
            'OPTIONS': {
                'context_processors': [
                    'django.template.context_processors.debug',
                    'django.template.context_processors.request',
                    'django.contrib.auth.context_processors.auth',
                    'django.contrib.messages.context_processors.messages',
                ],
            },
        },
    ]


#### Also add staticfiles directories

    STATICFILES_DIRS  = [

         os.path.join(BASE_DIR, 'reactapp/build/static'),

    ]

### 3.2 In urls.py of myproject

#### import TemplateView

      from django.views.generic import TemplateView
      
#### Add path to TemplateView which refers to react :arrow_right: index.html

      urlpatterns = [
    
             path(' ',TemplateView.as_view(template_name = 'index.html')),
             
              ]
