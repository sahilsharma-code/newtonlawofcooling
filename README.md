# Newton's Law of Cooling Simulation: Exact Differential Equations Approach

An interactive web-based mathematical simulation modeling Newton's Law of Cooling, designed specifically to demonstrate how the cooling equation is solved by converting it into an **Exact Differential Equation** using an integrating factor.

This project was built for a Mathematics project statement showcasing real-life cooling applications (Forensics/CSI, Culinary, Industrial Engineering) while maintaining complete portability for cloud deployment.

---

## 📐 Mathematical Formulation

### 1. The Physical Law
Newton's Law of Cooling states that the rate of temperature change of a body is proportional to the temperature difference between the body and its surroundings:

$$\frac{dT}{dt} = -k(T - T_m)$$

Where:
* $T(t)$ is the temperature of the object at time $t$
* $T_m$ is the constant temperature of the ambient environment
* $k > 0$ is the cooling rate constant (dependent on surface area, materials, insulation, etc.)

---

### 2. Formulating the Differential Form
To analyze the equation under the exactness framework, we rearrange the equation into standard differential form:

$$M(t, T)dt + N(t, T)dT = 0$$

Multiplying the rate equation by $dt$ and moving terms:

$$k(T - T_m)dt + dT = 0$$

Here, the coefficients are:
* $M(t, T) = k(T - T_m)$
* $N(t, T) = 1$

---

### 3. Testing for Exactness
For a differential equation to be exact, the partial derivatives must satisfy:

$$\frac{\partial M}{\partial T} = \frac{\partial N}{\partial t}$$

Let's compute them:
* $\frac{\partial M}{\partial T} = \frac{\partial}{\partial T}[k(T - T_m)] = k$
* $\frac{\partial N}{\partial t} = \frac{\partial}{\partial t}[1] = 0$

Since $k \neq 0$, we have:

$$\frac{\partial M}{\partial T} \neq \frac{\partial N}{\partial t}$$

Thus, **the raw differential equation is NOT exact**.

---

### 4. Constructing the Integrating Factor $\mu(t)$
Because the raw equation is not exact, we calculate an integrating factor $\mu$ to enforce exactness. We check if the ratio depends only on $t$:

$$\frac{1}{N} \left( \frac{\partial M}{\partial T} - \frac{\partial N}{\partial t} \right) = \frac{k - 0}{1} = k$$

Since $k$ is a constant (which is a function of $t$ only), the integrating factor $\mu(t)$ is:

$$\mu(t) = e^{\int k \, dt} = e^{kt}$$

---

### 5. Multiplying and Verifying Exactness
Multiplying the original differential form by our integrating factor $e^{kt}$:

$$k(T - T_m)e^{kt}dt + e^{kt}dT = 0$$

Our modified coefficients are:
* $M'(t, T) = k(T - T_m)e^{kt}$
* $N'(t, T) = e^{kt}$

Re-evaluating the partial derivatives:
* $\frac{\partial M'}{\partial T} = ke^{kt}$
* $\frac{\partial N'}{\partial t} = ke^{kt}$

Since $\frac{\partial M'}{\partial T} = \frac{\partial N'}{\partial t}$, **the equation is now EXACT**.

---

### 6. Solving the Exact Equation
We solve for the potential function $\psi(t, T) = C$ such that:

$$\frac{\partial \psi}{\partial T} = N' = e^{kt} \quad \text{and} \quad \frac{\partial \psi}{\partial t} = M' = k(T - T_m)e^{kt}$$

1. Integrate $N'$ with respect to $T$:
   $$\psi(t, T) = \int e^{kt} \, dT = T e^{kt} + g(t)$$

2. Differentiate $\psi$ with respect to $t$:
   $$\frac{\partial \psi}{\partial t} = k T e^{kt} + g'(t)$$

3. Equate $\frac{\partial \psi}{\partial t}$ to $M'$:
   $$k T e^{kt} + g'(t) = k(T - T_m)e^{kt} \implies k T e^{kt} + g'(t) = k T e^{kt} - k T_m e^{kt}$$

4. Solve for $g'(t)$ and integrate:
   $$g'(t) = -k T_m e^{kt}$$
   $$g(t) = -T_m e^{kt} + C_0$$

5. Assemble the potential function:
   $$\psi(t, T) = (T - T_m)e^{kt} = C$$

---

### 7. Applying Boundary Conditions (Initial Temperature $T_0$)
At $t = 0$, $T = T_0$:

$$(T_0 - T_m)e^{0} = C \implies C = T_0 - T_m$$

Substitute $C$ back:

$$(T - T_m)e^{kt} = T_0 - T_m$$

$$T(t) - T_m = (T_0 - T_m)e^{-kt}$$

$$T(t) = T_m + (T_0 - T_m)e^{-kt}$$

This is the standard Newton's Law of Cooling cooling curve, derived rigorously via the **Exact Differential Equation** method.
