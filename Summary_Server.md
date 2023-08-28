# Summary for Gaussian

## Gaussian

**Use sub.gaussian bash**
Enter the correlated file path and input following command in the terminal  
`sbatch sub.gaussian`
**How to open the .chk file**  
Add `formchk <filename>` to convert the file to .fchk which is smaller and easier to open

### About Gaussian 16 input

* ASCII text file
**Basic structure**

* Link 0 Commands: Locate and name scratch files (not blank line terminated).
Route section (# lines): Specify desired calculation type, model chemistry, and other options (blank line terminated). See Model Chemistries and Job Types for information about Gaussian 16 capabilities.
* Title section: Brief description of the calculation (blank line-terminated). This section is required in the input, but is not interpreted in any way by the Gaussian 16 program. It appears in the output for purposes of identification and description. Typically, this section might contain the compound name, its symmetry, the electronic state, and any other relevant information. The title section cannot exceed five lines and must be followed by a terminating blank line. The following characters should be avoided in the title section: @  #  !  –  _  \  control characters (especially Ctrl-G)
* Molecule specification: Specify molecular system to be studied (blank line-terminated). Full information is available in Molecule Specifications.
* Optional additional sections: Additional input needed for specific job types (usually blank line-terminated).  
**Syntax Rules** Please refer to [here](https://gaussian.com/input/?tabid=0)

### Read output log file

Point [here](https://www.youtube.com/watch?v=AUb2AZwsuoI) for video

1. Some may have the following at the beginning

    ```txt
    Default is to use a total of 12 processors:
                                12 via shared-memory
                                1 via Linda
    Entering Link 1 = ......
    ```  

2. Authors and contributors  
3. The version of gaussian and your input files

   ```txt
    ******************************************
    Gaussian 16:  ES64L-G16RevA.03 25-Dec-2016
                17-Aug-2023 
    ******************************************
   ```  

4. Then the initial parameters

    ```txt
    ----------------------------
    !    Initial Parameters    !
    ! (Angstroms and Degrees)  !
    ```  

5. Input Oritentataion

    We will convert the input using distance metrix in standard coordination   

    ```txt
     Stoichiometry    C4H8F2NNaO7S2
    Framework group  C1[X(C4H8F2NNaO7S2)]
    Deg. of freedom    69
    Full point group                 C1      NOp   1
    Largest Abelian subgroup         C1      NOp   1
    Largest concise Abelian subgroup C1      NOp   1
    ```

    In the second line  `C1` is the symmetry of the mulecule.

6. After standard orientation is the basis function for the calculation.  Click [here](https://en.wikipedia.org/wiki/Basis_set_(chemistry)) to see what is a base set.

    ```txt
    Standard basis: 6-311++G(d,p) (5D, 7F)
    There are   471 symmetry adapted cartesian basis functions of A   symmetry.
    There are   454 symmetry adapted basis functions of A   symmetry.
    ```  

7. Polarizable Continuum Model (PCM)  
    I do not know much about the part

8. Atomic radii for non-electrostatic terms: SMD-CDS.  
    I do not know much about the part

9. Population analysis using the SCF density.  
    I do not know much about the part

10. Charges:
    Mulliken charges:  
    Mulliken charges with hydrogens summed into heavy atoms:  
    APT charges:  
    APT charges with hydrogens summed into heavy atoms:  

    **Note**: **Mulliken charges** are partial atomic charges based on the linear combination of atomic orbitals molecular orbital method. Mulliken charges are basis set dependent. In order to calculate the exactly Mulliken charges, one has to use a complete basis set for a molecule by placing a large set of functions on a single atom. These problems can be addressed by modern methods for computing net atomic charges, such as density derived electrostatic and chemical analysis, electrostatic potential analysis, and natural population analysis.Mulliken charge is calculated directly based on density matrix (a special representation of electronic wavefunction), it is the oldest method for calculating atomic charge. Although it is very fast, there are many well drawbacks of this method, such as poor reproducibility of dipole moment and electrostatic potential(ESP), heavily underestimate ionicity of highly ionic bonds, very high sensitivity to basis set and nonconvergence with respect to increase of basis set size.[From here](https://www.researchgate.net/post/What-is-the-difference-between-Mulliken-charge-analysis-and-Merz-Singh-Kollman-MK-Scheme#:~:text=Mulliken%20charges%20are%20partial%20atomic,functions%20on%20a%20single%20atom.)  
    More method to determine partial charges.See [here](https://en.wikipedia.org/wiki/Partial_charge)

11. blabla
12. This is the end of the first ite

    ```txt
            Item               Value     Threshold  Converged?
    Maximum Force            0.070348     0.000450     NO 
    RMS     Force            0.009404     0.000300     NO 
    Maximum Displacement     1.666619     0.001800     NO 
    RMS     Displacement     0.455254     0.001200     NO 
    Predicted change in Energy=-2.058740D-02
    ```  

    They all need to converge. And then the optimization will started again.  
    When it is all over  

    ```txt
             Item               Value     Threshold  Converged?
    Maximum Force            0.000019     0.000450     YES
    RMS     Force            0.000004     0.000300     YES
    Maximum Displacement     0.001645     0.001800     YES
    RMS     Displacement     0.000591     0.001200     YES
    Predicted change in Energy=-1.753599D-08
    Optimization completed.
    -- Stationary point found.
    ```  

    This means the over of the calculation

13. Then the frequency calculation will be started. The result of the optimization will be used to further calcuation.
14. Then thermochemistry calculation


