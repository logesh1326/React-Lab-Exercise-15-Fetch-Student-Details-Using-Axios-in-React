# React Lab Exercise 15: Fetch Student Details Using Axios in React
## Name: LOGESH S
## Roll no: 2305001014
## Department: CSE

## AIM

To develop a React application that uses Axios to send a GET request to a REST API, receive student information in JSON format, and display the details when the user clicks the View Details button.

## PROGRAM

### i) App.jsx

```javascript
import { useState } from "react";
import axios from "axios";
import "./App.css";

function App() {
  const [student, setStudent] = useState(null);
  const [loading, setLoading] = useState(false);
  const [error, setError] = useState("");

  async function getStudentDetails() {
    setLoading(true);
    setError("");
    setStudent(null);

    try {
      const response = await axios.get(
        "https://jsonplaceholder.typicode.com/users/1"
      );

      setStudent(response.data);
    } catch (err) {
      setError("Unable to fetch student details. Try again.");
    } finally {
      setLoading(false);
    }
  }

  return (
    <div className="container">
      <h1>Student Management System</h1>

      <p>Click below to view student details.</p>

      <button onClick={getStudentDetails} disabled={loading}>
        {loading ? "Loading..." : "View Details"}
      </button>

      {loading && <p>Fetching student data...</p>}

      {error && <p className="error">{error}</p>}

      {student && (
        <div className="student-card">
          <h2>Student Details</h2>

          <p><strong>ID:</strong> {student.id}</p>
          <p><strong>Name:</strong> {student.name}</p>
          <p><strong>Email:</strong> {student.email}</p>
          <p><strong>City:</strong> {student.address.city}</p>
        </div>
      )}
    </div>
  );
}

export default App;
```

### ii) App.css

```css
* {
  box-sizing: border-box;
}

body {
  margin: 0;
  font-family: "Segoe UI", Arial, sans-serif;
  background: linear-gradient(135deg, #e0e7ff, #f5f3ff, #dbeafe);
  min-height: 100vh;
  color: #1e293b;
}

#root {
  min-height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
  padding: 25px;
}

.container {
  width: 100%;
  max-width: 520px;
  padding: 40px 35px;
  text-align: center;
  background: rgba(255, 255, 255, 0.95);
  border: 1px solid #e0e7ff;
  border-radius: 22px;
  box-shadow: 0 20px 50px rgba(79, 70, 229, 0.13);
}

h1 {
  margin: 0 0 14px;
  color: #312e81;
  font-size: 30px;
  letter-spacing: -0.8px;
}

.container > p {
  color: #64748b;
  font-size: 15px;
  line-height: 1.7;
  margin-bottom: 25px;
}

button {
  padding: 13px 28px;
  background: linear-gradient(135deg, #4f46e5, #7c3aed);
  color: white;
  border: none;
  border-radius: 10px;
  cursor: pointer;
  font-size: 16px;
  font-weight: 600;
  box-shadow: 0 6px 15px rgba(79, 70, 229, 0.22);
  transition: transform 0.2s, box-shadow 0.2s;
}

button:hover:not(:disabled) {
  transform: translateY(-2px);
  box-shadow: 0 10px 22px rgba(79, 70, 229, 0.3);
}

button:disabled {
  opacity: 0.6;
  cursor: not-allowed;
}

.student-card {
  margin-top: 30px;
  padding: 24px;
  text-align: left;
  background: #f8faff;
  border: 1px solid #c7d2fe;
  border-radius: 15px;
  animation: appear 0.35s ease-in-out;
}

.student-card h2 {
  margin-top: 0;
  margin-bottom: 20px;
  color: #4338ca;
  font-size: 21px;
  text-align: center;
}

.student-card p {
  margin: 12px 0;
  padding: 12px;
  background: white;
  border-radius: 8px;
  border: 1px solid #e2e8f0;
  font-size: 14px;
  overflow-wrap: anywhere;
}

.student-card strong {
  color: #3730a3;
}

.error {
  margin-top: 20px;
  padding: 12px;
  color: #b91c1c;
  background: #fef2f2;
  border: 1px solid #fecaca;
  border-radius: 9px;
}

@keyframes appear {
  from {
    opacity: 0;
    transform: translateY(10px);
  }

  to {
    opacity: 1;
    transform: translateY(0);
  }
}

@media (max-width: 480px) {
  #root {
    padding: 15px;
  }

  .container {
    padding: 28px 20px;
  }

  h1 {
    font-size: 25px;
  }

  .student-card {
    padding: 16px;
  }
}
```

## OUTPUT

<img width="1125" height="521" alt="image" src="https://github.com/user-attachments/assets/e45ddd1f-be5d-41ef-aa00-30170f224625" />


## RESULT

Thus, a React application was developed successfully using Axios to retrieve sample user information from a REST API and display the details with loading and error handling.
