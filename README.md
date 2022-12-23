# hw1
## Anaconda task
`conda create --name hw1env` creating an environement "hw1env"

`conda activate hw1env` activating the created environment

Installing specific versions of the packages:

`conda install -c bioconda fastqc=0.11.9`

`conda install -c bioconda star=2.7.10b`

`conda install -c bioconda -c conda-forge -c defaults samtools=1.16.1`

`conda install -c bioconda picard=2.27.5`

*(this version doesn’t exist, so installing the latest version 2.27.4)*

`conda install -c bioconda picard=2.27.4`

`conda install -c bioconda -c conda-forge -c defaults salmon=1.9.0`

`conda install -c bioconda bedtools=2.30.0`

`conda install -c bioconda -c conda-forge -c defaults multiqc=1.13`

`conda list -n hw1env` checking the installed packages

-c flag stands for --channel, which are locations where conda looks for packages

Exporting the environment file with only the installed packages:
`conda env export > hw1env.yml --from-history`
To check if the environment works we can use
`conda env remove --name hw1env

conda env create -f hw1env.yml

conda activate hw1env`


<img width="498" alt="Screenshot 2022-12-22 at 08 06 09" src="https://user-images.githubusercontent.com/121194805/209070524-3de380d8-1728-4ead-92a0-d59c8a16e49d.png">
