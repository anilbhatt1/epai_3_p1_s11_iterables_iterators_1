# Iterables and Iterators

#### Following topics are covered:
- **List Comprehensions**
    - Nested list comprehensions
    - Nested loops using list comprehensions
    - List comprehensions behave like functions interms of scope
- **Iteration using next_ method**
- **Iterators**
    - Iterators are objects that implement the __iter__ and __next__ methods.
    - The __iter__ method of an iterator just returns itself.
    - Iterator **will get exhausted**.
- **Iterators and iterables**
    - An iterable is an object that can return an iterator (__iter__).    
    - How to solve exhaustion problem
    - Iterable **wont get exhausted**.
    - **iter()** function is used to request an iterator object from an iterable.
        - How to use **iter** on **lists**
        - How to use **iter** on **range**

## Assignment
- Assignment is as below.

**Refactor the Polygons (sequence) type that was built in Sequence Types assignment, into an iterable. You'll need to implement both an iterable, and an iterator**

## Assignment Solution

- File that holds required functions for part 1: Polygon.py
- Github Location : https://github.com/anilbhatt1/epai_3_p1_s11_iterables_iterators_1/blob/master/Polygon.py
- Following functions are implemented:
- **__count_vertices__(self)**
    - This is a property.
    - Will give no: of vertices which is essentially No: of edges(n)
- **__count_edges__(self)**
    - This is a property.
    - Will give No: of edges(n)
- **__circumradius__(self)**
    - This is a property.
    - Will give circumradius (R)
- **__repr__(self)**
    - repr function for polygon class. Will give info on No: of edges(n), Circumradius(R).
- **__eq__()**
    - Checks whether a given polygon object is equal or not based on no:of edges and circumradius
- **__gt__**
    - Checks whether a given polygon object is greater than or not based on no:of edges
- **interior_angle(self)**
    - This is a property.
    - Calculates int_angle -> (n−2) * 180 * n.
- **side_length(self)**
    - This is a property.
    - Calculates s = 2 * R * sin(π/n)
- **apothem(self)**
    - This is a property.
    - Calculates a = R * cos(π * n)
- **area(self)**
    - This is a property.
    - Calculates area = 12 * n * s * a
- **perimeter(self)**
    - This is a property.
    - Calculates perimeter = n * s

- File that holds required functions for part 2 (sequence): Polygons.py
- Github Location : https://github.com/anilbhatt1/epai_3_p1_s11_iterables_iterators_1/blob/master/Polygons.py
- Following functions are implemented:
- **__init__(self)**
    - Will store no: of edges in seqeunce (m), common circumradius(R)
    - Also generates polygon correspodning to the 'm' and 'R' and stores it in a list 'self._polygon' 
- **__repr__(self)**
    - repr function for poly_seq class. Will give info on No: of edges(n) of largest polyon in the sequence and common Circumradius(R).
- **__len__()**
    - Returns length of polygon sequence. This will be m-2 as sides 1 and 2 are not polygons.
- **__getitem__(self, idx)**
    - getitem method that will help us to call the polygon sequences via index.
    - It will fetch required polygon from self._polygon[idx]
- **_calc_ratio(num_edges: int, c_radius: 'int or float')**
    - Returns area-perimeter ratio of the single polygon for given number of edges & circumradius.
    - This method is directly called in __getitem__() and indirectly called from max_efficient() methods.    
- **max_efficiency_polygon(self)**
    - This is a property.
    - This method returns the Polygon with the highest area: perimeter ratio.
    - Accesses self._polygon, calculates area:perimeter ratio for each polygon in list, sorts in descending order and returns first element (polygon with highest area:perimeter ratio)
- **__iter__(self)**
    - This is defined to make Polygons an iterable.
    - This calls the class **polyiterator**
- **__polyiterator__(self)**
    - This is a class defined to make Polygons an iterable.
    - **__init__(self, poly_obj)**
        - Essentially accepts the polygon sequence object from which it is called
        - Saves poly_obj in self._poly_obj.
        - Also maintains self._index
    - **__iter__(self)**
        - To maintain this as an iterator. Returns self.
    - **__next__(self)**
        - Returns sides, circumradius and area:perimeter ratio of polygons one by one by referring to the list **self._poly_obj._polygon**  
        - If self._index >= len(self._poly_obj) raises stopiteration. This avoids indefinite execution.

- Draft Jupyter version where assignment was initially tried out can be found below:
https://github.com/anilbhatt1/epai_3_p1_s11_iterables_iterators_1/blob/master/Iterables_1_Assignment_Draft.ipynb

## Testing
- All the above functions are tested using pytest.
- Testcase file : **test_Polygons.py** (Please note that that 'test_' need to be prefixed for Pytest to automatically identify that it is a testcase file).
- Github Location : https://github.com/anilbhatt1/epai_3_p1_s11_iterables_iterators_1/blob/master/test_Polygons.py
- Test snapshot results as below:
![Test_Pass](https://github.com/anilbhatt1/epai_3_p1_s11_iterables_iterators_1/blob/master/Assignment1_Test_Passed_Snapshot.png)
