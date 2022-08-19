all : ../LICENSE.md $(shell ls *.md)

ONE=cat $< | gawk 'BEGIN {FS="\n";RS=""} {print $$0 "\n"; exit}' | gawk '{print "  " $$0} END{print("\n\n")}' 
TWOPLUS=cat $@ | gawk 'BEGIN {FS="\n";RS=""} NR==1 { print("\n\n"); next} {print $$0 "\n\n"}'

pub:
	$(MAKE) all
	git add *;git commit -am save;git push;git status

../LICENSE.md : ../README.md Makefile; @echo "$@ ... " ; ($(ONE);  $(TWOPLUS)) > .tmp; mv .tmp $@
*.md          : ../README.md Makefile; @echo "$@ ... " ; ($(ONE);  $(TWOPLUS)) > .tmp; mv .tmp $@

