Bootstrap: docker
From: alpine:latest


%labels
	author Stefano Ghignone
	maintainer sghignone
	name rnnotator
	version v3.5.0
%post
	apk update && apk upgrade \
	&& apk add --no-cache sudo build-base wget
