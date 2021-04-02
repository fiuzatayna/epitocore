# EpitoCore

**EpitoCore** is a peptide-centric epitope prediction tool which takes into consideration pangenomic variation across strains of a given dataset, and reports conserved epitopes between homologues of those strains.

The EpitoCore program has been added to a Docker container in order to simplify installation.

This repository contains a Docker buildfile (Dockerfile) and folders with scripts and dependencies. To run this app the user must have admin rights.

**To build the container** 

Clone this repository:

```console
git clone https://github.com/fiuzatayna/epitocore
cd epitocore
```
Extract and enter docker folder:

```console
tar -xf EpitoCore_docker.tar.xz
cd EpitoCore
```
Build docker container:
```console
docker build -t epitocore .
```

**Running an EpitoCore analysis**

1. Enter the epitocore container:

```console
docker run -v [local path or $PWD]/Output:/home/Output -it epitocore /bin/bash
```

You can open another terminal inside this same container using your running container id. 
*Example: docker exec -it 109cff9ce41b bash*

2. Open the command_sequence.sh script

```console
nano command_sequence.sh
```

3. Insert species of interest name between the quotes in line

```console
echo " " > species_file
```

4. Run command_sequence.sh script

```console
./command_sequence.sh
```

The script will run each part of the code in sections until the IEDB immuno prediction is performed, then it will prompt:

- [ ] Number of strains
- [ ] Number of proteins
- [ ] Number of Alpha Transmembrane Domain Containing Proteins

Afterwards it will open a configuration_file file used by the R analysis and user must include

- [ ] IEDB consensus percentile rank thresholds
- [ ] Minimal number of strains in which a candidate peptide must be found
- [ ] Name of CMG Biotools clustering file

**Additional**

Inspect how many strains your species of interest has and other information with:

###### *Count strains*
```console
ls get_proteome_output/ | wc -l
```

###### *Count proteins*
```console
wc -l tmhmm_output/*
```

###### *Count alpha transmembrane domain containing proteins*
```console
wc -l filtered_tmhmm_output/*
```


###### *Open another terminal on the same container*
```console
docker exec -it [CONTAINERID] bash
```


<!---
6. Configure parameters for epitope selection 

```console
nano /scripts/configuration_file.R
```

7. Execute the r_command_sequence.sh 

```console
chmod u+x r_command_sequence.sh
./r_command_sequence.sh
```

8. Export results to your host machine
-->

