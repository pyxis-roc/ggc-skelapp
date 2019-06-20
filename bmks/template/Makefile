include ../common.mk

include app.mk

# do not change anything below unless you know what you're doing
DSTDIR=$(GENSRC)/$(BMKNAME)

all: $(DSTDIR) $(BMKNAME)

$(BMKNAME): $(DSTDIR)/Makefile  $(DSTDIR)/kernel.cu $(DSTDIR)/support.cu 

$(DSTDIR)/Makefile: 
	ln -sf $(GGCDIR)/skelapp/SAMakefile $@

$(DSTDIR)/kernel.cu: $(SRCPY)
	$(GGC) $(GGCFLAGS) -o $@ $<

$(DSTDIR)/support.cu: 
	ln -sf ../../bmks/$(BMKNAME)/$(SUPPORT) $@ 

include ../common-rules.mk

$(DSTDIR)/bmktest2.py: 
	ln -sf ../../bmks/$(BMKNAME)/bmktest2.py $@ 
