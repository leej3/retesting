FROM python:3.11-slim
SHELL ["/bin/bash", "--login", "-c"]
COPY --from=ghcr.io/astral-sh/uv:0.4.0 /uv /bin/uv
RUN mkdir -p /opt/data
RUN mkdir -p /opt/app
WORKDIR /opt/app
COPY pyproject.toml /opt/app
COPY README.rst /opt/app
COPY ./tftesting_dashboard /opt/app/tftesting_dashboard
RUN uv sync
RUN uv run flask --app tftesting_dashboard init-db
CMD ["uv","run","flask", "--app", "tftesting_dashboard","run","--debug","--host","0.0.0.0"]