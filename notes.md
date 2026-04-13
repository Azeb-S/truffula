# Truffula Notes

As part of Wave 0, please fill out notes for each of the below files. They are in the order I recommend you go through them. A few bullet points for each file is enough. You don't need to have a perfect understanding of everything, but you should work to gain an idea of how the project is structured and what you'll need to implement. Note that there are programming techniques used here that we have not covered in class! You will need to do some light research around things like enums and and `java.io.File`.

PLEASE MAKE FREQUENT COMMITS AS YOU FILL OUT THIS FILE.

## App.java

-main entery point of the program have main method (it Parses input, setup objects, start the program)
-it takes command-line arguments(args) as input
-it prints a directory tree structure
-(-h) show hidden files(Default is false)(-nc) disable color(Default coloer is ON)
-default behavore(color On, hidden OFF)
-a sirectiry path is required(absolute or relative) program will show error is the phath is invalid
-hidden files statrting with(.)
-Responsiblity of Main method:
-Create a TruffulaOptions object using args
-Create a truffulaPrinter using Sysytem.out
-Call printTree() to display the directory
1 ['-nc', '-h', '/path/to/directory']
→ Don't use color, do show hidden files
2 ['-h', '-nc', '/path/to/directory']
→ Don't use color, do show hidden files (order of flags is ignored).
3 ['/path/to/directory']
→ Use color, don't show hidden files.

## ConsoleColor.java

-It defines an enum calles ConsoleColor
-enum(use to define a fixed set of values allwed nothing else)
-It represents a different text colors fro console output
-ITs purpose is to use color text in the terminal
-How it works is each color has an ANSI escape code(a special string RED-> prints red text etc)
-RESET is used to return text to normal color
-private final String code (Stores the ANSI code for each color)
-Constructor (Assigns the ANSI code to each enum value)
-Method getCode() -> return ANSI code as string
-Method toSTring() -> Returs the ANSI code and allows using colors directly in print statement
-this file use for styling output not coltrol logic control the output look

## ColorPrinter.java / ColorPrinterTest.java

-This class use to print colored text to the console it uses ConsoleColor for colors and PrintStream like system.out
-it handesl output formatting
-It controles how text is printed (color + output)
-currentColor : stores the current color being used
-printStream: where output is sent (System.out)
-Methods
-SetCurrentColor(ConsoleColor color) -> chnag ethe color for duture prints
-getCurrentColor() -> return current color
-printli(String message)->Prints message + newline, Reset color after printing
-print(String message) -> prints without newline, Reset color after printing
-Overloaded version with boolean reset -> Decide if to reset color or keep it
-constructor Deafult color is white can alos set cutom color
-TruffulaPrinterTest.java Notes
-Junit test class build test directory structure to run the test
-helper methods
-isWindows()-> Detects if OS is windows
-createHiddenFile()->Creates hiddenfiles works on windows and unix
-testPrintTree_ExactOutput_WithCustomPrintStream()
-Creates folder structure use TruffulaOptions (config)and TruffulaPrinter (main logic)

## TruffulaOptions.java / TruffulaOptionsTest.java

-this class stores the Settings/option for printing the durectory tree
-it decides => What forlder to print => Whether to show hidden files => Where to use color
-Root => starting directory
-showHidden => true(include hidden files) false(skip hidden files)
-useColor => true(colored output) false(Print everything in white)
-Getter Methods
-getRoot()=> returns the root folder
-isShowHidden() => return whether hidden files should be shown
-isUseColor() => return where color should be used
-toString() => Gives a readable text version of the object
-TruffulaOptions(String[] args) => this constructor that muct parse command-line arguments
-TruffulaOptions(File root, boolean showHidden, boolean useColor)=> Let's code directly create options without parsing args
-TruffulaOptionsTest.java Notes
-junit test, test TruffulaOptions constructor that uses String[] args
-it checks getRoot()=> should match the directory path
-isShowHidden() => should be true becouse of -h
-isUseColor()=>should be false becouse of -nc

## TruffulaPrinter.java / TruffulaPrinterTest.java

## AlphabeticalFileSorter.java
