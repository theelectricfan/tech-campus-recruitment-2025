
# Log Extraction Solution (C++) for FarMart Tech Campus Recruitment 2025

## 📄 Problem Statement

The goal of this project is to efficiently extract log entries from a large log file (~1 TB) based on a specific date. Each log entry starts with a timestamp, followed by a log level and a descriptive message.

### Example Log Format:
```
2024-12-01 14:23:45 INFO User logged in
2024-12-01 14:24:10 ERROR Failed to connect to the database
2024-12-02 09:15:30 WARN Disk space running low
```

## 🎯 Objective
- Extract all log entries for a specific date provided as a command-line argument.
- Save the extracted logs in an output file inside the `output/` directory.
- Optimize the solution for speed and efficient memory usage.

---

## ⚙️ Solution Approach
- The C++ program reads the file line by line to minimize memory usage.
- Compares the start of each line with the given date.
- If a line matches the specified date, it writes the entry to the output file.
- Automatically creates an `output/` directory if it doesn't exist.

## 🛠️ How to Run

### **Prerequisites:**
- A C++ compiler (like `g++` on Linux or `MSVC` on Windows)

### **Compile the Code:**
```bash
g++ -o extract_logs extract_logs.cpp
```

### **Execute the Program:**
```bash
./extract_logs <path_to_log_file> <YYYY-MM-DD>
```

**Example:**
```bash
./extract_logs logs/large_log.txt 2024-12-01
```

### **Expected Output:**
- A file named `output/output_2024-12-01.txt` containing all log entries for the specified date.

---

## 📑 Project Structure
```
├── src/
│   └── extract_logs.cpp       # Main C++ script for log extraction
├── output/                    # Directory for extracted logs
├── Discussion.md              # Solution explanation and alternatives
├── README.md                  # Project documentation (this file)
```

---

## 📝 Discussion.md Content
1. **Solutions Considered:**
   - **Memory-heavy solution:** Loading the entire log file into memory, which is inefficient for large files.
   - **Line-by-line processing (final solution):** Efficient memory usage and quicker execution.

2. **Final Solution Summary:**
   - Reads the log file line by line.
   - Writes matching entries directly to an output file.
   - Handles directory creation for both Windows and Linux environments.

3. **Steps to Run:**
   - Compile the program using a C++ compiler.
   - Run the executable with the required arguments.
   - Extracted logs are saved in the `output/` directory.

---

## ✅ Evaluation Criteria
- **Total Running Time:** Optimized for speed and processing only relevant lines.
- **Code Quality:** Clear, modular, and includes proper error handling.
- **Resource Utilization:** Uses minimal memory by reading and writing line by line.

---

## 📬 Submission Guidelines
1. **Fork the Repository:** Fork the provided repository to your own GitHub account.
2. **Add Your Solution:** Place the working code in the `src/` directory.
3. **Submit Link:** Share the link to your forked repository via the provided Google form.

---

## 🚨 Notes
- Ensure your code is pushed to the `main` branch.
- Submissions made after 1 hour from the contest start will be disqualified.
- You are allowed to use external resources but ensure your solution is original.

---

**Developed by:** Gourav Goyal

