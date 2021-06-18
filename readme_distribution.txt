Create a binary distribution (for windows, already compiled):  python setup.py sdist bdist_wheel

Upload it on TestPyPi:    twine upload --repository-url https://test.pypi.org/legacy/ dist/*

Tell to pip to download it from TestPyPi instead of PyPi: pip install --index-url https://test.pypi.org/simple/ BCDI
or pip install -i https://test.pypi.org/simple/ BCDI

twine check dist/bcdii-0.0.6.tar.gz

the long_description can be rst but without Sphinx extensions. Therefore README.rst can not be used.

using the source (.tar.gz), one can install the package by running in the root directory: pip install .

using the source (.tar.gz), one can rebuild the documentation by running make.bat html (Windows) or makefile html (Mac?, Linux) in the doc/ folder

package_data can be used only if the data belongs to a package folder, otherwise it can be included only if written in MANIFEST.in

Upload a distribution on PyPI: twine upload dist/*

Check a distribution before uploading: twine check dist/*