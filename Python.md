![[Pasted image 20230813182937.png]]
![[Pasted image 20230813183122.png]]
![[Pasted image 20230813183242.png]]
To run a different version of python 
```console
PS C:\Python311> py -3.9
```

to list the version of python on your system
```console
py --list
```
to check your version of python
```console
py --version
```
to get the paths to the python directories
```console
py --list-paths
```
## Virtual Environments
```console
py -3.10 -m venv project_venv
```
## pip
1. activate the virtual enviornment
2. pip install package name
	1. pip install package_name==1.3.2
	2. pip install package_name<=1.2
	3. pip install package_name>2.0
3. requirements.txt
	1. keep track of required packages and versions
	2. filename can be anything
	3. pip install -r requirements.txt
## pip freeze to show libraries/dependencies
```powershell
pip freeze
```
pip install
```shell
pip install -r .\requirements.txt
```
## create requirements.txt file
1. install pipreqs
	```python
	   pip install pipreqs
```
2. do this
```python
pipreqs ./ --Force
```
--Force overwrite the requirements.txt that exists
./ is the current directory or point it to the directory you're trying to make


