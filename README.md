# Struts 1.x to Struts 6 Upgrade Documentation

This document outlines the steps required to upgrade a project from Struts 1.x to Struts 6, with necessary environment configuration and server setup.

## Steps for Upgrade

### 1. Update Environment Variables

To ensure compatibility with Struts 6, update the following environment variables:

- **JAVA_HOME**: Update `JAVA_HOME` from the older version (e.g., Java 1.8 or 1.7) to **JDK 21**.
  
  - On Windows:
    1. Open `System Properties` > `Advanced` > `Environment Variables`.
    2. Update the value of `JAVA_HOME` to the path where **JDK 21** is installed (e.g., `C:\Program Files\Java\jdk-21`).
    3. Update the `Path` variable and add the bin folder of JDK 21 (e.g., `C:\Program Files\Java\jdk-21\bin`).

  - On macOS/Linux:
    1. Open your terminal.
    2. Update the `JAVA_HOME` in the `.bash_profile` or `.zshrc` file to the JDK 21 path:
       ```bash
       export JAVA_HOME=/path/to/jdk-21
       export PATH=$JAVA_HOME/bin:$PATH
       ```
    3. Restart the terminal or run `source ~/.bash_profile` to apply the changes.

### 2. Add Apache Tomcat 9.0.89 as the Server

1. Download **Apache Tomcat 9.0.89** from the official website:
   - [Tomcat 9.0.89 Download](https://tomcat.apache.org/download-90.cgi)
   
2. Install Apache Tomcat by extracting the downloaded files to a suitable location on your system.

3. Configure the Tomcat server in your IDE (e.g., Eclipse):
   - In Eclipse, go to the `Servers` tab (usually at the bottom of the IDE).
   - Right-click on the server view and select **New** > **Server**.
   - Choose **Apache Tomcat v9.0** and point it to the folder where Tomcat 9.0.89 is installed.

### 3. Configure Project in Eclipse and Perform Maven Build

To make the project visible in Eclipse and perform a clean build:

1. Open Eclipse and ensure the project is imported into the workspace.
2. Right-click on the project in the **Package Explorer**.
3. Navigate to **Run As** > **Maven clean** to clean the previous build artifacts.
4. Then, select **Run As** > **Maven install**. This will:
   - Clean the old files.
   - Download the necessary dependencies.
   - Package the project.

### 4. Run the Project on Tomcat 9 Server

1. After building the project, you can deploy and run it on Apache Tomcat 9:
   - Right-click on the project in **Package Explorer**.
   - Navigate to **Run As** > **Run on Server**.
   - A dialog box will appear. Select **Apache Tomcat 9** and click **Next**.
   - Finally, click **Finish** to deploy the project.

2. The application should now be running on the Apache Tomcat server.

---

## Additional Notes

- **Dependencies**: Ensure that your `pom.xml` is updated to include the correct versions of Struts 6 and other required dependencies.
  
- **Configuration Changes**: Review the configuration files like `struts-config.xml` and `tiles-defs.xml` to ensure they are compatible with Struts 6.

- **Java Version Compatibility**: If the project uses legacy code or libraries, ensure that they are compatible with Java 21. You may need to update or replace certain dependencies.

---

## Troubleshooting

- If the project does not start after following these steps, check the Eclipse logs (`.log` files) and Tomcat logs (`logs/catalina.out`) for error messages.
- Verify that the necessary Struts 6 configurations are in place, and that Tomcat is correctly configured to work with the project.

