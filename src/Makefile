SRCS = l1.asm l2.asm l3.asm l4.asm l5.asm gravtbl.asm

PFILES = $(patsubst %.asm,%.p, $(SRCS))
LSTFILES = $(patsubst %.asm,%.lst, $(SRCS))
HEXFILES = $(patsubst %.asm,%.hex, $(SRCS))

all: $(LSTFILES) spacewar.hex

%.lst %.p: %.asm
	asl -cpu 8080 -L -C $<

%.hex: %.p
	p2hex $<
	srec_info $@ -intel

spacewar.p: $(PFILES)
	pbind $(PFILES) spacewar.p

clean:
	rm -f *.hex *.lst *.p
