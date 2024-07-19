# Use the official SonarQube image as the base
FROM sonarqube:latest

# Environment variables (you may choose to pass these as build arguments or use them directly in the compose file)
ENV SONAR_JDBC_MAXACTIVE=5 \
    SONAR_JDBC_MAXIDLE=2 \
    SONAR_JDBC_MINIDLE=1 \
    SONAR_JDBC_MAXWAIT=5000 

# Expose the port SonarQube runs on
EXPOSE 9000

# Mount the volumes for data, extensions, and logs
VOLUME ["/opt/sonarqube/data", "/opt/sonarqube/extensions", "/opt/sonarqube/logs"]
