# data_driven_PE_predictive_control
persistently exciting based predictive control

1. DeePC: Data-Enabled Predictive Control (ref: In the Shallows of the DeePC)
2. Data-driven MPC with equality terminal constraints (ref: Data-Driven Tracking MPC for Changing Setpoints)
   1. The simulation for the case study included in their paper not stable. My simulation is designed for a nominal system (no noise no disturbance); therefore, a nominal predictive control with terminal equality constraints applied. Should I use the robust version to acquire stability? -> next: either find why it is not stable or implement the robust version to see what is gonna happen.
   2. After adding the regularization term $\sigma_{alpha}$, the closed-loop is stable. However, constant tracking error exists. 
3. Data-driven MPC with terminal cost and terminal constraints (ref: On the design of terminal ingredients for data-driven MPC)
4. Stable, optimal, robust data-driven control: Formulas for Data-Driven Control (ref: Stabilization, Optimality, and Robustness)
