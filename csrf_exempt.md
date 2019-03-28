# @csrf_exempt ?

#### Csrf exempt is a cool feature of django which allows bypassing of csrf verification by django.

By default, django check for csrf token with each POST request, it verifies csrf token before rendering the view. Its a very good security practice to verify csrf of post requests as we know django can’t be compromised in case of security.



##### Then why do we need csrf_exempt??
The answer is simple, to customize django view. In some cases we do not need csrf validations, e.g for public APIs, common AJAX request, REST APIs. 

#### To suppress csrf verification message, we can use @csrf_exempt decorator for specific view.

```python
from django.views.decorators.csrf import csrf_exempt
from django.http import HttpResponse

@csrf_exempt
def public_api(request):
    if request.method=='POST':
       return HttpResponse('API hit with post method')
```
Above API will allow a post call without adding csrf parameter in it. 




