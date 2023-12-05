# Reproducible research: version control and R

**logistic growth analysis**



*Question 1.*

These analyses used the "experiment1.csv" file provided. 
A linear model applied to the pre-plateau phase (t < 2500) as apparent from the graphical plot gives a slope coefficient of 0.0080570 and intercept of 8.2606961. 
These estimates can be considered fairly accurate, the standard error of each being an order of magnitude smaller than the value itself, and an adjusted R squared of 0.9562 indicates very good model fit. 

Applying a linear model to the post-plateau phase (t > 2500) on the non-log-transformed dataset gives an intercept estimate of 5.979x10^10. This in turn estimates the parameter K from the model of logistic growth. 
A high t value of 551.4 and the clear correspondence with the plateau y level on the plots indicate very good fit.

When plotted as an exponential function against the data these linear-derived N0, r and K estimates produce a function that resembles the best fit of the curve in shape but is shifted in the positive x (t) direction by around t=1000. 
This is clearly capturing a correct dynamic but the function is sensitive to small errors  and this shift means that the derived function poorly predicts the data even if linear functions of its parameters do so better (up to y~k).



*Question 2.*
The estimated parameters N0 and r of the logistic equation are inserted into an exponential equation N= N0exp(rt) and when t=4980, N, the population size = 2.200836x10^18. 
In comparison, for t=4980 under the logistic model of growth with these parameters, N= 5.979x10^10, 8 orders of magnitude smaller.
t=4980 sits in the region of this logistic function where N is almost equal to K and the population growth rate is essentially 0, the stationary phase. 



*Question 3.*


![image](https://github.com/solarproblems/reproducible-research_homework/assets/152936548/3d962180-6271-4daf-b6dd-37048c06cf4b)




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
