THISDIR := phy454-continuumechanics
THISBOOK := phy454

BIBLIOGRAPHY_PATH := classicthesis_mine
HAVE_OWN_CONTENTS := 1
#HAVE_OWN_TITLEPAGE := 1
#HAVE_CUSTOM_DEDICATION := 1
MY_CLASSICTHESIS_FRONTBACK_FILES += ../latex/classicthesis_mine/FrontBackmatter/Index.tex
MY_CLASSICTHESIS_FRONTBACK_FILES += ../latex/classicthesis_mine/FrontBackmatter/ContentsAndFigures.tex
BOOKTEMPLATE := ../latex/classicthesis_mine/ClassicThesis2.tex

# comment this out for online pdf version (uncomment for KDP)
#PRINT_VERSION := 1
ifndef PRINT_VERSION
PARAMS += --no-print
endif
ifdef PRINT_VERSION
DISTEXTRA := kdp
endif

include make.revision
include ../latex/make.bookvars

FIGURES := ../figures/phy454-continuumechanics

SOURCE_DIRS += appendix
#SOURCE_DIRS += figures
SOURCE_DIRS += $(FIGURES)
SOURCE_DIRS += elastic/displacements
SOURCE_DIRS += elastic/strain
SOURCE_DIRS += elastic/stress
SOURCE_DIRS += fluids
SOURCE_DIRS += fluids/bernoulli
SOURCE_DIRS += fluids/boundaryLayers
SOURCE_DIRS += fluids/hydrostatics
SOURCE_DIRS += fluids/navierStokes
SOURCE_DIRS += fluids/nondimensionalisation
SOURCE_DIRS += fluids/singularPertubation
SOURCE_DIRS += fluids/surfaces
SOURCE_DIRS += fluids/surfaceTension
SOURCE_DIRS += fluids/thermal
SOURCE_DIRS += intro
SOURCE_DIRS += solutions

GENERATED_SOURCES += mathematica.tex
GENERATED_SOURCES += backmatter.tex

DO_SPELL_CHECK := $(shell cat spellcheckem.txt)

include ../latex/make.rules

.PHONY: spellcheck
spellcheck: $(patsubst %.tex,%.sp,$(filter-out $(DONT_SPELL_CHECK),$(DO_SPELL_CHECK)))

%.sp : %.tex
	spellcheck $^
	touch $@

distx:
ifdef DISTEXTRA
	cp $(THISBOOK).pdf ~/tmp/$(THISBOOK).$(DISTEXTRA).$(VER).pdf
else
	cp $(THISBOOK).pdf ~/tmp/$(THISBOOK).$(VER).pdf
endif

backmatter.tex: ../latex/classicthesis_mine/backmatter2.tex
	rm -f $@
	ln -s ../latex/classicthesis_mine/backmatter2.tex backmatter.tex
