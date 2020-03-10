SRC_NAME = chinadns-ng-latest
SRC_URL = https://github.com/zfl9/chinadns-ng/archive/latest.tar.gz
THISDIR = $(shell pwd)

all: download_test extract_test config_test

download_test:
	( if [ ! -f $(THISDIR)/$(SRC_NAME).tar.gz ]; then \
		wget -t5 --timeout=20 --no-check-certificate -O $(SRC_NAME).tar.gz $(SRC_URL); \
	fi )

extract_test:
	( if [ ! -d $(THISDIR)/$(SRC_NAME) ]; then \
		tar zxf $(SRC_NAME).tar.gz; \
	fi )

config_test:
	( if [ -f ./config_done ]; then \
		echo "the same configuration"; \
	else \
		make configure && touch config_done; \
	fi )

configure:
	cd $(SRC_NAME)

clean:
	rm -f config_done

romfs:
	$(ROMFSINST) -p +x $(THISDIR)/$(SRC_NAME)/chinadns-ng /usr/bin/chinadns-ng

