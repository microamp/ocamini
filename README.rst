ocamini
=======

microamp's first attempt at learning OCaml/ML (influenced by the excellent 'learnxinyminutes' series)

Pre-requisites
--------------
- utop ("A toplevel for OCaml that supports completion, colors, and parenthesis matching")


Examples
--------
Basic Arithmetics
~~~~~~~~~~~~~~~~~
.. code-block:: ocaml

    utop[]> 1 + 2;;  (* ocaml's toplevel requires ';;' at the end of each expression *)
    - : int = 3
    utop[]> 1 + "a";;  (* ocaml is strongly-typed *)
    Error: This expression has type string but an expression was expected of type
    int
    utop[]> 1.1 + 2.2;;  (* ocaml's type system is indeed very strict *)
    Error: This expression has type float but an expression was expected of type
    int
    utop[]> 1.1 +. 2.2;;  (* use '+.' to add two floating numbers together *)
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

    utop[]> let add x y = x + y;;  (* use 'let' to define a function *)
    val add : int -> int -> int = <fun>
    utop[]> adder 1 2;;
    - : int = 3
    utop[]> let equal_to_three x = x = 3;;  (* '=' used for equality test as well! *)
    val equal_to_three : int -> bool = <fun>
    utop[]> equal_to_three (adder 1 2);;
    - : bool = true

Type Inference
~~~~~~~~~~~~~~
.. code-block:: ocaml

    utop[]> let divide_int x y = x / y;;
    val divide_int : int -> int -> int = <fun>
    utop[]> let divide_float x y = x /. y;;
    val divide_float : float -> float -> float = <fun>

The type of an expression is not explicitly specified in OCaml. Instead, it is "inferred from the available type information about the components of that expression". The compiler determines that the variables, x and y, in the function 'divide_int' are of type int because it knows that the operator '/' requires both operands to be int.

Higher-Order Functions
~~~~~~~~~~~~~~~~~~~~~~
.. code-block:: ocaml

    utop[]> List.map;;  (* takes a func and a list, returns another list *)
    - : ('a -> 'b) -> 'a list -> 'b list = <fun>
    utop[]> let double x = x * 2;;
    val double : int -> int = <fun>
    utop[]> List.map double [1; 2; 3; 4];;
    - : int list = [2; 4; 6; 8]

.. code-block:: ocaml

    utop[]> List.filter;; (* takes a func and a list, returns another list of same type*)
    - : ('a -> bool) -> 'a list -> 'a list = <fun>
    utop[]> let is_even x = x mod 2 = 0;;
    val is_even : int -> bool = <fun>
    utop[]> List.filter is_even [1; 2; 3; 4];;
    - : int list = [2; 4]

List.map and List.filter are also good examples of parametric polymorphism.

Composite Data Structures: Tuples and Lists
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
.. code-block:: ocaml

    utop[]> let my_tuple = ("a", 1, true);;  (* comma-separated, arbitrary types *)
    val my_tuple : string * int * bool = ("a", 1, true)
    utop[]> let my_tuple = "a", 1, true;;  (* equivalent to the above *)
    val my_tuple : string * int * bool = ("a", 1, true)

.. code-block:: ocaml

    utop[]> let my_list = ["a"; "b"; "c"];;  (* semicolon-separated, single type *)
    val my_list : string list = ["a"; "b"; "c"]
    utop[]> let my_list = ["a"; "b"; 3];;  (* all items must be of the same type*)
    Error: This expression has type int but an expression was expected of type
    string

.. code-block:: ocaml

    utop[]> "x" :: my_list;;  (* add item to a list *)
    - : string list = ["x"; "a"; "b"; "c"]
    utop[]> my_list @ ["d"];;  (* list concatenation *)
    - : string list = ["a"; "b"; "c"; "d"]
    utop[]> my_list;;  (* original list never changes (immutable) *)
    - : string list = ["a"; "b"; "c"]

Pattern Matching
~~~~~~~~~~~~~~~~
.. code-block:: ocaml

    utop[]> let head :: tail = [1; 2; 3];;
    val head : int = 1
    Characters 4-16:
    val tail : int list = [2; 3]
    Warning 8: this pattern-matching is not exhaustive.
    Here is an example of a value that is not matched:
    []

Tail Recursion
~~~~~~~~~~~~~~
.. code-block:: ocaml

    utop[]> let rec sum numbers =
    match numbers with
    | [] -> 0  (* base case *)
    | first :: rest -> first + sum rest  (* inductive case *)
    ;;
    val sum : int list -> int = <fun>
    utop[]> sum [1; 2; 3];;
    - : int = 6

Records
~~~~~~~
N/A

Options
~~~~~~~
N/A
