# Analyzing Local Code with SonarQube

This guide provides step-by-step instructions on how to analyze your local code using SonarQube.

## Prerequisites

- **Java**: SonarQube requires Java 11 or higher.
- **SonarQube**: Download and install SonarQube Community Edition or another edition if you have a license.
- **SonarQube Scanner**: Download and configure SonarQube Scanner.

## Step 1: Install SonarQube Locally

### Download SonarQube

- Visit [SonarQube Downloads](https://www.sonarqube.org/downloads/) and download the latest SonarQube Community Edition.

### Extract SonarQube

1. Extract the downloaded SonarQube archive to a directory of your choice:

    ```bash
    unzip sonarqube-<version>.zip
    cd sonarqube-<version>
    ```

### Start SonarQube Server

1. Navigate to the `bin` directory for your operating system and start SonarQube:

   **Windows**:

    ```cmd
    cd sonarqube-<version>\bin\windows-x86-64
    StartSonar.bat
    ```

   **Linux/macOS**:

    ```bash
    cd sonarqube-<version>/bin/macosx-universal-64
    ./sonar.sh start
    ```

### Access SonarQube Dashboard

1. Open a browser and go to `http://localhost:9000`.
2. Log in with the default credentials:
   - **Username**: `admin`
   - **Password**: `admin`
3. Change the default password after logging in for security reasons.

## Step 2: Set Up SonarQube Scanner

### Download SonarQube Scanner

- Visit [SonarQube Scanner](https://docs.sonarqube.org/latest/analysis/scan/sonarscanner/) to download the latest SonarQube Scanner.

### Extract and Configure the Scanner

1. Extract the downloaded archive and add the `bin` directory to your system `PATH`.

   **Windows**:

    ```cmd
    set PATH=%PATH%;C:\path\to\sonar-scanner-<version>\bin
    ```

   **Linux/macOS**:

    ```bash
    export PATH=$PATH:/path/to/sonar-scanner-<version>/bin
    ```

### Verify Installation

1. Run the following command to verify the scanner installation:

    ```bash
    sonar-scanner --version
    ```

## Step 3: Analyze Your Local Code

### Create a `sonar-project.properties` File

1. In the root directory of your project, create a file named `sonar-project.properties` and add the following configurations:

    ```properties
    # Required metadata
    sonar.projectKey=my_project_key
    sonar.projectName=My Project
    sonar.projectVersion=1.0

    # Path to the source code
    sonar.sources=.

    # Optional configuration
    sonar.language=java
    sonar.sourceEncoding=UTF-8

    # For Java projects, include this for JaCoCo integration
    # sonar.java.binaries=target/classes
    # sonar.jacoco.reportPaths=target/jacoco.exec
    ```

   Adjust the properties according to your project’s language and structure.

### Run the SonarQube Scanner

1. Navigate to your project directory and execute the scanner:

    ```bash
    sonar-scanner
    ```

### Review Analysis Results

1. Open the SonarQube dashboard at `http://localhost:9000` and navigate to your project to view the analysis results.

## Additional Tips

- **Plugins**: Ensure that the necessary plugins for your project's language are installed in SonarQube.
- **CI/CD Integration**: Integrate SonarQube analysis into your CI/CD pipelines for automated code quality checks.

## Troubleshooting

- **Server Start Issues**: Check the logs in the `logs` directory if the server fails to start.
- **Permission Errors**: Ensure you have the necessary permissions to access and modify files.
- **Scanner Errors**: Verify that the `sonar-project.properties` file is correctly configured and that all paths are valid.
