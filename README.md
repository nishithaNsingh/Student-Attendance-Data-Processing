**Student Attendance Data Processing**

**Overview**
This script processes student attendance data from an Excel file. It extracts the semester and branch from roll numbers, categorizes students based on their attendance percentages, and saves the sorted data into separate Excel files.

**Features**
- Reads student data from an Excel file.
- Extracts semester and branch from roll numbers.
- Categorizes students based on attendance percentage ranges.
- Saves categorized data into separate Excel files organized by branch and semester.

**Prerequisites**
- Python 3.x
- Pandas library (`pip install pandas`)
- XlsxWriter library (`pip install xlsxwriter`)
- OpenPyXL library (`pip install openpyxl`)

**Installation**
1. Clone or download the repository.
2. Install the required dependencies:
   ```sh
   pip install pandas xlsxwriter openpyxl
   ```
3. Place your Excel file (e.g., `students_5000_new_diffy.xlsx`) in the working directory.

**Usage**
1. Update the `file_path` variable with your Excel file name in the script:
   ```python
   file_path = "students_5000_new_diffy.xlsx"
   ```
2. Run the script:
   ```sh
   python script.py
   ```
3. The output files will be stored in the `new_sorted_students` directory.

**Semester Calculation Logic**
The script determines a student’s semester based on their roll number’s admission year:

| Admission Year | Current Year | Semester |
|---------------|-------------|----------|
| 2024         | 2024        | 2nd      |
| 2023         | 2024        | 4th      |
| 2022         | 2024        | 6th      |
| 2021         | 2024        | 8th      |
| 2020 or earlier | 2024 | 8th (Final Year) |

**Attendance Categories**
Students are classified into different attendance percentage ranges:
- **<75%**
- **65-75%**
- **50-65%**
- **40-50%**
- **30-40%**
- **20-30%**
- **10-20%**
- **0-10%**

Each category is saved as a separate sheet in the corresponding Excel file.

**Output**
- Each semester-branch combination has a separate file in the `new_sorted_students` directory.
- The main sheet contains all students for that category.
- Additional sheets contain filtered students based on attendance percentage.

**Troubleshooting**
**Issue: `TypeError: 'Series' object is not callable`**
- Ensure the filtering condition is correctly applied using `group[condition]` instead of `condition(group['Attendance (%)'])`.
- Replace this line:
  ```python
  filtered_data = group[condition(group['Attendance (%)'])]
  ```
  with:
  ```python
  filtered_data = group[condition]
  ```

**Contributions**
Feel free to submit pull requests for improvements and bug fixes.

**License**
This project is open-source and available for use under the MIT License.
