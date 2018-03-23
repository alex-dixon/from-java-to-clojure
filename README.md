# From Java To Clojure
> From Java To Clojure - Your Cheat Sheet For Java To Clojure

---

> Java

```java
System.out.print("Amit Shekhar");
System.out.println("Amit Shekhar");
```

> Clojure

```clojure
(prn "Amit Shekhar")
(println"Amit Shekhar")
```

---

> Java

```java
String name = "Amit Shekhar";
final String name = "Amit Shekhar";
```

> Clojure

```clojure
(def ^:private name "Amit Shekhar")
(def name "Amit Shekhar")
```

---

> Java

```java
String otherName;
otherName = null;
```

> Clojure

```clojure
(declare other-name)
(def other-name nil)
```

---

> Java

```java
if (text != null) {
  int length = text.length();
}
```

> Clojure

```clojure
(def length (if (nil? text) nil (count text)))
```

---

> Java

```java
String firstName = "Amit";
String lastName = "Shekhar";
String message = "My name is: " + firstName + " " + lastName;
```

> Clojure

```clojure
(def first-name "Amit")
(def last-name "Shekhar")
(def message (str "My name is : " first-name " " last-name))
```

---

> Java

```java
String text = "First Line\n" +
              "Second Line\n" +
              "Third Line";
```

> Clojure

```clojure
(def text 
  (str "First Line\n" 
       "Second Line\n" 
       "Third Line"))
```

---

> Java

```java
String text = x > 5 ? "x > 5" : "x <= 5";

String message = null;
log(message != null ? message : "");
```

> Clojure

```clojure
(def text
  (if (> x 5) 
    "x > 5" 
    "x <= 5"
(def message nil)
(if message (log message) (log ""))
```

---

> java

```java
final int andResult  = a & b;
final int orResult   = a | b;
final int xorResult  = a ^ b;
final int rightShift = a >> 2;
final int leftShift  = a << 2;
```

> Clojure

```clojure
(def and-result (bit-and a b))
(def or-result (bit-or a b)
(def xor-result (bit-xor a b)
(def right-shift (bit-shift-right a 2))
(def left-shift (bit-shift-left a 2))
```

---

> Java

```java
if (object instanceof Car) {
}
Car car = (Car) object;
```

> Clojure

```clojure
(if (= (type object) Car))

(def car (cast object Car)
```

---

> Java

```java
if (object instanceof Car) {
   Car car = (Car) object;
}
```

> Clojure

```clojure
; Honestly casting is really unusual in Clojure since it is dynamically typed and not object-oriented
```

---

> Java

```java
if (score >= 0 && score <= 300) { }
```

> Clojure

```clojure
(if (and (>= score 0) (<= score 300)))
```

---

> Java

```java
int score = // some score;
String grade;
switch (score) {
	case 10:
	case 9:
		grade = "Excellent";
		break;
	case 8:
	case 7:
	case 6:
		grade = "Good";
		break;
	case 5:
	case 4:
		grade = "Ok";
		break;
	case 3:
	case 2:
	case 1:
		grade = "Fail";
		break;
	default:
	    grade = "Fail";				
}
```

> Clojure

```clojure
(let [score nil]
  (cond
    (#{9 10} score) "Excellent"
    (>= 6 8 score) "Good"
    (#{4 5} score) "Ok"
    (>= 1 3 score) "Fail"
    :default "Fail"
```

---

> Java

```java
for (int i = 1; i <= 10 ; i++) { }

for (int i = 1; i < 10 ; i++) { }

for (int i = 10; i >= 0 ; i--) { }

for (int i = 1; i <= 10 ; i+=2) { }

for (int i = 10; i >= 0 ; i-=2) { }

for (String item : collection) { }

for (Map.Entry<String, String> entry: map.entrySet()) { }
```

> Clojure

```clojure
(repeatedly 10 some-fn)

(dotimes [x 9] 
  (some-fn x)

(loop [x 10]
  (when-not (= x 0)
    (recur (- x 2))

(doseq [x coll])

(doseq [[k v] map])

(for [x coll]))

(for [[k v] map]
  (somefunc k v))

(for [x ['a 'b 'c] 
      y [1 2 3]]
  (println x y)
```

---

> Java

```java
final List<Integer> listOfNumber = Arrays.asList(1, 2, 3, 4);

final Map<Integer, String> keyValue = new HashMap<Integer, String>();
map.put(1, "Amit");
map.put(2, "Ali");
map.put(3, "Mindorks");

// Java 9
final List<Integer> listOfNumber = List.of(1, 2, 3, 4);

final Map<Integer, String> keyValue = Map.of(1, "Amit",
                                             2, "Ali",
                                             3, "Mindorks");
```

> Clojure

```clojure
(def list-of-number [1 2 3 4])

(def key-value {1 "Amit" 
                2 "Ali" 
                3 "Mindorks"})
```

---

> Java

```java
// Java 7 and below
for (Car car : cars) {
  System.out.println(car.speed);
}

// Java 8+
cars.forEach(car -> System.out.println(car.speed));

// Java 7 and below
for (Car car : cars) {
  if (car.speed > 100) {
    System.out.println(car.speed);
  }
}

// Java 8+
cars.stream().filter(car -> car.speed > 100).forEach(car -> System.out.println(car.speed));
```

> Clojure

```clojure
(doseq [car cars]
  (println (:speed car)))

(map (comp println :speed)
  (filter #(> (:speed %) 100) cars))
```

---

> Java

```java
void doSomething() {
   // logic here
}
```

> Clojure

```clojure
(defn do-something []
  ; logic here)
```

---

> Java

```java
void doSomething(int... numbers) {
   // logic here
}
```

> Clojure

```clojure
(defn do-something [& xs]
  ; logic here)
```

---

> Java

```java
int getScore() {
   // logic here
   return score;
}
```

> Clojure

```clojure
(defn get-score []
  ; logic here
  score)
```

---

> Java

```java
int getScore(int value) {
    // logic here
    return 2 * value;
}
```

> Clojure

```clojure
(defn get-score [value] 
  ; logic here
  (* 2 value))

; as a partially applied function definition
(def get-score (partial * 2))
```

---

> Java

```java
public class Utils {

    private Utils() { 
      // This utility class is not publicly instantiable 
    }
    
    public static int getScore(int value) {
        return 2 * value;
    }
    
}
```

> Clojure

```clojure
(defn get-score [value] (* 2 value))
```

---

> Java

```java
public class Developer {

    private String name;
    private int age;

    public Developer(String name, int age) {
        this.name = name;
        this.age = age;
    }

    public String getName() {
        return name;
    }

    public void setName(String name) {
        this.name = name;
    }

    public int getAge() {
        return age;
    }

    public void setAge(int age) {
        this.age = age;
    }

    @Override
    public boolean equals(Object o) {
        if (this == o) return true;
        if (o == null || getClass() != o.getClass()) return false;

        Developer developer = (Developer) o;

        if (age != developer.age) return false;
        return name != null ? name.equals(developer.name) : developer.name == null;

    }

    @Override
    public int hashCode() {
        int result = name != null ? name.hashCode() : 0;
        result = 31 * result + age;
        return result;
    }

    @Override
    public String toString() {
        return "Developer{" +
                "name='" + name + '\'' +
                ", age=" + age +
                '}';
    }
}
```

> Clojure

```clojure
(defrecord Developer [name age])

```

---

> Java

```java
public class Developer implements Cloneable {

    private String name;
    private int age;

    public Developer(String name, int age) {
        this.name = name;
        this.age = age;
    }

    @Override
    protected Object clone() throws CloneNotSupportedException {
        return (Developer)super.clone();
    }
}

// cloning or copying 
Developer dev = new Developer("Max", 30);
try {
     Developer dev2 = (Developer) dev.clone();
} catch (CloneNotSupportedException e) {
     // Handle Exception
}

```

> Clojure

```clojure
(defrecord Developer [name age])

// cloning or copying
(def dev (->Developer "Max" 30))
(def dev2 dev)
// in case you only want to copy selected properties
(def dev2 (map->Developer {:age 25})

```

---

> Java

```java
public class Utils {

    private Utils() { 
      // This utility class is not publicly instantiable 
    }
    
    public static int triple(int value) {
        return 3 * value;
    }
    
}

int result = Utils.triple(3);

```

> Clojure

```clojure
(defn triple [n] (* 3 n)

(def result (triple 3))
```

---

> Java

```java
ImageView imageView;
```

> Clojure

```clojure
(ImageView.)
```


---

### Important things to know in Clojure
- Functions
- Data structures
- Immutability
- Connecting your editor to a REPL
- Java interop
- Clojurescript
- Namespaces
- `deftype`, `definterface`, `defrecord` for object-oriented programming
- Atoms and binding for thread-safe mutability
- clojure.spec

