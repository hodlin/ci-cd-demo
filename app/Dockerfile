FROM python:3.7-slim

WORKDIR /app
RUN groupadd -r webservice && useradd --no-log-init -r -g webservice webservice
COPY . .
RUN pip install --user -r requirements.txt

USER webservice:webservice

EXPOSE 8080
ENTRYPOINT ["python"]
CMD ["app.py"]