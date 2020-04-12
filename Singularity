
Bootstrap: docker
From: sghignone/alpine-bioperl:latest
Stage: devel

%labels
	author Stefano Ghignone
	maintainer sghignone
	name rnnotator
	version v3.5.0
%post
	echo "Hello from inside the container"
	apk update && apk upgrade \
	&& apk add --no-cache htop

#	mkdir /opt/blat
	wget -c http://hgdownload.soe.ucsc.edu/admin/exe/linux.x86_64/blat/blat -P /opt/
	chmod +x /opt/blat
	ls -lh /opt/blat

%environment
	export PATH=/opt:$PATH
