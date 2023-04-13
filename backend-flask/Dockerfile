# FROM python:3.10-slim-buster

# WORKDIR /backend-flask

# COPY requirements.txt requirements.txt
# RUN pip3 install -r requirements.txt

# COPY . .

# ENV FLASK_ENV=development
# ENV FRONTEND_URL='*'
# ENV BACKEND_URL='*'

# EXPOSE ${PORT}
# CMD [ "./entrypoint.sh"]

# Stage 1: Build the application
FROM python:3.10-slim-buster AS build

WORKDIR /backend-flask

COPY requirements.txt requirements.txt
RUN pip3 install --user -r requirements.txt

COPY . .

RUN python3 -m compileall .

# Stage 2: Create the production-ready image
FROM python:3.10-slim-buster

WORKDIR /backend-flask

COPY --from=build /root/.local /root/.local
COPY --from=build /backend-flask .

ENV PATH=/root/.local/bin:$PATH
ENV FLASK_ENV=production
ENV FRONTEND_URL='*'
ENV BACKEND_URL='*'
ENV PORT=4567

EXPOSE ${PORT}

CMD [ "./entrypoint.sh" ]
