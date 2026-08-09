README - PVD Co-deposition Simulation & Dual Mask Optimization
1. Overview
This MATLAB script simulates the Physical Vapor Deposition (PVD) process via co-evaporation of MgF2 and TiO2. It implements a hybrid optimization algorithm (PSO + Nelder-Mead) to design dual masks that simultaneously achieve:
High thickness uniformity (< 5 nm RMSE).
A parabolic Graded Index (GRIN) refractive index profile.
The code is self-contained: all auxiliary functions, geometric definitions, and calculation routines are integrated into a single .m file, organized by clear sections.
2. System Requirements
Software
MATLAB R2023b or later (recommended for optimal graphics rendering and optimization functions).
Required Toolboxes:
Optimization Toolbox (For fminsearch, lsqcurvefit, and PSO implementation).
Statistics and Machine Learning Toolbox (For statistical functions like prctile and Bootstrap analysis).
Parallel Computing Toolbox (Optional, but recommended for accelerating Monte Carlo simulations if parallel loops are enabled).
Hardware Recommendations
RAM: Minimum 8 GB (16 GB recommended for 'slow' high-precision modes).
Processor: Modern multi-core CPU (Intel i7/i9 or AMD Ryzen 7/9).
3. Execution Instructions
Download the file Codeposito_Ingles_16.m.
Open MATLAB and set the current folder to the location of the file.
Run the main script from the Command Window:

Codeposito_Ingles_final

The script will automatically generate:
Figures 1 to 18 (including the Graphical Abstract).
.mat data files with numerical results.
A detailed log file Bitacora_PVD_Completa_HM.txt.
A technical dossier PVD_Technical_Dossier_Final_L.pdf.
4. Speed and Precision Configuration
At the beginning of the script (Section 0), you can select the execution mode by modifying the selected_mode variable. This automatically adjusts mesh resolution, PSO iterations, and rotation steps.

% Available options:
selected_mode = 'fast';        % Quick exploration (for initial testing)
selected_mode = 'fast_medium'; % Balance speed/quality (RECOMMENDED FOR TESTING)
selected_mode = 'medium';      % Standard balance
selected_mode = 'medium_slow'; % High quality
selected_mode = 'slow';        % Maximum precision (for final publication)

Note: For generating final figures and complete validation, it is recommended to use at least 'medium' mode.

5. Code Structure
The script is divided into logical sections to facilitate review and modification:
Section 0: Control Panel & Global Variables (Mode configuration and physical parameters).
Section 1: Preliminary Calculations (Aspheric geometry, time calibration).
Section 2: Physical Simulation (Static flux calculation and Monte Carlo).
Section 3: Optimization Block (Global PSO + Local Nelder-Mead for Single and Dual Masks).
Sections 4-6: Post-Processing (GRIN profile calculations, TMM spectral analysis, Monte Carlo robustness).
Sections 7-9: Validation (Cross-validation, mesh independency, Bootstrap analysis).
Sections 10-12: Visualization (Generation of Figures 1-18 and export to PDF/TXT).
Auxiliary Functions: All necessary helper functions (calculate_flux_static, objective_function_grin_dual, get_mask_blade_geometry, etc.) are located at the end of the file.
6. Troubleshooting
Memory Error: If using 'slow' mode with less than 16 GB of RAM, reduce global_config.opt_resolution manually or switch to 'medium'.
Empty Figures: Ensure the optimization completed successfully. Check the command window to verify that the final RMSE is finite.
Missing Toolbox: If you receive an error regarding fminsearch or prctile, verify that the Optimization and Statistics toolboxes are installed and licensed.
7. Citation and Use
If you use this code for your research, please cite the associated article and mention the code availability in the corresponding repository.






