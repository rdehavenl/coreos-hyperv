.SILENT:

win-test:
	vagrant up

packer-validate:
	echo "===Validating Template==="
	packer validate -machine-readable coreos-hyperv.json
	echo.

packer-logging:
    set PACKER_LOG=1

packer-build:
    echo "===Packer Building==="
	packer build -machine-readable -color=false coreos-hyperv.json
	echo "=== [DONE] ==="

vagrant-cleanup:
    echo "===Vagrant Cleanup==="
    -vagrant destroy -f
	-vagrant box remove coreos-hyperv2 -f
	echo.

vagrant-run:
    echo "===Register and Run Box==="
	vagrant box add ../local-data/output-boxes/coreos_hyperv.box --name coreos-hyperv2
	vagrant up

win-dev: vagrant-cleanup packer-validate packer-logging packer-build vagrant-run

win-build: vagrant-cleanup packer-validate packer-build vagrant-run

help:
	echo "This is help file"

.DEFAULT: win-build