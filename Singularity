Bootstrap: docker
From: bioperl/bioperl
Stage: devel

%labels
	author Stefano Ghignone
	maintainer sghignone
	name RNNOTATOR
	version 3.5(released YY-MM-DD) 

%environment
	export PATH=/usr/local/bin:$PATH

%post
	apt  update && apt -y full-upgrade && apt -y install build-essential wget git

	export LC_ALL="C.UTF-8"
	export LANG="C.UTF-8"
	echo 'export LC_ALL=C.UTF-8' >> "$SINGULARITY_ENVIRONMENT"
	echo 'export LANG=C.UTF-8' >> "$SINGULARITY_ENVIRONMENT"

	curl -L http://cpanmin.us | perl - --sudo App::cpanminus
	cpanm --quiet --notest Statistics::Descriptive Parallel::ForkManager Tree
	
	#Install BLAT
	wget -c http://hgdownload.soe.ucsc.edu/admin/exe/linux.x86_64/blat/blat -P /usr/local/bin
	chmod +x /usr/local/bin/blat
	
	#Move to install DIR
	cd /opt

	#Installing VELVET
	git clone https://github.com/dzerbino/velvet.git
	cd velvet && make
	chmod +x velvet?
	cd ..

	#Installing OASES
	git clone --recursive https://github.com/dzerbino/oases
	cd oases && make
	chmod +x oases
	cd ..

	#Installing BWA
	wget -c https://sourceforge.net/projects/bio-bwa/files/bwa-0.7.17.tar.bz2 -P /opt
	tar -xf bwa-0.7.17.tar.bz2 -C /opt
	cd bwa-0.7.17 && make
	cd ..
	rm bwa-0.7.17.tar.bz2

	#Installing MUMMER
	wget -c https://sourceforge.net/projects/mummer/files/mummer/3.23/MUMmer3.23.tar.gz -P /opt
	tar -xzf MUMmer3.23.tar.gz -C /opt
	cd MUMmer3.23 && make install
	cd .. 
	rm MUMmer3.23.tar.gz
	ln -s /opt/MUMmer3.23/nucmer /usr/bin/.
	ln -s /opt/MUMmer3.23/show-coords /usr/bin/.
	ln -s /opt/MUMmer3.23/delta-filter /usr/bin/.

%environment
	export PATH=/opt/velvet:/opt/oases:/opt/bwa-0.7.17:/opt/MUMmer3.23:$PATH		
