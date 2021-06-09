# MATLAB

## Table of Contents

* [Introduction to MATLAB and comparison with other languages](#Introduction-to-MATLAB-and-comparison-with-other-languages)
* [MATLAB IDE, documentation, and help](#MATLAB-IDE-documentation-and-help)
* [Variables, special variables](#Variables-special-variables)
* [Matrices](#Matrices)
* [Basic mathematical operations](#Basic-mathematical-operations)
* [2D plotting](#2D-plotting)
* [Importing and exporting datasets](#Importing-and-exporting-datasets)
* [Writing functions](#Writing-functions)

## Introduction to MATLAB and comparison with other languages

MATLAB (MATrix LABoratory) is a proprietary programming language and desktop computing environment.

## MATLAB IDE, documentation, and help
### Objectives

- Open MATLAB, set the working directory, and understand the layout of the MATLAB IDE.
- Open MATLAB documentation and help.

### Tutorial steps

1. Open the MATLAB application.
2. Update MATLAB display preferences.
3. Change the working directory to the `2021-reu-matlab-git` folder.
4. Type `doc` in the command window to view the MATLAB documentation.
5. Type `help help` in the command window to view help for `help`.
6. Type `doc help` in the command window to view the documentation for `help`.
7. Type `demo` in the command window to view MATLAB examples.
8. Type `lookfor mean` to search the MATLAB help for the keyword `mean`.

## Variables, special variables
### Objectives

- Learn how to use the command window for calculations.
- Learn how to define variables and inspect the variable type.

### Tutorial steps
1. Use the command window as a calculator:

    ```
    3 * 5
    ```

2. Assign a value to a variable using the equals sign:

    ```
    height = 3
    width = 5
    ```

> **NOTE**: We can use one of MATLAB's reserved characters `;` to suppress the
> output of the command: `height = 3;`.

3. View the type of the variables:

    `class(height)`

4. Assign an array of characters to a variable using single quotes:

    ```
    today = 'Wednesday'
    class(today)
    ```

5. Assign a string to a variable using double quotes:

    ```
    tomorrow = "Thursday"
    class(tomorrow)
    ```

6. Inspect the value of a special variable in MATLAB:

    ```
    disp(pi)
    format long
    disp(pi)
    ```

7. Clear a specific variable:

    `clear height`

8. Clear all variables:

    `clearvars`

9. Clear the command window:

    `clc`

> **NOTE**: These are only a small subset of the available
> [data types in MATLAB](https://www.mathworks.com/help/matlab/matlab_prog/fundamental-matlab-classes.html).

> **NOTE**: There are restrictions for what can be used as variable names in MATLAB:
> 1. Variable names are case sensitive.
> 2. Variable names must begin with a letter.
> 3. Variable names can be a mix of letters, digits, and underscores.
> 4. Variable names cannot use reserved characters (`% = + . ~ ; :  !  ‘  [ ] ( ) , @  #  $ &  ^`).
> 5. Variable names cannot equal reserved keywords (`iskeyword`).
> 6. Variable names can override special variables (e.g., `pi` and `i`), but this is
>    not recommended.

## Matrices

### Objectives

- Assign row vectors, column vectors, and matrices to variables in MATLAB.
- Use the colon operator to create a numeric vector with a certain range.
- Index values at specific locations in vectors and matrices.

### Tutorial steps

### Creating vectors and arrays

Vectors and matrices store sets of values that share a common type, where a vector is
equivalent to a 1-D array or matrix.

1. Create a row-wise vector (a variable of size 1 x n, where n > 1):

    ```
    row_vector = [9 3 1 1]
    size(row_vector)
    ```

2. Create a column-wise vector (a variable of size n x 1, where n > 1):

    ```
    column_vector = [9; 3; 1; 1]
    size(column_vector)
    ```

3. Create a matrix (a variable of size m x n, where m is the number of rows and n is
   the number of columns):

   ```
   data = [1 2 3; 4 5 6; 7 8 9]
   size(data)
   ```

4. Concatenate two row vectors together to form a matrix:

    ```
    row1 = [1 2 3]
    row2 = [4 5 6]
    data = [row1; row2]
    size(data)
    ```

5. Use the colon operator `:` to create a vector using the `begin:[increment]:end` syntax:

    ```
    long_row = 0:100;
    longer_row = 0:2:500;
    ```

6. Use MATLAB functions to create matrices:

    ```
    zeros_matrix = zeros(3,3);
    ones_matrix = ones(3,3);
    identity_matrix = eye(3);
    ```

### Indexing vectors and arrays

MATLAB uses parentheses to slice or index arrays. The first index in MATLAB is 1 (in
contrast to zero).

1. Retrieve all values from the `data` matrix using colons:

    `data(:,:)`

2. Retrieve the first row from the `data` matrix:

    `data(1,:)`

3. Retrieve the first column from the `data` matrix:

    `data(:,1)`

4. Retrieve the last element in the `long_row` vector:

    `long_row(end)`

5. Retrieve elements 4 to 7 in the `long_row` vector:

    `long_row(4:7)`

6. Use indexing notation to replace values in the `row1` vector:

    ```
    disp(row1)
    row1(2) = 10
    ```

7.  Add an element to `row1`:

    `row1(4) = 20`

8. Create a new vector array with values twice those in the vector `row1`:

    `row3 = row1 * 2`

9. Create a linear and logarithmic spaced vector:

    ```
    vector_linear = linspace(0,6,4);
    vector_log = logspace(0,2,3);
    ```

10. Delete the last element from the vector `row1`:

    `row1(end) = []`


## Basic mathematical operations

### Objectives

- Apply arithmetic operators to variables and values.
- Apply common simple functions to vectors and matrices.

### Tutorial steps

1. Try each of the following arithmetic operators in the command window:

    ```
    +
    -
    *
    /
    ^
    clc
    up arrow
    ```

2. Test out the order of operations:

    ```
    3 + 4 * 5
    (3 + 4) * 5
    ```

3. Apply arithmetic operators to vectors:

    ```
    row1 = [1 2 3]
    row2 = [4 5 6]
    row1 + row2
    ```

4. Apply matrix algebra to variables:

    ```
    row_vector * column_vector
    data_s = [0 1; -2 1]
    data_s * eye(2)
    data_s * inv(data_s)

    ```

5. Apply element-wise operations on matrices:

    ```
    row_vector * column_vector
    data_s .* eye(2)
    data_s.^2
    ```

6. Transpose the `data` matrix:

    ```
    disp(data)
    data'
    ```

7. Find the mean, median, and standard deviation of the `long_row` vector:

    ```
    mean(long_row)
    median(long_row)
    std(long_row)
    ```

8. Find the mean of the `data_s` matrix:

    ```
    mean(data_s)    % type help mean to understand this behavior
    data_s(:)       % quick method to unwrap data_s
    mean(data_s(:)) % find the mean of the elements in data_s
    ```


## 2D plotting

### Objectives

- Write a MATLAB script to create simple 2D plots.

### Tutorial steps

1. Open the MATLAB script plotting_intro.m:

    ```
    edit plotting_intro.m
    ```

2. Create a vector array from 0 to 3 pi, with an increment pi/100, assigned to
   the variable `x`.

3. Create a vector array that equals `cos(x)`, assigned to the variable `y`.

4. Create a line plot using the `plot()` function:

    `plot(x,y);`

5. Add a title to the line plot:

    `title('cos(x) vs. x');`

6. Add axis labels to the line plot:

    ```
    xlabel('x');
    ylabel('cos(x)');
    ```

7. View the documentation for plot:

    `doc plot`

8. Recreate the line graph using a dashed line:

    ```
    plot(x,y,'--');
    ```

9. Plot `cos(x)` and `sin(x)` on the same graph using the `hold on` command:

    ```
    plot(x,y);
    hold on
    plot(x,sin(x));
    ```

10. Create a legend for the two lines:

    ```
    legend('cos(x)','(sin(x)');
    ```

11. Close the current figure:

    ```
    close gcf % replace with close all to close all figures
    ```

## Importing and exporting datasets

### Objectives

- Import data from files.
- Save data to files.

### Tutorial steps

### Saving workspace variables

1. Use the `save()` function to save all current workspace variables to a `.mat` file:

    ```
    save('variables.mat');
    ```

2. Use the `save()` function to save only some of the variables to a `.mat` file:

    ```
    save('variables.mat','data','data_s');
    ```

3. Write the variable `data` to a csv using the `writematrix()` function:

    ```
    writematrix(data,'data.csv');
    ```

> **NOTE**: Older versions of MATLAB may require using (`csvwrite`)

4. Write the variable `data` to a tab delimited ascii file using the `writematrix()`
   function:

   ```
   writematrix(data,'data.dat','Delimiter','\t');
   ```

> **NOTE**: Older versions of MATLAB may require using (`writematrix`)

5. Write the variable `data` to a Microsoft Excel file:

    ```
    writematrix(data,'data.xlsx');
    ```

> **NOTE**: Older versions of MATLAB may require using (`xlswrite`)


### Loading data

1. Clear all workspace variables

    `clear all`

2. Load the previously saved data from the `.mat` file:

    ```
    load('variables.mat')
    ```

3. Load the previously saved data from the `.csv` file:

    ```
    data1 = readmatrix('data.csv');
    ```

> **NOTE**: Older versions of MATLAB may require using (`csvread`).

4. Load the previously saved data from the `.dat` file:

    ```
    data2 = readmatrix('data.dat','Delimiter','\t');
    ```

> **NOTE**: Older versions of MATLAB may require using (`dlmread`).

5. Load the previously saved data from the `.xslx` file:

    ```
    data3 = readmatrix('data.xlsx');
    table = readtable('data.xlsx');
    ```

## Writing functions

### Objectives

- Create a simple function in MATLAB to convert from feet to meters

### Tutorial steps

1. Click on new function in MATLAB.
2. Update the name of the function to ft2m.
3. Update the number of input variables to 1.
4. Update the number of output variables to 1.
5. Write code that converts from ft to m (1m = 1/3.2808 ft)
6. Call the function to convert a value from ft to m.
7. Call the function on an array of values.
