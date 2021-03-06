![AirBnB clone - The console](https://github.com/tatsOre/AirBnB_clone/blob/master/cover_hbnb.png)

## Description
This is the first step towards building a full web application: the AirBnB clone. This is the first stage to the project that will include the following: HTML/CSS templating, database storage, API, and front-end integration.

Each project's task is intended to:
* put in place a parent class (called BaseModel) to take care of the initialization, serialization and deserialization of instances.
* create a simple flow of serialization/deserialization: `Instance <-> Dictionary <-> JSON string <-> file`
* create all classes used for AirBnB (User, State, City, Place…) that inherit from BaseModel.
* create the first abstracted storage engine of the project: File storage.
* create all unittests to validate all classes and storage engine.

### Command interpreter functionalities:
* Create a new object (ex: a new User or a new Place)
* Retrieve an object from a file, a database etc…
* Do operations on objects (count, compute stats, etc…)
* Update attributes of an object
* Destroy an object

## Installation
All files are interpreted/compiled on Ubuntu 14.04 LTS using python3 (version 3.4.3)
* Clone repository: git clone "https://github.com/tatsOre/AirBnB_clone.git"
* Access to AirBnb directory: cd AirBnB_clone

## Execution
The console executes in non-interactive mode:
```bash
$ echo "help" | ./console.py
(hbnb)

Documented commands (type help <topic>):
========================================
EOF  all  create  destroy  help  quit  show  update
(hbnb) 
$
```
But also in interactive mode: **Use help command followed by [command] to get specific information about usage**
```bash
$ ./console.py
(hbnb) help

Documented commands (type help <topic>):
========================================
EOF  all  create  destroy  help  quit  show  update

(hbnb) help create

        Create command to create a new instance according Class name.
        Print the assigned id.
        Usage: create <class name>
        Classes: [BaseModel, User, Place, State, City, Amenity, Review]
        
(hbnb) 
(hbnb) quit
$
```
## Supported commands
|Command| Description |
|--|--|
| **create** | Creates a new instance based on the [class name], saves it (to a JSON file) and prints the [ID]. `$ create BaseModel` |
| **show** | Prints the string representation of an instance based on the [class name] and [ID]. `$ show BaseModel 1234-1234-1234` |
| **destroy** | Deletes an instance based on the [class name] and [ID] (saves changes into a JSON file). `$ destroy BaseModel 1234-1234-1234` |
| **all** | Prints all string representation of all instances based or not on the [class name]. `$ all BaseModel` or `$ all` | 
| **update** | Updates an instance based on the [class name] and [ID] by adding or updating attribute (saves changes into a JSON file). `$ update BaseModel 1234-1234-1234 email "airbnb@holbertonschool.com"`|
| **EOF** | Quits the program by EOF (CTRL+D) |
| **quit** | Exits the console |

## Alternative usage
|Command| Example |
|--|--|
|[class name].all()| BaseModel.all() |
|[class name].count()| BaseModel.count() |
|[class name].show()| BaseModel.show() |
|[class name].destroy()| BaseModel.destroy() |
|[class name].update([ID], [class attribute], [attribute value])| User.update("38f22813-2753-4d42-b37c-57a17f1e4f88", "first_name", "Thor") |
|(class name).update([ID], [dictionary])| User.update("38f22813-2753-4d42-b37c-57a17f1e4f88", {'first_name': "Charlie", "age": 30}) |

## Examples of use
* Create instances based on the Class Name and visualize them according ID, or class name:
```bash
$ ./console.py
(hbnb) create BaseModel
49faff9a-6318-451f-87b6-910505c55907
(hbnb)
(hbnb) all BaseModel
["[BaseModel] (49faff9a-6318-451f-87b6-910505c55907) {'created_at': datetime.datetime(2020, 10, 2, 3, 10, 25, 903293), 'id': '49faff9a-6318-451f-87b6-910505c55907', 'updated_at': datetime.datetime(2020, 10, 2, 3, 10, 25, 903300)}"]
(hbnb)
(hbnb) show BaseModel 49faff9a-6318-451f-87b6-910505c55907
[BaseModel] (49faff9a-6318-451f-87b6-910505c55907) {'created_at': datetime.datetime(2020, 10, 2, 3, 10, 25, 903293), 'id': '49faff9a-6318-451f-87b6-910505c55907', 'updated_at': datetime.datetime(2020, 10, 2, 3, 10, 25, 903300)}
(hbnb)
```
* Update or delete instances:
```bash
$ ./console.py
(hbnb) destroy
** class name missing **
(hbnb) destroy BaseModel 49faff9a-6318-451f-87b6-910505c55907
(hbnb) show BaseModel 49faff9a-6318-451f-87b6-910505c55907
** no instance found **
(hbnb)
(hbnb) show BaseModel 49faff9a-6318-451f-87b6-910505c55907
[BaseModel] (49faff9a-6318-451f-87b6-910505c55907) {'created_at': datetime.datetime(2020, 10, 2, 3, 10, 25, 903293), 'id': '49faff9a-6318-451f-87b6-910505c55907', 'updated_at': datetime.datetime(2020, 10, 2, 3, 10, 25, 903300)}
(hbnb) destroy
** class name missing **
(hbnb) update BaseModel 49faff9a-6318-451f-87b6-910505c55907 first_name "Betty"
(hbnb) show BaseModel 49faff9a-6318-451f-87b6-910505c55907
[BaseModel] (49faff9a-6318-451f-87b6-910505c55907) {'first_name': 'Betty', 'id': '49faff9a-6318-451f-87b6-910505c55907', 'created_at': datetime.datetime(2020, 10, 2, 3, 10, 25, 903293), 'updated_at': datetime.datetime(2020, 10, 2, 3, 11, 3, 49401)}
(hbnb)
```
* Count instances and update them from a dictionary: 
```bash
$ ./console.py
(hbnb) User.all()
["[User] (2fcc6d8d-ec16-4155-8683-ea92b9ab583b) {'id': '2fcc6d8d-ec16-4155-8683-ea92b9ab583b', 'created_at': datetime.datetime(2020, 6, 30, 15, 57, 55, 166650), 'updated_at': datetime.datetime(2020, 6, 30, 15, 57, 55, 166675)}", "[User] (785e3e40-8afd-443f-a737-4cfa475cc70c) {'id': '785e3e40-8afd-443f-a737-4cfa475cc70c', 'created_at': datetime.datetime(2020, 6, 30, 15, 58, 0, 386424), 'updated_at': datetime.datetime(2020, 6, 30, 15, 58, 0, 386444)}"]
(hbnb) User.count()
2
(hbnb) User.destroy("2fcc6d8d-ec16-4155-8683-ea92b9ab583b")
(hbnb) User.count()
1
(hbnb) User.destroy("Goodbye to All")
** no instance found **
(hbnb)
(hbnb) User.update("785e3e40-8afd-443f-a737-4cfa475cc70c", {'first_name': "Susie", 'age': 35, 'fav_band': "Joy Division"})
(hbnb) User.all()
["[User] (785e3e40-8afd-443f-a737-4cfa475cc70c) {'id': '785e3e40-8afd-443f-a737-4cfa475cc70c', 'created_at': datetime.datetime(2020, 6, 30, 15, 58, 0, 386424), 'updated_at': datetime.datetime(2020, 6, 30, 15, 58, 0, 386444), 'first_name': 'Susie', 'age': 35, 'fav_band': 'Joy Division'}"]
```

### Project Learning Objectives:
* How to create a Python package
* How to create a command interpreter in Python using the cmd module
* What is Unit testing and how to implement it in a large project
* How to serialize and deserialize a Class
* How to write and read a JSON file
* How to manage `datetime`
* What is an `UUID`
* What is `*args` and how to use it
* What is `**kwargs` and how to use it
* How to handle named arguments in a function

### Resources:
* [Python cmd Module](https://docs.python.org/3.4/library/cmd.html)
* [cmd – Create line-oriented command processors](https://pymotw.com/2/cmd/)
* [Python uuid Module](https://docs.python.org/3.4/library/uuid.html)
* [uuid — Universally Unique IDentifier](https://realpython.com/python-random/#one-last-candidate-uuid)
* [Python datetime Module](https://docs.python.org/3.4/library/datetime.html)
* [Datetime Module](https://realpython.com/python-datetime/#using-the-python-datetime-module)
* [Unit testing framework](https://docs.python.org/3.4/library/unittest.html#module-unittest)
* [Python Tutorial: Unit Testing Your Code with the unittest Module](https://www.youtube.com/watch?v=6tNS--WetLI&start=1828s)
* [A simple Python unittest](https://www.pythonsheets.com/notes/python-tests.html)
* [Args & Kwargs](https://realpython.com/python-kwargs-and-args/)
* [Python Packages](https://realpython.com/python-modules-packages/#python-packages)
* [How To Use *args and **kwargs in Python 3](https://www.digitalocean.com/community/tutorials/how-to-use-args-and-kwargs-in-python-3)
* [Regular Expressions: Regexes in Python (Part 1)](https://realpython.com/regex-python/)

### Authors:
* Juan Felipe Bustamante Muñoz | [Github](https://github.com/jfbm74)
* Tatiana Orejuela Zapata | [Github](https://github.com/tatsOre)

##### Holberton School - Foundations - Higher-level programming ― AirBnB clone
##### July, 2020. Cali, Colombia.