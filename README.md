# logic-tut

*HackDay Project: Logic and Relations Programming with Clojure's core.logic*


## Resources

* [API Reference](https://clojure.github.io/core.logic/)
* [core.logic Primer](https://github.com/clojure/core.logic/wiki/A-Core.logic-Primer)
* [core.logic Examples](https://github.com/clojure/core.logic/wiki/Examples)
* [Clojure translation of Reasoned Schemer examples](https://github.com/matlux/the-reasoned-schemer-clojure/blob/master/src/reasoned_schemer_clj/core.clj)


## Usage

For the Hack Day, we explore the possibility of converting OO, hierarchical code for querying satellite metadata to core.logic relations. To do this, we built a simplified graph database (vector of vectors) that connected the components together. After we wrote the appropriate relations, we were then able to write "querying" functions that performed the core.logic ``run*`` to get the list of items that satisfied the relations we created.

Below are example usages of these:

```
$ lein repl
```
```clj
logic-tut.dev=> (require '[logic-tut.sensor-simple :refer [satellites-for-mission
                                                           sensors-for-mission
                                                           sensors-for-satellite
                                                           sat-graph]])
nil
```

Get all satellites:

```clj
logic-tut.dev=> (satellites-for-mission sat-graph "Landsat")
("Landsat 4" "Landsat 5" "Landsat 7")
```

Get all sensors:

```clj
logic-tut.dev=> (sensors-for-mission sat-graph "Landsat")
("TM" "TM" "ETM")
```

Get sensors for satellites:

```clj
logic-tut.dev=> (sensors-for-satellite sat-graph "Landsat" "Landsat 4")
("TM")
logic-tut.dev=> (sensors-for-satellite sat-graph "Landsat" "Landsat 5")
("TM")
logic-tut.dev=> (sensors-for-satellite sat-graph "Landsat" "Landsat 7")
("ETM")
```


## License

Copyright © 2016 David Hill, Duncan McGreggor, Jon Morton
