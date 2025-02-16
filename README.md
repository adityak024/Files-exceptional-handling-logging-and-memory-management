# Files-exceptional-handling-logging-and-memory-management
GitHub is a cloud-based platform for version control, enabling developers to collaborate, track changes, and manage projects using Git. It supports file handling, exception tracking, logging, and memory management in software development. With repositories, pull requests, and automation tools.
Python File Handling, Exception Handling, Logging, and Memory Management
This repository contains examples and explanations related to Python file handling, exception handling, logging, and memory management. The examples cover various aspects of handling files, managing exceptions, logging information, and profiling memory usage in Python.

Table of Contents
Open a File for Writing

Read File Contents and Print Each Line

Handle File Not Found Error

Read from One File and Write to Another

Handle Division by Zero Error

Log Error Message for Division by Zero

Log Information at Different Levels

Handle File Opening Error

Read File Line by Line and Store in a List

Append Data to an Existing File

Handle Dictionary Key Error

Handle Multiple Exceptions

Check if File Exists Before Reading

Log Informational and Error Messages

Handle Empty File Case

Memory Profiling

Write List of Numbers to a File

Logging with Rotation After 1MB

Handle IndexError and KeyError

Use Context Manager to Read File

Count Word Occurrences in a File

Check if File is Empty Before Reading

Log Error During File Handling

1. Open a File for Writing
python
with open('example.txt', 'w') as file:
    file.write('Hello, this is a sample string.')
2. Read File Contents and Print Each Line
python
with open('example.txt', 'r') as file:
    for line in file:
        print(line, end='')
3. Handle File Not Found Error
python
try:
    with open('nonexistent_file.txt', 'r') as file:
        for line in file:
            print(line, end='')
except FileNotFoundError:
    print("The file does not exist. Please check the file name and try again.")
4. Read from One File and Write to Another
python
with open('source.txt', 'r') as source_file:
    content = source_file.read()

with open('destination.txt', 'w') as destination_file:
    destination_file.write(content)
5. Handle Division by Zero Error
python
try:
    result = 10 / 0
except ZeroDivisionError:
    print("Error: Division by zero is not allowed.")
6. Log Error Message for Division by Zero
python
import logging

logging.basicConfig(filename='error.log', level=logging.ERROR, format='%(asctime)s - %(levelname)s - %(message)s')

try:
    result = 10 / 0
except ZeroDivisionError:
    logging.error("Error: Division by zero is not allowed.")
7. Log Information at Different Levels
python
import logging

logging.basicConfig(filename='application.log', level=logging.DEBUG, format='%(asctime)s - %(levelname)s - %(message)s')

logging.debug('This is a debug message.')
logging.info('This is an info message.')
logging.warning('This is a warning message.')
logging.error('This is an error message.')
logging.critical('This is a critical message.')
8. Handle File Opening Error
python
try:
    with open('example.txt', 'r') as file:
        content = file.read()
        print(content)
except FileNotFoundError:
    print("Error: The file 'example.txt' does not exist. Please check the file name and try again.")
except IOError:
    print("Error: An I/O error occurred while opening the file.")
9. Read File Line by Line and Store in a List
python
with open('example.txt', 'r') as file:
    lines = file.readlines()

print(lines)
10. Append Data to an Existing File
python
with open('example.txt', 'a') as file:
    file.write('This is the new data that will be appended.\n')
11. Handle Dictionary Key Error
python
sample_dict = {'name': 'Alice', 'age': 30}

try:
    value = sample_dict['country']
except KeyError:
    print("Error: The key 'country' does not exist in the dictionary.")
12. Handle Multiple Exceptions
python
try:
    num1 = int(input("Enter the numerator: "))
    num2 = int(input("Enter the denominator: "))
    result = num1 / num2
    
    my_list = [1, 2, 3]
    index = int(input("Enter an index: "))
    element = my_list[index]
    
    print("The result of the division is:", result)
    print("The element at the specified index is:", element)
except ZeroDivisionError:
    print("Error: Division by zero is not allowed.")
except ValueError:
    print("Error: Invalid input. Please enter a valid number.")
except IndexError:
    print("Error: Index out of range. Please enter a valid index.")
13. Check if File Exists Before Reading
python
import os

file_path = 'example.txt'

if os.path.exists(file_path):
    if os.path.getsize(file_path) == 0:
        print(f"The file '{file_path}' is empty.")
    else:
        with open(file_path, 'r') as file:
            content = file.read()
            print(content)
else:
    print(f"Error: The file '{file_path}' does not exist.")
14. Log Informational and Error Messages
python
import logging

logging.basicConfig(filename='app.log', level=logging.DEBUG, format='%(asctime)s - %(levelname)s - %(message)s')

try:
    logging.info('This is an informational message.')

    num1 = 10
    num2 = 0
    result = num1 / num2

except ZeroDivisionError:
    logging.error('Error: Division by zero is not allowed.')

logging.info('Division operation completed.')
15. Handle Empty File Case
python
def read_and_print_file(file_path):
    try:
        with open(file_path, 'r') as file:
            content = file.read()
            if content:
                print(content)
            else:
                print("The file is empty.")
    except FileNotFoundError:
        print(f"Error: The file '{file_path}' does not exist. Please check the file name and try again.")
    except IOError:
        print("Error: An I/O error occurred while opening the file.")

file_path = 'example.txt'
read_and_print_file(file_path)
16. Memory Profiling
python
from memory_profiler import profile

@profile
def my_function():
    large_list = [i for i in range(1000000)]
    return large_list

if __name__ == "__main__":
    my_function()
Run the program with:

sh
python -m memory_profiler memory_test.py
17. Write List of Numbers to a File
python
numbers = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]

with open('numbers.txt', 'w') as file:
    for number in numbers:
        file.write(f'{number}\n')
18. Logging with Rotation After 1MB
python
import logging
from logging.handlers import RotatingFileHandler

logger = logging.getLogger('my_logger')
logger.setLevel(logging.DEBUG)

handler = RotatingFileHandler('my_log.log', maxBytes=1 * 1024 * 1024, backupCount=3)
handler.setLevel(logging.DEBUG)

formatter = logging.Formatter('%(asctime)s - %(levelname)s - %(message)s')
handler.setFormatter(formatter)

logger.addHandler(handler)

logger.debug('This is a debug message.')
logger.info('This is an info message.')
logger.warning('This is a warning message.')
logger.error('This is an error message.')
logger.critical('This is a critical message.')
19. Handle IndexError and KeyError
python
def handle_exceptions():
    my_list = [1, 2, 3]
    my_dict = {'name': 'Alice', 'age': 30}

    try:
        list_item = my_list[5]
        print("List item:", list_item)

        dict_item = my_dict['city']
        print(
