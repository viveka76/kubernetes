# problem
## here the problem is that a variable called ME_CONFIG_MONGODB_URL 
## inside the mongo-express pod which stores the url to connect to the database(in this case mongodb) is set by default to 
## "ME_CONFIG_MONGODB_URL=mongodb://mongo:27017"
## but the service that we created on the db-mongo.yaml file has name mongodb-service so the url that should be used to connect to db
## should be mongodb://mongodb-service:27017 which will internally expand to mongodb://mongo-root-username:mongo-root-password@mongodb-service:27017
## now we can do two things to solve this:
## EITHER
## we set the env varibale 
## ME_CONFIG_MONGODB_URL to mongodb://mongo-root-username:mongo-root-password@mongodb-service:27017/ in the yaml file just like we have done
## for ME_CONFIG_MONGODB_ADMINPASSWORD and ME_CONFIG_MONGODB_ADMINUSERNAME
## OR
## we change the service name in the yaml file from mongodb-service to mongo
