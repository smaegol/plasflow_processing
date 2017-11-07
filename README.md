# plasflow_processing

Scripts used during the development of PlasFlow.

All preprocessing steps producing kmer counts used for the neural network training can be run using command:

  ```
  bash PlasFlow_preprocessing.sh```

  Alternatively, all steps can be ran individually:

- Use `get_refseq_genomes_complete.sh` to download complete genomes (Archaea and Bacteria)
- Run `get_refseq_catalog_filter.sh` to get accessions numbers of each downloaded sequence and filtered RefSeq catalog files
- Run `Rscript create_annotation_of_data.R` to create the annotation table based on the RefSeq catalog (filtered to contain only downloaded sequences).

  - Uses rentrez to collect data from NCBI - may be slow

- Run `RScript generate_fragments_for_training.R`

  - May require large amounts of RAM - especially for longer kmers (hexamers, heptamers)

- Run training using `PlasFlow_train.py` script - requires TensorFlow 0.10.0 (see [requirements for PlasFlow](https://github.com/smaegol/PlasFlow#requirements))
  - As an input `kmern_split_raw_counts_tax_classes_numeric_annotated_filtered_tax.tsv` files should be used (where **n** is a kmer length)
  - Typical invocation of a script:

  ```
  python PlasFlow_train.py --input kmern_split_raw_counts_tax_classes_numeric_annotated_filtered_tax.tsv --hidden1 20 --hidden2 10 --activation relu --modeldir kmern_split_20_10_neurons_relu --steps 50000
```
    will run training on specified file, using 20 neurons in first hidden layer and 10 neurons in second hidden layer, using `relu` activation function and 50000 steps of training. Model will be saved in the `kmern_split_20_10_neurons_relu` folder
