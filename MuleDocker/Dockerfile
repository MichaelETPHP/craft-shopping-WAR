FROM java:openjdk-8-jdk

RUN rm -rf Mule
RUN mkdir Mule

#Add  Mule runtime to the Docker container
RUN echo "Adding Mule 4.3.0 to Docker container"
ADD  mule-ee-distribution-standalone-4.3.0.zip /Mule

#Add Work Directory
RUN echo "Adding Work Directory"
WORKDIR /Mule

#Extract and install the Mule runtime in the container
RUN echo "Extracting the zip file and installing the Mule runtime"
RUN         unzip mule-ee-distribution-standalone-4.3.0.zip && \
    rm mule-ee-distribution-standalone-4.3.0.zip

# Define volume mount points
VOLUME      ["/Mule/mule-enterprise-standalone-4.3.0-20210119/logs", "/Mule/mule-enterprise-standalone-4.3.0-20210119/apps", "/Mule/mule-enterprise-standalone-4.3.0-20210119/domains"]

#Copy and deploy mule application in the Mule 4.3.0 runtime
RUN echo "Deploying mule application in runtime"
COPY  craft-payment-api-getway.jar mule-enterprise-standalone-4.3.0-20210119/apps/
RUN ls -ltr mule-enterprise-standalone-4.3.0-20210119/apps/

# Expose the port 8087 as needed
EXPOSE      8087

# Start Mule runtime
RUN echo "Starting Mule runtime 4.3.0"
CMD         ["mule-enterprise-standalone-4.3.0-20210119/bin/mule"]
