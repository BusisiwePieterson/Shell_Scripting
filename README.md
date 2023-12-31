# Shell_Scripting

<img src='images/shell.webp' width='950' height='300'>

### **What is Shell Scripting?**

A shell script is a list of commands in a computer program that is run by the Unix shell which is a command line interpreter. A shell script usually has comments that describe the steps. The different operations performed by shell scripts are program execution, file manipulation and text printing. A wrapper is also a kind of shell script that creates the program environment, runs the program etc.

### **Why use Shell Scripting?**

- Batch jobs

    Several commands that would be entered manually in a command line interface can be executed automatically using a shell script. This can be done without the user needing to trigger each command separately.

- Generalisation

    It is much more flexible to use loops, variables etc for multiple tasks in shell script. An example of this is a Unix shell script known as bash, which converts jpg images to png images.

- Shortcuts

    There is a shortcut provided by a shell script for a system command where command options, environment settings or post processing apply. This still allows the shortcut script to act as a Unix command.
## Introduction to Shell Scripting and User Input

Shell scripts can be written in either a code editor like VSCode or you can use nano/ vim.
Since we want to keep our scripts we will be using VSCode. 

1. Create a folder - `mkdir shell_scripting`
2. cd into the folder - `desktop/shell_scripting`
3. create the file for the shell script - `touch myscript.sh`
4. open up VSCode - `code .`

![images](images/Screenshot_1.png)


## Shell Scripting Syntax

1. **Variables**: Variables are used to store information to be referenced, this can be of various types such as numbers, strings and arrays. You can assign values to variables using the **=** operator. To access the value of the variable use the **$** symbol e.g `$variable_name`

![images](images/Screenshot_3.png)


2. **Control Flow**: Bash **if-else** statements are used to perform conditional tasks in the sequential flow of execution of statements. Sometimes, we want to process a specific set of statements if a condition is true, and another set of statements if it is false. To perform such type of actions, we can apply the if-else mechanism.

![images](images/Screenshot_4.png)

**For loop** is a control structure that is used to perform repetitive tasks or execute a bunch of commands a specific number of times. With for loop, you can iterate through numbers, lists, files, or even directories.

***

3. **Input and Output**: The **read command**  is used to read input from the user or from a file and output the text using the echo command. You can also redirect input and output using operators like `>` output to a file, `<` input from a file, and `|`pipe the output of the one command as an input to another.


![images](images/Screenshot_9.png)

Here we have a script `echo Hello World` in our `myscript.sh` file, we will output the content into a new file `index.sh`

![images](images/Screenshot_10.png)

Below we see the content of `myscript.sh` in the new file

![images](images/Screenshot_11.png)

We can also pass the content of a file as input to a command.

`grep "demonstrate" < input.txt` - this will search for matching patterns in the `input.txt` file


![images](images/Screenshot_12.png)

![images](images/Screenshot_13.png)

***

5. **Functions**: Functions in bash scripting are a great option to reuse code. A Bash function can be defined as a set of commands which can be called several times within bash script. The purpose of function in bash is to help you make your scripts more readable and avoid writing the same code again and again.


![images](images/Screenshot_14.png)

## Time to our First Shell Script !!

Step 1: Inside your file copy and paste the code block below:

```
#!/bin/bash

# Prompt the user for their name
echo "Enter your name:"
read name

# Display a greeting with the entered name
echo "Hello, $name! Nice to meet you."

```
Step 2. Save your file

Step 3. Run the command `sudo chmod +x myscript.sh` this makes the file executable.

Step 6. Run the script using `./myscript.sh`

![images](images/Screenshot_15.png)

## Directory Manipulation and Navigation

This script will display the current directory, create a new directory called `"my_directory"`, change to that directory, create two files inside it, list the files, move back oe level up, remove the `"my_directory"` and its contents, and finally list the files in the current directory again.

Step 1: Open a file named navigating-linux-filesystem.sh

Step 2: paste the code block below into your file.

```
#!/bin/bash

# Display current directory
echo "Current directory: $PWD"

# Create a new directory
echo "Creating a new directory..."
mkdir my_directory
echo "New directory created."

# Change to the new directory
echo "Changing to the new directory..."
cd my_directory
echo "Current directory: $PWD"

# Create some files
echo "Creating files..."
touch file1.txt
touch file2.txt
echo "Files created."

# List the files in the current directory
echo "Files in the current directory:"
ls

# Move one level up
echo "Moving one level up..."
cd ..
echo "Current directory: $PWD"

# Remove the new directory and its contents
echo "Removing the new directory..."
rm -rf my_directory
echo "Directory removed."

# List the files in the current directory again
echo "Files in the current directory:"
ls

```

Step 3: Run the command `sudo chmod +x navigating-linux-filesystem.sh` to set execute permission on the file

Step 4: Run your script using the command `./navigating-linux-filesystem.sh`

Below is the expected output in the terminal:

![images](images/Screenshot_16.png)

## File Operations and Sorting

We will be writing a script that focuses on File Operations and Sorting.

This script creates three files `file1.txt, file2.txt, file3.txt`, displays the files in their current order. sorts them alphabetically, saves the sorted files in `sorted_files.txt`, displays the sorted files, removes the originalfiles, renames the sorted file to `sorted_files_sorted_alphabetically.txt` and finally displays the contents of the sorted file.

Step 1: Create a file `touch sorting.sh`

Step 2: Copy and paste the code block below into the file:

```
#!/bin/bash

# Create three files
echo "Creating files..."
echo "This is file3." > file3.txt
echo "This is file1." > file1.txt
echo "This is file2." > file2.txt
echo "Files created."

# Display the files in their current order
echo "Files in their current order:"
ls

# Sort the files alphabetically
echo "Sorting files alphabetically..."
ls | sort > sorted_files.txt
echo "Files sorted."

# Display the sorted files
echo "Sorted files:"
cat sorted_files.txt

# Remove the original files
echo "Removing original files..."
rm file1.txt file2.txt file3.txt
echo "Original files removed."

# Rename the sorted file to a more descriptive name
echo "Renaming sorted file..."
mv sorted_files.txt sorted_files_sorted_alphabetically.txt
echo "File renamed."

# Display the final sorted file
echo "Final sorted file:"
cat sorted_files_sorted_alphabetically.txt

```

Step 3: Set the execute permission `sudo chmod +x sorting.sh`

Step 4: Run your script using `./sorting.sh`


![images](images/Screenshot_17.png)


![images](images/Screenshot_18.png)

### Working with Numbers and Calculations

This script defines two variables num1 and num2 with numeric values, performs basic arithmetic operations(addition, subtraction, multiplication,division and modulus), and displays the results. It also performs more complex calculations such as raising num1 to the pwer of 2 and calculating the square root of num2, amd displays thos results as well.

Step 1: create a new file `tocuh calculations.sh`

Step 2: Copy and paste the code below:

```
#!/bin/bash

# Define two variables with numeric values
num1=10
num2=5

# Perform basic arithmetic operations
sum=$((num1 + num2))
difference=$((num1 - num2))
product=$((num1 * num2))
quotient=$((num1 / num2))
remainder=$((num1 % num2))

# Display the results
echo "Number 1: $num1"
echo "Number 2: $num2"
echo "Sum: $sum"
echo "Difference: $difference"
echo "Product: $product"
echo "Quotient: $quotient"
echo "Remainder: $remainder"

# Perform some more complex calculations
power_of_2=$((num1 ** 2))
square_root=$(echo "sqrt($num2)" | bc)

# Display the results
echo "Number 1 raised to the power of 2: $power_of_2"
echo "Square root of number 2: $square_root"

```

Step 3: Set the execute permission `sudo chmod +x calculations.sh`

Step 4: Run your script using `./calculations.sh`

![images](images/Screenshot_20.png)

## File Backup and Timestamping

This shell script focuses on file backup and timestamp.

This script defines the source directory and backup directory paths. It then creates a timestamp appended to its name. This script then copies all files from the source directory to the backup directory using the cp command with the `-r` option for recursive copying. Finally, it displays a message indicating the completion of the backup process and shows the path of the backup directory with the timestamp.

Step 1: Create a file `touch backup.sh`

Step 2: Copy and paste the code bock belwo into the file.

```
#!/bin/bash

# Define the source directory and backup directory
source_dir="/path/to/source_directory"
backup_dir="/path/to/backup_directory"

# Create a timestamp with the current date and time
timestamp=$(date +"%Y%m%d%H%M%S")

# Create a backup directory with the timestamp
backup_dir_with_timestamp="$backup_dir/backup_$timestamp"

# Create the backup directory
mkdir -p "$backup_dir_with_timestamp"

# Copy all files from the source directory to the backup directory
cp -r "$source_dir"/* "$backup_dir_with_timestamp"

# Display a message indicating the backup process is complete
echo "Backup completed. Files copied to: $backup_dir_with_timestamp"

```

Step 3: Set execute permission `sudo chmod +x backup.sh`

Step 4: Run your script `./backup.sh`

![images](images/Screenshot_21.png)


# THE END !!!