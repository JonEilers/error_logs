```bash
snakemake --configfile=snakemake.yml --use-singularity --cores=all
INFO:    Using cached SIF image
INFO:    Converting SIF file to temporary sandbox...
INFO:    Cleaning up image...
Building DAG of jobs...
Using shell: /usr/bin/bash
Provided cores: 80
Rules claiming more threads will be scaled down.
Job stats:
job                                                count    min threads    max threads
-----------------------------------------------  -------  -------------  -------------
ALL                                                    1              1              1
collect                                                1             70             70
make_merge_config                                      1              1              1
mark_assembly_preliminary_gap_closed                   1              1              1
mask_dust                                              1              1              1
mask_reads                                             1              1              1
mask_self                                              2              1              1
mask_tandem                                            2              1              1
mask_tandem_block                                      5              1              1
merge_insertions                                       1              1              1
preliminary_closed_gaps_bed2mask                       1              1              1
preliminary_gap_closed2dam                             1              1              1
preliminary_gap_closed_vs_reads_alignment              1              1              1
preliminary_gap_closed_vs_reads_alignment_block        1             70             70
preliminary_output                                     1              1              1
process                                                1             70             70
propagate_mask_back_to_reference                       3              1              1
propagate_mask_back_to_reference_block                 3              1              1
propagate_mask_batch                                   3              1              1
propagate_mask_to_reads_block                          3              1              1
purged_output                                          1              1              1
reads2db                                               1              1              1
ref_vs_reads_alignment                                 1              1              1
ref_vs_reads_alignment_block                           1             70             70
self_alignment                                         2              1              1
self_alignment_block                                  11             70             70
skip_gaps                                              1              1              1
split_preliminary_gap_closed_vs_reads_alignment        1              1              1
tandem_alignment_block                                 5             70             70
validate_regions                                       1              1              1
validate_regions_block                                32             70             70
total                                                 91              1             70

Select jobs to execute...

[Tue Sep 28 20:43:34 2021]
localcheckpoint reads2db:
    input: pacbio_SRR6282347.fasta
    output: /home/jon/Working_Files/dentist/pacbio_SRR6282347.db, /home/jon/Working_Files/dentist/.pacbio_SRR6282347.bps, /home/jon/Working_Files/dentist/.pacbio_SRR6282347.idx
    jobid: 6
    resources: tmpdir=/tmp
Downstream jobs will be updated after completion.

Activating singularity image /home/jon/Working_Files/dentist/.snakemake/singularity/1aa939115af17aa65dcd7164899b9ec7.simg

[Tue Sep 28 20:43:34 2021]
rule tandem_alignment_block:
    input: dentist.json, <TBD>, /home/jon/Working_Files/dentist/.assembly.Ajap_genome
    output: /home/jon/Working_Files/dentist/TAN.Ajap_genome.1.las
    log: /home/jon/Working_Files/dentist/logs/tandem-alignment.Ajap_genome.1.log
    jobid: 16
    wildcards: dam=Ajap_genome, block=1
    threads: 70
    resources: tmpdir=/tmp

INFO:    Converting SIF file to temporary sandbox...
File pacbio_SRR6282347.fasta, Line 1: Pacbio header line format error
INFO:    Cleaning up image...
[Tue Sep 28 20:43:36 2021]
Error in rule reads2db:
    jobid: 6
    output: /home/jon/Working_Files/dentist/pacbio_SRR6282347.db, /home/jon/Working_Files/dentist/.pacbio_SRR6282347.bps, /home/jon/Working_Files/dentist/.pacbio_SRR6282347.idx
    shell:
        fasta2DB /home/jon/Working_Files/dentist/pacbio_SRR6282347.db pacbio_SRR6282347.fasta && DBsplit -x1000 -a -s200 /home/jon/Working_Files/dentist/pacbio_SRR6282347.db
        (one of the commands exited with non-zero exit code; note that snakemake uses bash strict mode!)

Activating singularity image /home/jon/Working_Files/dentist/.snakemake/singularity/1aa939115af17aa65dcd7164899b9ec7.simg
INFO:    Converting SIF file to temporary sandbox...
INFO:    Cleaning up image...
[Tue Sep 28 20:43:41 2021]
Error in rule tandem_alignment_block:
    jobid: 16
    output: /home/jon/Working_Files/dentist/TAN.Ajap_genome.1.las
    log: /home/jon/Working_Files/dentist/logs/tandem-alignment.Ajap_genome.1.log (check log file(s) for error message)
    shell:
        
            {
                cd /home/jon/Working_Files/dentist
                datander '-T70' -s126 -l500 -e0.7 Ajap_genome.1
            } &> /home/jon/Working_Files/dentist/logs/tandem-alignment.Ajap_genome.1.log
        
        (one of the commands exited with non-zero exit code; note that snakemake uses bash strict mode!)

Shutting down, this might take some time.
Exiting because a job execution failed. Look above for error message
Complete log: /home/jon/Working_Files/dentist/.snakemake/log/2021-09-28T204325.753521.snakemake.log
```
