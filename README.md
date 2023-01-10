# User Guide of SCRL

##Introduction

This is the SCRL toolkit developed for learning meaningful representations for scRNA-seq data by integrating multiple source of network information, which also helps overcoming the high noise of scRNA-seq data. Please ensure that the GSL package (http://www.gnu.org/software/gsl/) is installed on your Linux.
```
Xiangyu Li (xyli2011@sina.com or lixiangyu13@tsinghua.org.cn) 
```

##Usage
```
./SCRL -train_net cell_context.txt -train_prior gene_context.txt -output_cell cell_emb.txt -output_gene gene_emb.txt –output_context context_emb.txt -binary 0 -size 200 -negative 5 -samples 1000 -rho 0.025 -threads 100 -plambda 1 -pgamma 1 
```

- -train_net, the input file of the cell-context gene network;
- -train_prior, the input file of the gene-context gene network;
- -output_cell, the output file of the cell representation learning;
- -output_gene, the output file of the gene representation learning;
- -output_context, the output file of the context-gene representation learning;
- -binary, whether saving the output file in binary mode; the default is 0 (off);
- -negative, the number of negative samples used in negative sampling; the deault is 5;
- -rho, the starting value of the learning rate; the default is 0.025;
- -samples, the total number of training samples (*Million);
- -threads, the total number of threads used; the default is 1;
- -plambda, the weight of the cell-context gene network;
- -pgamma, the weight of the gene-gene network.

##Network Input

The file cell_context.txt contains the edges of the cell-context network, the format of each row is "cell context-gene expression" (can be either separated by blank or tab). An example is given below:
```
ICM_EPI_SC4     A1BG    0.0173315
ICM_PE_SC1      A1BG    0.0117372
ICM_PE_SC2      A1BG    2.74588
ICM_PE_SC3      A1BG    0.796826
ICM_PE_SC4      A1BG    0.667247
```

The file gene_context.txt contains the edges of the gene-context network, the format of each row is "gene context-gene weight" (can be either separated by blank or tab). An example is given below:
```
NDUFV2   SURF1   1
SURF1    NDUFV2  1
PRKDC    VCAM1   1
VCAM1    PRKDC   1
```
