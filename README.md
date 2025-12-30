# Humidity_and_Temperature_Sensor
# 1. Unzip the files
# 2. Connect the Arduino Temp and Hum sensor to the computer
# 3. In line 11 of the "server.js" change the port name to the one your Arduino is connected("COM3" for example)
# 4. In the command prompt of the project folder start the server by typing "node server.js" and pressing enter. The Arduino should start to collect data.
# 5. In Google Chrome open localhost:3000. You should see your server displaying the readings on a chart. Scrolling lower, you will see a history of all the readings with their time at which they were taken.


# The server.js file acts as a bridge between an Arduino hardware sensor and a web dashboard. It collects real-time environmental data, saves it to a database, and provides an API for a frontend to display that data.

# 1. Hardware Communication (Serial Port)
# The code uses the serialport library to listen to a physical connection (in this case, COM4).
# It expects the Arduino to send data as a string of numbers separated by a comma (e.g., 45.5,22.0).
# It sorts this string into Humidity and Temperature.

# 2. Database Management (SQLite)
# The script automatically sets up a local database file named sensor_history.db.
# It creates a table called readings if it doesn't already exist.
# Every time a new piece of data comes in from the Arduino, the server saves the humidity and temperature along with a timestamp.

# 3. Data Processing & API Endpoints
# The server hosts two endpoints that a website can call to get information:
# Real-time Data (/api/data): Returns the very latest reading received from the sensor.
# Historical Trends (/api/history): This part of the code groups the thousands of individual readings into 5-minute intervals and calculates the average temperature and humidity for each block. It returns the 20 most recent intervals.

# 4. Web Hosting
# App.use(express.static('public')) tells the server to serve any HTML, CSS, or JavaScript files located in a folder named public.
