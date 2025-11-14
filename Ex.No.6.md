# Ex06 BMI Calculator
## Date: 12-11-25

## AIM
To create a BMI calculator using React Router 

## ALGORITHM
### STEP 1 State Initialization
Manage the current page (Home or Calculator) using React Router.

### STEP 2 User Input
Accept weight and height inputs from the user.

### STEP 3 BMI Calculation
Calculate the BMI based on user input.

### STEP 4 Categorization
Classify the BMI result into categories (Underweight, Normal weight, Overweight, Obesity).

### STEP 5 Navigation
Navigate between pages using React Router.

## PROGRAM

### App.jsx
```
import React from "react";
import { Routes, Route, Link } from "react-router-dom";
import Home from "./components/Home.jsx";
import BMICalculator from "./components/bmi.jsx";

function App() {
  return (
    <>
      <nav className="navbar">
        <h2 className="logo">BMI App</h2>
        <div className="nav-links">
          <Link to="/">Home</Link>
          <Link to="/calculator">Calculator</Link>
        </div>
      </nav>

      <div className="page-wrapper">
        <Routes>
          <Route path="/" element={<Home />} />
          <Route path="/calculator" element={<BMICalculator />} />
        </Routes>
      </div>
    </>
  );
}

export default App;
```

### App.css
```
/* ----------------------------------------------------
   GLOBAL STYLES — Clean, Light, Premium
---------------------------------------------------- */

* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
  font-family: "Inter", system-ui, sans-serif;
}

body {
  background: linear-gradient(to right, #e3fdfd, #cbf1f5, #a6e3e9, #71c9ce);
  min-height: 100vh;
  display: flex;
  justify-content: center;
  overflow-x: hidden;
}

/* Page wrapper ensures content doesn't sit behind navbar */
.page-wrapper {
  width: 100%;
  padding-top: 130px;
  display: flex;
  justify-content: center;
}


/* ----------------------------------------------------
   NAVBAR
---------------------------------------------------- */

.navbar {
  width: 100%;
  position: fixed;
  top: 0;
  left: 0;
  padding: 14px 50px;
  display: flex;
  justify-content: space-between;
  align-items: center;

  background: rgba(242, 229, 229, 0.4);
  backdrop-filter: blur(15px);
  border-bottom: 1px solid rgba(255, 255, 255, 0.4);
  box-shadow: 0 4px 15px rgba(0, 0, 0, 0.06);
  z-index: 1000;
}

.logo {
  font-size: 1.8rem;
  font-weight: 800;
  color: #1269ba;
  letter-spacing: 1px;
}

.nav-links {
  display: flex;
  align-items: center;
}

.nav-links a {
  margin-left: 18px;
  padding: 8px 14px;
  font-size: 15px;
  font-weight: 600;
  color: #124d7b;
  text-decoration: none;
  transition: 0.25s ease;
  border-radius: 8px;
}

.nav-links a:hover {
  background: rgba(0, 0, 0, 0.08);
}

.nav-links .active {
  background: #28c3b8;
  color: white !important;
}


/* ----------------------------------------------------
   CONTAINER (Centering Layout)
---------------------------------------------------- */

.container {
  width: 100%;
  max-width: 600px;
  text-align: center;
  margin: auto;
  padding: 0 20px;
}


/* ----------------------------------------------------
   TITLES
---------------------------------------------------- */

.title,
h1 {
  color: #1269ba;
  text-align: center;
  font-weight: 800;
  font-size: 2.3rem;
  margin-bottom: 20px;
}


/* ----------------------------------------------------
   CARD — Glassmorphism
---------------------------------------------------- */

.glass-card {
  background: rgba(255, 255, 255, 0.45);
  padding: 35px;
  border-radius: 20px;
  backdrop-filter: blur(15px);
  box-shadow: 0 10px 25px rgba(0, 0, 0, 0.08);
  margin: auto;
}


/* ----------------------------------------------------
   INPUT GROUP
---------------------------------------------------- */

.input-group {
  text-align: left;
  margin-bottom: 18px;
  width: 100%;
}

.input-group label {
  font-size: 14px;
  color: #035c63;
  font-weight: 600;
}

input {
  width: 100%;
  margin-top: 5px;
  padding: 12px;
  border-radius: 10px;
  border: none;
  background: #fff;
  font-size: 15px;
  box-shadow: 0 0 0 2px transparent;
  transition: 0.25s;
}

input:focus {
  outline: none;
  box-shadow: 0 0 0 3px #28c3b855;
}


/* ----------------------------------------------------
   BUTTONS — Final Professional Style
---------------------------------------------------- */

.btn,
.start-btn,
.btn.primary,
.btn.calculate {
  background: linear-gradient(135deg, #1abc9c, #17a589);
  color: white;
  padding: 14px 30px;
  font-size: 16px;
  font-weight: 700;
  border: none;
  border-radius: 14px;
  cursor: pointer;
  letter-spacing: 0.4px;

  display: inline-flex;
  justify-content: center;
  align-items: center;

  transition: 0.25s ease;
  box-shadow: 0px 6px 14px rgba(26, 188, 156, 0.35);
}

.btn:hover,
.start-btn:hover,
.btn.primary:hover,
.btn.calculate:hover {
  background: linear-gradient(135deg, #17a589, #14997b);
  transform: translateY(-3px);
  box-shadow: 0px 8px 18px rgba(26, 188, 156, 0.45);
}

.btn:active,
.start-btn:active,
.btn.primary:active,
.btn.calculate:active {
  transform: scale(0.97);
}

/* Reset button */
.btn.reset {
  background: #ff6b81;
  color: white;
}

.btn.reset:hover {
  background: #ff4d68;
  transform: translateY(-3px);
}


/* ----------------------------------------------------
   RESULT
---------------------------------------------------- */

.result {
  margin-top: 25px;
  padding: 20px;
  border-radius: 18px;
  background: rgba(255, 255, 255, 0.55);
  color: #035c63;
  font-weight: 700;
}

.category {
  margin-top: 12px;
  padding: 10px 18px;
  border-radius: 50px;
  font-size: 14px;
}

.normal-weight {
  background: #2ecc71;
  color: white;
}
.underweight {
  background: #3498db;
  color: white;
}
.overweight {
  background: #f1c40f;
  color: #664d00;
}
.obesity {
  background: #e74c3c;
  color: white;
}

.fade-in {
  animation: fade 0.7s ease;
}

@keyframes fade {
  from { opacity: 0; transform: translateY(10px); }
  to { opacity: 1; transform: translateY(0); }
}


/* ----------------------------------------------------
   HOME PAGE
---------------------------------------------------- */

.landing {
  height: 70vh;
  display: flex;
  flex-direction: column;
  justify-content: center;
}

.hero-title {
  font-size: 2.5rem;
  color: #1269ba;
  font-weight: 800;
}

.hero-subtitle {
  font-size: 1.2rem;
  margin: 15px 0 30px;
  opacity: 0.8;
  color: #035c63;
}


/* ----------------------------------------------------
   FOOTER
---------------------------------------------------- */

.footer {
  margin-top: 40px;
  text-align: center;
  font-size: 14px;
  color: #035c63;
  font-weight: 600;
  opacity: 0.85;
}
```

### bmi.jsx:
```
import React, { useState } from "react";

function BMICalculator() {
  const [weight, setWeight] = useState("");
  const [height, setHeight] = useState("");
  const [bmi, setBmi] = useState(null);
  const [category, setCategory] = useState("");

  const calculateBMI = () => {
    if (weight && height) {
      const heightInMeters = height / 100;
      const bmiValue = (weight / (heightInMeters * heightInMeters)).toFixed(2);
      setBmi(bmiValue);

      if (bmiValue < 18.5) setCategory("Underweight");
      else if (bmiValue < 25) setCategory("Normal weight");
      else if (bmiValue < 30) setCategory("Overweight");
      else setCategory("Obesity");
    }
  };

  const reset = () => {
    setWeight("");
    setHeight("");
    setBmi(null);
    setCategory("");
  };

  return (
    <div className="container">
      <h1 className="title">BMI Calculator</h1>
      <div className="card glass-card">
        <div className="input-group">
          <label>Weight (kg)</label>
          <input
            type="number"
            value={weight}
            onChange={(e) => setWeight(e.target.value)}
            placeholder="Enter weight"
          />
        </div>

        <div className="input-group">
          <label>Height (cm)</label>
          <input
            type="number"
            value={height}
            onChange={(e) => setHeight(e.target.value)}
            placeholder="Enter height"
          />
        </div>

        <div className="buttons">
          <button className="btn calculate" onClick={calculateBMI}>
            Calculate
          </button>
          <button className="btn reset" onClick={reset}>
            Reset
          </button>
        </div>

        {bmi && (
          <div className="result fade-in">
            <h2>Your BMI: {bmi}</h2>
            <p className={`category ${category.toLowerCase().replace(" ", "-")}`}>
              {category}
            </p>
          </div>
        )}
      </div>
      <p className="footer">Designed by Austin 🤍</p>
    </div>
  );
}

export default BMICalculator;
```

### Home.jsx:
```
import React from "react";
import { Link } from "react-router-dom";

function Home() {
  return (
    <div className="landing">
      <div className="hero">
        <h1 className="hero-title">Track Your Health Easily</h1>
        <p className="hero-subtitle">
          Calculate your BMI instantly and understand your health category.
        </p>
        <Link to="/calculator">
          <button className="btn primary">Start Calculating</button>
        </Link>
      </div>
      <p className="footer">Designed by Austin 🤍</p>
    </div>
  );
}

export default Home;
```


## OUTPUT
<img width="1919" height="842" alt="Screenshot 2025-11-14 155916" src="https://github.com/user-attachments/assets/7f91b2d1-f914-4727-8213-163d5a18a202" />

<img width="1918" height="996" alt="Screenshot 2025-11-14 155755" src="https://github.com/user-attachments/assets/e1bd4be8-8ace-4e08-aa2e-84c2627add16" />

<img width="1919" height="987" alt="Screenshot 2025-11-14 155833" src="https://github.com/user-attachments/assets/1f1b5302-6080-4cd1-805a-c465c7722af0" />

<img width="1919" height="1014" alt="Screenshot 2025-11-14 155902" src="https://github.com/user-attachments/assets/063c2029-f097-490e-8326-1ceb387f87aa" />

## RESULT
The program for creating BMI Calculator using React Router is executed successfully.
