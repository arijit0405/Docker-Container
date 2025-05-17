# Stage 1: Build stage (install Python and prepare app)
FROM ubuntu:22.04 as build

WORKDIR /app


RUN apt-get update && apt-get install -y python3 python3-pip

# Copy your calculator app to the container
COPY calci.py .

# (Optional) If you had a requirements.txt:
# COPY requirements.txt .
# RUN pip3 install -r requirements.txt

# Stage 2: Final lightweight image
FROM ubuntu:22.04

WORKDIR /app

# Install only Python in final image
RUN apt-get update && apt-get install -y python3

# Copy the built app from the build stage
COPY --from=build /app /app

# Default command to run the calculator
CMD ["python3", "calci.py"]
