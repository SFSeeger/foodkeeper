FROM python:3.10
ARG appdir=/app/
WORKDIR ${appdir}
COPY ./src ./src
COPY requirements-dev.txt requirements-dev.txt
RUN pip install -r requirements-dev.txt
WORKDIR ${appdir}/src/
RUN python3 manage.py migrate
RUN python3 manage.py collectstatic --noinput
RUN python3 manage.py compilemessages
ENTRYPOINT [ "python3", "manage.py", "runserver", "0.0.0.0:8000" ] 
EXPOSE 8000
