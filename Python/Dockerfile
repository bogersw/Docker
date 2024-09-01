# syntax=docker/dockerfile:1

FROM python:3.12.5-slim

LABEL maintainer="WalterB" \
      version="1.0.1" \
      description="Python 3.12.5"

ENV PIP_DEFAULT_TIMEOUT=100 \
    PYTHONUNBUFFERED=1 \
    PIP_DISABLE_PIP_VERSION_CHECK=1 \
    PIP_NO_CACHE_DIR=1 \
    PYTHONDONTWRITEBYTECODE=1

COPY requirements.txt /app/requirements.txt
RUN pip install --no-cache-dir -r /app/requirements.txt

WORKDIR /home/jupyter

EXPOSE 8888

CMD ["jupyter", "lab", "--port=8888", "--no-browser", "--ip=0.0.0.0", "--allow-root",  "--NotebookApp.token=''", "--NotebookApp.password=''"]
