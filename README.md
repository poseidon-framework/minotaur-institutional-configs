# minotaur-institutional-configs

A collection of nextflow configurations files for different computational clusters.

## Using an existing config

To use an existing configuration file with [Minotaur](https://github.com/poseidon-framework/poseidon-eager), you can specify the desired profile to the launching script ([run_eager.sh](https://github.com/poseidon-framework/poseidon-eager/blob/main/scripts/run_eager.sh)), which will ensure Nextflow downloads and loads the appropriate configuration file, and its associated `local_paths` sub-profile.

For example, to use the EVA Minotaur configuration, you would run:

```bash
./run_eager.sh -p eva_minotaur
```

## Adding a new config

If you decide to upload your custom config file to this repository, then this will ensure that your custom config file will be automatically downloaded, and become available to Minotaur.

Steps to add a new config file:

1. Add your custom `.config` file within the `conf/` directory of this repository.
    - Ensure that the file name ends in `_minotaur.config`.
    - Ensure your config file declares within its params scope any local paths for the `fasta`, `fasta_index`, `bwa_index`, and `seq_dict` parameters.
2. Add a new profile in the [minotaur_custom.config](https://github.com/poseidon-framework/minotaur-institutional-configs/blob/main/minotaur_custom.config), named after your profile, which includes your custom config file.
    - For example, if your config file is named `my_custom_minotaur.config`, you would add a profile named `my_custom_minotaur` that includes this config file with `includeConfig()`.
3. Test your configuration locally to ensure it works as expected.
    - You can do this by running Minotaur with your custom profile, by changing the default values for `custom_minotaur_config_base` and/or `custom_minotaur_config_version`.
4. Add a readme describing the contents of the profile in `docs/`.
    - This should include the name of the profile, a brief description of its purpose, and a brief outline of configurations or resources it modifies. (See [docs/eva_minotaur.md](https://github.com/poseidon-framework/minotaur-institutional-configs/blob/main/docs/eva_minotaur.md) for an example).
5. Commit your changes and open a Pull request to this repository.

Once the PR is merged, you can use your custom config with Minotaur by providing the profile name when launching the pipeline, e.g., `./run_eager.sh -p my_custom_minotaur`.
