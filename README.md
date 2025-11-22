Java Installation on Windows
Step-by-Step Installation Guide
Step 1: Download JDK
Visit Oracle JDK Downloads or OpenJDK
Select Windows x64 Installer for your version (Java 11+ recommended)
Download the .exe file
Step 2: Install JDK
Run the downloaded installer as Administrator
Follow installation wizard (accept default paths)
Installation typically goes to C:\Program Files\Java\jdk-[version]
Step 3: Set Environment Variables
Open System Properties → Advanced → Environment Variables
Create JAVA_HOME variable:
Variable name: JAVA_HOME
Variable value: C:\Program Files\Java\jdk-[version]
Update PATH variable:
Add %JAVA_HOME%\bin to the PATH
Step 4: Verify Installation
Open Command Prompt and run:

java -version
javac -version
Eclipse IDE Setup
Installation Steps
Download Eclipse IDE for Java Developers from eclipse.org
Extract the downloaded archive to desired location
Launch Eclipse and select workspace location
Creating New Java Project
File → New → Java Project
Project name: CCRM
Use default JRE (should match your installed JDK)
Create src folder structure with packages



How to Run
Prerequisites
JDK Version: Java 11 or higher
IDE: Eclipse IDE for Java Developers (recommended)
Operating System: Windows 10/11 (installation guide provided)

Evolution of Java
Java Timeline - Key Milestones
1991: Java project started at Sun Microsystems (originally named "Oak")
1995: Java 1.0 released - "Write Once, Run Anywhere" philosophy
1997: Java 1.1 - Inner classes, JavaBeans, JDBC introduced
1998: Java 2 (J2SE 1.2) - Collections framework, Swing GUI toolkit
2000: J2SE 1.3 - HotSpot JVM, Java Sound API
2002: J2SE 1.4 - Regular expressions, NIO, XML processing
2004: Java 5 (J2SE 1.5) - Generics, annotations, enums, enhanced for-loop
2006: Java 6 (J2SE 6) - Performance improvements, scripting support
2011: Java 7 - Diamond operator, try-with-resources, NIO.2
2014: Java 8 - Lambda expressions, Stream API, functional interfaces
2017: Java 9 - Module system, JShell, reactive streams
2018: Java 10 - Local variable type inference (var keyword)
2018: Java 11 - LTS release, HTTP client, string methods
2019: Java 12-13 - Switch expressions, text blocks preview
2020: Java 14-15 - Pattern matching, records preview
2021: Java 16-17 - LTS release, sealed classes, pattern matching
2022-2024: Java 18-21 - Virtual threads, pattern matching enhancements

Technical Implementation Mapping
Syllabus Topic	Implementation Location	Description
OOP - Encapsulation	edu.ccrm.domain.*	Private fields with getters/setters in Student, Course classes
OOP - Inheritance	edu.ccrm.domain.Person → Student, Instructor	Abstract Person class extended by concrete classes
OOP - Abstraction	edu.ccrm.domain.Person	Abstract class with abstract methods getRole(), displayInfo()
OOP - Polymorphism	edu.ccrm.service.* interfaces	Persistable interface with multiple implementations
Interfaces	edu.ccrm.service.Persistable	Generic interface with default methods
Enums	edu.ccrm.domain.Grade, Semester	Enums with constructors and fields
Exception Handling	edu.ccrm.exception.*	Custom exceptions: DuplicateEnrollmentException, MaxCreditLimitExceededException
Collections Framework	StudentService, CourseService	HashMap for storage, List for collections
Generics	Persistable<T> interface	Generic interface and method parameters
Lambda Expressions	edu.ccrm.util.Comparators	Student sorting, course filtering predicates
Stream API	TranscriptService.generateReports()	GPA calculations, filtering, data aggregation
Date/Time API	edu.ccrm.domain.Student	LocalDateTime for enrollment dates, timestamps
NIO.2	edu.ccrm.io.ImportExportService	Path, Files APIs for CSV operations
Recursion	edu.ccrm.util.RecursiveUtils	Directory size calculation, file tree traversal
Design Patterns - Singleton	edu.ccrm.config.AppConfig	Thread-safe singleton implementation
Design Patterns - Builder	edu.ccrm.domain.Course.Builder	Builder pattern for Course construction
Nested Classes	Course.Builder (static), TranscriptGenerator.ReportFormatter (inner)	Static nested and inner class examples
Anonymous Classes	MainMenu.createComparator()	Anonymous Comparator implementation
Assertions	Throughout service classes	Invariant checking with assert statements
Package Structure and Architecture
src/edu/ccrm/
├── cli/                           # Command Line Interface
│   ├── MainMenu.java             # Main menu system with switch statements
│   ├── StudentMenuHandler.java   # Student-specific operations
│   └── CourseMenuHandler.java    # Course-specific operations
├── domain/                        # Domain Models
│   ├── Person.java               # Abstract base class
│   ├── Student.java              # Student entity (extends Person)
│   ├── Instructor.java           # Instructor entity (extends Person)
│   ├── Course.java               # Course entity with Builder pattern
│   ├── Enrollment.java           # Enrollment relationship
│   ├── Grade.java                # Grade enum with grade points
│   ├── Semester.java             # Semester enum
│   └── CourseCode.java           # Immutable value object
├── service/                       # Business Logic Layer
│   ├── Persistable.java          # Generic persistence interface
│   ├── StudentService.java       # Student CRUD operations
│   ├── CourseService.java        # Course CRUD operations
│   ├── EnrollmentService.java    # Enrollment business rules
│   └── TranscriptService.java    # GPA calculation, transcript generation
├── io/                            # File Operations
│   ├── ImportExportService.java  # CSV import/export with NIO.2
│   ├── BackupService.java        # Backup operations with timestamping
│   └── CSVParser.java            # CSV parsing utilities
├── util/                          # Utilities
│   ├── Validators.java           # Input validation methods
│   ├── Comparators.java          # Lambda-based comparators
│   └── RecursiveUtils.java       # Recursive file operations
├── config/                        # Configuration
│   ├── AppConfig.java            # Singleton configuration
│   └── DatabaseConfig.java       # Data persistence settings
├── exception/                     # Custom Exceptions
│   ├── DuplicateEnrollmentException.java    # Checked exception
└── CCRMApplication.java           # Main application entry point
Enabling Assertions
Assertions are used throughout the application to verify invariants and preconditions. To enable assertions:

Command Line
# Enable all assertions
java -ea edu.ccrm.CCRMApplication

# Enable for specific package
java -ea:edu.ccrm.domain... edu.ccrm.CCRMApplication

# Enable system assertions
java -esa edu.ccrm.CCRMApplication
Eclipse IDE
Run → Run Configurations
Select your configuration → Arguments tab
In VM arguments, add: -ea
Example Assertion Usage
// In StudentService.java
public void enrollStudent(String studentId, String courseCode) {
    assert studentId != null && !studentId.trim().isEmpty() : "Student ID cannot be null or empty";
    assert courseCode != null && !courseCode.trim().isEmpty() : "Course code cannot be null or empty";

    Student student = findById(studentId);
    assert student != null : "Student must exist before enrollment";

    // Business logic continues...
}
Sample Commands and Usage
Basic Operations
# Start application
java -ea -cp bin edu.ccrm.CCRMApplication

# Menu navigation examples:
# 1. Manage Students
# 2. Manage Courses
# 3. Enrollment Operations
# 4. Grade Management
# 5. Reports and Transcripts
# 6. File Operations
# 7. Backup and Recovery
# 0. Exit
File Operations Examples
The application supports importing/exporting data through CSV files:

Sample Student CSV Format:

id,regNo,fullName,email,status
STU001,2023001,John Doe,john.doe@university.edu,ACTIVE
STU002,2023002,Jane Smith,jane.smith@university.edu,ACTIVE
Sample Course CSV Format:

code,title,credits,instructor,semester,department
CS101,Introduction to Programming,3,Dr. Johnson,FALL,Computer Science
MATH201,Calculus II,4,Prof. Anderson,SPRING,Mathematics
Project Demonstration Flow
When you run the application, you'll experience:

Initialization: AppConfig singleton loads configuration settings
Main Menu: Console-based menu system with numbered options
Student Operations: Add/update/list students with validation
Course Management: Create courses using Builder pattern, search with Stream API
Enrollment System: Enroll students with business rule validation
Grade Recording: Record grades and calculate GPA automatically
File Operations: Import sample data, export current state
Backup System: Create timestamped backups with recursive directory operations
Reports: Generate academic reports using Stream operations
Platform Info: Display Java SE vs ME vs EE summary
Test Data
The project includes sample test data in the test-data/ directory:

students.csv: Sample student records for import testing
courses.csv: Sample course data with various departments
enrollments.csv: Sample enrollment records
Technical Notes
Java Platform Summary
This application demonstrates Java SE (Standard Edition) capabilities:

Java SE: Provides core APIs for desktop applications, server-side development
Java ME: Designed for resource-constrained devices (legacy)
Java EE: Enterprise features for web applications and distributed systems
Performance Considerations
Uses HashMap for O(1) lookup performance in services
Stream API for efficient data processing and filtering
NIO.2 for improved file I/O performance
Lazy initialization in Singleton pattern
Future Enhancements
Database persistence with JDBC
GUI interface using JavaFX or Swing
RESTful API endpoints for web integration
Advanced reporting with data visualization



# java-project-vityarti
git clone [your-repository-url]
cd CCRM

javac -d bin src/edu/ccrm/**/*.java
Technical Implementation Mapping
Syllabus Topic	Implementation Location	Description
OOP - Encapsulation	edu.ccrm.domain.*	Private fields with getters/setters in Student, Course classes
OOP - Inheritance	edu.ccrm.domain.Person → Student, Instructor	Abstract Person class extended by concrete classes
OOP - Abstraction	edu.ccrm.domain.Person	Abstract class with abstract methods getRole(), displayInfo()
OOP - Polymorphism	edu.ccrm.service.* interfaces	Persistable interface with multiple implementations
Interfaces	edu.ccrm.service.Persistable	Generic interface with default methods
Enums	edu.ccrm.domain.Grade, Semester	Enums with constructors and fields
Exception Handling	edu.ccrm.exception.*	Custom exceptions: DuplicateEnrollmentException, MaxCreditLimitExceededException
Collections Framework	StudentService, CourseService	HashMap for storage, List for collections
Generics	Persistable<T> interface	Generic interface and method parameters
Lambda Expressions	edu.ccrm.util.Comparators	Student sorting, course filtering predicates
Stream API	TranscriptService.generateReports()	GPA calculations, filtering, data aggregation
Date/Time API	edu.ccrm.domain.Student	LocalDateTime for enrollment dates, timestamps
NIO.2	edu.ccrm.io.ImportExportService	Path, Files APIs for CSV operations
Recursion	edu.ccrm.util.RecursiveUtils	Directory size calculation, file tree traversal
Design Patterns - Singleton	edu.ccrm.config.AppConfig	Thread-safe singleton implementation
Design Patterns - Builder	edu.ccrm.domain.Course.Builder	Builder pattern for Course construction
Nested Classes	Course.Builder (static), TranscriptGenerator.ReportFormatter (inner)	Static nested and inner class examples
Anonymous Classes	MainMenu.createComparator()	Anonymous Comparator implementation
Assertions	Throughout service classes	Invariant checking with assert statements
Package Structure and Architecture
src/edu/ccrm/
├── cli/                           # Command Line Interface
│   ├── MainMenu.java             # Main menu system with switch statements
│   ├── StudentMenuHandler.java   # Student-specific operations
│   └── CourseMenuHandler.java    # Course-specific operations
├── domain/                        # Domain Models
│   ├── Person.java               # Abstract base class
│   ├── Student.java              # Student entity (extends Person)
│   ├── Instructor.java           # Instructor entity (extends Person)
│   ├── Course.java               # Course entity with Builder pattern
│   ├── Enrollment.java           # Enrollment relationship
│   ├── Grade.java                # Grade enum with grade points
│   ├── Semester.java             # Semester enum
│   └── CourseCode.java           # Immutable value object
├── service/                       # Business Logic Layer
│   ├── Persistable.java          # Generic persistence interface
│   ├── StudentService.java       # Student CRUD operations
│   ├── CourseService.java        # Course CRUD operations
│   ├── EnrollmentService.java    # Enrollment business rules
│   └── TranscriptService.java    # GPA calculation, transcript generation
├── io/                            # File Operations
│   ├── ImportExportService.java  # CSV import/export with NIO.2
│   ├── BackupService.java        # Backup operations with timestamping
│   └── CSVParser.java            # CSV parsing utilities
├── util/                          # Utilities
│   ├── Validators.java           # Input validation methods
│   ├── Comparators.java          # Lambda-based comparators
│   └── RecursiveUtils.java       # Recursive file operations
├── config/                        # Configuration
│   ├── AppConfig.java            # Singleton configuration
│   └── DatabaseConfig.java       # Data persistence settings
├── exception/                     # Custom Exceptions
│   ├── DuplicateEnrollmentException.java    # Checked exception
└── CCRMApplication.java           # Main application entry point
Enabling Assertions
Assertions are used throughout the application to verify invariants and preconditions. To enable assertions:

Command Line
# Enable all assertions
java -ea edu.ccrm.CCRMApplication

# Enable for specific package
java -ea:edu.ccrm.domain... edu.ccrm.CCRMApplication

# Enable system assertions
java -esa edu.ccrm.CCRMApplication
Eclipse IDE
Run → Run Configurations
Select your configuration → Arguments tab
In VM arguments, add: -ea
Example Assertion Usage
// In StudentService.java
public void enrollStudent(String studentId, String courseCode) {
    assert studentId != null && !studentId.trim().isEmpty() : "Student ID cannot be null or empty";
    assert courseCode != null && !courseCode.trim().isEmpty() : "Course code cannot be null or empty";

    Student student = findById(studentId);
    assert student != null : "Student must exist before enrollment";

    // Business logic continues...
}
Sample Commands and Usage
Basic Operations
# Start application
java -ea -cp bin edu.ccrm.CCRMApplication

# Menu navigation examples:
# 1. Manage Students
# 2. Manage Courses
# 3. Enrollment Operations
# 4. Grade Management
# 5. Reports and Transcripts
# 6. File Operations
# 7. Backup and Recovery
# 0. Exit
File Operations Examples
The application supports importing/exporting data through CSV files:

Sample Student CSV Format:

id,regNo,fullName,email,status
STU001,2023001,John Doe,john.doe@university.edu,ACTIVE
STU002,2023002,Jane Smith,jane.smith@university.edu,ACTIVE
Sample Course CSV Format:

code,title,credits,instructor,semester,department
CS101,Introduction to Programming,3,Dr. Johnson,FALL,Computer Science
MATH201,Calculus II,4,Prof. Anderson,SPRING,Mathematics
Project Demonstration Flow
When you run the application, you'll experience:

Initialization: AppConfig singleton loads configuration settings
Main Menu: Console-based menu system with numbered options
Student Operations: Add/update/list students with validation
Course Management: Create courses using Builder pattern, search with Stream API
Enrollment System: Enroll students with business rule validation
Grade Recording: Record grades and calculate GPA automatically
File Operations: Import sample data, export current state
Backup System: Create timestamped backups with recursive directory operations
Reports: Generate academic reports using Stream operations
Platform Info: Display Java SE vs ME vs EE summary
Test Data
The project includes sample test data in the test-data/ directory:

students.csv: Sample student records for import testing
courses.csv: Sample course data with various departments
enrollments.csv: Sample enrollment records
Technical Notes
Java Platform Summary
This application demonstrates Java SE (Standard Edition) capabilities:

Java SE: Provides core APIs for desktop applications, server-side development
Java ME: Designed for resource-constrained devices (legacy)
Java EE: Enterprise features for web applications and distributed systems
Performance Considerations
Uses HashMap for O(1) lookup performance in services
Stream API for efficient data processing and filtering
NIO.2 for improved file I/O performance
Lazy initialization in Singleton pattern
Future Enhancements
Database persistence with JDBC
GUI interface using JavaFX or Swing
RESTful API endpoints for web integration
Advanced reporting with data visualization
Acknowledgments
This project was developed as part of Java Programming coursework, demonstrating comprehensive usage of Java SE features, OOP principles, and software engineering best practices. All code is original implementation following academic integrity guidelines.
java -cp bin edu.ccrm.CCRMApplication
java -ea -cp bin edu.ccrm.CCRMApplication
