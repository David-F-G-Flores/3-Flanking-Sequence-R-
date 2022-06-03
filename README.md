# Flanking-Sequence-R-
To extract 50bp flanking sequence from biomaRt using rsID.

```R
Flanks <- list()

for (snp in rsIDs) {
  print(snp)
  flanks <- getBM(attributes=c('refsnp_id'
                            ,'snp'
                            ,'ensembl_peptide_allele'
                            , 'allele'
                            , 'chr_name'),filters=c('snp_filter','downstream_flank','upstream_flank'),value=list(snip,downstream=50,upstream=50),mart = snpmart, checkFilters=F)
  Flanks[[snp]] <- flanks
}

Flanks<-do.call('rbind',Flanks)  ## list to df 
```
