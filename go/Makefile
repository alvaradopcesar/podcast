#
# Makefile for the Go modules
#

#Check all the code things - fmt, imports, vet and lint
code-check: fmt imports vet lint

#Go Format all the code
fmt:
	goapp fmt ./...

#Update all imports, and remove any that aren't necessary, for all go files we can find.
imports:
	find -name '*.go' -exec goimports -w {} \;

#vet everything, test it for
vet:
	go vet ./src/...

#lint everything, make sure it conforms
lint:
	golint .

EPS_MODULE=./src/modules/eps/app.yaml

serve-eps: code-check
	gb gae serve -port 8080 -host 0.0.0.0 $(EPS_MODULE)

deploy-eps:
	gb gae deploy $(EPS_MODULE)
