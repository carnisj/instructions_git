Create a binary distribution (for windows, already compiled):  python setup.py bdist_wheel

Upload it on TestPyPi:    twine upload --repository-url https://test.pypi.org/legacy/ dist/*

Tell to pip to download it from TestPyPi instead of PyPi: pip install --index-url https://test.pypi.org/simple/ BCDI
or pip install -i https://test.pypi.org/simple/ BCDI