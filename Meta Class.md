## Meta Inner Class in Django Models

This is just a class container with some options (metadata) attached to the model. It defines such things as available permissions, associated database table name, whether the model is abstract or not, singular and plural versions of the name etc.

#### Meta options

Give your model metadata by using an inner class Meta, like so:

```python
from django.db import models

class Ox(models.Model):
    horn_length = models.IntegerField()

    class Meta:
        ordering = ["horn_length"]
        verbose_name_plural = "oxen"
```
Model metadata is “anything that’s not a field”, such as ordering options (ordering), database table name (db_table), or human-readable singular and plural names (verbose_name and verbose_name_plural). None are required, and adding class Meta to a model is completely optional.

A complete list of all possible Meta options 


* abstract

 Options.abstract

	If abstract = True, this model will be an abstract base class.


* app_label

 Options.app_label

	If a model is defined outside of an application in ```INSTALLED_APPS```, it must declare which app it belongs to:
```python
app_label = 'myapp'
```

* db_table

 Options.db_table

	The name of the database table to use for the model:
```python
db_table = 'music_album'
```

* get_latest_by

 Options.get_latest_by

	The name of a field or a list of field names in the model, typically DateField, DateTimeField, or IntegerField. This specifies the default field(s) to use in your model Manager’s latest() and earliest() methods.
```python
# Latest by ascending order_date.
get_latest_by = "order_date"

# Latest by priority descending, order_date ascending.
get_latest_by = ['-priority', 'order_date']
```

* ordering

 Options.ordering

	The default ordering for the object, for use when obtaining lists of objects:
```python
ordering = ['-order_date']
```
This is a tuple or list of strings and/or query expressions. Each string is a field name with an optional “-” prefix, which indicates descending order. Fields without a leading “-” will be ordered ascending. Use the string “?” to order randomly.

For example, to order by a pub_date field ascending, use this:
```python
ordering =['pub_date']
```
To order by pub_date descending, use this:
```python
ordering = ['-pub_date']
```
To order by pub_date descending, then by author ascending, use this:
```python
ordering = ['-pub_date', 'author']
```
You can also use query expressions. To order by author ascending and make null values sort last, use this:
```python
from django.db.models import F

ordering = [F('author').asc(nulls_last=True)]
```

* verbose_name

 Options.verbose_name

	A human-readable name for the object, singular:
```python
verbose_name = "pizza"
```

* verbose_name_plural

 Options.verbose_name_plural

	The plural name for the object:

```python
verbose_name_plural = "stories"
```
 > Source: Stackoverflow and Django Official Doc.
