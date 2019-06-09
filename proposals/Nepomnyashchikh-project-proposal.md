# Background
&nbsp;&nbsp;&nbsp;Multiphase flows appear in various real life situations. This project focuses on gas-liquid flows in drilling industry.  

&nbsp;&nbsp;&nbsp;Due to geological reasons, there are reservoirs with pressurized fluids under the Earth's surface which are spread randomly. When drilling a well (e.g, geo-thermal or oil well), one can penetrate such a reservoir. Pressurized fluid then enters the drilling annulus where it mixes with the drilling fluid (drilling fluid is a fluid which is pumped through the drilling string into the drilling annulus to wash out the cuttings). That's how a two phase flow can occur in the annulus. Being highly pressurized, such a flow can damage the drilling facility and even kill drillers (the most prominent example is "Deep water horizon").  

&nbsp;&nbsp;&nbsp;Therefore, influxes need to be detected as early as possible. The smallest detection time can be achieved by real time multiphase flow modeling. Hence, a fast and reasonably accurate mathematical model of multiphase flow should be chosen from the existing pool of multiphase flow models. The chosen model is called drift-flux model. It allows for quick computation and returns sufficiently accurate results [1].  

&nbsp;&nbsp;&nbsp;When modeling an influx, one faces a problem of phase occurrence/vanishing. It happens because when an influx occurs, there is a single phase flow of drilling fluid in the annulus. After the influx has occurred, there is a multiphase flow in the annulus.  

&nbsp;&nbsp;&nbsp;Drift-flux model's behavior in the event of phase occurrence/vanishing has not been explored much. For example, drift-flux model is used for influx modeling in [2]. But any exploration of appropriateness of its usage is not presented there. Still, phase occurrence/vanishing  is the major part of influx modeling. Thus, it was chosen to be explored in the project.

# Problem to be solved
&nbsp;&nbsp;&nbsp;A drift-flux model of a steady air-liquid flow in a vertical pipe is chosen to be a case flow for this project.

&nbsp;&nbsp;&nbsp;Prior to the simulation, a mathematical analysis of the model behavior in the event of gas phase vanishing will be done. Revealed issues, if any, will be recorded. Ways of fixing the issues will be developed.

&nbsp;&nbsp;&nbsp;Then simulation will be done. The revealed issues will be proven. Then the the ways of issues fixing will be tried and the most effective way will be chosen. In case of no issues, simulation will be done to prove that the model can handle the event of gaseous phase vanishing.

&nbsp;&nbsp;&nbsp;This project is based on the research work done by the author and devoted to transient influx modeling. During the work on transient influx modeling, a transient drift-flux model was used and it was revealed that there are problems with single to two phase flow transition. Hence, it is necessary to find and fix that problems. It is the reason why the specified subject is chosen for the current project.

&nbsp;&nbsp;&nbsp;For the purposes of the current project, the code written for transient influx modeling will be rewritten for the case of steady flow. It will require recreation of the numerical scheme from the beginning (transient drift-flux model is a system of PDEs, whereas steady drift-flux model is a system of ODEs). Moreover, steady drift-flux model doesn't allow for influx modeling - it only allows for manual altering between two and single phase flows. Hence, influx modeling part will also be removed from the original code.

&nbsp;&nbsp;&nbsp;Intended software will take as inputs flow parameters at the bottom of the pipe (pressure, gas phase density, gas phase velocity and gas  
concentration) and will return as outputs distribution of that parameters along
the pipe.

&nbsp;&nbsp;&nbsp;The primary characteristic of the intended software will be its ability to take as input zero gaseous phase concentration (i.e., to model a single phase flow).

&nbsp;&nbsp;&nbsp;The code will be written in Python 3. The anticipated packages to be used are matplotlib, pyqt5, numpy, scipy and math. Matplotlib will be used for plotting results. But it proved to be very slow in some cases of wellbore flows modeling. If such an issue were encountered, the pyqtgraph function of the pyqt5 package would be used. It allows for relatively quick plotting of big sets of data.

&nbsp;&nbsp;&nbsp;The resultant code can be used by researches who work with drift-flux models to reliably model either a single or a two phase flow in a vertical pipe using drift-flux model. Still, its main goal is to give an insight on how to make transient drift-flux model be valid for both single and two phase flows.

&nbsp;&nbsp;&nbsp;Since the problem is new for the author, the stated aim may not be achieved within the given period of time. Therefore, it is anticipated that at least steady influx simulation for a narrow range of flow conditions will be achieved.

# Difference between the work already done and the proposed project
&nbsp;&nbsp;&nbsp;Drift-flux model is a system of 3 equations: mass conservation equations for each of the phases of a multiphase flow and 1 momentum conservation equation for the mixture (for the flow). In general, this equations are PDEs because they contain time dependency of the variables as well as coordinate dependency. What I already did is I solved the general form of the drift-flux model, i.e. accounting for time dependency. Now I propose to solve drift-flux model for a steady flow, i.e. without time dependent term. In this case I have a system of 3 ODEs (because drift-flux model is a 1D model). For this purpose I will need to rewrite the numerical scheme and, hence, the code. Moreover, we modeled influx by introducing time dependent boundary conditions. When I am dealing with a steady model I can't introduce time-dependent boundary conditions. Hence, I will be manually change concentration of gas phase and analyze simulation behavior.

&nbsp;&nbsp;&nbsp;Overall,

&nbsp;&nbsp;&nbsp;*I already did*: 1) solution of transient 1D drift-flux model; 2) came up with a way to model influx and showed that it can be modeled; 3) noticed that drift-flux model behaves weirdly sometimes when dealing with influxes, i.e. with phase vanishing or occurrence;

&nbsp;&nbsp;&nbsp;*I propose*: 1) solve a steady 1D drift-flux model; 2) simplicity of a steady model will allow me to analyze mathematical peculiarities of drift-flux model when it's dealing with a phase occurrence/vanishing; 3) based on the analysis done, I will introduce corrections to the steady model which allow for reliable simulation of a steady gas-liquid flow in a wide range of conditions.

# References
1. Aarsnes, U. J. F. (2016). *Modeling of two-phase flow for estimation and
   control of drilling operations.* PhD thesis, Norwegian University of Science
   and Technology.​
2. Nikoofard, A., Aarsnes, U. J. F., Johansen, T. A., Kaasa, G. (2017). State
   and parameter estimation of a drift-flux model for under-balanced drilling
   operations. In *IEEE Transactions on Control Systems Technology*,
   pages 2000-2009.
