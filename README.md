# Defense Finder Models

This repository contains MacSyFinder models allowing for a systematic search of anti-phage systems.

The repo is formatted according to [MacSyData guidelines](https://macsyfinder.readthedocs.io/en/latest/modeler_guide/index.html) and synchronized with [macsy-models repository](https://github.com/macsy-models) to be available in macsydata.

## More information on the systems

To simplify the access to the detection rules of the models we created a table (DefenseFinder_rules.tsv) that recapitulate all the rules of detections for each systems.

For the HMM models, we added the "Liste_hmm_system.md" to give all the threshold used for each models.

More information on the different systems are available on the [DefenseFinder wiki](https://defensefinder.mdmlab.fr/wiki/).

### Modifying the models

To change the models, first create a new remove git branch from master:

```
git push origin master:<your-branch-name>
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
### Update the release updates file

Add one line per new system.

Add a column with 0 and 1 for the presence of each system in the new version.

Add one Status_vx.x.x for each system: New, modified, removed or From version vx.x.x (version where the system appears).

Add one column Comment_vx.x.x: with information on the modification or other comment.

### Releasing

Once your pull request has been validated and merged, you need to create a release.

Decide of a new version number according to [semantic versionning](https://semver.org/).

Then update the version number in `metadata.yml`, and merge it to master.

Once you've done this, create a tarball with the following command (don't forget to replace <your-version> with your version).

```
tar -czf defense-finder-models-<your-version>.tar.gz \
  ./defense-finder-models/LICENSE \
  ./defense-finder-models/README.md \
  ./defense-finder-models/definitions \
  ./defense-finder-models/metadata.yml \
  ./defense-finder-models/profiles/
```

Then go to [Github](https://github.com/mdmparis/defense-finder-models/releases).
From there, create a new release with the correct version number and the tarball you've just created as attached file.

One you've done this, your new version is discoverable through:

```
macsydata available --org mdmparis
```

And you can install it following those lines:

```
macsydata download --org mdmparis defense-finder-models
macsydata install defense-finder-models-<version>.tar.gz
```

Or if you're using the `mdmparis-defense-finder` python package, just run `defense-finder update`.
