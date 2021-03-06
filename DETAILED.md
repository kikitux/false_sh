# Detailed instructions on how this repo/task was done

## DONE
- Create new repo
- Set description
- Select create README
- Select License, choose MIT
- create new branch
- Add this file
- Create new branch `addVagrantfile`
- Create Vagrantfile for a VM with `vagrant init -m firedot/xenial64`

```
cat Vagrantfile

Vagrant.configure("2") do |config|
  config.vm.box = "firedot/xenial64"
end
```

- Create ```.gitignore``` with ```.vagrant/``` in it: 

```
echo '.vagrant/' >> .gitignore
```

- Git add the new files
- Git commit the new files
- Git push the new files

```
git push --set-upstream origin addVagrantfile
```
- Create new branch ```addFalse_sh```
- Create ```false.sh``` that produces and exit code of 1

```
#!/usr/bin/env bash

exit 1
```
- Add ```false.sh``` to this repo
```
git add false.sh
git commit -m "Added false.sh"
git push --set-upstream origin addFalse_sh
```

- Add repo to travis (enable repository on travis)
- Create `.travis.yml` with test that always fail

```
language: generic
dist: xenial
sudo: required
script:
- exit 1
```

- Create test that tests ```false.sh``` with Travis

```
#!/usr/bin/env bash

bash true.sh
if [ $? -eq 1 ]; then
  echo SUCCESS: test pass
else
  echo FAILURE: test fail
  exit 1
fi
```

- Update ```.travis.yml``` to use ```test.sh```

```
language: generic
dist: xenial
sudo: required
script:
- bash test.sh
```
- setup release for `false.sh`
- do a release `0.1` to confirm all works


