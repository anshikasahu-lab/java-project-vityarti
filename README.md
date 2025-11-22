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


# java-project-vityarti
git clone [your-repository-url]
cd CCRM

javac -d bin src/edu/ccrm/**/*.java

java -cp bin edu.ccrm.CCRMApplication
java -ea -cp bin edu.ccrm.CCRMApplication
