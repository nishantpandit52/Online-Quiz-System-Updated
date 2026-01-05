Guide: Upgrading this project to Java 21 (LTS)

Summary
- The project is a simple Java app compiled/run via the included `compile_and_run.bat` script.
- Automated GitHub Copilot Java upgrade tools are not available in this environment.
- This guide explains how to install JDK 21 on Windows and configure the project to use it via `JAVA_HOME`.

Steps
1. Download and install a JDK 21 distribution.
   - Recommended: Eclipse Temurin (Adoptium) or Microsoft Build of OpenJDK 21.
   - Visit https://adoptium.net/ or https://learn.microsoft.com/en-us/java/openjdk/download and download the Windows x64 MSI or ZIP for JDK 21.

2. Set JAVA_HOME and update PATH
   - If you installed via MSI: set `JAVA_HOME` to the installation folder, e.g. `C:\Program Files\Eclipse Adoptium\jdk-21.0.x`.
   - To set in PowerShell (current session):

     $env:JAVA_HOME = 'C:\Program Files\Eclipse Adoptium\jdk-21.0.x'
     $env:PATH = "$env:JAVA_HOME\bin;" + $env:PATH

   - To set permanently, use System > Advanced system settings > Environment Variables, or run PowerShell as admin and set the registry-backed user/system variables.

3. Verify installation
   - In PowerShell:

     & "$env:JAVA_HOME\bin\java" -version
     & "$env:JAVA_HOME\bin\javac" -version

   - Expected output should mention `openjdk version "21` or similar.

4. Compile & run the project
   - From the `guvi` folder, run the included batch file (it prefers `JAVA_HOME` if set):

     .\compile_and_run.bat

Notes
- If you prefer to keep multiple JDKs, use the JAVA_HOME approach to select JDK 21 for this project only.
- If you want the repository to enforce a toolchain, consider adding a Maven or Gradle wrapper and toolchain config. I can help add that if you'd like.
