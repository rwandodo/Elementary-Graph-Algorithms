# Elementary-Graph-Algorithms

Give a linear-time algorithm that takes as input a directed acyclic graph G=(V,E) and two vertices s and t,
and returns the number of simple paths from s to t in G. For example, the directed acyclic graph of the Figure below contains 
exactly four simple paths from vertex p to vertex v: pov, poryv, and psryv.

<a href="https://ibb.co/mKwQSm"><img src="https://image.ibb.co/cB63DR/graph.png" alt="graph" border="0"></a>
--------------------------------------------------------------------------------------------------------------
 
The java code:

package PakgAssignment3611;
import java.util.HashMap;
import java.util.LinkedHashSet;
import java.util.LinkedList;
import java.util.Map;

public class ElementaryGraphAlgorithms {
	
    private static String from = "p";
    private static String to = "v";

private static Map<String, LinkedHashSet<String>> myGragh = new HashMap();
    public static void main(String[] args) {
  addEdge("m", "q");  addEdge("m", "x");  addEdge("m", "r");  addEdge("q", "t");
  addEdge("n", "q");  addEdge("n", "u");  addEdge("n", "o");  addEdge("u", "t");
  addEdge("r", "u");  addEdge("r", "y");  addEdge("y", "v");  addEdge("o", "r");
  addEdge("o", "s");  addEdge("o", "v");  addEdge("v", "x");  addEdge("v", "w");
  ddEdge("s", "r");  addEdge("p", "o");  addEdge("p", "s");  addEdge("p", "z");
  addEdge("w", "z"); 
        
        LinkedList<String> colored = new LinkedList(); colored.add(from);
           System.out.println ("\nThe paths from node " + from +" to the node " + to + " are as follows:");
        System.out.println ("--------------------------------------------------");
        new ElementaryGraphAlgorithms().DF( colored);
    }

    private void DF( LinkedList<String> colored) {
        LinkedList<String> vertices = calcNeighborsVertices(colored.getLast());

        for (String v : vertices) {
            if (colored.contains(v))continue;
            if (v.equals(to)) {
            colored.add(v);  PathPrint(colored);  colored.removeLast(); break;
            }
        }
 
        for (String  vv : vertices) {
            if (colored.contains(vv) || vv.equals(to)) continue;
            colored.addLast(vv);   DF( colored);  colored.removeLast();
        }
    }

//The complete implementation for these functions are in the attached jave file 

    private void PathPrint(LinkedList<String> colored);
    public static void addEdge(String n1, String n2) ;    
    public static LinkedList<String> calcNeighborsVertices(String end);
}

--------------------------------------------------------------------------------------------------------------

Explanation:

In my programming this problem, I used a map which I construct me graph Map<String, LinkedHashSet<String>>, 
after that I entered all the vertices and edges which are in this graph as in the figure above,
I used the depth first algorithm in order to code a linear program, starting with coloring the visited vertices to distinguish them from the not visited yet. While processing the depth first algorithm 
every time I visit a vertex, I colored it and compute its neighbor ones by calling this function: calcNeighborsVertices.
Looping over all neighbors to detect to the last vertex and see if I can arrive to the last vertex which I want to arrive, 
here in our case the last one is “v”, and going like that. 
While going in complete this process I call another function for printing my path which start from “from node, here is “p” ” to “to node, here is “v” ”.

The output:

<a href="https://ibb.co/m5NX7m"><img src="https://preview.ibb.co/jQ4106/teh_outputtt.png" alt="teh_outputtt" border="0"></a>


