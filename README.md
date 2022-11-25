# Neotropical soils submission

prepare and format metadata for a EBI/ENA submission of the Neotropical metabarcoding data

## tasks

- [x] start the project,
- [x] clone,
- [x] create folders,
- [x] add placeholders,
- [ ] start a Rmd file,
- [ ] check that I have metadata entries all the samples I need to
      submit (454 and Illumina),
- [ ] ...

## get a list of all available read files (SFF and fastq)

```sh
# aragorn
cd ${HOME}/projects/neotropical-soils-submission/data/

(
    cd ${HOME}/projects/Ciliata_neotropical/data/
    echo -e "run\tSubmitted_files"
    (
        find . -name "*.sff"
        find ./201*/ -name "*.fastq.*" | \
            grep -vE "_P[13]_|_NT[13]_|_K[14]_|_H?T[13]_"
    ) | \
        sort | \
        tr "/" "\t" | \
        cut -f 1 --complement | \
        sed 's/\.bz2/.gz/'
) > list_of_read_files.tsv
```
