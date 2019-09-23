# robin



*ROBIN (Robustness In Network)* is an R package for the Validation of community detection it has a double aim it studies the robustness of a community detection algorithm and compares the robustness of two community detection algorithms. 

The package implements a methodology that detects if the community structure 
found by a detection algorithm is statistically significant or is a result 
of chance, merely due to edge positions in the network. It performs a 
perturbation strategy and runs a null model to build a set of procedures based 
on different stability measures. 

###### It provides:
*A procedure to examine the stability of the partition recovered against random 
perturbations of the original graph structure
*Three tests to determine whether the obtained clustering departs significantly 
from the null model
*A routine to compare different detection algorithms applied to the same 
network to discover which fits better
*A graphical interactive representation



##### Example 1: "Robustness of a community detection"
```{r}
graph <- prepGraph(file=my_network, file.format="gml")
graphRandom <- random(graph=graph)
proc <- robinRobust(graph=graph, graphRandom=graphRandom, measure="vi", 
                  method="louvain", type="independent")               
plotRobin(graph=graph, model1=proc$Mean, model2=proc$MeanRandom, 
legend=c("real data", "null model"), measure="vi")
robinGPTest(ratio=proc$ratios)
```
<img class="aligncenter size-full wp-image-8747" alt="markdown" src="http://www.maffucci.it/wp-content/uploads/2013/08/markdown.jpg" width="640" height="108" />

<img src="https://github.com/ValeriaPolicastro/robin/blob/master/R/Figure_Paper_files/figure-latex/unnamed-chunk-1-1.pdf" width="640" height="108" />



##### Example 2: "Comparison of two community detection"
```{r}
graph <- prepGraph(file=my_network, file.format="gml")
comp <- robinCompare(graph=graph, method1="fastGreedy",
                method2="louvain", measure="vi", type="independent")                
plotRobin(graph=graph, model1=comp$Mean1, model2=comp$Mean2, measure="vi", 
legend=c("fastGreedy", "louvain"), title="FastGreedy vs Louvain")
```
## License
[Copyright (c) 2019 V. Policastro,  A. Carissimo, L. Cutillo, I. De Feis and D. Righelli.](https://github.com/ValeriaPolicastro/robin/blob/master/LICENCE)

