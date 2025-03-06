# **GridWorld Environment and Imitation Learning**  

A **Reinforcement Learning** project implementing a **GridWorld environment** with **Behavioral Cloning (BC)** and **DAgger (Dataset Aggregation)** for imitation learning. This project trains an agent to navigate a **grid-based world** while avoiding obstacles and following an expert policy.

---

## **Features**  

✔️ **Customizable GridWorld environment** with obstacles.  
✔️ **Expert demonstrations** generated using a predefined policy.  
✔️ **Behavioral Cloning (BC) implementation** for training an agent from expert demonstrations.  
✔️ **DAgger (Dataset Aggregation) implementation** for interactive learning with expert guidance.  
✔️ **Performance evaluation** using **accuracy, loss, precision, recall, and F1-score**.  
✔️ **Statistical analysis** comparing **Behavioral Cloning** and **DAgger**.  

---

## **GridWorld Environment**  

### **Class: `GridWorldEnvironment`**  

#### **Attributes:**  
- 🏗️ **`grid_size`**: Tuple defining the dimensions of the grid.  
- 🔢 **`state_space`**: Total number of states in the grid.  
- 🎮 **`action_space`**: Four possible actions (**Up, Down, Left, Right**).  
- 📍 **`state`**: Current state of the agent.  
- 🚧 **`obstacles`**: List of obstacle positions.  

#### **Methods:**  
- 🔄 **`reset()`**: Initializes the agent's position, ensuring it is not an obstacle.  
- ➡️ **`step(action)`**: Moves the agent in the grid based on the given action. Returns:  
  - **`next_state`**: New state after taking the action.  
  - **`reward`**: Reward based on reaching the goal or hitting an obstacle.  
  - **`done`**: Boolean indicating if the goal is reached.  

---

## **Expert Demonstrations**  

### **📌 `generate_expert_demonstrations(env, num_demos)`**  
Generates `num_demos` expert trajectories using a **simple policy** that moves the agent **right and down** until it reaches the goal.  

### **📌 `expert_policy(state)`**  
Defines an **expert policy** that guides the agent towards the goal efficiently.  

---

## **Imitation Learning**  

### 🔹 **1. Behavioral Cloning (BC)**  

#### **Model: `BehavioralCloningModel`**  
- A **feedforward neural network** trained using **supervised learning** on expert demonstrations.  
- Uses **CrossEntropyLoss** and **Adam optimizer**.  
- Trains using **`trainBC()`** function, which logs **loss and accuracy** over multiple epochs.  

### 🔹 **2. DAgger (Dataset Aggregation)**  

#### **Model: `DaggerModel`**  
- Similar architecture to **BC** but **iteratively queries the expert policy** to relabel actions taken by the learned policy.  
- Uses **`trainDA()`** function to:  
  - Train with initial expert demonstrations.  
  - Gather new data using the learned policy.  
  - Query the expert for corrections and add them to the dataset.  

---

## **Performance Evaluation**  

### **📊 Metrics**  
- ✅ **Accuracy**: Measures the proportion of correctly predicted actions.  
- 📉 **Loss**: Tracks training progression.  
- 📊 **Precision, Recall, F1-score**: Evaluated using **`evaluate_model()`**.  

### **📊 Statistical Analysis**  
- 📈 **Paired T-test** is performed to determine if there is a significant difference between **Behavioral Cloning** and **DAgger**.  
- **Results Interpretation:**  
  - If **p-value < 0.05**, significant difference exists.  
  - If **p-value ≥ 0.05**, no significant difference.  

---

## **Results**  

### **📌 Behavioral Cloning achieved:**  
- 🎯 **Accuracy**: `0.7012`  
- 🎯 **Precision**: `0.8298`  
- 🎯 **Recall**: `0.7373`  
- 🎯 **F1 Score**: `0.7206`  

### **📌 DAgger achieved:**  
- 🎯 **Accuracy**: `0.5907`  
- 🎯 **Precision**: `0.7843`  
- 🎯 **Recall**: `0.6102`  
- 🎯 **F1 Score**: `0.5482`  

### **📌 T-Test Results:**  
- 📊 **t-value** = `4.3360`, **p-value** = `0.0226`  
- **Conclusion**: There is a **significant difference** between **Behavioral Cloning and DAgger**.  

---

## **Visualization**  

The training progression is visualized using **matplotlib**:  
- 📉 **Loss and Accuracy curves** for both **BC** and **DAgger**.  
- 📊 **Comparison plots** showing differences in training efficiency.  

---

## **Conclusion**  

✅ **Behavioral Cloning** achieves **higher accuracy** but lacks adaptability.  
✅ **DAgger** allows **online corrections** but struggles initially.  
✅ The **statistical test confirms** a **significant difference** in their performances.  
✅ **Future Work**: Incorporating **reinforcement learning** for improved adaptability.  

---

## **Authors**  
📌 **Emir TAS** & **Kishanthan KINGSTON**
