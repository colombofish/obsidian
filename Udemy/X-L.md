**Formatting & short-cuts**
Ctrl Home - to go to top left cell; Ctrl + Down Arrow - to go to the bottom data cell. 
Shift + Space - select row; Ctrl + Space - select column.
Ctrl + Backspace - show active cell. 
Ctrl + A - to select the data set area when I am in one of the cells. 
Alt Enter - to add a newline within a cell
quick double click on Format Painter - to apply same formatting on multiple cells multiple times.
Ctrl + ; - to enter the current date; Ctrl + : - to enter current time
Ctrl + 1 - format cells dialog box
Alt+= to invoke the Autosum.
F4 - does the last format action issued. 
To move a row/column to another location highlight/select the row/column, then hold Shift key and drag it to the correct location. 

**Functions**
AutoSum (Alt + =) - an intuitive f-n. Make sure to un/check the flash or auto formatting options if needed.
Alternatively, if I want to copy the formula w-out formatting the cells, highlight the cells area where the formula to be copied, press F2, then press Ctrl + Enter. 

**Speak cells**
Available options: Start; Stop speaking cells; By rows; By columns; on Enter etc. 

**Flash Fill**
Ctrl + e; - Flash fill [sometimes, when we type the first cell, then the second cell, Flash fill recognizes the pattern and suggest for the rest of the cells]
*==Note==:* Days, Weekdays, Months etc. are set by default in a list. That's why the autofill/Flash fill is able to fill accordingly. If we want to enhance the list with Custom Fill, Go to File / Options / Advanced / Edit Custom Lists. 

Notes & Comments option could be used for description and commenting the cells accordingly, where Comments can be used to reply by other co-workers. Look at the options in Review menu to display or hide these options. 

To find excel Formulas, Constants etc. use **Go To Special** function.

**Data Validation**
Data validation in cells can be used when we create a template, which will be filled by others or for reports. To enable this, select the cells/range of cells then menu Data -> Data Validation (select appropriate icon), define the parameters accordingly. Or if you wanna copy the Data Validation formula, use copy Special and select Data Validation. 
==*Note*==: For a list you can use comma separated values if it is fixed or make a cell range reference if you wanna dynamic options, which can be changed or add more items to the list. 

To make the Date validation to be less than today's date, use the f-n '=today()'.

**Tooltips or screen tips**
This you find from Data Validation option, where you select the Input message. 

***Grouping col/rows***
Instead of hiding col/rows, we can group them and click on the '-' sign to hide it. This way, the worksheet will display a '+' sign if need to unhide it. 

**Protecting workbook/sheet**
To protect the file - go to File -> Save As -> More options -> Tools -> General Options ....
Review menu has Protect Workbook, Protect Sheet options.
Protect Workbook - enables protecting the structure of the workbook, so that workbook's sheets cannot be deleted or moved. 
Protect Sheet - allows to not to modify the cells unless they are unlocked. To unlock the cells, go to Format cells (Ctrl + 1), then under Protection tab, untick the 'Locked' button.
==Note==: Home -> Find icon -> Go To Special (this allows to find the formulas or other info from the cell when they are selected). 

**Calculations, Order of Precedence**
(), Negation ex: -1*2=-2, %, Exponentiation ex: 2^2 *2=8, Multiplication/Division, Addition/Subtraction, Comparison ex: 1+2 = 1+2 = True

When you do calculation in Excel with True/False, Excel calculates as 1/0. So, True + True = 2.

If I want to show the formula used in a separate cell use '=FORMULATEXT(cell#)'.

*Essential Rules when working with Formulas*:
1. Do not put constant values within formula. Ex: VAT of 20% or other values. Exceptions could be like 24 Hour a day, 7 days per week etc. 
2. Formulas in a range should be consistent. Do not change in middle of table to have different formula. If you expect error otherwise, make some if-error f-ns to cover those scenarios. 

**Absolute and Relative Cell referencing** - The '$' sign in front of row/column determines if the row/col is fixed or not. Use 'F4' to toggle. 

*A cell typically has it's address. However, this can be changed by giving some logical names when required. Ex name: Discount if a cell contains a percentage or a value, which can be used as discount.*
==Note== Above Discount cell becomes global, which can be used to do any calculations within other sheets of the same workbook. Refer to the Name Manager, which is in the Formula menu. 
Similar to Discount cell mentioned above, we can also give a name for a range. Ex: pricelist, and use f-ns such as =average(pricelist) to do math. operations. 

**Referencing other workbooks or sheets** 
Simply insert the relevant cell in another sheet within your formula. Make sure to make it absolute or partially relative if you want to. If I want to reference to another workbook, then open that workbook too to reference it. 

To **Combine values from 2 or more cells**, use '&'. Ex: '=A1&"-"B1', where cell A1 contains "Scarf" and B1 contains "W". So the end result will be "Scarf-W". 

**Functions**
Count() - counts for the #of cells which has numbers. (Date is also a number).
Counta(), counts the #of cells, which are not empty, so includes numbers and texts.
Countblank(), counts the #of empty cells. So, if I wanna check only the #of texts in a large file/columns/cells,  '=CountA(:) - Count(:)'

The F-n library is within Formulas. 
Ex: a) =COUNTIF(B5:B35,"missing"), 
b) =COUNTIFS(D5:D35,">"&H16, D5:D35, "<"&H17) etc. 
==Note== the ">" is written as text within "" and the cell is concatenated using &. 
COUNTIF() does similar, but with only one criteria it can have. 

SUMIF(range, criteria, sum_range), where sum_range are the actual cells to sum. 
SUMIFS(sum_range, criteria_range1, criteria1, criteria_range2, criteria2)
AVERAGEIFS(average_range, criteria_range1, criteria1, criteria_range2, criteria2)
Ex: AVERAGEIFS(D5:D167, A5:A167, H16, B5:B167, H17, D5:D167, ">"&0). Note the last range is same as the average_range to exclude the 0 values to get the average. 
MAX(range); MIN(range); MAXIFS(max_range, criteria_range1, criteria1...)
ROUND(number, 0) - rounds to integer ex: 4852
ROUND(number, 1) - rounds to 1 decimal ex: 4852.40
ROUND(number, -1) - rounds to multiples of 10 ex: 4850.00 (base 4852.3654)
ROUND(number, -2) - rounds to multiples of 100 ex: 4900.00 (base 4852.3654)

**Date f-n**
ex: cell A8 contains 01/09/2019 => Year(A8) -> 2019; Month(A8) -> 09; Day(A8) -> 1;
Date(year, month, day) -> this makes the date from year, month and day. 
Days(today(), A8) -> gives the #of days elapsed from the date in A8, 
EOMONTH(A8,0) -> gives the last day of the month in A8; If you change 0 to -1, it will give the last day of previous month, +1 then next month's last day etc.
In addition to that, we can do arithmetic operation to dates, like 25/2/2024 + 10 = 06/03/2024; 

Today() - gives today's date, where Now() - gives today's date with time. Note, these are dynamic data, which will change auto if the file is open on other days. 

Time - is calculated in numbers too. Note, 24 hours is calculated as a fraction from the elapsed hours. Ex: 6:00AM will have the value (if you change to the General view instead of Date view) 0.25 (6/24), and 6PM will be as 0.75 (18/24). With this analogy in mind, worked hours in a timesheet can be calculated. 

**Error handling**
IFError(value, value_if_error); value - to have the normal result, value_if_error - the value which will be put into the cell if an error occurs. So, IFError() is a common evaluation without specifying an error. Ex: IFERROR((B5-C5)/C5, "") - Upon an exception, an "" will be put to the cell. 

IF(logical_test, value_if_true, value_if_false). Note we can also nest another if within the IF() condition. 
ex1: IF(D5>0, C5/D5-1, "NA"); ex2: IF(ISTEXT(B32),"", IF(B32>$C$30, "Yes", "No"))

**Some other used f-ns**
ISTEXT(), ISNUMBER(), ISBLANK(), NOT(ISNUMBER(A8)), AND(), OR(), VLOOKUP()

**Vlookup**(Lookup_value, Table_array, Col_index_num, Range_Lookup) - Looks for a value in the leftmost column of a table, and returns a value in the same row from a column that you specify (by numbering from 1, 2, 3, etc.). Note, Range_Lookup the last argument TRUE (if you r looking for an approximate value, if so, the table should be sorted in ascending order), or FALSE for exact value. 

**Data Cleaning and Management (Sorting, Filtering & Replacing Data)**
For Sorting, make sure to have a table where you don't have empty rows/cols in between. Then right-click (or use the sort icon) to sort by ascending, descending or custom sort if you want to sort using more than one column. By default, we can sort ascending or descending for the numbers or texts. However, if we wanna have a custom sort, we can add under the Custom Sort option. Ex: if a Division column contains values such as Utility, Productivity, Game then add these in the required order to sort it. 

==Note== if for any reason, I should have the original table format in the future, then add an additional index column to the left, then play around sorting, so we can always sort according to the index to return to the original table structure. 

**Subtotal to sorted data**
Data -> Outline -> Subtotal; you can start from the level from the left, then add other levels. If you wanna have multiple subtotals within the same table, make sure to un-tick the Replace... option.
Use the page-break option, if I wanna to print each division separately. 

**Filtering Data**
Short-cut keys to activate Filter is 'Ctrl + Shift + L' or just click on Filter icon when you're within the said table. Make sure to have headings to the columns.
Most of the options are logical. Just right-click and see the options. We can also filter by colors if colors are applied to the cells. 
We can also use wild-cards filters, to include the texts what we want to look in the table (Text Filters). 

**Deleting blank or Empty rows**
If a dataset has empty rows or cells, then highlight the area, then Go to Special, select Blanks. This will select all empty cells. From here, we can right-click and delete all rows, having blank cells. If we want to delete rows only, then
1. enable filter for the whole area, then select blank from each column until you get the empty rows, right-mouse-click and delete the empty rows. Or
2. Make a header ex: Flag in the next empty column. Apply the formula **CountBlank(left_cells_range)**. Enable filter to get the #of cells empty only, and delete accordingly.

**Fill Empty Cells in one Go**
Lets assume the cell above to the blank cell has the correct value, which can be copied into the blank cell below. To do this dynamically, 
1. Select the area, GoTo Special -> Blank [this will select all blank cells], 
2. Go to the formula bar and type '=Above-Cell-Address', then press Ctrl + Enter
That should fill the blank cells. If we wanna insert '0' inside the empty cells, then similarly select the blank cells as in point #1 above, then Go to Formula bar '=0', then press Ctrl + Enter. 

**Remove duplicates**
Data -> Remove Duplicates option allows to remove the duplicates from the data set. But, make sure to have a backup of the data if we ever want to return to the original data.

**Tables**
When you create/structure/design/make tables, you get an additional "Table Design" menu, where you can give a name to the table (without space) and many other f-ns in it, such as "Total Row". This row can be adjusted with sum, average, min, max etc. 

**Formatting**
If you want to make a text to look like heading in between columns, you can select the text column along with remaining empty columns. Then invoke the Format Cell dialog box (Ctrl + 1), under Text alignment select "Centre Across Selection". The Merge & Centre also does the same formatting. However, this can cause issues if we want to select the total column for using formula or calculation. 

**Justify trick**
If you have a lengthy text in XL, and want to distribute it among multiple lines, then first select the number of rows the text to be put, next go to Home -> Fill -> Justify. That's it. This saves our usual manual typing into multiple rows. 

**Conditional Formatting**
See the options, they are all intuitional. To apply cond. formatting select the cells, then select the "Cond. Formatting" option. Check the available options or select "Manage Rules...". Ex1: select "Conditional Formatting" > "Highlight Cells Rules" > "Greater Than..." specify a value and select the formatting options for the cell. 
Ex2: instead of "Greater Than...", you can try "Between..." option and provide two values, such as two dates. 
*Note1: There is no restriction that only one rule can be applied for the selected cells. So, multiple rules can be applied.
Note2: when you copy the cells, which has Cond. Format., it will also carry the formatting*

