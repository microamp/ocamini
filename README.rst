ocamini
=======

microamp's first attempt at learning OCaml/ML following a format that is similar to that of the excellent 'learnxinyminutes' series


Pre-requisites
--------------

Examples
--------
Basic Arithmetics
~~~~~~~~~~~~~~~~~
.. code-block:: ocaml

    utop[]> 1 + 2;;  (* ocaml's toplevel requires ';;' at the end of each expression *)
    - : int = 3
    utop[]> 1.1 + 2.2;;  (* '+' expects type int, not float (strongly-typed) *)
    Error: This expression has type float but an expression was expected of type int
    utop[]> 1.1 +. 2.2;;  (* use '+.' instead *)
    - : float = 3.3

Let Bindings
~~~~~~~~~~~~
.. code-block:: ocaml

    utop[]> let x = 3;;  (* let binding to create a variable *)
    val x : int = 3
    utop[]> let X = 3;;  (* variable cannot start with a capital letter *)
    Error: Unbound constructor X

Basic Functions
~~~~~~~~~~~~~~~
.. code-block:: ocaml

    utop[]> let adder x y = x + y;;  (* use 'let' to define a function *)
    val adder : int -> int -> int = <fun>
    utop[]> adder 1 2;;
    - : int = 3
    utop[]> let equal_to_three x = x = 3;;  (* '=' used for equality test as well! *)
    val equal_to_three : int -> bool = <fun>
    utop[]> equal_to_three (adder 1 2);;
    - : bool = true

Higher-Order Functions
~~~~~~~~~~~~~~~~~~~~~~

Composite Data Structures: Tuples and Lists
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. code-block:: ocaml

    utop[]> let my_tuple = ("a", 1, 10.0 /. 3.0, false);;  (* comma-separated, arbitrary types *)
    val my_tuple : string * int * float * bool = ("a", 1, 3.33333333333, false)
    utop[]> let my_list = ["a"; "b"; "c"];;  (* colon-separated, single type *)
    val my_list : string list = ["a"; "b"; "c"]
    utop[]> let my_list = ["a"; "b"; 3];;  (* list must be of a single type *)
    Error: This expression has type int but an expression was expected of type string
    utop[]> "x" :: my_list;;  (* add item to a list *)
    - : string list = ["x"; "a"; "b"; "c"]
    utop[]> my_list @ ["d"];;  (* list concatenation *)
    - : string list = ["a"; "b"; "c"; "d"]
    utop[]> my_list;;  (* original list never changes (immutable) *)
    - : string list = ["a"; "b"; "c"]

Pattern-Matching (match)
~~~~~~~~~~~~~~~~~~~~~~~~

Recursion
~~~~~~~~~
