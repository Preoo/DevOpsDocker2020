FROM node:alpine
COPY . .
RUN npm install
EXPOSE 8000
# ENV variables for following exercises
ENV FRONT_URL=http://localhost:5000
# Remove apt-get lists and other install related artifacts
CMD npm start
