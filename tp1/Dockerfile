FROM python:latest
 
WORKDIR /python-docker

# Install Flask and Gunicorn
RUN pip3 install --no-cache-dir flask

COPY . .
 
# Start SSH server
CMD [ "python3", "-m" , "flask", "run", "--host=0.0.0.0"]
