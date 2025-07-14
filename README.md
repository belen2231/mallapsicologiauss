# mallapsicologiauss
body {
  font-family: 'Segoe UI', sans-serif;
  background-color: #fff0f5;
  color: #880088;
  text-align: center;
}

h1 {
  margin-top: 30px;
  color: #cc0099;
}

#grid {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(320px, 1fr));
  gap: 20px;
  margin: 40px;
  padding: 20px;
}

.course {
  background-color: #ffe6f0;
  border: 2px solid #ff66cc;
  border-radius: 12px;
  padding: 16px;
  box-shadow: 2px 2px 12px rgba(255, 0, 128, 0.3);
  transition: transform 0.2s;
}

.course:hover {
  transform: scale(1.03);
}

.course.approved {
  background-color: #f0cfe3;
  border-color: #cc3399;
}

button {
  background-color: #ff3399;
  color: white;
  border: none;
  border-radius: 6px;
  padding: 10px 20px;
  cursor: pointer;
  font-weight: bold;
}

button:disabled {
  background-color: #ffcce6;
  cursor: not-allowed;
}
