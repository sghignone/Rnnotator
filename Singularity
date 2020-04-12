
Bootstrap: docker
From: sghignone/alpine-bioperl:latest
Stage: devel

%labels
	author Stefano Ghignone
	maintainer sghignone
	name rnnotator
	version v3.5.0
%post
	apk update && apk upgrade \
	&& apk add --no-cache htop
