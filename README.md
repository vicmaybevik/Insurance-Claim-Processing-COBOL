#user info
    Hello! My name is Victor Taiwo, i am Northern Illinois University student studying computer science with a focus on mainframe programming. projects on cobol and mainframe are important to me because of the versatility and consolidation benefits a mainframe system offers, it's also extremely efficient and adapts to new technology pretty well. My skills are currrently intermidate but will improve over time. Thanks for checking my code.


#Project overview
    Insurance companies face a massive issue in maintaining records and running their billing systems efficiently. They cater to thousands (sometimes even lakhs) of customers and so, they require an efficient system to manage their records, bills, etc. One of the areas where insurance companies feel the need for an efficient system the most is processing claims. So, in this project, you’d build a mainframe solution for processing claims for an insurance company. The system would take input, validate, filter, and adjudicate the claims. Then it’ll produce reports from NH/ME/CT. 

#Main tasks
    Perform technical reviews of the system
    Prepare a detailed design for your proposed system and create its specification documentation
    Prepare COBOL standards document, which explains the required changes in code

#setup instructions 
    Choose your operating system in which you will run the program
    Download the GnuCOBOL installer:Go to https://sourceforge.net/projects/gnucobol/files/gnucobol/ 
    Click on the most recent version folder
    Download the .exe file (e.g., "gnucobol-3.1.2-64bit-MinGW-setup.exe")
    Verify the installation: Open Command Prompt (you can search for "cmd" in the Start menu)
    Type cobc --version and press Enter
    If you see version information, the installation was successful.
    "this is a simplified COBOL environment for learning and small-scale development. It doesn't replicate a full mainframe environment with CICS, JCL, and DB2 that you'd use in a professional setting."
    As a Mac user terminal, geany and vs code were very helpful and effective.

#Cobol code
    Create a new COBOL file: 
    Open your preferred text editor(Eg virtual studio code VS code, Sublime text, atom.)
    Understand and know the project requirements for this code, Read through the project description carefully. try understanding the main components: input processing, validation, filtering, adjudication, and reporting.
    articles that helped me with this. [https://www.upgrad.com/blogmainframe-projects-ideas-topics-for-beginners/], [https://1000projects.org/projects/mainframe-projects], [https://brew.sh/], [https://chatgpt.com/].
    Identify the specific states involved (NH/ME/CT)
    understand the system analysis, which includes creating a document that states the current issues in the insurance industry, list the goal of the new system that you want to implement.
    Begin with technical aspects, which can be documenting and researching on findings.
    Create a detailed design which can be drawing a flowchart of the entire claim processing system. i was able to do this easily with the help of this website. [https://app.diagrams.net/]
    Design the data structures which willbe implemented in your code, If youre a fellow NIU computer student you should be some what familiar with this topic.
    Plan the code structure (main program and subprograms)
    Here's a basic structure to start with:

        IDENTIFICATION DIVISION. //This names your program
        PROGRAM-ID. CLAIM-PROCESS. 
        ENVIRONMENT DIVISION. //This describes the program's environment, including file definitions.
        INPUT-OUTPUT SECTION.
        FILE-CONTROL.
            SELECT CLAIM-FILE ASSIGN TO CLAIMIN
                ORGANIZATION IS LINE SEQUENTIAL.
        DATA DIVISION. //This defines the structure of your data
        FILE SECTION. //Describes the structure of your input and output files
        FD CLAIM-FILE.
        01 CLAIM-RECORD.
            05 CLAIM-ID              PIC X(10).
            05 CUSTOMER-NAME         PIC X(30).
            05 CLAIM-AMOUNT          PIC 9(7)V99.
            05 CLAIM-STATE           PIC X(2).
        WORKING-STORAGE SECTION.
        01 WS-EOF                    PIC X VALUE 'N'.
        PROCEDURE DIVISION.
        MAIN-PROCEDURE. //The main flow of your program
            PERFORM 100-INITIALIZE  //Opens the input and output files
            PERFORM 200-PROCESS-CLAIMS UNTIL WS-EOF = 'Y' //Reads claims and processes them until the end of the file.
            PERFORM 300-FINALIZE //Placeholder for report generation (400 does the cleanup and ends the file)
            STOP RUN.
        100-INITIALIZE.
            OPEN INPUT CLAIM-FILE.
        200-PROCESS-CLAIMS.
            READ CLAIM-FILE
                AT END
                    MOVE 'Y' TO WS-EOF
                NOT AT END
                    PERFORM 250-VALIDATE-CLAIM
                    PERFORM 260-ADJUDICATE-CLAIM
                    PERFORM 270-GENERATE-REPORT.
        250-VALIDATE-CLAIM.
            * Add validation logic here
        260-ADJUDICATE-CLAIM.
            * Add adjudication logic here
        270-GENERATE-REPORT.
            * Add reporting logic here
        300-FINALIZE.
            CLOSE CLAIM-FILE.

    Develop COBOL standards
    create documentation with various tests
    also utilize JCL to compile and run your GNUcobol code
    develop a system test plan
    track issues you encountered along the way (optional)
    project organization
    Research if you're having additional issues.

#Key learnings or challenges overcome
    Syntax errors in 210-VALIDATE-CLAIM and 220-ADJUDICATE-CLAIM paragraphs were hard to get around.
     All claims were being rejected it was fixed by reworking on the validation logic and the format of  input data
     No claims are being counted for any state which was fixed by makibg sure the code and the claims.dat file match with terms of input data.