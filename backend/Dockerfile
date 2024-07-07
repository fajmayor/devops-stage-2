# Use the official Python image as a base image
FROM python:3.12-slim

ENV POETRY_HOME="/opt/poetry" \
    PIP_NO_CACHE_DIR=off \
    POETRY_VIRTUALENVS_PATH="/app/.venv"

ENV PATH="$POETRY_HOME/bin:$POETRY_VIRTUALENVS_PATH/bin:$PATH"

WORKDIR /app/

# Install dependencies and Poetry
RUN apt-get update \
    && apt-get install --no-install-recommends -y \
        curl \
        bash \
        build-essential
    
RUN curl -sSL https://install.python-poetry.org | python3 -

RUN poetry --version

RUN poetry config virtualenvs.create false

# Copy the project files
COPY ./pyproject.toml ./poetry.lock* ./
COPY ./alembic.ini ./
COPY ./prestart.sh ./
COPY ./app ./app

# Install dependencies using Poetry
RUN poetry install

# Ensure the start scripts are executable
RUN chmod +x /app/prestart.sh

# Run the prestart script and then start the application using Poetry
CMD ["bash", "-c", "poetry run bash ./prestart.sh && poetry run uvicorn app.main:app --reload --host 0.0.0.0 --port 8000"]

# Expose the port
EXPOSE 8000
