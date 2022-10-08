# Install SDKMAN!
curl -s "https://get.sdkman.io" | sh

Close terminal and open a new one.

# Show SDKMAN! version
sdk version

# Show available commands
sdk help

# List all available SDKs
sdk list

# List available versions of Java
sdk list java

# Install specific Java version
sdk install java 18.0.1-oracle
sdk install java 11.0.15-zulu

# Switch Java version temporarily
sdk use java 18.0.1-oracle

# Switch Java version permanently
sdk default java 11.0.15-zulu

# Remove Java version
sdk uninstall java 18.0.1-oracle

# Show current Java version
sdk current java
java -version

# Show version of SDK in use
sdk current

# Offline Mode
sdk offline enable
sdk offline disable

# Self-update
sdk selfupdate

# Update candidate versions
sdk update

# Get HOME directory of SDK
sdk home java 18.0.1-oracle

# Flush - Clear storage
sdk flush
sdk flush broadcast
sdk flush archives
sdk flush tmp


# Notes

The SDKs get installed into ~/.sdkman/candidates, e.g. Java SDK can be found in ~/.sdkman/candidates/java/ directory.
