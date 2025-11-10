FROM public.ecr.aws/lambda/python:3.13

# install uv
COPY --from=ghcr.io/astral-sh/uv:latest /uv /uvx /bin/

# copy pyproject.toml and install dependencies
COPY pyproject.toml .
RUN uv sync

# copy handler
COPY handler.py .

# set PYTHONPATH to include uv-installed packages
ENV PYTHONPATH=/var/task/.venv/lib/python3.13/site-packages

# set the Lambda handler
CMD ["handler.exif_handler"]
