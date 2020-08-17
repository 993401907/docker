from centos:7


RUN yum install -y wget
RUN cd /etc/yum.repos.d/ && cp CentOS-Base.repo CentOS-Base-repo.bak
RUN wget http://mirrors.163.com/.help/CentOS7-Base-163.repo
RUN yum clean all && mv -f CentOS7-Base-163.repo CentOS-Base.repo
RUN yum makecache && yum -y update
RUN yum -y install  gcc gcc-c++ autoconf automake make
RUN yum -y install  zlib zlib-devel openssl* pcre*  lua-devel
RUN wget http://nginx.org/download/nginx-1.19.2.tar.gz && tar -zxvf nginx-1.19.2.tar.gz 
RUN rm -rf nginx-1.19.2.tar.gz
WORKDIR /nginx-1.19.2
RUN ls
RUN ./configure --with-stream
RUN  make && make install
RUN rm -rf /nginx-1.19.2
COPY nginx.conf /usr/local/nginx/conf/nginx.conf
RUN /usr/local/nginx/sbin/nginx -c /usr/local/nginx/conf/nginx.conf

EXPOSE 80 443 3308 8080

CMD ["/usr/local/nginx/sbin/nginx","-g","daemon off;"]