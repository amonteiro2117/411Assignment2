# 411Assignment2

Partners: Alex Monterieo, Cody Chu

Collabraters: TA Eric, TA Sam
Approximately 12 hours were spent completing this assignment 

PART A: IMPLEMENTATION
	1	Vec abstraction supports two-dimensional arrays
	2	Array2 has width and a height instead of a length
	3	Elements of Array2 are identified by two indices - the column or x index measures the distance between the element and the left edge of the array, while the row or y index measures the distance between the element and the top row of the array
	4	Row-major and column-major iteration are supported with functions named iter_row_major and iter_col_major,
	5	Constructors such as from_row_major, from_col_major are present, and a blank slate constructor that allows for a single value to be copied to each element
	6	Function present that allows access to an element by a pair of coordinates


PART B: IMPLEMENTATION
	1	Read a portable graymap file representing a sudoku puzzle (9x9)
	2	Check if the puzzle is solved, i.e. it meets the following conditions:
	1	Maximum pixel intensity is 9
	2	No pixel has zero intensity
	3	Each row has unique intensities
	4	Each column has unique intensities
	5	Each 3x3 submap has unique intensities
	3	If the puzzle is solved, call exit(0), else call exit(1)
	4	Handle invalid input by terminating with a checked run-time error
	5	Use the csc411_image crate for reading the input file
	6	Read the input as a GrayImage with pixels, width, height, and denominator fields


Critical parts of design checklist below

Interfaces and design checklists
Design checklists (based on design-adt.pdf on EdStem) for the Array2 Abstraction
 

1. **What problem are you trying to solve?**
   - The problem is to determine whether a given grayscale image represents a valid Sudoku puzzle. This involves checking if the image dimensions are 9x9, if all pixel intensities are within the range 1 to 9, and if there are no duplicates in rows, columns, or subgrids.

2. **What example inputs will help illuminate the problem?**
   - Example inputs include grayscale images representing Sudoku puzzles of various configurations. These images should have dimensions of 9x9 and contain pixel intensities representing the numbers 1 to 9.

3. **What example outputs go with those example inputs?**
   - The output would be a boolean value indicating whether the input image represents a valid Sudoku puzzle. `true` would mean the puzzle is valid, while `false` would indicate it's not.

4. **Into what steps or subproblems can you break down the problem?**
   - Checking image dimensions.
   - Verifying pixel intensity range.
   - Ensuring no duplicates in rows, columns, and subgrids.

5. **What data are in each subproblem?**
   - Image dimensions for the first subproblem.
   - Pixel intensities for the second subproblem.
   - Pixel values for each row, column, and subgrid for the third subproblem.

6. **What code or algorithms go with that data?**
   - For the first subproblem, comparing image dimensions with 9x9.
   - For the second subproblem, checking pixel intensity range.
   - For the third subproblem, iterating over rows, columns, and subgrids to detect duplicates.

7. **What abstractions will you use to help solve the problem?**
   - Abstractions include a function to read the grayscale image and a function to validate the Sudoku puzzle.

8. **If you have to create new abstractions, what are their design checklists?**
   - Ensure the abstractions are reusable, easy to use, and efficient.

9. **What invariant properties should hold during the solution of the problem?**
   - The image dimensions should remain 9x9.
   - Pixel intensities should be within the range 1 to 9.
   - Each row, column, and subgrid should have unique pixel intensities.

10. **What algorithms might help solve the problem?**
    - Iterating algorithms to traverse rows, columns, and subgrids.
    - Range-checking algorithms to verify pixel intensities.

11. **What are the major components of your program, and what are their interfaces?**
    - Major components include the `read` function to read the image and the `is_valid_sudoku` function to validate the Sudoku puzzle. The interface involves passing the grayscale image to the `is_valid_sudoku` function.

12. **How do the components in your program interact?**
    - The `main` function reads the input image and passes it to the `is_valid_sudoku` function. The `is_valid_sudoku` function checks the validity of the Sudoku puzzle based on the given criteria and returns a boolean value indicating the result.

13. **Test cases to ensure that the program works correctly could include:**
    - An image with a valid Sudoku puzzle.
    - An image with invalid dimensions.
    - An image with invalid pixel intensity range.
    - An image with duplicate pixel intensities in rows, columns, or subgrids.
