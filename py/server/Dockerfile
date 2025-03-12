FROM python:3.9-alpine
LABEL authors="Sebastian"

ARG SRC_FOLDER="server"

# Poetry required files
COPY poetry.lock .
COPY pyproject.toml .
COPY README.md .

# Install Poetry and Python dependencies
# See https://python-poetry.org/docs/faq#poetry-busts-my-docker-cache-because-it-requires-me-to-copy-my-source-files-in-before-installing-3rd-party-dependencies
RUN pip install poetry && poetry install --only main --no-root --no-directory

# Copy source code
COPY ${SRC_FOLDER}/ ./${SRC_FOLDER}

RUN poetry install --only main

CMD ["poetry", "run", "flask", "--app", "server.app", "--debug", "run", "--host", "0.0.0.0", "--port", "5001"]
