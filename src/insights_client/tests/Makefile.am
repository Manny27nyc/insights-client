check_SCRIPTS = test_commands.py
nodist_check_SCRIPTS = test_sed.py

if HAVE_PYTEST
TESTS = pytest.sh
endif

pytest.sh: $(nodist_check_SCRIPTS) $(check_SCRIPTS)
	echo 'PYTHONPATH=$(top_srcdir)/src:$(top_srcdir)/data/rpm.egg $(PYTEST) $(PYTEST_FLAGS) ./*.py' > $@
	chmod +x $@

CLEANFILES = pytest.sh $(nodist_check_SCRIPTS)

%: %.in Makefile
	$(AM_V_GEN) $(SED) \
		-e 's,[@]top_srcdir[@],$(top_srcdir),g' \
		$< > $@.tmp && mv $@.tmp $@

EXTRA_DIST = test_sed.py.in

-include $(top_srcdir)/git.mk
