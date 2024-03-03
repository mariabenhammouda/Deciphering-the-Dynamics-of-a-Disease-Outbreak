# Simulation and Analysis of Disease Outbreaks via Zombie Apocalypse: A MATLAB Approach
### The zombie master code can be found here: https://drive.google.com/file/d/1HkmI5mP4VjGg3GI5ppjhNd2JW3RxLETL/view?usp=sharing
### Attached is the comprehensive PDF detailing the Mathematical Modeling and Analysis of Disease Outbreak Dynamics During a Zombie Apocalypse, along with the corresponding parameter settings.

This is a more optimized version (**created by Kin Fai Franco Chan and Zakaria Achouri**) of the original MATLAB zombie apocalypse group project (https://github.com/UoMLegends/Zombie). This version uses vectorization for movement increment, uses `knnsearch` for finding the nearest enemy, and preallocation for memory efficiency.

### To run the simulation, do the following steps:
1. save all the m files from this repository
2. execute `zombieBasic.m` using MATLAB
3. enjoy watching the zombie apocalypse simulation
4. execute `population.m` to plot the graphs of zombie population and human population versus time 



To simplify things, we modeled our zombie apocalypse based on a few simple behaviors of both zombies and humans.
### Basic behaviors of zombies and humans:
* If human and zombie are **far away** from each other, they simply **move randomly** (Brownian motion).
* If a human and a zombie are **relatively close** to each other, then the zombie would **chase** after the human, and the human would **run away**.
* If a zombie is close to **multiple humans**, then the zombie would chase after the **closest** human.
* If human and zombie are **very close** to each other, then they will **fight**. Sometimes the human wins the fight, which results in killing the zombie. Sometimes the zombie wins the fight, which results in turning the human into a zombie.


### Feel free to modify the parameters on `zombieBasic.m`:
Parameters | Descriptions
---------- | ------------
`z0` | the initial zombie population
`h0` | the initial human population
`zSpeed` | zombie movement top speed
`hSpeed` | human movement top speed
`zSightRadius` | maximum distance a zombie can sense the presence of a human (for chase)
`hSightRadius` | maximum distance a human can sense the presence of a zombie (for chase)
`zAttackRadius` | maximum distance a zombie can attack from (for fight)
`hAttackRadius` | maximum distance a human can attack from (for fight)
`lim` | the length and the width of the arena (square arena)
`pz`| the probability of a zombie successfully converting a human to a zombie
`ph`| the probability of a human successfully killing a zombie

# Introduction
Whilst the zombie apocalypse is one of the most popular themes in entertainment, besides the pop-cultural study surrounding the living dead, another branch of zombie research is more scientific and is concerned with using the attack of the living dead as a metaphor and modeling tool to understand and bring attention to epidemiological processes of infection as well as global disasters including malaria, SARS, STDs, influenza, MRSA, Ebola, rabies, scrapie, and mastitis (e.g. Brooks, 2003; Engler, 2012; Stanley, 2012). This has been applied as a system of ‘Susceptible, Infected, Recovered’ to model numerous pandemics including the 2020 COVID pandemic (Batista et al., 2021). Conversely, the simulation can be used in drug experimental testing and vaccines through a population-based approach (Computer Simulations, 2018b). Suppose we wish to simulate the effectiveness of a vaccine against a virus, we can tune the potency and population of the antibodies and viruses to quantify the success rate of the drug or vaccine. Within the medical scope, a research center utilizes machine learning to predict pregnancy and multiple pregnancy risks following in vitro fertilization-embryo transfer (Wen et al., 2022). However, we believe that with the integration of new parameters and constraints, the zombie simulation can serve as an efficient tool in reproductive medicine to predict the success rate of a vitro fertilization-embryo transfer. Many factors have been known to affect IVF outcomes including age, sperm quality, fertilization rate, embryo quality, frequency of transferred embryos, and endometrial thickness. The humans and zombies would represent the gametes, and the population and fertilization rate of each can be varied as per the gamete recipients’ age, sperm quality, fertilization rate, embryo quality, etc. In conclusion, a population-based simulation can be an efficient modeling tool to quantify the outcomes of any engineering problem with Bernoulli distribution, success, and failure parameters.

# Approach
We model a zombie attack by introducing a basic model of a zombie-to-human ratio in Zombieville, determining the probability of survival/strength of humans against humans(phh) and zombies(phz), then simulating numerous motion steps governed by predetermined laws of motion. Then we examine the impact of 𝑝h𝑧 parameter on the basic, flight, and flight models. The outcomes are illustrated with mathematical interpretation, we derive conditions under which the eradication of humans can occur and what parameters are necessary to preserve the human population. We show that, unlike the expectation, a population of humans with less than a 40% chance of survival against a zombie can go extinct if they follow a fight response. We also show how and why the flight response is overall the smartest strategy in a zombie apocalypse.

# Description of ZombieVille:
Zombieville is a square-shaped city divided into evenly distributed squares and represented as an 𝑛 × 𝑛 matrix. Each cell can either be empty, occupied by a zombie, or a living person. Let Xi,j(t) ∈ {−1,0,1} be the state of the cell (i,j) at time t, representing the location in row i, column j. Xi,j(t) = 0 means that cell (i,j) is empty, Xi,j(t) = −1 that the cell is occupied by a zombie, and Xi,j(t) = 1 that the living occupies the cell. The simulation executes a total of 100,000 steps where only one person can move per step. The Zombieville we chose to simulate is one with the basic assumption that will be presented in the next section. Both species; humans and zombies move at equivalent rates and are constrained by the same laws of motion. However, ‘humans’ are either in fight mode, hence fiercer than their counterparts, and hunt the zombies across Zombieville or humans are in flight mode, hence avoid zombies and instead seek refuge in empty cells or other human-containing cells.

# Conclusions:
An outbreak of zombies infecting humans is likely to be disastrous would it result in the extinction of living beings and the complete eradication of human civilization. While a high 𝑝h𝑧 such as 𝑝h𝑧 > 0. 8 and a low 𝑝hh ≤ 0. 05, regardless of the human flight or fight response may eradicate the infection, it is very unlikely to happen. The 𝑝hh parameter in the above experiments was set to a constant 0. 05 irrespective of 𝑝h𝑧 and the flight/fight response. The 𝑝hh in this simulation assumes the best of human nature and eliminates the possibility of human intraspecies aggression or high suicide rate. Likewise, a high 𝑝h𝑧 translates to a scenario where at every encounter of a human and a zombie, the human has an 80% chance of killing the zombie. In real life, we know that the human population ranges in age, size, and physical abilities therefore to rely on a human strength of 80% to save the human population from extinction is naive.

The key difference between the models presented here and other models of infections is that the models depicted here represent the two automatic physiological reactions to an event that is perceived as stressful or frightening; fight and flight. Although the models used are binary, meaning that a human can either be in fight or in flight mode throughout all time steps, they provide a close approximation to the zombie apocalypse.

We anticipated that a fight response would slow down the growth of the zombie population due to the scores setup whereby a human is twice as likely to target a zombie than other cells. We find that when comparing the final zombie population in both models for a 𝑝h𝑧 < 0. 5 and a 𝑝h𝑧 > 0. 5 is less than that of the flight mode. The difference is largest at 𝑝h𝑧 > 0. 5 because humans are twice as likely to attack a zombie and if they do, they are more likely to kill it. While some might conclude that the flight response is the safest and smartest option as it guarantees the survival of humans for a significantly low chance of survival and a large range of phz, 0. 2 ≤ 𝑝h𝑧 ≤ 1. Others suggest that the decrease in the zombie population resulting in the fight response is a valuable trade-off to the smaller range, 0. 4 ≤ 𝑝h𝑧 ≤ 1.
Through assessing multiple ranges of 𝑝h𝑧 we find that 𝑝h𝑧 = 0. 5 marks a critical point for the fraction of zombies. Below the critical point, zombies grow drastically, whereas above the critical point, the fraction of zombies no longer oscillates and instead much like the fraction of human plot, decays exponentially. 

A human population of a range 0. 2 ≤ 𝑝h𝑧 ≤ 1 is guaranteed to survive a zombie apocalypse when in flight response. Likewise, A human population of a range 0. 4 ≤ 𝑝h𝑧 ≤ 1 is guaranteed to survive a zombie apocalypse when in fight response, with the added advantage of an overall lowered zombie population in comparison to that of the flight response. In other words, the flight response in a zombie apocalypse is an optimum strategy for populations with groups of highly susceptible individuals such as the elderly, ill, or physically disabled that have a low 𝑝h𝑧. This is because, by the simulation results for flight response, we find that the human civilization can still survive in a zombie apocalypse despite the survival chance of humans against zombies being as low as 20%. Moreover, populations with more capable groups will have a higher 𝑝h𝑧 and therefore can opt to adopt the fight response. However, for the human species to survive the apocalypse human individuals must have a probability of survival against zombies no less than 40%.

The conclusions drawn from each human response are significant because not only can we recommend the optimum tactic to preserve human populations according to the individuals’ strengths but we can also extend these outcomes to draw parallels between this simulation and real-life applications. For instance, we can apply these strategies to the pandemic engineering problem mentioned in the introduction. Let 𝑝h𝑧, represent the immune system strength whilst factoring in age, family history, and overall fitness of the population's individuals. Then, a population that is composed of highly susceptible groups with a low survival rate against a virus (low phz) such as the elderly, unhealthy, or physically unfit, is obliged to stay home and self-isolate. This represents the flight response in our simulation for a low phz. However, if the majority of the population is young, healthy, and strong individuals with a strong immune response (high phz), we can allow for more flexibility with everyday activities. This represents the fight response in our simulation for a high phz.

In summary, we derive that the following parameter settings preserve the human civilization:
1. A 𝑝h𝑧 ≥ 0. 4 and a fight response
2. A 𝑝h𝑧 ≥ 0. 2 and a flight response
