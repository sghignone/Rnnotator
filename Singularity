
Bootstrap: docker
From: alpine:latest


%labels
	author Stefano Ghignone
	maintainer sghignone
	name rnnotator
	version v3.5.0
%post
	apk update && apk upgrade \
	&& apk add --no-cache sudo build-base curl wget perl

	curl -L http://xrl.us/cpanm > /bin/cpanm && chmod +x /bin/cpanm

	cpanm --quiet --notest install Bundle::BioPerl
	cpanm --quiet --notest install Parallel::ForkManager Tree
	cpanm --quiet --notest install BioPerl
