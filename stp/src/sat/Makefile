.PHONY: core
core:
	$(MAKE) -C core all	
	$(MAKE) -C simp lib all

.PHONY: cryptominisat2
cryptominisat2:
	$(MAKE) -C cryptominisat2 lib all

.PHONY: clean
clean:
	rm -rf *.o *~ libminisat.a
	$(MAKE) -C core    clean
	$(MAKE) -C simp    clean
	$(MAKE) -C cryptominisat2 clean

