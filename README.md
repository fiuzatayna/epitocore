# EpitoCore

**EpitoCore** is a peptide-centric epitope prediction tool which takes into consideration pangenomic variation across strains of a given dataset, and reports conserved epitopes between homologues of those strains.

The EpitoCore program has been added to a Docker container in order to simplify installation.

This repository contains a Docker buildfile (Dockerfile) and folders with scripts and dependencies. To run this app the user must have admin rights.

To build the app you must clone this repository:

git clone https://github.com/fiuzatayna/epitocore
cd epitocore
docker etc etc copiar comando certinho

**Running an EpitoCore analysis**

1. Enter the epitocore container:

```console
docker etc etc
```

You can open another terminal inside this same container using your running container id. Example: docker exec -it 109cff9ce41b bash

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
chmod u+x command_sequence.sh
./command_sequence.sh
```

5. Inspect how many strains your species of interest has and other information with:

How many strains
```console
ls get_proteome_output/ | wc -l
```

How many proteins
```console
wc -l tmhmm_output/*
```

How many alpha transmembrane domain containing proteins
```console
wc -l filtered_tmhmm_output/*
```

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


