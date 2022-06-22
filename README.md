<h1>Example Site> </h1>

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

# This is to demonstate implemntation if it were a different number of people in the table.
# For this example, we have 4 people which are G1,G2,G3 and G4
# graph ={
#  'G1'   : [ 'G2'],
#  'G2'   : [ 'G3'],
#  'G3'  : [ 'G4'],
#  'G4'  : [ 'G1'],
# 
#     }


<h4><em> These are the nodes and where they are comfortable to sit on thier left(clockwise)</em></h4>


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
   

print(counted)'
</code>


<h2>Explanaion and how to implement</h2>
<h4><code>    
 'G1'   : [ 'G2'],
 'G2'   : [ 'G3'],
 'G3'  : [ 'G5'],
 'G4'  : [ 'G1'],
 'G5' :  [ 'G4'],


    }
 </code><em> These are the nodes(people) and who they are comfortable to sit on thier left(clockwise). This code has to be here to describe the group of people</em></h4>



<h4><code>
visited =[]
queue =[]
</code>






