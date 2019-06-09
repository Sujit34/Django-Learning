#### reverse() function: It’s similar to the url template tag which use to convert namespaced url to real url pattern.


#### reverse_lazy() function: This is a reverse() function’s lazy version. It’s prevent to occur error when URLConf is not loaded. Generally we use this function in case below:

 * providing a reversed URL as the url attribute of a generic class-based view.
 * providing a reversed URL to a decorator (such as the login_url argument for the django.contrib.auth.decorators.permission_required() decorator)
 * providing a reversed URL as a default value for a parameter in a function’s signature.

