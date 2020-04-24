# If you had to do any changes explain what you had to change.
Hello CORS my old friend, I've come to talk you again....
Due to change with nginx I had to adjust FRONT_ and API_URL environment variables.
Instead of doign that in respective Dockerfiles, I simply added overwriting entry
to their service definition in `docker-compose.yml`. With those modifcations all buttons are working as they should
