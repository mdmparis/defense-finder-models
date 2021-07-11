# Defense Finder Models

This repository contains MacSyFinder models allowing for a systematic search of anti-phage systems.

The repo is formatted according to [MacSyData guidelines](https://macsyfinder.readthedocs.io/en/latest/modeler_guide/index.html) and synchronized with [macsy-models repository](https://github.com/macsy-models) to be available in macsydata.

## Contributing

### Modifying the models

To change the models, first create a new remove git branch from master:

```
git push origin master <your-branch-name>
```

Then checkout (= "go to") your branch locally:

```
git checkout <your-branch-name>
```

Bring your modifications, then don't forget to check validity of the models:

```
macsydata check
```

You can now commit and push:

``` 
git status # Visualize which files have changed
git add <the files you want to commit>
git diff --cached # control what you're going to commit 
git commit -m 'Fixed the ... model'
git push
```

The next step is to go to [the defense-finder-models Github repository](https://github.com/mdmparis/defense-finder-models) and submit a pull request.

### Updating MacSyData repository 

Once your pull request has been validated and merged, you need to update the [macsy-models repository](https://github.com/macsy-models).

[WIP]
