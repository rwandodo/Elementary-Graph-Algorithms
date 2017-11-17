
Elementary Graph Algorithms2

Problem Statement:

Arbitrage is the use of discrepancies in currency exchange rates to transform one unit of a currency into more than one unit of the same currency. For example, suppose that 1 U.S. dollar buys 49 Indian rupees, 1 Indian rupee buys 2 Japanese yen, and 1 Japanese yen buys 0.0107 U.S. dollars. Then, by converting currencies, a trader can start with 1 U.S. dollar and buy 49x2x0.0107 = 1.0486 U.S. dollars, thus turning a profit of 4.86 percent. 
Suppose that we are given 𝑛 currencies 𝑐1,2,;…,𝑐𝑛 and an 𝑛 𝑥 𝑛 table 𝑅 of exchange rates, such that one unit of currency 𝑐𝑖 buys 𝑅[𝑖,𝑗] units of currency 𝑐𝑗 . 

a) Give an efficient algorithm to determine whether or not there exists a sequence     of currencies <𝑐𝑖1,𝑐𝑖2,…,𝑐𝑖𝑘> such that 𝑅[𝑖1,𝑖2].𝑅[𝑖2,𝑖3]…𝑅[𝑖𝑘−1,𝑖𝑘].𝑅[𝑖𝑘,𝑖1]>1 Analyze the running time of your algorithm. 

b) Give an efficient algorithm to print out such a sequence if one exists. Analyze the running time of your algorithm. 


Explanation:
  
In my thinking in such a problem, I consider myself as an owner of a company, so that I’m looking always for a profit. My company is international and deals with customers from all over the world. So then one of the most and main important ways to profit is converting from one currency to other and so forth.
As a company owner and a PHD computer engineer student, and I have a nice DR. Serap hoca, I think to use the methodologies in our Advanced Algorithm Design and Analysis course, why not?
So the steps are like that:
1-	Draw a directed graph with the following matrix as: 
Vertices are currency names
Directed edges are the account to convert from one currency to the other 


           Cur1    Cur2       Cur3     Cur4     Cur5
Cur1   1          0.741      0.657   1.061    1.005
Cur2   1.349   1             0.888   1.433    1.366
Cur3   1.521   1.126      1           1.614   1.538
Cur4   0.942    0.698     0.619    1           0.953
Cur5   0.995   0.732     0.650    1.049    1


An arbitrage opportunity is a directed cycle such that the product of the exchange rates is greater than one. For example, our table says that 1,000 U.S. dollars will buy 1,000.00 × .741 = 741 euros, then we can buy 741 × 1.366 = 1,012.206 Canadian dollars with our euros, and finally, 1,012.206 × .995 = 1,007.14497 U.S. dollars with our Canadian dollars, a 7.14497-dollar profit!
So, for each input in the table above we must determine whether a sequence of currency exchanges exists or not? And after that to check the ones which result with a profit > 1.
In such problem we can employ Floyd-Warshall-Algorithm, this algorithm detect the existence of a negative cycle in the graph or not, don’t solve like arbitrage problem directly, so if we can make some changes in our input data and make use of this Floyd-Warshall-Algorithm in solving such arbitrage problem, so that, how to convert from a multiply sequence to an addition one instead?
We can convert the relation from multiplication to addition as the following:
 

Suppose our matrix name is R, so that, 
𝑅[cur1,cur2] * 𝑅[cur2,cur3] * …* 𝑅[cur𝑘−1,cur𝑘] * 𝑅[cur𝑘,cur1] > 1
To be:  
ln  1/𝑅[cur1,cur2]+ ln 1/ 𝑅[cur2,cur3] + … + ln  1/𝑅[cur𝑘−1,cur𝑘]+ ln 1/𝑅[cur𝑘,cur1] < 1
So, like applying the final formula is like to detect the existence of such a negative cycles in the directed graph, so we can easily apply Floyd-Warshall-Algorithm like the following pseudocode:



<a href="https://ibb.co/cNvif6"><img src="https://preview.ibb.co/idGBYR/rrrrrrrrrrrrrr.png" alt="rrrrrrrrrrrrrr" border="0"></a><br /><a target='_blank' href='https://ar.imgbb.com/'>image host</a><br />

Here we must change in that Floyd-Warshall-Algorithm so that whenever we catch a path from some point return back to the same point with a shortest length and at that point to test if the length is negative (less than one or not?) to return a Boolean value indicating if it contains or not.
So, like by adding some code to the above code so to detect the existence of such a negative length cycle, so we can easily edit Floyd-Warshall-Algorithm like the following pseudocode:


Procedure Floyd-Warshall-DetectnegativeCycle (G, R, n): 
    for i:=1 to n  
        for j:=1 to n  
             if (i, j) ∈ G.E then currencyRate[i][j]:=R(i,j) else currencyRate [i][j]:=+ infinity
 
    for k:=1 to n 
          for i:=1 to n 
               for j:=1 to n
                           if currencyRate [i][j]> currencyRate [i][k]+ currencyRate [k,j] 
                                then  currencyRate [i][j] := currencyRate [i][k]+ currencyRate [k][j] 
    for i:=1 to n 
    if currencyRate [i][i] < 0 
   then return true 
   return false

<a href="https://ibb.co/c31vtR"><img src="https://preview.ibb.co/kdGjnm/eeeeeeeeeeeeeeeeeeeeeeeeeeeeeeee.png" alt="eeeeeeeeeeeeeeeeeeeeeeeeeeeeeeee" border="0"></a>

Fig 2. Edited Floyd-Warshall-Algorithm for determining the shortest path negative length cycles.

The run time of the algorithm is O (n3) due to the three nested for loop.



Applyıng a Java code output:

<a href="https://ibb.co/k6pyDR"><img src="https://image.ibb.co/hG4n7m/trtr.png" alt="trtr" border="0"></a><br /><a target='_blank' href='https://ar.imgbb.com/'>images upload</a><br />


