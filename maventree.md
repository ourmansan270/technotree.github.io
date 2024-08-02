
```markdown
# Maven Documentation Tree

## Overview
- **What is Maven?**
  Apache Maven is a build automation tool used primarily for Java projects. It simplifies the build process by managing project dependencies, compiling code, and packaging applications.

## Installation
- **Installing Maven**
  - **On Windows**
    ```sh
    # Download and extract Maven binaries
    wget https://archive.apache.org/dist/maven/maven-3/3.8.6/binaries/apache-maven-3.8.6-bin.zip
    unzip apache-maven-3.8.6-bin.zip
    # Add Maven to PATH
    setx PATH "%PATH%;C:\path\to\apache-maven-3.8.6\bin"
    ```
  - **On macOS**
    ```sh
    # Install Maven using Homebrew
    brew install maven
    ```
  - **On Linux**
    ```sh
    # Download and extract Maven binaries
    wget https://archive.apache.org/dist/maven/maven-3/3.8.6/binaries/apache-maven-3.8.6-bin.tar.gz
    tar -xzf apache-maven-3.8.6-bin.tar.gz
    # Add Maven to PATH
    export PATH=$PATH:/path/to/apache-maven-3.8.6/bin
    ```

## Configuration
- **Maven Settings**
  - **`settings.xml` Configuration**
    - Location: `~/.m2/settings.xml`
    - Key Configuration Options:
      ```xml
      <settings>
        <mirrors>
          <mirror>
            <id>central</id>
            <mirrorOf>central</mirrorOf>
            <url>https://repo.maven.apache.org/maven2</url>
          </mirror>
        </mirrors>
        <profiles>
          <profile>
            <id>default</id>
            <properties>
              <maven.compiler.source>1.8</maven.compiler.source>
              <maven.compiler.target>1.8</maven.compiler.target>
            </properties>
          </profile>
        </profiles>
      </settings>
      ```

## Project Structure
- **Directory Layout**
  - **Standard Maven Project Layout**
    ```
    my-project/
    ├── src/
    │   ├── main/
    │   │   ├── java/           # Java source files
    │   │   └── resources/      # Resource files
    │   └── test/
    │       ├── java/           # Test source files
    │       └── resources/      # Test resource files
    ├── target/                  # Compiled files
    ├── pom.xml                  # Project Object Model file
    └── .mvn/                    # Maven wrapper
    ```

## Commands

### Build and Package
- **Compile Project**
  ```sh
  mvn compile
  ```

- **Package Project**
  ```sh
  mvn package
  ```

- **Install Package Locally**
  ```sh
  mvn install
  ```

### Dependency Management
- **Add Dependency**
  - Modify `pom.xml`
    ```xml
    <dependency>
      <groupId>com.google.guava</groupId>
      <artifactId>guava</artifactId>
      <version>30.1-jre</version>
    </dependency>
    ```

- **Update Dependencies**
  ```sh
  mvn dependency:resolve
  ```

### Lifecycle Phases
- **Clean**
  ```sh
  mvn clean
  ```

- **Validate**
  ```sh
  mvn validate
  ```

- **Test**
  ```sh
  mvn test
  ```

- **Install**
  ```sh
  mvn install
  ```

- **Deploy**
  ```sh
  mvn deploy
  ```

## Troubleshooting

### Common Issues
- **Dependency Resolution Issues**
  - Check `pom.xml` for correct dependency declarations.
  - Clear local repository cache:
    ```sh
    mvn dependency:purge-local-repository
    ```

- **Build Failures**
  - Verify correct Maven version.
  - Check build logs for specific errors and fix accordingly.

### Diagnostic Commands
- **Display Effective POM**
  ```sh
  mvn help:effective-pom
  ```

- **View Plugin Configuration**
  ```sh
  mvn help:effective-pom -Doutput=plugin-config.xml
  ```

## Monitoring
- **View Build Logs**
  ```sh
  mvn clean install -X
  ```

- **Maven Debug Mode**
  ```sh
  mvn clean install -X
  ```

## Scenarios

### Scenario 1: Creating a New Maven Project
- **Objective:** Set up a new Maven project with default configuration.
- **Steps:**
  1. **Generate Project Structure:**
     ```sh
     mvn archetype:generate -DgroupId=com.example -DartifactId=my-app -DarchetypeArtifactId=maven-archetype-quickstart -DinteractiveMode=false
     ```
  2. **Navigate to Project Directory:**
     ```sh
     cd my-app
     ```
  3. **Build the Project:**
     ```sh
     mvn package
     ```

### Scenario 2: Adding and Managing Dependencies
- **Objective:** Add and manage dependencies for a Java project.
- **Steps:**
  1. **Add Dependencies to `pom.xml`:**
     ```xml
     <dependency>
       <groupId>org.apache.commons</groupId>
       <artifactId>commons-lang3</artifactId>
       <version>3.12.0</version>
     </dependency>
     ```
  2. **Update Project Dependencies:**
     ```sh
     mvn dependency:resolve
     ```

### Scenario 3: Running Unit Tests
- **Objective:** Execute unit tests and generate test reports.
- **Steps:**
  1. **Run Tests:**
     ```sh
     mvn test
     ```
  2. **View Test Results:**
     - Test results are typically found in the `target/surefire-reports` directory.

### Scenario 4: Deploying Artifacts to a Remote Repository
- **Objective:** Deploy built artifacts to a remote Maven repository.
- **Steps:**
  1. **Configure Deployment in `pom.xml`:**
     ```xml
     <distributionManagement>
       <repository>
         <id>releases</id>
         <url>https://my-repo/repository/releases/</url>
       </repository>
     </distributionManagement>
     ```
  2. **Deploy Artifacts:**
     ```sh
     mvn deploy
     ```

## Advanced Topics

### Multi-Module Projects
- **Definition**
  - Projects with multiple sub-modules that are managed in a single parent project.
- **Setup**
  - **Parent POM Configuration**
    ```xml
    <project>
      <modules>
        <module>module-a</module>
        <module>module-b</module>
      </modules>
    </project>
    ```
  - **Build All Modules**
    ```sh
    mvn clean install
    ```

### Custom Maven Plugins
- **Create a Custom Plugin**
  - **Generate Plugin Project:**
    ```sh
    mvn archetype:generate -DgroupId=com.example -DartifactId=my-plugin -DarchetypeArtifactId=maven-archetype-plugin
    ```
  - **Develop and Build Plugin:**
    ```sh
    mvn clean install
    ```

### Profiles and Build Variants
- **Define Profiles in `pom.xml`:**
  ```xml
  <profiles>
    <profile>
      <id>dev</id>
      <properties>
        <env>development</env>
      </properties>
    </profile>
    <profile>
      <id>prod</id>
      <properties>
        <env>production</env>
      </properties>
    </profile>
  </profiles>
  ```
- **Activate Profile:**
  ```sh
  mvn clean install -Pdev
  ```

## Integration with GitHub Actions

### Setting Up a Maven Build in GitHub Actions
- **Objective:** Automate Maven builds and tests using GitHub Actions.
- **Steps:**

  1. **Create a GitHub Actions Workflow File:**
     - File path: `.github/workflows/maven-build.yml`
     ```yaml
     name: Maven Build

     on:
       push:
         branches:
           - main
       pull_request:
         branches:
           - main

     jobs:
       build:
         runs-on: ubuntu-latest

         steps:
           - name: Checkout code
             uses: actions/checkout@v3

           - name: Set up JDK 11
             uses: actions/setup-java@v3
             with:
               java-version: '11'

           - name: Build with Maven
             run: mvn clean install

           - name: Run tests
             run: mvn test
     ```

  2. **Add Secrets for Deployment (Optional):**
     - Store deployment credentials or other secrets in GitHub repository settings.
     - Example: `MAVEN_DEPLOYMENT_USERNAME`, `MAVEN_DEPLOYMENT_PASSWORD`.

  3. **Configure Deployment (Optional):**
     - Add steps to deploy artifacts to a remote repository in the workflow.
     ```yaml
     - name: Deploy


       run: mvn deploy -DskipTests
       env:
         MAVEN_USERNAME: ${{ secrets.MAVEN_DEPLOYMENT_USERNAME }}
         MAVEN_PASSWORD: ${{ secrets.MAVEN_DEPLOYMENT_PASSWORD }}
     ```

### Example Output of GitHub Actions Workflow
- **Build Log**
  ```plaintext
  Run mvn clean install
  [INFO] Scanning for projects...
  [INFO] 
  [INFO] -----------< com.example:my-app >-----------
  [INFO] Building my-app 1.0-SNAPSHOT
  [INFO] --------------------------------[ jar ]---------------------------------
  [INFO] 
  [INFO] --- maven-clean-plugin:3.1.0:clean (default-clean) @ my-app ---
  [INFO] Deleting /home/runner/work/my-app/my-app/target
  [INFO] 
  [INFO] --- maven-resources-plugin:3.2.0:resources (default-resources) @ my-app ---
  [INFO] Using 'UTF-8' encoding to copy filtered resources.
  [INFO] Copying 1 resource
  [INFO] 
  [INFO] --- maven-compiler-plugin:3.8.1:compile (default-compile) @ my-app ---
  [INFO] Compiling 1 source file to /home/runner/work/my-app/my-app/target/classes
  [INFO] 
  [INFO] --- maven-surefire-plugin:2.22.2:test (default-test) @ my-app ---
  [INFO] 
  [INFO] --- maven-jar-plugin:3.2.0:jar (default-jar) @ my-app ---
  [INFO] Building jar: /home/runner/work/my-app/my-app/target/my-app-1.0-SNAPSHOT.jar
  ```

