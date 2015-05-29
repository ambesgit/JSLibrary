
      Created  by Ambasager Gebremeskel  05/28/2015   currently looking for a job 
      you can reach me at 202 412 1503 or 703-945-0620

# JSLibrary
	this JSLibrary has many functions to manuplate strings, arrays, objects and numbers. Also it has factory functions to 	create specialized objects
	like Set, Stack, Queue, Map.

the collections object is the core of the library, it has many functions to work with numbers,strings,array, and objects

Demo

	var myapp=jsquery;   //gives you a reference to the grand dad object

Customized objects

createSet()

	var set=myapp.$collections.createSet()   //creates a set object 
	set.add(1);                             // adds the element to the set
	set.add(1)                              // no repeatation so it will not add this value
	set.size()                             //1
	set.find(1)                          // returns 1
	set.add(2)                         //added
	set.size                         //2
	set.findAll()                   //[1,2]

createQueue() 

	var queue=myapp.$collections.createQueue()
	queue.add(1)                   //1 added
	queue.add(2)                  //2 added
	queue.add(1)                  // 1 added
	queue.size()                  //3
	queue.next()                  //returns 1
	queue.next()                  // returns 2
	queue.size()               //1
	queue.findAll()            //1

createStacke()

	var stack=myapp.$collections.createStacke()
	stack.add(3)                   //3 added
	stack.add(4)                  //4 added
	stack.add(3)                  // 3 added
	stack.size()                  //3
	stack.next()                  //returns 3
	stack.next()                  // returns 4
	stack.size()               //1
	stack.findAll()            //3
	
createMap()

	var mapObject=myapp.createMap()      //you can use all functions which the native Map object provdes

Events
	
	myapp.createEvent("data",{});                //creates an event named data

	myapp.on("data")                           //listens to the data event

	myapp.emit("data")                        //fires the "data" event

css()

	myapp.css("bgcb", "background-color:black")   //creates the style and stores it in $css object as key value pair

html()

	myapp.html("bd", "body div")          // get a reference to the queryselector using the given name

cssHtml()

	myapp.cssHtml("bgcb","bd")          //binds the two so the div elements in the body will have black background

	myapp.cssHtml("bgcb","bd","delete")   //attaches an event called "delete" so if it fires and if event handler is 		listening to it change will reflect on the body div 
	if "bgcb" is deleted from the $css object then the background will changed to default color

	myapp.html("bp","body p")
	myapp.cssHtml("bgcb","bp")       //the p element in the body will have black background create once apply to any one 	you want

data()

	myapp.data("sample", "[1,2,3,4,5]")   //store the array in a $data objec with the given name as key value pairs

dataHtml()

	myapp.html("list" "#ulid")      //identifies an element with the given id in the currently loaded page
	myapp.dataHtml("sample","list")  //the data will loaded to the element identified by "list", if you have more data, 		new element with the same type will be created
                                  <li>1</li>, <li>2</li>......<li>5</li>
	if  new entry is added to the array identified by the name "sample", it will not appear in the html page, to do so 		you need to attach event to the dataHtml() binder.....dataHtml("sample","list", "change"), this assums you create 	an event called change and listen to it
	now if you add new entry to the array, it will appear in the html too


AJAX  reusable components 

model()  only json resources

	myapp.model("customer","http://localhost:6060/models/customers");      //gets the resource identified by the url and 	stores it in the $model object by the "customer" so any part of your application can access this resource using the 			"customer" name
	
view()

	myapp.view("customerview","http://localhost:6060/customers");   //gets the resource which is part of html page 

controller()

	myapp.controller("add",function(a,b){return a+b;})   // creates a controller and stores it in the $controllers object
            later you can call this using myapp.$controllers.add(2,3)   //5
            
            
Functions of $collections object

group()
    
	myapp.$collections.group([1,2,1,2,3,3,4,4,5,5,1,3])  //[[1,1,1],[2,2],[3,3,3],[4,4],[5,5]]

carproduct()

	myapp.$collections.carproduct([1,2,3],[1,2,3],"*")  //[1,4,9]
	myapp.$collections.carproduct([1,2,3],[1,2,3],"/")  //[1,1,1]

XOR()

	myapp.$collections.XOR([1,2,3,4],[1,2,3,5])    //[5,4]

union

	myapp.$collections.union([1,2,3,4,5,6],[1,2,5,6,7])   //[1,2,3,4,5,6,7]

inetersection()

	myapp.$collections.intersection({a:[1,2,3,4,5,6],b:98,c:88},{a:[1,2,5,6,7],b:90})  //[["a","b"]]

subset()

	myapp.$collections.subset([1,2,3,4,5,6,2],2,4)     //[3,4,5]
	myapp.$collections.subset([1,2,3,4,5,6,2],4)     //[5,2]

isEqaul()

	myapp.$collections.isEqaul({a:1,b:2,c:{e:8,f:9}},{a:1,b:2,c:{e:8,z:9}})  //false because of the z and f keys 
	myapp.$collections.isEqaul({a:1,b:2,c:{e:8,f:9}},{a:1,b:2,c:{e:8,f:100}})  //true

compare()

	myapp.$collections.compare([1,2,3,4],[2,3,4,5])  //0
	myapp.$collections.compare([1,2,3],[2,3,4,5])  //-1
	myapp.$collections.compare([1,2,3,4],[2,3,4])  //1

keys()

	myapp.$collections.keys({a:1,b:2,c:{e:8,f:9}})    //[["a","b","c"],["e","f"]]
	
invert()

	myapp.$collections.invert({a:20,b:30,c:{d:49,f:{e:23}}})    //{20: "a", 30: "b"}

sort()

	myapp.$collections.sort([4,3,2,6,1,[4,2,3,1]])  //[1,2,3,4,6,[1,2,3,4]]
	myapp.$collections.sort([4,3,2,6,1,[4,2,3,1]],true)  //[6,4,3,2,1,[4,3,2,1]]
	myapp.$collections.sort(["abc","cdf","bdc"])    //["abc","bdc","cdf"]

strCompact()

	myapp.$collections.strCompact("  ambes    tetemke")   //["ambes tetemke"]

pick()

	myapp.$collections.pick("ambesa","a")   //["a",2]

index()

	myapp.$collections.index([1,2,3,4,5,6,2],2)     //[1,6]

strEndWith()

	myapp.$collections.strEndwith(["ambes.html","tetemke.doc",'html')     //["ambes.html"]

strContain()

	myapp.$collections.strContain(["ambes","tetemke","but","bteer"],"b")  //["ambes", "but", "bteer"]
	myapp.$collections.strStratwith("ambes",'be')  //["ambes"]
	myapp.$collections.strStratwith("ambes",'ts')     //[]

strStartWith()

	myapp.$collections.strStratwith("ambes",'be')  //[]
	myapp.$collections.strStratwith("ambes",'am')		//["ambes"]
	myapp.$collections.strStratwith("ambes",'a')     //["ambes"]
	
strTrim()

	myapp.$collections.strTrim([" abc ", " derf "])  //["abc","derf"]

strTrimLeft()

	myapp.$collections.strTrimLeft([ "  abc  ", "derf  "])   //["abc  ", "derf  "]
	
strTrimRight()

	myapp.$collections.strTrimRight([" abc ", " derf "])  //[" abc"," derf"]

strJoin()

	myapp.$collections.strJoin(["ambes","adu"],["yahoo","gmail"] ,"@") //["ambes@yahoo","adu@gmail"]

charAtReplace()

	myapp.$collections.charAtReplace("abe",2,"c")  //"abc"
	myapp.$collections.charAtReplace(["abe"],2,"c")  //"abc"

charAt()

	myapp.$collections.charAt(["abc","dce"],2) //["c","e"]
	myapp.$collections.charAt("about",1)  //b

charAtDelete()

	myapp.$collections.charAtDelete("gosd",2)    //god
	myapp.$collections.charAtDelete(["scchohool","about"],2,2)  //["school","ab"]

charAppend()

	myapp.$collections.charAppend("attache","d")   //"attached"

charPreppend()
	myapp.$collections.charPreppend("chool","s")    //"school"

enclosed()

	myapp.$collections.enclosed("input","<",">")  //"<inpute>"

insertChar()

	myapp.$collections.insertChar("schol",2,"o")           //school

reverse()

	myapp.$collections.reverse("goodluck")    //kculdoog

extract()

	myapp.$collections.extract(["ambes1123, adu908"],true)  //["ambes"  "adu"]
	myapp.$collections.extract("ambes20983",false)        //209683

count()

	myapp.$collections.count([2,1,3,4,4,3],3)  //2

mean()

	myapp.$collections.mean([1,2,3,4,5])   //3

max()

	myapp.$collections.max([1,2,3,4])   //4

min()

	myapp.$collections.min([1,2,3,4])   //1

replace()

	myapp.$collections.replace("amxes","x","b")  //"ambes"

find()

	myapp.$collections.find([1,2,3,4],4)  //[4]
	myapp.$collections.find([1,2,3,4],8)  //[]

sum()

	myapp.$collections.sum([1,2,3,4,5])  //15

map()
	
	myapp.$collections.map([1,2,3],3,"*")  //[3,6,9]
	myapp.$collections.map([1,2,3],3,"+")  //[4,5,6]
	myapp.$collections.map([1,2,3],3)  //[3,6,9]   the default operator(*)

type()

	myapp.$collections.type([1],[1,2,3,4]) //true
	myapp.$collections.type([1,2],{a:2})  //false








