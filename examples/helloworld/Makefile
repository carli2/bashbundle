helloworld.bashbundle: data/* privkey.pem
	../../bin/bbpack data privkey.pem helloworld.bashbundle

run: helloworld.bashbundle
	../../bin/bbrun helloworld.bashbundle

clean: reset_config
	rm helloworld.bashbundle || true
	rm data/version || true

reset_config:
	rm ~/.bashbundle/versions/helloworld.bashbundle.version || true
