# Gaussian NBO analysis

## NBO analysis

### What is Natural orbital,Natural Atomic Obitals,Natural Bond Obitals？

See [here](https://nbo6.chem.wisc.edu/webnbo_css.htm)  
**Summary**:  

* Natural Orbitals (NOs) are the unique orbitals chosen by the wavefunction itself as optimal for its own description.
* Natural Atomic Orbitals (NAOs) {Θk(A)} are localized 1-center orbitals that can be described as the effective "natural orbitals of atom A"  
* Natural Bond Orbitals (NBOs) are localized few-center orbitals ("few" meaning typically 1 or 2, but occasionally more) that describe the Lewis-like molecular bonding pattern of electron pairs (or of individual electrons in the open-shell case) in optimally compact form.  

### Lewis orbital and non Lewis orbitals

See [here](https://en.wikipedia.org/wiki/Natural_bond_orbital)  

### What is in the  NBO part of log file?

See [here](https://www.cup.uni-muenchen.de/ch/compchem/pop/nbo2.html)  
Or the [NBO 3.0 Program Manual](http://www.ccl.net/cca/software/MS-WIN95-NT/mopac6/nbo.htm)  
Gaussian contains version 3.1 of the NBO program by F. Weinhold and coworkers. NBO analysis is based on a method for optimally transforming a given wave function into localized form, corresponding to the one-center ("lone pairs") and two-center ("bonds") elements of the chemist's Lewis structure picture.  

In NBO analysis, the input atomic orbital basis set is transformed via natural atomic orbitals (NAOs) and natural hybrid orbitals (NHOs) into natural bond orbitals (NBOs). The NBOs obtained in this fashion correspond to the widely used Lewis picture, in which two-center bonds and lone pairs are localized.  
This include basic information about the:

1. headings
2. NAO table  
   1. angular momentum type: s,px,py,pz
   2. orbital type: Cor, Val  
   3. Orbital occupancy (the number of electrons)  
   4. Orbital energy in Hartree $E_h: 1 Hartree = 4.3597447222071(85)×10^{−18} J$
3. Atomic summary: natural atomic charges(nuclear charge-summed natural popilations of NAOs on the atom) then core valence rydberg total
4. Natural Electron configuration: 可以体现杂化和电子归属。
5. NBO analysis  
   1. First segment reports on the details of **the search for and NBO natural Leiws structure.**

   ```txt
   occ.                   Occupancies      Lewis Structure   Low   High
   Cycle Thresh.         Lewis Non-Lewis  CR  BD  3C  LP    (L)   (NL)   Dev
 
   Structure accepted: RESONANCE keyword permits strongly delocalized structure
   ```

    cycle: the cycle in NBO search
    Thresh: the occupancy threshold for a "good" pair in the NBO search
    Lewis and non-Lewis NBOs
    CR: number of cores  
    BD: 2-center bonds  
    3C: 3-center bonds  
    LP: lone pairs
    RY: 1-center Rydberg
    Dev: the maximum deviation ('Dev') of any formal bond order from a nominal estimate (NAO Wiberg bond index) for the structure. If the latter exceeds 0.1, additional NBO searches are initiated (indicated by the parenthesized number under 'Cycle') for alternative Lewis structures.  
    **What does those order numbers mean?What does the comment mean?**  
    2. **A more detailed breakdown(Summary)**  
    3. **(Occupancy)   Bond orbital/ Coefficients/ Hybrids(A main list of NBOs).**  
   This first NBO corresponds to a sigma(C-O) bond with approximate composition of $0.6435 C(sp^{1.91}) + 0.7654 O(sp^{3.16})$. The weights are obtained from the squares of the coefficients as $(0.6435)^2 = 0.4141$, corresponding to 41.41 % localization on carbon C1. In a similar way the 58.59 % localization on oxygen O2 is obtained. Overall, this describes a polar sigma(C-O) bond. 

    ```txt
        (Occupancy) Bond orbital/ Coefficients/ Hybrids
        ----------------------------------------------------------
      1. (1.99777) BD ( 1) C 1 - O 2
            ( 41.41%) 0.6435* C 1 s( 34.36%)p 1.91( 65.64%)
            0.0000 0.5862 0.0000 0.0000 0.8102
            1s     2s     2px    2py    2pz
            ( 58.59%) 0.7654* O 2 s( 24.04%)p 3.16( 75.96%)
            0.0000 0.4903 0.0000 0.0000 -0.8716
    ```  

    There is also CR,LP，RY and BD* RY* "*" means the none Lewis part ??.  
    4. **NHO directional analysis**: How the hybrid orbital is deviated from the line of centers  
    5. **Second Order Perturbation Theory Analysis**: How the orbitals(antibond lone pair especially) interacted with each other.  
    6. **NBO sunnmary**  : Orbital and energy analysis
    7. 

