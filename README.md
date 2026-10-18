Photosynthesis under fluctuating light: model and frequency-domain analysis

SM1. Code description

The code BDM3.2 Core Code LN1.nb was developed in Wolfram Mathematica 15.1 to accompany a manuscript that was submitted to PNAS Nexus. It is a project that continues the earlier model developments in https://github.com/DREAM-EIC/DREAM-Model/.

SM1.1. Organization of simulation outputs
During evaluation, simulation outputs are saved in a folder created in the same directory as the Mathematica notebook. For the configuration corresponding to Figs. 1, 2, and 3, this folder is named Freq_sweep_consL500_amplL400. The numbers 500 and 400 denote the mean illumination and the amplitude of sinusoidal light modulation, respectively, both expressed in µmol photons m⁻² s⁻¹.
Each evaluation creates a separate subdirectory identified by its date and time, allowing repeated simulations with identical illumination settings to be stored without overwriting previous results.

SM1.2. Summary outputs for the complete period sweep
Each run directory contains five PDF files summarizing the simulations across the range of forcing periods.
Four files, DeltaChlF_vs_T_*.pdf, DeltaNPQ_vs_T_*.pdf, DeltaO2_vs_T_*.pdf, and DeltaObservables_vs_T_*.pdf, show the differences between the period-averaged values of the observables (chlorophyll fluorescence, non-photochemical quenching, and oxygen evolution) and their corresponding steady-state values under constant illumination.
The fifth file, ConvergenceVsT_*.pdf, shows the number of oscillation cycles required to satisfy the Poincaré convergence criterion as a function of the forcing period.
The numerical results are provided in ConvergenceSweep_*.xlsx, together with the simulation metadata, initial conditions, steady-state observables, convergence data, and optional Floquet results.
The sweep information is additionally stored in DYNAMICS_SWEEP_BUNDLE_*.wdx and INDEX_Tsweep_*.mx, which can be used for further analysis within Wolfram Mathematica.

SM1.3. Frequency-response and nonlinear distortion analysis
The SweepSpectra subdirectory contains the results of Fourier-based analysis of the simulated time series.
The FRF1_Sweep_PDF subdirectory contains plots of the magnitude and phase of the fundamental-harmonic frequency-response function for each observable, plotted against the forcing period on a logarithmic axis. The corresponding numerical values are provided in FRF1Sweep_*.xlsx.
The Distortion_Sweep_PDF subdirectory contains plots of the relative amplitudes of higher harmonics, expressed as the ratio of each harmonic amplitude to the fundamental amplitude. The corresponding numerical values are provided in DistortionSweep_*.xlsx.
The THD_Sweep_PDF subdirectory contains plots of total harmonic distortion (THD) as a function of the forcing period. The corresponding numerical values are provided in THDSweep_*.xlsx.

SM1.4. Outputs for individual forcing periods
In addition to the sweep-level summaries, the code creates a separate subdirectory for each simulated forcing period.
Each period-specific directory contains PDF files showing the temporal response of chlorophyll fluorescence (ChlF_*.pdf), non-photochemical quenching (NPQ_*.pdf), and oxygen evolution (O2_*.pdf) to the imposed illumination, together with the corresponding input–output response loops.
The Fourier-based frequency-response analysis is exported to FRF_*.csv.
The workbook Summary_*.xlsx contains the simulation metadata, sampled time series, discrete Fourier transform coefficients, frequency-response functions, fundamental-harmonic response, harmonic distortion coefficients, and THD values.
These period-specific results provide the numerical basis for the sweep-level frequency-response and nonlinear distortion analyses.

SM1.5. Code modifications for individual figures
The notebook BDM3.2 Core Code LN1.nb is provided with the parameter settings used to generate Figs. 1–3.
Figure 4 shows how total harmonic distortion (THD) depends on the amplitude of sinusoidal light modulation across the range of forcing periods. The illumination conditions are specified in the first two lines of Section 0, User knob:
constL = 500;  (* Mean intensity, µmol photons m^-2 s^-1 *)
amplL = 400;   (* Modulation amplitude, µmol photons m^-2 s^-1 *)
The additional modulation amplitudes used for Fig. 4 are amplL = 300, 200, 100, 50, and 25, expressed in µmol photons m⁻² s⁻¹. Additional mean illumination levels used in the simulations are constL = 250 and 125 µmol photons m⁻² s⁻¹.
Figures 5–7 were generated using analogous modifications of the illumination parameters. In addition, these simulations compare the frequency responses obtained with and without the contributions of zeaxanthin-dependent (Zea) and PsbS-dependent regulation.
To suppress Zea-dependent regulation, the activation rate constant k3 was decreased from 0.001 to 0.0001, while the deactivation rate constant k4 was increased from 0.0001 to 1.
Similarly, to suppress PsbS-dependent regulation, the activation rate constant k9 was decreased from 0.01 to 0.0001, while the deactivation rate constant k10 was increased from 0.001 to 1.
These parameter modifications strongly favor the inactive states of the respective regulatory processes, making their contributions negligible under the simulated conditions. To suppress both regulatory processes, both sets of parameter modifications were applied simultaneously.
All other model equations and parameters were retained unchanged.
