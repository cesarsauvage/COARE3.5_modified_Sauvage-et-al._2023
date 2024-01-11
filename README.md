# COARE3.5 modified (Sauvage et al. 2023)

Instruction:  
a. If cp is a peak wave period and theta is not provided, this is identical to the original COARE3.5 wave based formulations (Edson et al. 2013).  

b. If cp is a peak period but theta is provided, then it will use the revised COARE3.5 wave based formulation #1 (Sauvage et al. 2023), which accounts for the wind wave misalignment.    

new roughness formulation:  zo_new=sigH.*Ad_new.*(usr./cp).^Bd_new;  
where new coefficients are used, notably based on findings from Porchetta et al. 2019:  
Ad_new=0.091.*cos(0.45.*theta);    
Bd_new=2.*cos(-0.32.*theta);  

with theta (θ) in radians, the angle between the wind direction and the wave direction which varies between 0 and π.  
i.e., if θ = 0, wind and waves are perfectly aligned, whereas θ = π means wind and waves are opposed.   

c. If cp is a mean period but theta is not provided, it will use the revised COARE3.5 wave based formulation #2 (Sauvage et al. 2023) which uses the mean wave age.  

new roughness formulation:  zo_new=sigH.*Ad_new.*(usr./cp).^Bd_new;  
Ad_new=0.39    
Bd_new=2.6  

These coefficients have been tuned using the COARE3.5 set of observations.   
The mean wave age used as input here uses the mean period, Tm. Tm is based on the zero-crossing period, as it is the one used to describe the mean period in the observation.  

d. If cp is a mean period, and theta is provided, this will abort. In the current implementation, our study shows that it results in overfitting.  

<ins>Citation:</ins>  Sauvage, C., Seo, H., Clayson, C. A., & Edson, J. B. (2023). Improving wave-based air-sea momentum flux parameterization in mixed seas. Journal of Geophysical Research: Oceans, 128, e2022JC019277. https://doi.org/10.1029/2022JC019277 

<ins>Contact:</ins> César Sauvage at csauvage@whoi.edu  
<ins>Website:</ins>  https://cesarsauvage.github.io/  
<ins>GitHub:</ins>  https://github.com/cesarsauvage  


<ins>References:</ins>  
Porchetta, S., Temel, O., Muñoz-Esparza, D., Reuder, J., Monbaliu, J., van Beeck, J., and van Lipzig, N.: A new roughness length parameterization accounting for wind–wave (mis)alignment, Atmos. Chem. Phys., 19, 6681–6700, https://doi.org/10.5194/acp-19-6681-2019, 2019.  
Edson, J. B., Jampana, V., Weller, R. A., Bigorre, S. P., Plueddemann, A. J., Fairall, C. W., Miller, S. D., Mahrt, L., Vickers, D., & Hersbach, H. (2013). On the Exchange of Momentum over the Open Ocean. Journal of Physical Oceanography, 43(8), 1589-1610. https://doi.org/10.1175/JPO-D-12-0173.1  
