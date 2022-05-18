FROM python:3.7-slim AS test-image

EXPOSE 8080
RUN mkdir app
WORKDIR /app
COPY . .
RUN pip install --user -r requirements_test.txt
RUN python -m pytest


FROM python:3.7-slim AS build-image

RUN groupadd -r webservice && useradd --no-log-init -r -g webservice webservice
COPY --from=test-image /app /app
WORKDIR /app
USER webservice:webservice
RUN pip install --user -r requirements.txt

EXPOSE 8080
ENTRYPOINT ["python"]
CMD ["app.py"]