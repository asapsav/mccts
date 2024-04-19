# mccts
High performant implementation for Monte Carlo *Code* Tree Search with LLMs


## motivation, in no particular order

* it seems that there is a big chunk of usefull code gen 
tasks are translation type -> we do we use a decoder only model then???
use encoder to encode the task and decoder to write implemenationf or it (ofc, an arguement against would be an emptitical result that decoder only in enough, and choise should be always for a simpler solution)
* can (should we?) we make attenction ona  higher than tocken level of abstractions (say, on a level of language statements)? Ex.:

`some code` 

    -> key = "i'm a code that sorts a list" . 
    -> query = " I need python environment with numpy "

`a code that imports libraries`

    -> key "I import libraries like nunmpy"
    -> query "I need a python REPL"

`a bash script that make a REPL`

    -> key "..."
    -> query "..."

* following an amazing result on AlphaZero and inspired by the way I personally sometimes think (is bad to do that, but still): when trying to search a much larger solution space (~ system 2 thinking), it usefull to constrult a decision tree. thefore, lets implement a MCTS algo to utilise potential outputs from non zero temperature, and also to try and capture usefull training data. cool think about ToT is that it can also be somewhat parrallelised. good think about using code as a domain is because its more or less formal and we can extract and backprop a lot of rewards (if the code does not compute what u need or does not compile - thats a negative reward and etc.)