## Chapter01_Genetic Algorithm GA 基因算法

# Genetic Algorithm

Genetic Algorithm, GA, Simple Genetic Algorithm, SGA, Canonical Genetic Algorithm, CGA.

## Taxonomy

The Genetic Algorithm is an Adaptive Strategy and a Global Optimization technique. It is an Evolutionary Algorithm and belongs to the broader study of Evolutionary Computation. The Genetic Algorithm is a sibling of other Evolutionary Algorithms such as Genetic Programming, Evolution Strategies, Evolutionary Programming, and Learning Classifier Systems. The Genetic Algorithm is a parent of a large number of variant techniques and sub-fields too numerous to list.

## Inspiration

The Genetic Algorithm is inspired by population genetics (including heredity and gene frequencies), and evolution at the population level, as well as the Mendelian understanding of the structure (such as chromosomes, genes, alleles) and mechanisms (such as recombination and mutation). This is the so-called new or modern synthesis of evolutionary biology.

## Metaphor

Individuals of a population contribute their genetic material (called the genotype) proportional to their suitability of their expressed genome (called their phenotype) to their environment, in the form of offspring. The next generation is created through a process of mating that involves recombination of two individuals genomes in the population with the introduction of random copying errors (called mutation). This iterative process may result in an improved adaptive-fit between the phenotypes of individuals in a population and the environment.

## Strategy

The objective of the Genetic Algorithm is to maximize the payoff of candidate solutions in the population against a cost function from the problem domain. The strategy for the Genetic Algorithm is to repeatedly employ surrogates for the recombination and mutation genetic mechanisms on the population of candidate solutions, where the cost function (also known as objective or fitness function) applied to a decoded representation of a candidate governs the probabilistic contributions a given candidate solution can make to the subsequent generation of candidate solutions.

## Procedure

Algorithm (below) provides a pseudocode listing of the Genetic Algorithm for minimizing a cost function.

Pseudocode for the Genetic Algorithm

## Heuristics

Binary strings (referred to as 'bitstrings') are the classical representation as they can be decoded to almost any desired representation. Real-valued and integer variables can be decoded using the binary coded decimal method, one's or two's complement methods, or the gray code method, the latter of which is generally preferred.
Problem specific representations and customized genetic operators should be adopted, incorporating as much prior information about the problem domain as possible.
The size of the population must be large enough to provide sufficient coverage of the domain and mixing of the useful sub-components of the solution [Goldberg1992].
The Genetic Algorithm is classically configured with a high probability of recombination (such as 95%-99% of the selected population) and a low probability of mutation (such as  where  is the number of components in a solution) [Muhlenbein1992] [Back1993].
The fitness-proportionate selection of candidate solutions to contribute to the next generation should be neither too greedy (to avoid the takeover of fitter candidate solutions) nor too random.

## Code Listing

Listing (below) provides an example of the Genetic Algorithm implemented in the Ruby Programming Language. The demonstration problem is a maximizing binary optimization problem called OneMax that seeks a binary string of unity (all '1' bits). The objective function provides only an indication of the number of correct bits in a candidate string, not the positions of the correct bits.

The Genetic Algorithm is implemented with a conservative configuration including binary tournament selection for the selection operator, one-point crossover for the recombination operator, and point mutations for the mutation operator.

```java

```

## References

### Primary Sources

Holland is the grandfather of the field that became Genetic Algorithms. Holland investigated adaptive systems in the late 1960s proposing an adaptive system formalism and adaptive strategies referred to as 'adaptive plans' [Holland1962](http://www.cleveralgorithms.com/nature-inspired/evolution/genetic_algorithm.html#Holland1962) [Holland1962a](http://www.cleveralgorithms.com/nature-inspired/evolution/genetic_algorithm.html#Holland1962a) [Holland1969](http://www.cleveralgorithms.com/nature-inspired/evolution/genetic_algorithm.html#Holland1969). Holland's theoretical framework was investigated and elaborated by his Ph.D. students at the University of Michigan. Rosenberg investigated a chemical and molecular model of a biological inspired adaptive plan [Rosenberg1967](http://www.cleveralgorithms.com/nature-inspired/evolution/genetic_algorithm.html#Rosenberg1967). Bagley investigated meta-environments and a genetic adaptive plan referred to as a genetic algorithm applied to a simple game called hexapawn [Bagley1967](http://www.cleveralgorithms.com/nature-inspired/evolution/genetic_algorithm.html#Bagley1967). Cavicchio further elaborated the genetic adaptive plan by proposing numerous variations, referring to some as 'reproductive plans' [Cavicchio1970](http://www.cleveralgorithms.com/nature-inspired/evolution/genetic_algorithm.html#Cavicchio1970).

Other important contributions were made by Frantz who investigated what were referred to as genetic algorithms for search [Frantz1972](http://www.cleveralgorithms.com/nature-inspired/evolution/genetic_algorithm.html#Frantz1972), and Hollstien who investigated genetic plans for adaptive control and function optimization [Hollstien1971](http://www.cleveralgorithms.com/nature-inspired/evolution/genetic_algorithm.html#Hollstien1971). De Jong performed a seminal investigation of the genetic adaptive model (genetic plans) applied to continuous function optimization and his suite of test problems adopted are still commonly used [Jong1975](http://www.cleveralgorithms.com/nature-inspired/evolution/genetic_algorithm.html#Jong1975). Holland wrote the the seminal book on his research focusing on the proposed adaptive systems formalism, the reproductive and genetic adaptive plans, and provided a theoretical framework for the mechanisms used and explanation for the capabilities of what would become genetic algorithms [Holland1975](http://www.cleveralgorithms.com/nature-inspired/evolution/genetic_algorithm.html#Holland1975).

### Learn More

The field of genetic algorithms is very large, resulting in large numbers of variations on the canonical technique. Goldberg provides a classical overview of the field in a review article [Goldberg1994](http://www.cleveralgorithms.com/nature-inspired/evolution/genetic_algorithm.html#Goldberg1994), as does Mitchell [Mitchell1995](http://www.cleveralgorithms.com/nature-inspired/evolution/genetic_algorithm.html#Mitchell1995). Whitley describes a classical tutorial for the Genetic Algorithm covering both practical and theoretical concerns [Whitley1994](http://www.cleveralgorithms.com/nature-inspired/evolution/genetic_algorithm.html#Whitley1994).

The algorithm is highly-modular and a sub-field exists to study each sub-process, specifically: selection, recombination, mutation, and representation. The Genetic Algorithm is most commonly used as an optimization technique, although it should also be considered a general adaptive strategy [Jong1992](http://www.cleveralgorithms.com/nature-inspired/evolution/genetic_algorithm.html#Jong1992). The schema theorem is a classical explanation for the power of the Genetic Algorithm proposed by Holland [Holland1975](http://www.cleveralgorithms.com/nature-inspired/evolution/genetic_algorithm.html#Holland1975), and investigated by Goldberg under the name of the building block hypothesis [Goldberg1989](http://www.cleveralgorithms.com/nature-inspired/evolution/genetic_algorithm.html#Goldberg1989).

The classical book on genetic algorithms as an optimization and machine learning technique was written by Goldberg and provides an in-depth review and practical study of the approach [Goldberg1989](http://www.cleveralgorithms.com/nature-inspired/evolution/genetic_algorithm.html#Goldberg1989). Mitchell provides a contemporary reference text introducing the technique and the field [Mitchell1998](http://www.cleveralgorithms.com/nature-inspired/evolution/genetic_algorithm.html#Mitchell1998). Finally, Goldberg provides a modern study of the field, the lessons learned, and reviews the broader toolset of optimization algorithms that the field has produced [Goldberg2002](http://www.cleveralgorithms.com/nature-inspired/evolution/genetic_algorithm.html#Goldberg2002).

## Bibliography

[Back1993]	T. Bäck, "[Optimal Mutation Rates in Genetic Search](http://scholar.google.com.au/scholar?q=Optimal+Mutation+Rates+in+Genetic+Search)", in Proceedings of the Fifth International Conference on Genetic Algorithms, 1993.
[Bagley1967]	J. D. Bagley, "[The behavior of adaptive systems which employ genetic and correlation algorithms](http://scholar.google.com.au/scholar?q=The+behavior+of+adaptive+systems+which+employ+genetic+and+correlation++algorithms)", [PhD Thesis] University of Michigan, 1967.
[Cavicchio1970]	D. J. Cavicchio Jr., "Adaptive Search Using Simulated Evolution", [PhD Thesis] The University of Michigan, 1970.
[Frantz1972]	D. R. Frantz, "Non-linearities in genetic adaptive search", [PhD Thesis] University of Michigan, 1972.
[Goldberg1989]	D. E. Goldberg, "Genetic Algorithms in Search, Optimization, and Machine Learning", Addison-Wesley, 1989.
[Goldberg1992]	D. E. Goldberg and K. Deb and J. H. Clark, "Genetic Algorithms, Noise, and the Sizing of Populations", Complex Systems, 1992.
[Goldberg1994]	D. E. Goldberg, "Genetic and evolutionary algorithms come of age", Communications of the ACM, 1994.
[Goldberg2002]	D. E. Goldberg, "The design of innovation: Lessons from and for competent genetic algorithms", Springer, 2002.
[Holland1962]	J. H. Holland, "Outline for a logical theory of adaptive systems", Journal of the ACM (JACM), 1962.
[Holland1962a]	J. H. Holland, "Information processing in adaptive systems", in Processing of Information in the Nervous System, 1962.
[Holland1969]	J. H. Holland, "Adaptive plans optimal for payoff-only environments", in Proceedings of the Second Hawaii Conference on Systems Sciences, 1969.
[Holland1975]	J. H. Holland, "Adaptation in natural and artificial systems: An introductory analysis with applications to biology, control, and artificial intelligence", University of Michigan Press, 1975.
[Hollstien1971]	R. B. Hollstien, "Artificial genetic adaptation in computer control systems", [PhD Thesis] The University of Michigan, 1971.
[Jong1975]	K. A. De Jong, "An analysis of the behavior of a class of genetic adaptive systems", [PhD Thesis] University of Michigan Ann Arbor, MI, USA, 1975.
[Jong1992]	K. A. De Jong, "Genetic Algorithms are NOT Function Optimizers", in Proceedings of the Second Workshop on Foundations of Genetic Algorithms, 1992.
[Mitchell1995]	M. Mitchell, "Genetic algorithms: An overview", Complexity, 1995.
[Mitchell1998]	M. Mitchell, "An Introduction to Genetic Algorithms", MIT Press, 1998.
[Muhlenbein1992]	H. Mühlenbein, "How Genetic Algorithms Really Work: I. Mutation and Hillclimbing", in Parallel Problem Solving from Nature 2, 1992.
[Rosenberg1967]	R. Rosenberg, "Simulation of genetic populations with biochemical properties", [PhD Thesis] University of Michigan, 1967.
[Whitley1994]	D. Whitley, "A Genetic Algorithm Tutorial", Statistics and Computing, 1994.
