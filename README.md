# simplecondarecipe

I think conda recipes are way easier than writing setup.py for python packages.  If you are in an environment where you don't need to publish to pypi, and conda is sufficient (think enterprise) this can be a much easier way to build packages, rather than fiddling with setup.py options, diagnosing issues with include_package_data and pacakge_data_dirs for non python includes (think html template directories)

Here is the meta.yaml

```
package:
  name:  examplepackage
  version: "1.0"

source:
  path:  ../

requirements:
  build:
    - python
```

The only part I felt was extraneous was setting a build requirement of python - this is necessary because conda precompiles pyc files.  Also doing so ensures that the site packages directory has been created

Here is the build.sh

```
cp -rf $SRC_DIR/examplepackage $SP_DIR
```

