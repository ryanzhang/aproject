SRC_DIR = {{ cookiecutter.repo_name }}
DOC_DIR = docs
MAKE = make

all:
	make install
	make test
	make html
	make clean

install:
	pip install -q -e .[dev,test,docs]

lint:
	prospector $(SRC_DIR) --strictness veryhigh

test:
	nosetests -c nose.cfg

testall:
	tox

html:
	cd $(DOC_DIR) && $(MAKE) html

htmlci:
	curl -X POST http://readthedocs.org/build/{{ cookiecutter.repo_name }}

htmlci:
	curl -X POST http://readthedocs.org/build/onehalfpiece

testdist:
	python setup.py sdist bdist_wheel
	twine upload --repository-url https://test.pypi.org/legacy/ dist/*

sdist:
	twine upload dist/*
	
clean:
	rm -rf *.egg-info
	rm -rf build/*
	rm -rf dist/*
	rm -rf $(SRC_DIR)/*.egg-info
	find $(SRC_DIR) -name "*.pyc" | xargs rm
