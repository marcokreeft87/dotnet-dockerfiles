ARG BASE
FROM mcr.microsoft.com/windows:$BASE

# Install Chocolatey
RUN powershell -Command \
  Set-ExecutionPolicy Bypass -Scope Process -Force; \
  [System.Net.ServicePointManager]::SecurityProtocol = [System.Net.ServicePointManager]::SecurityProtocol -bor 3072; \
  iex ((New-Object System.Net.WebClient).DownloadString('https://chocolatey.org/install.ps1'))

# copy the chrome portable to the container
RUN mkdir "C:\Program Files\Google\Chrome\Application"

ARG src="GoogleChromePortable64"
ARG target="C:\Program Files\Google\Chrome\Application"
COPY ${src} ${target}

# Install Chrome, ChromeDriver, Python, and pip
RUN choco install googlechrome -y
RUN choco install chromedriver -y
RUN choco install python --version=3.10.0 -y --ignore-checksums

# Install additional Robot Framework packages
RUN pip install robotframework robotframework-seleniumlibrary robotframework-requests robotframework-databaselibrary robotframework-csvlibrary JayDeBeApi rpaframework-pdf pymssql

# Set environment variables for Chrome and ChromeDriver
#ENV CHROME_BIN="C:\Program Files (x86)\Google\Chrome\Application\chrome.exe"
ENV CHROME_BIN="C:\Program Files\Google\Chrome\Application"
ENV CHROMEDRIVER_PATH="C:\ProgramData\chocolatey\bin\chromedriver.exe"

# Set working directory
WORKDIR "C:\robotframework"
