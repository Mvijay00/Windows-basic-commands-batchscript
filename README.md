# Windows-basic-commands-batchscript
Ex08-Windows-basic-commands-batchscript

# AIM:
To execute Windows basic commands and batch scripting

# DESIGN STEPS:

### Step 1:

Navigate to any Windows environment installed on the system or installed inside a virtual environment like virtual box/vmware 

### Step 2:

Write the Windows commands / batch file . Save each script in a file with a .bat extension. Ensure you have the necessary permissions to perform the operations. Adapt paths as needed based on your system configuration.
### Step 3:

Execute the necessary commands/batch file for the desired output. 


# WINDOWS COMMANDS:
## Exercise 1: Basic Directory and File Operations
<br>

### Create a directory named "my-folder"
## COMMAND AND OUTPUT
mkdir my-folder <br>
<img width="795" height="143" alt="image" src="https://github.com/user-attachments/assets/7bce62af-2504-4c98-bf8f-7864fa51f086" />
<hr>

### Remove the directory "my-folder"
## COMMAND AND OUTPUT
rmdir my-folder <br>
<img width="755" height="123" alt="image" src="https://github.com/user-attachments/assets/bdbac9de-e779-4f60-b9c3-1b3d8eae2fd0" />
<hr>

### Create the file Rose.txt
## COMMAND AND OUTPUT
copy con Rose.txt <br>
dir Rose.txt <br>
<img width="765" height="313" alt="image" src="https://github.com/user-attachments/assets/85f6ac0f-826f-4821-8c35-9d09c88657c9" />
<hr>

### Create the file hello.txt using echo and redirection
## COMMAND AND OUTPUT
echo "hello world" > hello.txt <br>
type hello.txt <br>
<img width="718" height="141" alt="image" src="https://github.com/user-attachments/assets/97742fe9-1606-44ce-b6eb-f7258ef0bf0e" />
<hr>

### Copy the file hello.txt into the file hello1.txt
## COMMAND AND OUTPUT
copy hello.txt hello1.txt <br>
type hello1.txt <br>
<img width="733" height="147" alt="image" src="https://github.com/user-attachments/assets/351e54df-45f2-4507-b323-2bc328e9a580" />
<hr>

### Remove the file hello1.txt
## COMMAND AND OUTPUT
del hello1.txt <br>
<img width="791" height="81" alt="image" src="https://github.com/user-attachments/assets/8f4ce2d3-e32a-416a-b89b-8495a3bbe1fb" />
<hr>

### List out the file hello1.txt in the current directory
## COMMAND AND OUTPUT
dir hello1.txt <br>
<img width="721" height="173" alt="image" src="https://github.com/user-attachments/assets/d04e3125-9933-4244-b853-6c0006841d21" />
<hr>

### List out all the associated file extensions 
## COMMAND AND OUTPUT
assoc | more <br>
<img width="723" height="365" alt="image" src="https://github.com/user-attachments/assets/6ec5e9ac-88ae-47d6-b0fc-27ee4dfccb65" />
<hr>

### Compare the file hello.txt and rose.txt
## COMMAND AND OUTPUT
fc hello.txt Rose.txt <br>
<img width="606" height="197" alt="image" src="https://github.com/user-attachments/assets/9843e4fe-f00f-49cd-9f82-d6db97c2d21a" />
<hr>


## Exercise 2: Advanced Batch Scripting


Create a batch file named on the desktop. The batch file need to have a variable assigned with a desired name for ex. name="John" and display as "Hello, John".

notepad 1.bat
```
@echo off
set name=John
echo Hello, %name%!
pause
```
1.bat

## OUTPUT
<img width="840" height="135" alt="image" src="https://github.com/user-attachments/assets/08331254-9943-4aa3-affb-69b65736e004" />
<hr>



Create a batch file  on the desktop that checks whether a user-input number is odd or not. The script should:
Prompt the user to enter a number.
Calculate the remainder when the number is divided by 2.
Display whether the number is odd or not.
Ask the user if they want to check another number.
Repeat the process if the user enters Y, and exit with a thank-you message if the user enters N.
Handle invalid inputs for the continuation prompt (Y/N) gracefully.

notepad 2.bat
```
@echo off
:main
set /p number=Enter a number: 
rem Calculate remainder when divided by 2
set /a remainder=%number% %% 2
if %remainder%==1 (
    echo %number% is an odd number.
) else (
    echo %number% is not an odd number.
)
:choice
set /p continue=Do you want to check another number? (Y/N): 
if /i "%continue%"=="Y" goto main
if /i "%continue%"=="N" goto end
echo Invalid choice, please enter Y or N.
goto choice
:end
echo Thank you for using the odd number checker!
pause
```
2.bat

## OUTPUT
<img width="709" height="221" alt="image" src="https://github.com/user-attachments/assets/2984ab10-0ddc-4610-80b6-a8748dd35bc7" />
<hr>




Write a batch file that uses a FOR loop to iterate over a sequence of numbers (1 to 5) and displays each number with the label Number:. The output should pause at the end.

notepad 3.bat
```
@echo off
for %%i in (1 2 3 4 5) do (
    echo Number: %%i
)
pause
```
3.bat

## OUTPUT
<img width="743" height="169" alt="image" src="https://github.com/user-attachments/assets/7a30861c-e883-45e4-99df-029acca64e2c" />
<hr>



Write a batch script to check whether a file named sample.txt exists in the current directory. If the file exists, display the message sample.txt exists. Otherwise, display sample.txt does not exist. Pause the script at the end to view the result.

Instructions:
Use the IF EXIST conditional statement.
Make sure the script works for files located in the same directory as the batch file.
Use pause to keep the command window open after displaying the message.
Expected Output (if the file exists):

notepad 4.bat
```
@echo off
if exist sample.txt (
    echo sample.txt exists.
) else (
    echo sample.txt does not exist.
)
pause
```
echo "hello world" > sample.txt

4.bat

## OUTPUT
<img width="737" height="222" alt="image" src="https://github.com/user-attachments/assets/b6dbdfb6-6877-4198-8012-b98ca2f7e6b9" />
<hr>


Write a batch script that displays a simple menu with three options:
Say Hello – Displays the message Hello, World!
Create a File – Creates a file named newfile.txt with the content This is a new file
Exit – Exits the script with a goodbye message
The script should repeatedly display the menu until the user chooses to exit. Use goto statements to handle menu navigation.

notepad 5.bat
```
@echo off
:menu
echo 1. Say Hello
echo 2. Create a File
echo 3. Exit
set /p choice=Choose an option: 
if "%choice%"=="1" goto hello
if "%choice%"=="2" goto createfile
if "%choice%"=="3" goto end

:hello
echo Hello, World!
goto menu

:createfile
echo Creating a file...
echo This is a new file > newfile.txt
goto menu
:end
echo Goodbye!
pause
```
5.bat

## OUTPUT
<img width="626" height="331" alt="image" src="https://github.com/user-attachments/assets/a5490ea7-1dbe-44fd-95e8-35c12b400cee" />
<hr>


# RESULT:
The commands/batch files are executed successfully.
