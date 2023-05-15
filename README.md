![logo](https://github.com/Dikachi-official/AirBnB_clone/assets/86185353/40521c73-a3f3-4481-afe6-96efdbc3a6e8)
<h1>0x00. AirBnB clone - The console</h1>
<h3>Description</h3>
<p>This is a complete web application, integrating database storage, a back-end API, and front-end interfacing in a clone of AirBnB.
</p>
<h3>Classes</h3>
<strong>The project has the following classes:</strong>
<ul>
<li>BaseModel</li>
<li>User</li>
<li>State</li>
<li>City</li>
<li>Place</li>
<li>Amenity</li>
<li>Review</li>
<li>Storage</li>
</ul>

<p>The above classes are handled by the abstracted storage engine defined in the FileStorage class.
</p>

<p>
Every time the backend is initialized, hbnb instantiates an instance of FileStorage called storage. The storage object is loaded/re-loaded from any class instances stored in the JSON file file.json. As class instances are created, updated, or deleted, the storage object is used to register corresponding changes in the file.json.
</p>

<h3>Console</h3>
<p>
The console is a command line interpreter that permits management of the backend of hbnbBnB. It can be used to handle and manipulate all classes utilized by the application (achieved by calls on the storage object defined above).
</p>
<h3>Using the Console</h3>
<p>
The hbnbBnB console can be run both interactively and non-interactively. To run the console in non-interactive mode, pipe any command(s) into an execution of the file console.py at the command line.
</p>

$ echo "help" | ./console.py
(hbnb) 
Documented commands (type help <topic>):
========================================
EOF  all  count  create  destroy  help  quit  show  update

(hbnb) 
$
```html

Alternatively, to use the hbnb console in interactive mode, run the
file `console.py` by itself:

```html
./console.py
While running in interactive mode, the console displays a prompt for input:

$ ./console.py
(hbnb) 
To quit the console, enter the command quit, or input an EOF signal (ctrl-D).

$ ./console.py
(hbnb) quit
$
$ ./console.py
(hbnb) EOF
$
Console Commands
The hbnb console supports the following commands:

create
Usage: create <class>
Creates a new instance of a given class. The class' ID is printed and the instance is saved to the file file.json.

$ ./console.py
(hbnb) create BaseModel
5fe40558-76e4-4331-aac5-9ada7acd550d
(hbnb) quit
$ cat file.json ; echo ""
{"BaseModel.5fe40558-76e4-4331-aac5-9ada7acd550d": {"id": "5fe40558-76e4-4331-aac5-9ada7acd550d", "created_at": "2022-08-06T21:46:16.635887", "updated_at": "2022-08-06T21:46:16.635887", "__class__": "BaseModel"}}
show
Usage: show <class> <id> or <class>.show(<id>)
Prints the string representation of a class instance based on a given id.

$ ./console.py
(hbnb) create User
d27f7b98-7245-4242-8134-3510f2f411ad
(hbnb)
(hbnb) show User d27f7b98-7245-4242-8134-3510f2f411ad
['type'] d27f7b98-7245-4242-8134-3510f2f411ad {'id': 'd27f7b98-7245-4242-8134-3510f2f411ad', 'created_at': datetime.datetime(2022, 8, 6, 21, 48, 0, 796174), 'updated_at': datetime.datetime(2022, 8, 6, 21, 48, 0, 796174)}
(hbnb) 
(hbnb) User.show(d27f7b98-7245-4242-8134-3510f2f411ad)
['type'] d27f7b98-7245-4242-8134-3510f2f411ad {'id': 'd27f7b98-7245-4242-8134-3510f2f411ad', 'created_at': datetime.datetime(2022, 8, 6, 21, 48, 0, 796174), 'updated_at': datetime.datetime(2022, 8, 6, 21, 48, 0, 796174)}
(hbnb) 
destroy
Usage: destroy <class> <id> or <class>.destroy(<id>)
Deletes a class instance based on a given id. The storage file file.json is updated accordingly.

$ ./console.py
(hbnb) create State
a83b9d85-fa65-4fab-895b-2f5cfc420e1f
(hbnb) create Place
8ae9fd6c-7fbc-4337-bcff-adfb8a228ba2
(hbnb)
(hbnb) destroy State 8ae9fd6c-7fbc-4337-bcff-adfb8a228ba2
(hbnb) Place.destroy(8ae9fd6c-7fbc-4337-bcff-adfb8a228ba2)
(hbnb) quit
$ cat file.json ; echo ""
{}
all
Usage: all or all <class> or <class>.all()
Prints the string representations of all instances of a given class. If no class name is provided, the command prints all instances of every class.

$ ./console.py
(hbnb) create BaseModel
fce2124c-8537-489b-956e-22da455cbee8
(hbnb) create BaseModel
450490fd-344e-47cf-8342-126244c2ba99
(hbnb) create User
b742dbc3-f4bf-425e-b1d4-165f52c6ff81
(hbnb) create User
8f2d75c8-fb82-48e1-8ae5-2544c909a9fe
(hbnb)
(hbnb) all BaseModel
["[BaseModel] (450490fd-344e-47cf-8342-126244c2ba99) {'updated_at': datetime.da
tetime(2022, 8, 3 21, 45, 5, 963516), 'created_at': datetime.datetime(2022, 8
, 17, 21, 45, 5, 963516), 'id': '450490fd-344e-47cf-8342-126244c2ba99'}", "[Bas
eModel] (fce2124c-8537-489b-956e-22da455cbee8) {'updated_at': datetime.datetime
(2022, 8, 3 21, 43, 56, 899348), 'created_at': datetime.datetime(2022, 8, 3
21, 43, 56, 899348), 'id': 'fce2124c-8537-489b-956e-22da455cbee8'}"]
(hbnb)
(hbnb) User.all()
["[User] (8f2d75c8-fb82-48e1-8ae5-2544c909a9fe) {'updated_at': datetime.datetim
e(2022, 8, 3 21, 44, 44, 428413), 'created_at': datetime.datetime(2022, 8, 17
, 21, 44, 44, 428413), 'id': '8f2d75c8-fb82-48e1-8ae5-2544c909a9fe'}", "[User] 
(b742dbc3-f4bf-425e-b1d4-165f52c6ff81) {'updated_at': datetime.datetime(2022, 8
, 17, 21, 44, 15, 974608), 'created_at': datetime.datetime(2022, 8, 3 21, 44,
15, 974608), 'id': 'b742dbc3-f4bf-425e-b1d4-165f52c6ff81'}"]
(hbnb) 
(hbnb) all
["[User] (8f2d75c8-fb82-48e1-8ae5-2544c909a9fe) {'updated_at': datetime.datetime(2022, 8, 3 21, 44, 44, 428413), 'created_at': datetime.datetime(2022, 8, 17
, 21, 44, 44, 428413), 'id': '8f2d75c8-fb82-48e1-8ae5-2544c909a9fe'}", "[BaseMo
del] (450490fd-344e-47cf-8342-126244c2ba99) {'updated_at': datetime.datetime(20
19, 2, 17, 21, 45, 5, 963516), 'created_at': datetime.datetime(2022, 8, 3 21,
45, 5, 963516), 'id': '450490fd-344e-47cf-8342-126244c2ba99'}", "[User] (b742db
c3-f4bf-425e-b1d4-165f52c6ff81) {'updated_at': datetime.datetime(2022, 8, 3 2
1, 44, 15, 974608), 'created_at': datetime.datetime(2022, 8, 3 21, 44, 15, 97
4608), 'id': 'b742dbc3-f4bf-425e-b1d4-165f52c6ff81'}", "[BaseModel] (fce2124c-8
537-489b-956e-22da455cbee8) {'updated_at': datetime.datetime(2022, 8, 3 21, 4
3, 56, 899348), 'created_at': datetime.datetime(2022, 8, 3 21, 43, 56, 899348
), 'id': 'fce2124c-8537-489b-956e-22da455cbee8'}"]
(hbnb) 
count
Usage: count <class> or <class>.count()
Retrieves the number of instances of a given class.

$ ./console.py
(hbnb) create Place
8ae9fd6c-7fbc-4337-bcff-adfb8a228ba2
(hbnb) create Place
c7854150-d828-49bc-967a-eee37dfd0953
(hbnb) create City
1fa46dfc-c634-460a-ad9c-ce5a59829e1a
(hbnb) create City
ceb92f23-5164-4c48-8451-515975a7cf89
(hbnb) 
(hbnb) count Place
2
(hbnb) city.count()
2
(hbnb) 
update
Usage: update <class> <id> <attribute name> "<attribute value>" or <class>.update(<id>, <attribute name>, <attribute value>) or <class>.update( <id>, <attribute dictionary>).
Updates a class instance based on a given id with a given key/value attribute pair or dictionary of attribute pairs. If update is called with a single key/value attribute pair, only "simple" attributes can be updated (ie. not id, created_at, and updated_at). However, any attribute can be updated by providing a dictionary.

<h3>Authors</h3>
<p>The project has been authored by individuals in <strong><i>AUTHORS</i></strong></p>
