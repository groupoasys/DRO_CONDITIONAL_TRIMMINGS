# Data of Numerical Experiments of the paper entitled "Distributionally robust stochastic programs with side information based on trimmings"

## Goals

The aim of this repository is to provide the details of the numerical experiments coded in Python programming language used in the paper [[1]](https://arxiv.org/abs/2009.10592). This article have been developed by some members of the [OASYS group](https://sites.google.com/view/groupoasys/home) thanks to the funding of the project [Flexanalytics](https://groupoasysflexanalytics.readthedocs.io/en/latest/). We suggest you to visit the related links to know more our research.

## Contents

This repository includes the data about the two test problems used in the paper:

- Single-item Newsvendor problem with side information:

  * [singlenewsvendor_generation_data](): This folder contains the data used in the numerical experiment corresponding to the single-item Newsvendor problem with side information used in [[1]](https://arxiv.org/abs/2009.10592) . The files "indices+str(N)".csv contains the 400 samples' index of size N, that is, each row (total=400) of the .csv file represents a sample of size N. The data points of the bivariate distribution are in the file entitled ""  . The rest of the parameters of the numerical experiments are described in [[1]](https://arxiv.org/abs/2009.10592).

- Portfolio allocation problem with side information.

  * [portfolio_generation_data]:   This folder contains the data used in the numerical experiment corresponding to the portfolio allocation problem with side information used in [[1]](https://arxiv.org/abs/2009.10592).    The files "indices+str(N)".csv contains the 200 samples' index of size N, that is, each row (total=200) of the .csv file represents a sample of size N. The data points of the joint distribution are in the file entitled "muestra_real_conjunta.csv".  The rest of the parameters of the numerical experimet are described in [[1]](https://arxiv.org/abs/2009.10592). The main test case deals with the case in which alpha=0 and the data points of the true conditional distribution of this case are in the file entitled "muestra_dist_real". Some important remarks to reproduce the numerical experiments in the paper in the case alpha=0:
            The y-data are not scaled so they must be scaled in order to reproduce fairly the experiments as follows:
            
            
            #Side/contextual information (scaled):  [(1000-1000)/50,(0.01-0.02)/0.01,(5-math.exp(1/2))/(math.sqrt((math.exp(1)-1)*math.exp(1)))]
            #mean vector: mean=[86.8625, 71.6059, 75.3759, 97.6258, 52.7854, 84.8973]
            #matrix used in the numerical experiments to define the sigma matrix in the numerical experiments: matrix_sigmasquare=np.array([[136.687,8.79766,16.1504,18.4944,3.41394,24.8156],[8.79766,142.279,15.0637,15.6961,16.5922,18.7292],[16.1504,15.0637,122.613,26.344,14.8795,17.1574],[18.4944,15.6961,26.344,139.148,13.9914,6.36536],[3.41394,16.5922,14.8795,13.9914,151.732,24.7703],[24.8156,  18.7292,  17.1574,  6.36536,  24.7703,  144.672]]) 
            #The y-data coordenates ofthe samples from the joint distribution are scaled as follows:
             puntos_yconjunta_real=muestra_real_conjunta[:,[3,4,5,6,7,8]]  #The y-data coordenates ofthe samples from the joint distribution, muestra_real_conjunta[:,[0,1,2]]              represents th feature coordenates of the samples from the joint distribution.


              cov_yrealconjunta=np.cov(puntos_yconjunta_real,rowvar=False)


              std_yrealconjunta=np.diag(np.sqrt(np.diag(cov_yrealconjunta)))  
              
              
              media_yrealconjunta=puntos_yconjunta_real.mean(axis=0) #mean vector
              #SCALE THE POINTS OF THE JOINT DISTRIBUTION:
              np.dot(inv(std_yrealconjunta), muestra_conjunta_sample[j,[3,4,5,6,7,8]]-media_yrealconjunta)
   
  
  *  Other related and complementary numerical tests :
  * [Case varying the side information](https://drive.google.com/drive/folders/1K3nKyZbqEQBDPp2ThtRYr-vRCqCiBhle?usp=sharing): In this case the sample corresponding to muestra_real_conjunta[indices[0]] ( for each value of N considered, indices[0] contains the indices of the sample fo size N ) is chosen. Note that in this case the sample is fixed and we vary the side information (we consider 200 samples of the z-distribution which are located in the file "zdatasamples_variando.csv"). The files entitled "muestra_dist_realindex.csv" in the folder "conditional_distributions" are the conditional distributions corresponding to the index from 0 to 199  of the features as the side information used to compute the performance metrics. 
  * [Case alpha>0, additional numerical experiments at the Supplemental Material](https://drive.google.com/drive/folders/1uNYYbg6FK1PSViV43zLc0yQbHnF2VdZN?usp=sharing): In this case, the file "muestra_real_conjunta_alfapos.csv"  contains the data of the joint probability distribution. The files "indices_alphaposN.csv" contains the indices of the sample of size N used in the numerical experiments.

The folder Codes contains the codes used in the numerical experiments.
 
## References 📚
[1] Esteban-Pérez, A., & Morales, J. M. (2020). Distributionally robust stochastic programs with side information based on trimmings. arXiv preprint arXiv:2009.10592.



## Do you want to contribute? 👨🏾‍🔬
 
 Any feedback is welcome :sparkles: so feel free to ask or comment anything you want via a Pull Request in this repo.
 If you need extra help, you can ask Adrián Esteban-Pérez (adrianesteban@uma.es) :e-mail:.

 ## Contributors
 
 * [OASYS group](http://oasys.uma.es) -  groupoasys@gmail.com
 
 ## Developed by 👨🏾‍💻
 * [Adrián Esteban-Pérez](https://scholar.google.es/citations?user=iDEU4ZAAAAAJ&hl=es https://www.researchgate.net/profile/Adrian_Esteban-Perez) - adrianesteban@uma.es 

 ## License 📝
 
    Copyright 2021 Optimization and Analytics for Sustainable energY Systems (OASYS)

    Licensed under the GNU General Public License, Version 3 (the "License");
    you may not use this file except in compliance with the License.
    You may obtain a copy of the License at

       http://www.gnu.org/licenses/gpl-3.0.en.html

    Unless required by applicable law or agreed to in writing, software
    distributed under the License is distributed on an "AS IS" BASIS,
    WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
    See the License for the specific language governing permissions and
    limitations under the License.
