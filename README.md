# Reproducible research: version control and R

## Answer section

*Questions 1, 2, 3* https://github.com/solarproblems/logistic_growth

*Question 4* 
- Both iterations of a random walk produce a path that ranges across at least 10 square spatial units, with some regions where it loops back on itself and some regions with no looping. 
These appear to be somewhat evenly distributed. The beginning and end regions are not necessarily distant from one another, and in one case the end region is very close to the origin.

- A random seed is a numerical string that serves as the input to a the function that makes up a deterministic pseudo-random number generator. The output must be pseudo-random in that its distribution closely resembles a random distribution, and would not vary in a clear pattern with respect to the input seed's value. The same seed applied to the function will produce the same output every time. This makes seeds useful for reproducibility in that a large pseudo-random distribution can be summarised and shared by a short seed plus the function, that together necessarily entail the distribution. It is easier to share a seed and a function than it is to share a large dataset of random elements. For a set of pseudo-random simulations if you set a seed beforehand, the set of simulations will still be pseudo-random but replicable every time the program is reset and the set of simulation results created again.

- ![image](https://github.com/solarproblems/reproducible-research_homework/assets/152936548/3454fda7-58d5-4d97-b6ad-546010aa96cb)
This comparison shows the reproducibility elements (adding a seed, storing the package versions) highlighted in red on the left because I didn't commit an earlier version, so I had to then remove those to show the differences. Either way it shows the changes I made, the two versions in the history are just the other way around. 


*Question 5*

-The table has 13 columns and 33 rows. 

-I use a natural log transformation on both axes.

-The regression produces an estimate for an exponent of 1.52 with a p value of 6.44x10^-10. The estimate for the scaling factor is 1182, a back transformation of the intercept 7.0748, with a p value of 2.28x10^-10. Both are significant at the 0.001 level. In addition both values match those obtained by the original researchers through their analysis.  

- ![image](https://github.com/solarproblems/reproducible-research_homework/assets/152936548/7767d518-2ca5-4da8-bf6a-307ce75a8fef)
('table' is the name given to the dataset earlier in the code)
![image](https://github.com/solarproblems/reproducible-research_homework/assets/152936548/199806f0-2459-42f9-9825-df18d3d15c55)
And here is the code output. 

- Using our linear model we can produce an estimate for virion volume from a genome length. For 300kb, using our raw model outputs for a log-log transformation,
  e^(1.5152*log(300) + 7.0748) =  *6697007nm^3*


  *Bonus Question*

In scientific research, reproducibility and replicability are different but related concepts. Reproducibility refers to how easy it is to analyse the same existing data repeatedly and come to the same conclusions. Ideally every mechanistic step of the analysis should be repeatable. Replicability, concerns itself with the entire process from data collection to conclusions, and making it possible to repeat all this. Git, and the web based hosting service using it Github, are promising tools for both of these but mainly reproducibility. 

Reproducibility is easier to control as it is limited to the analysis stage. The most basic element is the availability of both the data itself and a comprehensive record of each step used to process it. This ideally includes every step including any cleaning of the most raw data, all the way to the software functions used to calculate summary statistics or fit models. Even software version should be recorded, as updates can alter useful functions. Github allows open online file sharing
of software and data, and has a rigorous process of saving versions, each recorded stage of alteration of a file, using the software 'Git'. However, the effectiveness of these systems assumes that the order/process in which to use the data and software are either made explicit or are simple enough to easily deduce. Version control also requires discipline by the original researcher, as it cannot capture every keystroke; Useful script may go unsaved or deleted within the session where it is used. Reproducibility also applies less well to any qualitative step, as only mechanistic analyses on numerical data can really be recorded fully. Qualitative judgement and weighting, even of a strong statistical result, cannot be fully controlled.

Replicability can be more difficult at the experimental end, where the object the data is measuring is variable and thus the data would differ even if the same methodology was applied again. The primary exception is where software is used in the data collection, where there is some software step prior to the raw data. For hardware-embedded algorithms such as some acoustic monitoring devices etc., some of the data processing may not be possible to include in a public repository such as Github, and version control is irrelevant. On the other hand, if software is used to generate the data, as in simulation, then there are plenty of protocols available for replicability. Here, all code and versions thereof can be made available on a public host such as Github, and for anything involving a pseudo-random number generator a seed can be used to maintain the random quality of the output but ensure this output is identical every time the code is run, including by other researchers so long as they have the seed. In essence, this makes the data of a simulation more available, improving the reproducibility of any further analyses. 

In its owk right, Github can be deterrent to researchers in that it has a steep learning curve and many features are paywalled for access or amount usable. Git and Githubs's branching system also means that when many researchers work analysis for the same project, there may be some parallel analyses. While the full extent and history of this branching can be made available, reproducibility requires that the data analysis pipeline is clear and linear, a single sequence. Otherwise there may be ambiguity and conflict even when all recorded procedures are followed from a Github repository. 


## Instructions

The homework for this Computer skills practical is divided into 5 questions for a total of 100 points (plus an optional bonus question worth 10 extra points). First, fork this repo and make sure your fork is made **Public** for marking. Answers should be added to the # INSERT ANSWERS HERE # section above in the **README.md** file of your forked repository.

Questions 1, 2 and 3 should be answered in the **README.md** file of the `logistic_growth` repo that you forked during the practical. To answer those questions here, simply include a link to your logistic_growth repo.

**Submission**: Please submit a single **PDF** file with your candidate number (and no other identifying information), and a link to your fork of the `reproducible-research_homework` repo with the completed answers. All answers should be on the `main` branch.

## Assignment questions 

1) (**10 points**) Annotate the **README.md** file in your `logistic_growth` repo with more detailed information about the analysis. Add a section on the results and include the estimates for $N_0$, $r$ and $K$ (mention which *.csv file you used).
   
2) (**10 points**) Use your estimates of $N_0$ and $r$ to calculate the population size at $t$ = 4980 min, assuming that the population grows exponentially. How does it compare to the population size predicted under logistic growth? 

3) (**20 points**) Add an R script to your repository that makes a graph comparing the exponential and logistic growth curves (using the same parameter estimates you found). Upload this graph to your repo and include it in the **README.md** file so it can be viewed in the repo homepage.
   
4) (**30 points**) Sometimes we are interested in modelling a process that involves randomness. A good example is Brownian motion. We will explore how to simulate a random process in a way that it is reproducible:

   - A script for simulating a random_walk is provided in the `question-4-code` folder of this repo. Execute the code to produce the paths of two random walks. What do you observe? (10 points)
   - Investigate the term **random seeds**. What is a random seed and how does it work? (5 points)
   - Edit the script to make a reproducible simulation of Brownian motion. Commit the file and push it to your forked `reproducible-research_homework` repo. (10 points)
   - Go to your commit history and click on the latest commit. Show the edit you made to the code in the comparison view (add this image to the **README.md** of the fork). (5 points)

5) (**30 points**) In 2014, Cui, Schlub and Holmes published an article in the *Journal of Virology* (doi: https://doi.org/10.1128/jvi.00362-14) showing that the size of viral particles, more specifically their volume, could be predicted from their genome size (length). They found that this relationship can be modelled using an allometric equation of the form **$`V = \beta L^{\alpha}`$**, where $`V`$ is the virion volume in nm<sup>3</sup> and $`L`$ is the genome length in nucleotides.

   - Import the data for double-stranded DNA (dsDNA) viruses taken from the Supplementary Materials of the original paper into Posit Cloud (the csv file is in the `question-5-data` folder). How many rows and columns does the table have? (3 points)
   - What transformation can you use to fit a linear model to the data? Apply the transformation. (3 points)
   - Find the exponent ($\alpha$) and scaling factor ($\beta$) of the allometric law for dsDNA viruses and write the p-values from the model you obtained, are they statistically significant? Compare the values you found to those shown in **Table 2** of the paper, did you find the same values? (10 points)
   - Write the code to reproduce the figure shown below. (10 points)

  <p align="center">
     <img src="https://github.com/josegabrielnb/reproducible-research_homework/blob/main/question-5-data/allometric_scaling.png" width="600" height="500">
  </p>

  - What is the estimated volume of a 300 kb dsDNA virus? (4 points)

**Bonus** (**10 points**) Explain the difference between reproducibility and replicability in scientific research. How can git and GitHub be used to enhance the reproducibility and replicability of your work? what limitations do they have? (e.g. check the platform [protocols.io](https://www.protocols.io/)).
