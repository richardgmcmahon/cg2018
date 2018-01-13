# Make for IOA Consolidated Grant
# History 
# Original 10-Jan-2015: Richard McMahon

# make info to test
# make all to create case and cp to Website
# make tar to create tar file and cp to Website


OS := $(shell uname)
DATESTAMP = $(shell date +%Y%m%d)
ROOT_PATH='/home/rgm/Projects/Grants/CG2019_2022/'


BACKUP_PATH='/home/rgm/public_html/private/CG2019_2022/'
BACKUP_TAR_PATH='/home/rgm/public_html/private/CG2019_2022/Backup_tar/'

MASTER = CG2016_2019_master_v1
MASTER = CG2016_2019_master_v2
MASTER = CG2019_2022

DATE_PREFIX= 20150110a
CASE_GPE =  CG2016_2019_GPE

# does not work
ifeq ($(OS), Darwin)
  OPEN= open
endif
ifeq ($(OS),Linux)
  OPEN = acroread 
endif


#MASTER= $(PREFIX)_$(DATE_PREFIX) 

info:
	@echo 'OS: ' $(OS)
	@echo 'OPEN: ' $(OPEN)
	@echo 'DATESTAMP: ' $(DATESTAMP)
	@echo 'MASTER: ' $(MASTER)
	@echo 'ROOT_PATH: ' $(ROOT_PATH)
	@echo 'BACKUP_PATH: ' $(BACKUP_PATH)
	@echo 'BACKUP_TAR_PATH: ' $(BACKUP_TAR_PATH)


# place the tar file in directory below to prevent recursively adding
# tar files to each new tar file
tar:
	@echo 'DATESTAMP: ' $(DATESTAMP)
	mkdir -p $(BACKUP_TAR_PATH)
	tar -cvf $(ROOT_PATH)/CG2019_2022_$(DATESTAMP)_backup.tar  -C $(ROOT_PATH)/Draft .
	cp $(ROOT_PATH)CG2019_2022_$(DATESTAMP)_backup.tar $(BACKUP_TAR_PATH)/.

all: $(MASTER).pdf
	@echo $(OS)
	pdflatex $(MASTER)
	pdflatex $(MASTER)
	cp $(MASTER).pdf $(BACKUP_PATH)/
	cp $(MASTER).pdf $(BACKUP_PATH)/$(MASTER)_$(DATESTAMP).pdf
	$(OPEN) $(MASTER).pdf


submit: 
	@echo $(OS)
	pdflatex $(MASTER)
	pdflatex $(MASTER)
	cp $(MASTER).pdf $(BACKUP_PATH)/CG2019_2022_IOA_final.pdf
	cp $(MASTER).pdf $(BACKUP_PATH)/CG2019_2022_IOA_final_$(DATESTAMP).pdf
	$(OPEN) $(MASTER).pdf
	@echo 'DATESTAMP: ' $(DATESTAMP)
	tar -cvf $(ROOT_PATH)/CG2019_2022_$(DATESTAMP)_backup.tar  -C $(ROOT_PATH)/Draft .
	cp $(ROOT_PATH)CG2019_2022_$(DATESTAMP)_backup.tar $(BACKUP_TAR_PATH)/.


open:
	$(OPEN) $(MASTER).pdf


$(MASTER).pdf: $(MASTER).tex 
	pdflatex $(MASTER)
	pdflatex $(MASTER)
	cp $(MASTER).pdf /home/rgm/public_html/private/$(MASTER)/.
	cp $(MASTER).pdf /home/rgm/public_html/private/$(MASTER)/$(MASTER)_$(DATESTAMP).pdf
	$(OPEN) $(MASTER).pdf 

clean:
	rm -rf *.aux *.bbl *.toc *.log *.dvi

