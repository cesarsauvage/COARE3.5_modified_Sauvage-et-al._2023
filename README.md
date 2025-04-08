# COARE3.5 modified (Sauvage et al. 2023)

<ins>**Instructions:**</ins>  


**a.** If wave parameters ($c_p,H_s ,\theta$) are not provided, this is identical to the original COARE3.5 wind speed-dependent formulation, Eq. 12,13 in Edson et al. 2013 (see also corrigendum): $z_0 = \alpha (u_\*^2/g)$ with $\alpha = 0.0017 U_{10N} -0.005$

**b.** If $c_p$ is provided but $\theta$ and $H_s$  are not provided, this is identical to the original COARE3.5 wave based formulation (Eq. 15 in Edson et al. 2013: $z_o = 0.114(u_\*/c_p)^{0.622}$

**c.** If $c_p$ and $H_s$  are provided but $\theta$ is not provided, this is identical to the original COARE3.5 wave based formulation (Eq. 19 in Edson et al. 2013: $z_o = H_s0.09(u_\*/c_p)^2$    

**d.** If $c_p$, $H_s$  and $\theta$ are provided, then it will use the revised COARE3.5 wave based formulation, Eq. 13 in Sauvage et al. 2023, which accounts for the wind wave misalignment:    

new roughness formulation:  $z_{0}=H_sA_{new}(u_\*/c_p)^{B_{new}}$  
where new coefficients are used, notably based on findings from Porchetta et al. 2019:  
$A_{new} = 0.091cos(0.45\theta)$    
$B_{new} = 2cos(-0.32\theta)$

with $\theta$ in radians, the angle between the wind direction and the wave peak direction which varies between 0 and π.  
i.e., if $\theta$ = 0, wind and waves are perfectly aligned, whereas $\theta$ = π means wind and waves are opposed.   

**e.** If $c_m$ (mean wave speed) and $H_s$ are provided but $\theta$ is not provided, it will use the revised COARE3.5 wave based formulation, Eq. 12 in Sauvage et al. 2023, which uses the mean wave age:  

new roughness formulation:  $z_0=H_s*A_{new}(u_\*/c_m)^{B_{new}}$  
$A_{new} = 0.39$    
$B_{new} = 2.6$  

These coefficients have been tuned using the COARE3.5 set of observations.   
The mean wave speed used as input here uses the mean period, $T_m$. $T_m$ is based on the zero-crossing period, as it is the one used to describe the mean period in the observation.  

**f.** If $c_m$ and $\theta$ are provided, this will abort. In the current implementation, our study shows that it results in overfitting.  

<ins>**Variables:**</ins>

$z_0$ = ocean surface roughness length

$U_{10N}$ = 10m neutral wind speed

$g$ = gravitational acceleration

$c_p$ = peak wave speed

$c_m$ = mean wave speed

$H_s$ = significant wave height

$\theta$ = angle between wind direction and wave peak dircetion (between 0 and π)

$u_\*$ = wind friction velocity


<ins>**Citation:**</ins>  Sauvage, C., Seo, H., Clayson, C. A., & Edson, J. B. (2023). Improving wave-based air-sea momentum flux parameterization in mixed seas. Journal of Geophysical Research: Oceans, 128, e2022JC019277. https://doi.org/10.1029/2022JC019277 

<ins>**References:**</ins>  

Porchetta, S., Temel, O., Muñoz-Esparza, D., Reuder, J., Monbaliu, J., van Beeck, J., and van Lipzig, N.: A new roughness length parameterization accounting for wind–wave (mis)alignment, Atmos. Chem. Phys., 19, 6681–6700, https://doi.org/10.5194/acp-19-6681-2019, 2019.  

Edson, J. B., Jampana, V., Weller, R. A., Bigorre, S. P., Plueddemann, A. J., Fairall, C. W., Miller, S. D., Mahrt, L., Vickers, D., & Hersbach, H. (2013). On the Exchange of Momentum over the Open Ocean. Journal of Physical Oceanography, 43(8), 1589-1610. https://doi.org/10.1175/JPO-D-12-0173.1  

Edson, J. B., Jampana, V., Weller, R. A., Bigorre, S. P., Plueddemann, A. J., Fairall, C. W., Miller, S. D., Mahrt, L., Vickers, D., & Hersbach, H. (2014). CORRIGENDUM. Journal of Physical Oceanography, 44(9), 2590-2590. https://doi.org/10.1175/JPO-D-14-0140.1


=======================================================================================  
<ins>Contact:</ins> César Sauvage at csauvage@hawaii.edu  
<ins>Website:</ins>  https://cesarsauvage.github.io/  
<ins>GitHub:</ins>  https://github.com/cesarsauvage  
