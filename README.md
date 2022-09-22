# This is a template for any new hash-based MLST database

## Database format

In the db folder, each scheme has two files.

* `refs.fasta` - reference alleles for each locus
* `alleles.tsv`
   * tab separated values: hash of the sequence, locus name, hash-type, attributes
      * hash-type is currently md5, indicating a base64 of md5sum.
      * attributes are key/values separated by `=`.
      * different attributes are separated with `;`.
      * defined attributes are allele-caller, allele-caller-version, sequencing-platform, sequencing-platform-model, assembler, assembler-version
      * example attributes: allele-caller=chewbbaca;allele-caller-version=2
   * `alleles.tsv` can be chunked into files of at most 500k lines to avoid having huge files
      * These need to be concatenated later at time of use

## Example

    mkdir -v db
    perl scripts/digestFasta.pl t/senterica/*.tfa --out db/senterica --force

## Installation

1. Clone the repo
2. Put `scripts` into your PATH
3. Requires BioPerl to read the fasta files

