---
title       : On the importance of small changes in RNA expression.
subtitle    : St Laurent, G., Shtokalo, D., Tackett, M.R., Yang, Z., Vyatkin, 
              Y. Milos, P.M., Seilheimer, B., McCaffrey, T.A., Kapranov, P.
author      : Keith Hughitt
job         : 
framework   : io2012        # {io2012, html5slides, shower, dzslides, ...}
highlighter : highlight.js  # {highlight.js, prettify, highlight}
hitheme     : solarized_light
widgets     : [mathjax]
github:
  user: khughitt
  repo: slidify-small-changes-in-rna-expression
mode        : selfcontained # {standalone, draft}
--- .segue .dark

<!-- Custom Styles -->
<style type='text/css'>
    slides > slide {
        height: 800px;
        margin-top: -400px;
    }
    img {
        max-height: 560px;
        max-width: 964px;
    }
    slide a {border-bottom: none;}
    .references li { font-size: 18px; }
</style>

## Background

---

## Motivation

>- Often transcript profiling (microarray, RNA-Seq, etc) experiment are
   conducted, and "differentially expressed" genes are determined based on 
   thresholds for:
    1. Fold change (FC)
    2. p-value
>- Setting a minimum p-value makes sense, but what about the FC requirement?
   There are several possible reasons for setting a minumum fold change.
>- There are at least a couple reasons this is done:
    1. Noisy data collection (ligation, amplification, imperfect sampling)
    2. Assumption that most interested biological effects will involve large
       increases/decreases in transcript levels.
>- However:
    * Are these valid assumptions?
    * What effect do these thresholds have on the loss of biological 
      information?

---

## Approach

Figure 1: Example fold changes for markers of early immune response

![Fig1](assets/img/1-s2.0-S1046202313000960-gr1.jpg)

--- .segue .dark

## Results

---

## Question: How often are p-value and/or FC cutoffs applied?

### Approach
>- Pulled 40 most recent papers in PubMed for query "microarray expression
   profiling" (...It would be interesting to know results for "RNA-Seq")

### Result
>- At least 50% of studied applied a FC cutoff (the rest used p-values only)
>- This means that any biologically relevant DE genes below the FC cutoff
   will be missed.

---

## Question: What is the average fold change cutoff used?

### Approach
>- Sampled 10 papers for which FC filtering was used.

### Result
>- Papers used a cutoff of either 1.5 or 2.0. ($\mu = 1.725$)
>- Authors also suggest, however, that based on MAQC study results, microarrays
   tend to underestimate the actual FC compared with qRTPCR (Canales et al. 
   2006).
>- Adjusted microarray cutoff likely closer to 3.45.

---

## Question: Which statistical methods work best for detecting low FC genes?

### Approach
>1. Compared performance of six different methods for detecting genes with < 2
FC:
    - edgeR
    - t-test
    - DESeq
    - baySeq
    - Welch's test
    - NOIseq
>2. <span class='blue'>Performance metric</span>: Enrichment of a subset of
the 23 inflammation-related GO categories.
    * For each method, sorted genes by p-value, selected top 2000 genes, and
      selected upregulated genes with FC < 2.
    * GO enrichment evaluated using the Fisher exact test, adjusted for
      multiple testing with the Benjamini-Hochberg correction.
    * Control: randomized timepoints

---

## Question: Which statistical methods work best for detecting low FC genes?

### Result

>1. Overall, methods all performed pretty similarly:
    - <span class='blue'>Number genes</span>
        * 355 (DESeq)
        * 410 (edgeR)
    - <span class='blue'>p-value (Immune system response)</span>
        * 4.36E-41 (baySeq)
        * 3.91E-47 (t-test)
>2. Best method, however: Keep any gene found by at least one of the methods
    - 631 genes
    - p-value: <1E-50
>3. <span class='red'>Conclusion</span>: Existing methods are sufficient to
    detect biologically meaningful enrichment at low FC.

--- .references

## References





- Roger D Canales, Yuling Luo, James C Willey, Bradley Austermiller, Catalin C Barbacioru, Cecilie Boysen, Kathryn Hunkapiller, Roderick V Jensen, Charles R Knight, Kathleen Y Lee, Yunqing Ma, Botoul Maqsodi, Adam Papallo, Elizabeth Herness Peters, Karen Poulter, Patricia L Ruppel, Raymond R Samaha, Leming Shi, Wen Yang, Lu Zhang, Federico M Goodsaid,   (2006) Evaluation of Dna Microarray Results With Quantitative Gene Expression Platforms.  <em>Nature Biotechnology</em>  <strong>24</strong>  1115-1122  <a href="http://dx.doi.org/10.1038/nbt1236">10.1038/nbt1236</a>
- Georges St. Laurent, Dmitry Shtokalo, Michael R. Tackett, Zhaoqing Yang, Yuri Vyatkin, Patrice M. Milos, Bernd Seilheimer, Timothy A. McCaffrey, Philipp Kapranov,   (2013) on The Importance of Small Changes in Rna Expression.  <em>Methods</em>  <strong>63</strong>  18-24  <a href="http://dx.doi.org/10.1016/j.ymeth.2013.03.027">10.1016/j.ymeth.2013.03.027</a>


<!-- Custom JavaScript -->
<script src="http://ajax.aspnetcdn.com/ajax/jQuery/jquery-1.7.min.js"></script>
<script type='text/javascript'>
$(function() {
    $("p:has(img)").addClass('centered');
});
</script>


