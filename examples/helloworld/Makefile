helloworld.bashbundle: data/* privkey.pem
	../../bin/bbpack data privkey.pem helloworld.bashbundle

run: helloworld.bashbundle
	../../bin/bbrun helloworld.bashbundle

clean:
	rm helloworld.bashbundle || true
	rm data/version || true
