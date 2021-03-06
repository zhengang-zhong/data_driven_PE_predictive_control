# data_driven_PE_predictive_control
persistently exciting based predictive control

1. Paper 1 DeePC: Data-Enabled Predictive Control (ref: In the Shallows of the DeePC)

   1. Example: Mass spring system with full observation

      ![Mass spring system with full observation](images/mass_spring_DeePC.png)

2. Paper 2 Data-driven MPC with equality terminal constraints (ref: Data-Driven Tracking MPC for Changing Setpoints)

   1. Example 1: mass spring system

      1. Full observation

         ![Mass spring system with full observation](images/mass_spring_PE_full_obs_with_eq_terminal.png)

      2. Partial observation

         ![Mass spring system with partial observation](images/mass_spring_PE_partial_obs_with_eq_terminal.png)

   2. Example 2: four tank system

      1. The simulation for the case study included in their paper not stable. My simulation is designed for a nominal system (no noise no disturbance); therefore, a nominal predictive control with terminal equality constraints applied. Should I use the robust version to acquire stability? -> next: either find why it is not stable or implement the robust version to see what is gonna happen. Explanation: since the set point in the paper is not an equilibrium point, slack variable ($\lambda_{\sigma}$) for $y$ is need. $\lambda_{\alpha}$ is also needed for a stable controller.

      2. After adding the regularization term $\lambda_{\alpha}$ ($\lambda_{\alpha} \bar{\varepsilon} = 0.1$), the closed-loop is stable. However, constant tracking error exists. 

         ![Mass spring system with partial observation](images/four_tank_PE_partial_obs_with_eq_terminal_sigma_alpha.png)

         3. By replace `R = eye([1e-4]*nu)`  to  `R = eye([1]*nu)` all fixed now.

            1. 1e-4 * $I$

            ![](images/four_tank_PE_partial_obs_with_eq_terminal_sigma_alpha_Q=1e-4.png)

            2. $I$

            ![](images/four_tank_PE_partial_obs_with_eq_terminal_sigma_alpha_Q=1.png)

         4. Potential remedy: full observation, set equilibrium point as the set point `ry = [0.64440373,0.75261324,0.80263158,1.14285714], ru = [1,1]), lambda_alpha*epsilon = 1.2, n = 1, L = 30, T = 400`

            1. If `R=1e-4I` sometimes still not stable

         ![Full observation](images/four_tank_PE_full_obs_with_eq_terminal_sigma_alpha.png)

         2. Fix by setting `R=I`

            ![Full observation](images/four_tank_PE_full_obs_with_eq_terminal_sigma_alpha_R=1.png)

3. Paper 3 Data-driven MPC with terminal cost and terminal constraints (ref: On the design of terminal ingredients for data-driven MPC)

   1. Using P provided by Julian

      ![four tank with terminal ingredients](images/four_tank_PE_partial_obs_with_terminal_ingredients.png)

   2. Next step: update the LMI function (may because some strictly LMI not satisfied)

4. Paper 4 Stable, optimal, robust data-driven control: Formulas for Data-Driven Control (ref: Stabilization, Optimality, and Robustness)

   1. Stable feedback gain

      ![Mass spring system with partial observation](images/mass_spring_stable_fb.png)





Thanks for Julian's help. As the author of many of the papers above, he shared his insights about PE-based data-driven control and his simulation configurations. 
