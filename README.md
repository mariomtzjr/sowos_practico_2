# Examen 2

## Pregunta
Queremos agregar un timestamp de created_at a los modelos creados anterior mente. Escriba los cambios a continuacion. Incluyendo los comandos asociados para que django aplique los cambios.
```
class Customer(models.Model):
    created_at = models.DateTimeField(auto_now=True)

class Person(models.Model):
    created_at = models.DateTimeFied(auto_now=True)

class Person(models.Model):
    created_at = models.DateTimeFied(auto_now=True)

class User(models.Model):
    created_at = models.DateTimeField(auto_now=True)
```  

Seguido de `python manage.py makemigrations && python manage.py migrate`

## Pregunta
Dado este diagrama ER escriba los modelos necesarios para que django pueda hacer mapping a estas tablas
```
class User(models.Model):
    id = models.IntegerField()
    uuid = models.CharField(max_lenght=36)

class Person(models.Model):
    id = models.IntegerField()
    user_id = models.ForeigKey(User, on_delete=models.CASCADE)
    name = models.CharField(max_lenght=200)
    last_name = models.CharField(max_lenght=200)

class Customer(models.Model):
    id = models.IntegerField()
    person_id = models.ForeignKey(Person, on_delete=models.SET_NULL)
```
## Pregunta
Se nos ha encargado consumir una api https://swapi.dev/documentation se requiere obtener al personaje Luke Skywalker e imprimir por pantalla su nombre completo su genero y las naves que a piloteado. Escriba la función que puede realizar esta tarea

```
import requests
import json

response = requests.get('https://swapi.dev/api/people/1/')
response = response.text
response = json.loads(response)

nombre = response['name']
genero = response['gender']
naves = [json.loads(requests.get(url).text)['name'] for url in response['starships']]

print(f"Nombre: {nombre}; Género: {genero}, naves: {naves}")
```
