<h1>Seating arrangement for 5 people in a circle </h1>

This is a sample readme file for our five people sitting in a table problem

The code demonstrates the seating position depending on the peoples comfort sitting next to each other.

Therefore assumptions on seating plan have been made prior to coding 


<code>
graph ={    
    
 'G1'   : [ 'G2'],
 'G2'   : [ 'G3'],
 'G3'  : [ 'G5'],
 'G4'  : [ 'G1'],
 'G5' :  [ 'G4'],


    }




visited =[]
queue =[]


def bfs (visted,graph,node):
    
  visited.append(node)  
  queue.append(node)
  
  
  while queue:
      s=queue.pop(0)
      print(s,end= "  ")
      
      
      for neighbour in graph[s]:
          if neighbour not in visited :
              visited.append(neighbour)
              queue.append(neighbour)
              
print("BFS for 5 people in a circle in clockwise starting from G1")

bfs(visited,graph,'G1')



user_input = input("Type the number of people in the table :   ")
counted={'People':0}

for i in user_input:
    if i.isalpha():                   
        counted['People']+=1
   

print(counted)
</code>


<h2>Explanation and how to implement</h2>
<em> These are the nodes(people) and who they are comfortable to sit on thier left(clockwise). This code has to be here to describe the group of people</em>
<h4><code>    
 'G1'   : [ 'G2'],
 'G2'   : [ 'G3'],
 'G3'  : [ 'G5'],
 'G4'  : [ 'G1'],
 'G5' :  [ 'G4'],


    }
 </code></h4>

<hr>

<em> Visited function will list visited nodes and Queue function will initiate queue</em>
<h4><code>

visited =[]
queue =[]
</code> </h4>
<hr>

<em> This is the breadth first search first which will store the leaf node value first in visited and queue. For Example G1 will first be in visited[G1] and queue[G1]  </em>  
<h4><code>
def bfs (visted,graph,node):
    
  visited.append(node)  
  queue.append(node)
    </code></h4>
<hr>    

<em> This while loop will check if the queue is empty. If it is not empty it will pop the value to make room for neighbour nodes. Print function will print visited nodes</em>
<h4><code>
  while queue:
  s=queue.pop(0)
  print(s,end= "  ")
    </code></h4>
<hr>

<em> For loop is to place unvisited neighbours nodes in the queue</em>

 <h4><code>
for neighbour in graph[s]:
          if neighbour not in visited :
              visited.append(neighbour)
              queue.append(neighbour)
     
 </code></h4>
 <hr>             
 
<em> This print function will print the query and the bfs function will be called when placed the node</em>
    
<h4><code>   
print("BFS for 5 people in a circle in clockwise starting from G1")

 bfs(visited,graph,'G1')
  </code></h4>

<hr>
 <em>This is a user input, which will be prompted when the program runs. The user will key in the number of people in the table.
 The for loop will catch it and will count the amount of letters by using isalpha. The result will be printed then </em>


<h4><code>
user_input = input("Type the number of people in the table :   ")
counted={'People':0}

for i in user_input:
    if i.isalpha():                   
        counted['People']+=1    
    print(counted)
    </code></h4>
<hr>
<hr>

<h2>This is to demonstrate another implementation if the user wishes to arrange any other number of people in their seating plan
For this example we will be using 4 people and we will remove G5 from the list. This will leave us with G1,G2,G3 and G4</h2>

<h3><code>graph ={
'G1' :['G2'],
'G2' :['G3'],
'G3' :['G4'],
'G4' :['G1'],

    </code></h3>
