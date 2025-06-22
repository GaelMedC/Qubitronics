# Simulación Cuántica del Modelo de Ising con Campo Transversal

Este proyecto fue desarrollado como parte del **Hack The QuBit 2025**, organizado por el **Quantum Computing Club** y el **Data Science Hub** del Tecnológico de Monterrey. El reto consistía en simular un sistema físico cuántico, formular su Hamiltoniano, construir un circuito cuántico equivalente e implementar una estrategia de mitigación de errores.

## 📌 Resumen del Proyecto

Simulamos el **modelo de Ising en 1D con dos qubits y un campo transversal**, utilizando Qiskit 2.1.0. El objetivo fue estimar la energía del estado fundamental mediante un algoritmo variacional (VQE), **simular la evolución temporal mediante trotterización**, y analizar los resultados obtenidos en simuladores y hardware real. Se utilizó el ansatz `EfficientSU2` y se aplicó mitigación de errores de lectura (`mthree.M3Mitigation`).

## 🧠 Objetivos del Hackathon

1. Formular el Hamiltoniano del sistema físico.
2. Resolverlo analíticamente (energías, evolución, observables).
3. Construir un circuito cuántico que lo modele.
4. Aplicar una técnica de mitigación o corrección de errores.
5. Ejecutar el circuito en simulador (ideal y ruidoso).
6. Ejecutar en hardware real de IBM Quantum.
7. Analizar resultados y fidelidad del sistema.

## ⚙️ Tecnologías y Herramientas

- Python 3.10
- Qiskit 2.1.0
- `qiskit.primitives.StatevectorEstimator`
- `qiskit_aer.AerSimulator`
- `qiskit.circuit.library.EfficientSU2`
- `qiskit.quantum_info.SparsePauliOp`
- `matplotlib`, `numpy`, `scipy.optimize`
- Mitigación: **Readout Error Mitigation (M3Mitigation)** con `mthree`

## 🧮 Formulación del Hamiltoniano

El Hamiltoniano simulado fue:

\[
H = -J Z_0 Z_1 - g X_0 - g X_1
\]

donde:

- \( J \) representa la interacción entre qubits,
- \( g \) es el campo transversal aplicado en la dirección X.

Implementado en Qiskit como `SparsePauliOp` con etiquetas de Pauli `"ZZ"`, `"XI"`, `"IX"`.

## 🔬 Resolución Analítica y Evolución Temporal

Se compararon los valores de energía mínima encontrados por el algoritmo VQE contra los valores esperados de la diagonalización exacta del Hamiltoniano. 

Además, se simuló la **evolución temporal del sistema desde el estado \(|00\rangle\)** utilizando **trotterización**, una técnica que permite aproximar la evolución bajo un Hamiltoniano no trivial mediante productos de exponentiales de sus términos individuales. Esto permitió observar cómo cambian las poblaciones de los estados medidos en función del tiempo, revelando oscilaciones cuánticas coherentes.

## ⚛️ Circuito Cuántico

Se utilizó un circuito variacional con el ansatz `EfficientSU2` sobre 2 qubits, parametrizado por un `ParameterVector`. La optimización se realizó con `COBYLA`, minimizando el valor esperado del Hamiltoniano.

## 🛡️ Mitigación de Errores

Se aplicó **Readout Error Mitigation** utilizando la biblioteca `mthree`. El mitigador `M3Mitigation` se calibró en el backend real de IBM Quantum (`ibm_sherbrooke`) para los qubits medidos. Esta técnica permite reducir errores sistemáticos de lectura, mejorando la fidelidad sin alterar el circuito cuántico.

## 📈 Resultados

- El VQE logró aproximar correctamente la energía del estado fundamental.
- La simulación de la evolución temporal mostró oscilaciones esperadas.
- Se observó una mejora significativa en fidelidad al aplicar mitigación de errores.
- El código está preparado para correr en backends reales de IBMQ, como `ibm_sherbrooke`.

## 👥 Equipo

**Participante principal:**  
José Gabriel Castillo García  
Estudiante de Maestría en Inteligencia Artificial Aplicada  
Tecnológico de Monterrey – Líderes del Mañana

Gael

Emilio

## 📄 Licencia

Este repositorio está bajo la licencia MIT. Puedes usar, modificar y distribuir libremente este código, siempre que se mencione al autor original.

---

> 💡 *"La computación cuántica no solo consiste en simular sistemas ideales, sino en enfrentar el reto real: hacer ciencia sobre hardware imperfecto."*

