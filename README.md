Download Link: https://assignmentchef.com/product/solved-cop3530-project-3-simplified-page-rank-algorithm
<br>
In late 90’s as the number of webpages on the internet were growing exponentially different search engines were trying different approaches to rank the webpages.  At Stanford, two computer science PhD students, Sergey Brin and Larry Page were working on the following questions: How can we trust information? Why are some web pages more important than others? Their research led to the formation of the Google search engine. In this programming assignment, you are required to implement a simplified version of the original PageRank algorithm on which Google was built.

<strong>Representing the Web as a Graph </strong>

The idea that the entire internet can be represented as a graph. Each node represents a webpage and each edge represents a link between two webpages. This graph can be implemented as an Adjacency Matrix or an Adjacency List.  <strong>Feel free to use any data structure. </strong>







Now for the sake of simplicity, we are explaining the assignment in the form of an Adjacency Matrix.  We represent the graph in the form of |V|x|V| matrix where |V| is the total number of vertices in the graph. This is mapped to the webpages in the entire internet. Thus, if there is an edge from V<sub>i</sub> to V<sub>j </sub>(the from_page points to_page), we have the value in our adjacency matrix M<sub>ij </sub>= 1 and 0 otherwise.

<strong> </strong>




<table width="144">

 <tbody>

  <tr>

   <td width="24"><strong>1 </strong></td>

   <td width="24">0</td>

   <td width="24">1</td>

   <td width="24">0</td>

   <td width="24">1</td>

   <td width="24">0</td>

  </tr>

  <tr>

   <td rowspan="2" width="24"><strong>2 </strong><strong>3 </strong></td>

   <td width="24">0</td>

   <td width="24">0</td>

   <td width="24">0</td>

   <td width="24">1</td>

   <td width="24">0</td>

  </tr>

  <tr>

   <td width="24">0</td>

   <td width="24">0</td>

   <td width="24">0</td>

   <td width="24">0</td>

   <td width="24">1</td>

  </tr>

  <tr>

   <td width="24"><strong>4 </strong></td>

   <td width="24">0</td>

   <td width="24">0</td>

   <td width="24">1</td>

   <td width="24">0</td>

   <td width="24">0</td>

  </tr>

  <tr>

   <td width="24"><strong>5 </strong></td>

   <td width="24">1</td>

   <td width="24">1</td>

   <td width="24">0</td>

   <td width="24">0</td>

   <td width="24">0</td>

  </tr>

 </tbody>

</table>

<strong><em>        </em>1       2       3       4       5 </strong>

<strong> </strong>

<strong> </strong>

<strong>                                                M= </strong>

<strong> </strong>

<strong> </strong>

<strong> </strong>

<strong> </strong>

<strong>Core Idea of PageRank </strong>

<strong> </strong>

<ol>

 <li>Important web pages will point to other important webpages.</li>

 <li>Each page will have a score and the results of the search will be based on the page score (called page rank).</li>

</ol>

























Rank(i) = j/out_degree(j) + k/out_degree(k)

























Each webpage is thus a node in the directed graph and has incoming edges and outgoing edges. Each node has a rank. According to PageRank, this rank is equally split among the node’s outgoing links and this rank is equal to the sum of the incoming ranks. The rank is based on the indegree (the number of nodes pointing to it) and the importance of incoming node. This is important considering let’s say you create your personal website and have a million links to other pages of importance. If this was not the case and rank used out links, we can easily dupe the algorithm. Therefore, the rank is based on in-links.

<strong>Goal </strong>

In this assignment, you need to compute the rank of the webpages using a Simplified Algorithm explained in the example below.




<strong>Input </strong>

Line 1 contains the number of lines (n) that will follow and the number of power iterations you need to perform. Each line from

2 to n will contain two URL’s –  <em>from_page    to_page</em>    separated by a space. This means from_page points to the URL to_page.




<strong>Output </strong>

Print the PageRank of all pages after n powerIterations in ascending alphabetical order of webpage. Also, round off the rank of the page to two decimal places.

<strong> </strong>

<strong> </strong>

<h1>Explanation through a Core Example</h1>

<table width="197">

 <tbody>

  <tr>

   <td width="48"><strong> </strong><strong>Input: </strong></td>

   <td width="96">7 2</td>

   <td width="53"> </td>

  </tr>

  <tr>

   <td width="48"> </td>

   <td width="96">google.com</td>

   <td width="53">gmail.com</td>

  </tr>

 </tbody>

</table>

google.com               maps.com facebook.com        ufl.edu ufl.edu                           google.com ufl.edu                                     gmail.com maps.com               facebook.com gmail.com maps.com

<sup>(2)</sup>

<strong>Output </strong>facebook.com 0.20 gmail.com 0.20 google.com 0.10 maps.com 0.30

ufl.edu 0.20




<strong>Step 1: Mapping for Simplicity (Optional but you will need a mechanism to store unique vertices) </strong>Use a map/array to map the URL’s with a unique id

<strong><em>           </em>Data Structure 1 </strong>

<table width="137">

 <tbody>

  <tr>

   <td rowspan="2" width="31"><strong>1 </strong><strong>2 </strong></td>

   <td width="106">google.com</td>

  </tr>

  <tr>

   <td width="106">gmail.com</td>

  </tr>

  <tr>

   <td width="31"><strong>3 </strong></td>

   <td width="106">facebook.com</td>

  </tr>

  <tr>

   <td width="31"><strong>4 </strong></td>

   <td width="106">maps.com</td>

  </tr>

  <tr>

   <td width="31"><strong>5 </strong></td>

   <td width="106">ufl.edu</td>

  </tr>

 </tbody>

</table>

<ul>

 <li>com</li>

 <li>com</li>

 <li>com</li>

 <li>com</li>

 <li>edu</li>

</ul>




<strong>Step 2: Graph Representation and Page Rank </strong>

In page rank, the equation for your graph is given as follows:-

<strong>Rank of a Page, r= M.r    where, </strong>

M is the matrix with values given by the following:

M<sub>ij </sub>= 1/d<sub>j</sub>         if there is an edge from V<sub>j</sub> to V<sub>i </sub>(d<sub>j </sub>is the outdegree of node j)




<ul>

 <li>otherwise</li>

</ul>




For our graph, the adjacency matrix, M will look like:




<strong> </strong>

<strong> </strong>

<strong> </strong>

<strong> </strong>

<strong> </strong>




<ul>

 <li><strong>2 3                4                5 </strong></li>

</ul>

<table width="202">

 <tbody>

  <tr>

   <td rowspan="5" width="24"><strong>1 </strong><strong>2 </strong><strong>3 </strong><strong>4 </strong><strong>5 </strong></td>

   <td width="35">0</td>

   <td width="36">0</td>

   <td width="36">0</td>

   <td width="36">0</td>

   <td width="35">1/d<sub>5</sub></td>

  </tr>

  <tr>

   <td width="35">1/d<sub>1</sub></td>

   <td width="36">0</td>

   <td width="36">0</td>

   <td width="36">0</td>

   <td width="35">1/d<sub>5</sub></td>

  </tr>

  <tr>

   <td width="35">0</td>

   <td width="36">0</td>

   <td width="36">0</td>

   <td width="36">1/d<sub>4</sub></td>

   <td width="35">0</td>

  </tr>

  <tr>

   <td width="35">1/d<sub>1</sub></td>

   <td width="36">1/d<sub>2</sub></td>

   <td width="36">0</td>

   <td width="36">0</td>

   <td width="35">0</td>

  </tr>

  <tr>

   <td width="35">0</td>

   <td width="36">0</td>

   <td width="36">1/d<sub>3</sub></td>

   <td width="36">0</td>

   <td width="35">0</td>

  </tr>

 </tbody>

</table>

<strong>Step 3: Power iteration, r(t+1)=M.r(t) </strong>

This means that a rank of the webpage at time t+1 is equal to the rank of that page at time t multiplied by matrix, M. To achieve this, we create our matrix M based on input. Next, we initialize r(t) which is a matrix of size |V|x1 and consists of the ranks of every webpage. We initialize r(t) to 1/|V|. Next we compute power_iterations based on our input.

<strong>                                                                                                                                                                                       r(0)                                                                  M   </strong>

<strong>                                                                   </strong>

<strong><em>          </em>1                                         <em>          </em>1           2           3           4           5 </strong>

<strong> </strong>

<table width="343">

 <tbody>

  <tr>

   <td width="100">


    <table width="59">

     <tbody>

      <tr>

       <td width="24"><strong>1 </strong></td>

       <td width="35">1/5</td>

      </tr>

      <tr>

       <td width="24"><strong>2 </strong></td>

       <td width="35">1/5</td>

      </tr>

      <tr>

       <td rowspan="2" width="24"><strong>3 </strong><strong>4 </strong></td>

       <td width="35">1/5</td>

      </tr>

      <tr>

       <td width="35">1/5</td>

      </tr>

      <tr>

       <td width="24"><strong>5 </strong></td>

       <td width="35">1/5</td>

      </tr>

     </tbody>

    </table></td>

   <td width="243">


    <table width="202">

     <tbody>

      <tr>

       <td width="24"><strong>1 </strong></td>

       <td width="36">0</td>

       <td width="36">0</td>

       <td width="36">0</td>

       <td width="36">0</td>

       <td width="35">1/d<sub>5</sub></td>

      </tr>

      <tr>

       <td width="24"><strong>2 </strong></td>

       <td width="36">1/d<sub>1</sub></td>

       <td width="36">0</td>

       <td width="36">0</td>

       <td width="36">0</td>

       <td width="35">1/d<sub>5</sub></td>

      </tr>

      <tr>

       <td rowspan="2" width="24"><strong>3 </strong><strong>4 </strong></td>

       <td width="36">0</td>

       <td width="36">0</td>

       <td width="36">0</td>

       <td width="36">1/d<sub>4</sub></td>

       <td width="35">0</td>

      </tr>

      <tr>

       <td width="36">1/d<sub>1</sub></td>

       <td width="36">1/d<sub>2</sub></td>

       <td width="36">0</td>

       <td width="36">0</td>

       <td width="35">0</td>

      </tr>

      <tr>

       <td width="24"><strong>5 </strong></td>

       <td width="36">0</td>

       <td width="36">0</td>

       <td width="36">1/d<sub>3</sub></td>

       <td width="36">0</td>

       <td width="35">0</td>

      </tr>

     </tbody>

    </table></td>

  </tr>

 </tbody>

</table>

<strong> </strong>

<strong>                                                                   </strong>

<strong>                                                                            <em>            </em>1           2           3            4              5          <em>                                   </em>1           <em>            </em>1 </strong>

<strong> </strong>

<strong>1 </strong>

<table width="61">

 <tbody>

  <tr>

   <td width="24"><strong>1 </strong></td>

   <td width="37">1/10</td>

  </tr>

  <tr>

   <td width="24"><strong>2 </strong></td>

   <td width="37">1/5</td>

  </tr>

  <tr>

   <td rowspan="2" width="24"><strong>3 </strong><strong>4 </strong></td>

   <td width="37">1/5</td>

  </tr>

  <tr>

   <td width="37">3/10</td>

  </tr>

  <tr>

   <td width="24"><strong>5 </strong></td>

   <td width="37">1/5</td>

  </tr>

 </tbody>

</table>

<table width="250">

 <tbody>

  <tr>

   <td width="35">0</td>

   <td width="36">0</td>

   <td width="36">0</td>

   <td width="36">0</td>

   <td width="36">1/2</td>

   <td width="38"><strong>1 </strong></td>

   <td width="35">1/5</td>

  </tr>

  <tr>

   <td width="35">1/2</td>

   <td width="36">0</td>

   <td width="36">0</td>

   <td width="36">0</td>

   <td width="36">1/2</td>

   <td width="38"><strong>2 </strong></td>

   <td width="35">1/5</td>

  </tr>

  <tr>

   <td width="35">0</td>

   <td width="36">0</td>

   <td width="36">0</td>

   <td width="36">1</td>

   <td width="36">0</td>

   <td rowspan="2" width="38">x <strong> 3 </strong><strong>4 </strong></td>

   <td width="35">1/5</td>

  </tr>

  <tr>

   <td width="35">1/2</td>

   <td width="36">1</td>

   <td width="36">0</td>

   <td width="36">0</td>

   <td width="36">0</td>

   <td width="35">1/5</td>

  </tr>

  <tr>

   <td width="35">0</td>

   <td width="36">0</td>

   <td width="36">1</td>

   <td width="36">0</td>

   <td width="36">0</td>

   <td width="38"><strong>5 </strong></td>

   <td width="35">1/5</td>

  </tr>

 </tbody>

</table>

r(t+1)=r(0+1)=r(1) =M.r(0)=               <strong>2 </strong>=

<sup>                                                                 </sup><strong>3 </strong>

<strong><sup>                                                                 </sup>4 </strong>

<strong><sup>                                                                 </sup>5 </strong>

<strong> </strong>

<strong>                                                                                               M                         x                      r(0)                   =                     r(1) </strong>

<strong> </strong>

In this input case, the number of power_iterations is 2, if it is 1 then return the initializing rank matrix or r(0). If iterations&gt;2, the process repeats where you multiply the matrix, M with the new rank matrix r(t+1) at the next iteration.




<strong> </strong>

<strong> </strong>

<strong>Stepik Test Case Two Explanation:- (Power_iteration=3) </strong>

<strong>                                                                   </strong>

<strong>                                                                            <em>           </em>1           2           3           4              5           <em>                                   </em>1           <em>            </em>1 </strong>

<strong> </strong>

<strong>1 </strong>

<table width="61">

 <tbody>

  <tr>

   <td width="24"><strong>1 </strong></td>

   <td width="37">1/10</td>

  </tr>

  <tr>

   <td width="24"><strong>2 </strong></td>

   <td width="37">3/20</td>

  </tr>

  <tr>

   <td width="24"><strong>3 </strong></td>

   <td width="37">3/10</td>

  </tr>

  <tr>

   <td width="24"><strong>4 </strong></td>

   <td width="37">1/4</td>

  </tr>

  <tr>

   <td width="24"><strong>5 </strong></td>

   <td width="37">1/5</td>

  </tr>

 </tbody>

</table>

<table width="252">

 <tbody>

  <tr>

   <td width="35">0</td>

   <td width="36">0</td>

   <td width="36">0</td>

   <td width="36">0</td>

   <td width="35">1/2</td>

   <td rowspan="2" width="38"><strong>1 </strong><strong>2 </strong></td>

   <td width="37">1/10</td>

  </tr>

  <tr>

   <td width="35">1/2</td>

   <td width="36">0</td>

   <td width="36">0</td>

   <td width="36">0</td>

   <td width="35">1/2</td>

   <td width="37">1/5</td>

  </tr>

  <tr>

   <td width="35">0</td>

   <td width="36">0</td>

   <td width="36">0</td>

   <td width="36">1</td>

   <td width="35">0</td>

   <td width="38">x <strong> 3 </strong></td>

   <td width="37">1/5</td>

  </tr>

  <tr>

   <td width="35">1/2</td>

   <td width="36">1</td>

   <td width="36">0</td>

   <td width="36">0</td>

   <td width="35">0</td>

   <td width="38"><strong>4 </strong></td>

   <td width="37">3/10</td>

  </tr>

  <tr>

   <td width="35">0</td>

   <td width="36">0</td>

   <td width="36">1</td>

   <td width="36">0</td>

   <td width="35">0</td>

   <td width="38"><strong>5 </strong></td>

   <td width="37">1/5</td>

  </tr>

 </tbody>

</table>

r(t+1)=r(1+1)=r(2) =M.r(1)=               <strong>2 </strong>=

<sup>                                                                 </sup><strong>3 </strong>

<strong><sup>                                                                 </sup>4 </strong>

<strong><sup>                                                                 </sup>5 </strong>

<strong> </strong>

<strong>                                                                                               M                         x                      r(1)                   =                     r(2) </strong>

<strong> </strong>

<strong> </strong>

<strong> </strong>

<strong> </strong>

<strong> </strong>

<strong> </strong>

<strong> </strong>

<strong> </strong>

<strong> </strong>

<strong> </strong>

<strong> </strong>

<strong> </strong>

<strong> </strong>

<strong> </strong>

<strong>Template </strong>

You are allowed to use your own template but make sure your code passes the sample test cases. An example template to think about the problem is :




Class AdjacencyListorMatrix {                   private:

//Think about what member variables you need to initialize                 public:

//Think about what helper functions you will need in the algorithm

};




void AdjacencyListorMatrix::PageRank(int n){  }     // prints the PageRank of all pages after n powerIterations in ascending alphabetical order of webpage and rounding rank to two decimal places]




// This class and method are optional. To accept input, you can use this method:







int main()

{

int no_of_lines, power_iterations;

std::string from, to;     std::cin &gt;&gt; no_of_lines;     std::cin &gt;&gt; power_iterations;

for(int i=0;i&lt; no_of_lines;i++)

{                                std::cin&gt;&gt;from;                          std::cin&gt;&gt;to;

// Do Something

}

//Create a graph

Created_Graph.PageRank(power_iterations);

}