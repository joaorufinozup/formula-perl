# Make Run Perl
BINARY_NAME_UNIX=run.sh
BINARY_NAME_WINDOWS=run.bat
BIN_FOLDER=bin

build: perl-build docker

perl-build:
	mkdir -p $(BIN_FOLDER)
	cp -r src/* $(BIN_FOLDER)
	echo '#!/bin/sh' > $(BIN_FOLDER)/$(BINARY_NAME_UNIX)
	echo 'if [ -f /.dockerenv ] ; then' >> $(BIN_FOLDER)/$(BINARY_NAME_UNIX)
	echo '	export PERL5LIB=/rit/bin' >> $(BIN_FOLDER)/$(BINARY_NAME_UNIX)
	echo 'fi' >> $(BIN_FOLDER)/$(BINARY_NAME_UNIX)
	echo 'perl "$$(dirname "$$0")"/main.pl' >>  $(BIN_FOLDER)/$(BINARY_NAME_UNIX)
	echo 'perl main.pl' > $(BIN_FOLDER)/$(BINARY_NAME_WINDOWS)
	chmod +x $(BIN_FOLDER)/$(BINARY_NAME_UNIX)

docker:
	cp Dockerfile set_umask.sh $(BIN_FOLDER)
