# Using official python runtime base image
FROM schoolofdevops/voteapp-python:v0.1.0

# Set the application directory
WORKDIR /app

# Install our requirements.txt
ADD requirements.txt /app/requirements.txt
RUN pip install -r requirements.txt \
    && chgrp -R 0 /app \
    && chmod -R g=u /app

# Copy our code from the current folder to /app inside the container
ADD . /app

# Make port 8080 available for links and/or publish
EXPOSE 8080

# Define our command to be run when launching the container
CMD ["gunicorn", "app:app", "-b", "0.0.0.0:8080", "--log-file", "-", "--access-logfile", "-", "--workers", "4", "--keep-alive", "0"]
