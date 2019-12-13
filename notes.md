Follow the instructions given here
https://github.com/CloudNativeJS/docker

## To create docker image

Run the following command from inside the directory where Dockerfile is available, :
`docker build -t mernapiserver -f Dockerfile .` here `.` means current directory

## To run the docker image just created

Run the following command from inside the directory where Dockerfile is available, :
`docker run -i -p 3000:3000 -t mernapiserver`

## Create Development based docker image

Run the following command from inside the directory where Dockerfile is available, :
`docker build -t mernapiserver-tools -f Dockerfile-tools .` here `.` means current directory
