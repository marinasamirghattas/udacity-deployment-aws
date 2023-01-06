pipline process:

circleci jops :

--build :

-   to install backages for both front-end and back end
-   to build both front-end and back end

-- deploy :

-   to deploy api to AWS
-   to deploy front end to AWS

pipline diagram :

 local code => push code to github repo => circleCi => AWS(eb for front-end , S3 for back-end)

 
## Pipeline Architecture

![pipeline](./pipeline.PNG)


#### GitHub
Developer push code to the GitHub repo which  linked to the CircleCI platform and  triggers it

#### CircleCI
CircleCI reads cofigrations from `.circleci/config.yml` file which tells the service what has to be done. In the case of Udagram,
there are 2 jobs (frontend & server) to be run by CircleCI.
- **Frontend**: Runs the `build` script given in the `package.json` file. Then uses AWS CLI to upload assets to S3.
- **Server**: Runs the `build` script, exports all environment variables from CircleCI configuration to a `.env` file. Then uses AWS CLI to upload archive to S3.