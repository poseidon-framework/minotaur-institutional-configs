# poseidon-framework/minotaur-institutional-configs: EVA Configuration

Configuration options for running nf-core/eager through Minotaur in the Department of Genetics and Archaeogenetic's clusters at the [Max Planck Institute for Evolutionary Anthropology (MPI-EVA)](http://eva.mpg.de).

To use, run the pipeline with `-profile eva_minotaur`. This will download and launch the [`eva_minotaur.config`](../conf/eva_minotaur.config), adjusting the resources used by nf-core/eager jobs launched through Minotaur.

## Additional Profiles

Minotaur institutional configs come with a sub-profile named `local_paths` that points to the loacl paths for the `fasta`, `fasta_index`, `bwa_index`, and `seq_dict` parameters.

The `eva_minotaur` profile increases the number of concurrent jobs to 24, and tweaks the resources provided to `bwa` and `markduplicates` processes.
