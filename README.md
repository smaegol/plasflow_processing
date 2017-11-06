# plasflow_processing

Scripts used during the development of PlasFlow

- Use `get_refseq_genomes_complete.sh` to download complete genomes (Archaea and Bacteria)
- Run `get_refseq_catalog_filter.sh` to get accessions numbers of each downloaded sequence and filtered RefSeq catalog files
- Run `Rscript create_annotation_of_data.R` to create the annotation table based on the RefSeq catalog (filtered to contain only downloaded sequences).

  - Uses rentrez to collect data from NCBI - may be slow

- Run "RScript generate_fragments_for_training.R"

  - May require large amounts of RAM

- Run training using `PlasFlow_train.py` script - requires TensorFlow 0.10.0 (see [requirements for PlasFlow](https://github.com/smaegol/PlasFlow#requirements))
