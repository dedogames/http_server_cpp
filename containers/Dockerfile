FROM geoldery/ggr_cpp_image:0.1

RUN yum install -y telnet gdb git \
    && yum clean all
# create project directories
RUN mkdir /project/ \ 
    && mkdir /project/http_server/ \
    && mkdir /project/http_server/.vscode
ENTRYPOINT ["tail", "-f", "/dev/null"]

#build
#docker build --tag ggr_cpp_image:debug -f ./containers/debug/Dockerfile .
#docker tag local-image:ggr_cpp_image:0.1 new-repo:ggr_cpp_image:0.1