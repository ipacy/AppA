# pull official base image
FROM python:3.6.0-alpine

# set work directory
WORKDIR /usr/src/HelloDjango

# set environment variables
ENV PYTHONDONTWRITEBYTECODE 1
ENV PYTHONUNBUFFERED 1

# install psycopg2 dependencies
RUN apk update \
    && apk add postgresql-dev gcc python3-dev musl-dev

# install dependencies
RUN pip install --upgrade pip
COPY ./requirements.txt /usr/src/HelloDjango/requirements.txt
RUN pip install -r requirements.txt

# copy entrypoint.sh
#COPY ./entrypoint.sh /usr/src/HelloDjango/entrypoint.sh

# copy project
COPY . /usr/src/HelloDjango/

# run entrypoint.sh
#RUN chmod +x entrypoint.sh
#ENTRYPOINT ["/usr/src/HelloDjango/entrypoint.sh"]



EXPOSE 8000
CMD ["gunicorn", "--bind", ":8000", "--chdir", "HelloDjango", "HelloDjango.wsgi:application"]
