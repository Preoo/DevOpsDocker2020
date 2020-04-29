FROM node:alpine as build-stage
# Build
COPY . .
RUN npm run build

# Deploy
FROM node:alpine
# Copy artifacts from build-stage
COPY --from=build-stage ./dist/ ./app

# By default serve on port 5000
EXPOSE 5000
RUN adduser -D app
USER app
# For next part, example on using env
ENV API_URL=http://localhost:8000
# Remove apt-get lists and other install related artifacts
# so far with FROM node:* only thing I could do is to remove
# curl
# CMD npm start
CMD serve -s -l 5000 app
