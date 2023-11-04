# Dynamic Analysis Tool for Java Test Coverage

## Introduction

This repository contains a dynamic analysis tool for collecting method-level coverage information for test cases in a Java project. The tool is designed to analyze a Java project, identify classes and methods, extract test cases (JUnit test methods), collect coverage information for each test case, and determine which methods are covered by each test case. This information is then summarized and output in a JSON file.

## Table of Contents

- [Requirements](#requirements)
- [Usage](#usage)
- [Output](#output)
- [Performance](#performance)
- [Testing](#testing)
- [Questions](#questions)

## Requirements

To use this tool, make sure you meet the following requirements:

**1.** Any programming language can be used for your implementation. However, the target project is a Java project.

**2.** Your program should take a git repository location as input; the git repository is a Java project. Your program can take a cloned local directory of a git repository to simplify the problem.

**3.** Your program shall take other optional parameters if necessary.

**4.** Your program shall produce a JSON file as output for each project; this should be stored into a designated location by an optional parameter.

**5.** Your program shall produce a file summarizing the results of the target project in the following format:

```json
{
  "location": "/a/b/c",
  "stat_of_repository": {
    "num_java_files": 30,
    "num_classes": 193,
    "num_methods": 401,
    "num_test_methods": 200
  },
  "test_coverage_against_methods": {
    "org.apache.math.DoubleTest#test1": ["org.apache.math.Double#setDouble", "org.apache.math.Int#setInt"],
    "org.apache.math.DoubleTest#test2": ["org.apache.math.Double#getDouble", "org.apache.math.Int#getInt"]
  }
}
```

**6.** Your program should take a ruleset file path as a parameter.

**7.** Your program should perform, at least, 1.0s/Java_file. In other words, your program shall finish processing a repository with 1,000 Java files within 1000s.

**8.** You can test your program with the [https://github.com/apache/commons-lang](https://github.com/apache/commons-lang) repository.

## Usage

### Prerequisites

Before you can run this project, you need to have the following software installed on your system:

- **Java 11:** You should have Java Development Kit (JDK) 11 or a compatible version installed. You can download and install it from [Oracle's website](https://www.oracle.com/java/technologies/javase-jdk11-downloads.html) or use OpenJDK.

- **Maven:** This project uses Maven as the build tool. Make sure you have Maven installed. You can download it from [here](https://maven.apache.org/download.cgi) or use a package manager relevant to your operating system.

### Running the Project

To run the project locally, follow these steps:

1. Clone this repository to your local machine using Git:
   ```sh
   git clone https://github.com/ammaralii/java-test-coverage-analyzer.git
   ```
2. Navigate to the project directory:
    ```sh
   cd java-test-coverage-analyzer
    ```
3. Build the project using Maven:
    ```sh
   mvn clean install
    ```
3. Run the application:
    ```sh
   java -jar target/test-coverage-analyzer-1.0-SNAPSHOT.jar https://github.com/apache/commons-lang.git
    ```
   Instead of https://github.com/apache/commons-lang.git you can pass any public GitHub repository and check the code coverage.

## Output

The tool will produce a JSON file in the specified location, as described in Requirement 5. The output will include project statistics and test coverage information for each test case.

## Performance

The tool is designed to meet the performance requirements outlined in Requirement 7. It should be capable of processing a repository with 1,000 Java files within 1000 seconds.

We make it superfast as it'll process 1500 java files in 1 second. Here is the output:
```
Repository cloned from https://github.com/apache/commons-lang.git to /Users/ammarali/home/projects/java-test-coverage-analyzer/test_coverage_projects/commons-lang.git
Step 0: (Clone repository as not exists) Execution Time: 28375 ms
Step 1: (Add Jacoco Dependency and Plugin to Cloned Repo) Execution Time: 8 ms
Step 2: (Run Maven Test on project) Execution Time: 91944 ms
Step 3: (Count Methods) Execution Time: 263 ms
Step 4: (Coverage Info) Execution Time: 486 ms
Step 5: (List Java Files) Execution Time: 16 ms
JSON data has been written to the file.
```

## Testing

You can test the tool with the [https://github.com/apache/commons-lang](https://github.com/apache/commons-lang) repository as suggested in Requirement 8.

## Questions

If you have any questions or need further assistance, please don't hesitate to reach out. We are here to help you with any inquiries you may have.


Happy coding! Life is Logically programmed