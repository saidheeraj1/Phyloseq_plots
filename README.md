# Phyloseq_plots
Includes different plots like Bar plot, tree diagram etc
# Tree diagram
> library("ape")
> physeq = phyloseq(newOTU, newTAX)
> newrandom_tree = rtree(ntaxa(physeq), rooted = TRUE, tip.label = taxa_names(physeq))
> plot(random_tree)
> physeq1 = phyloseq(newOTU, newTAX, newrandom_tree)
# Bar plot
> plot_bar(physeq1, fill="taxonomy3")
# Ordination
> GP.chl = subset_taxa(physeq1)

> GP.chl = prune_samples(names(which(sample_sums(GP.chl) >= 20)), GP.chl)

> GP.chl.r = rarefy_even_depth(GP.chl)

> GP.chl

> gpsfb.wUF = distance(GP.chl.r, "unifrac", weighted = TRUE)

> gpsfb.NMDS = ordinate(GP.chl.r, "CCA", gpsfb.wUF)

> library("ggplot2")

> p1 = plot_ordination(GP.chl.r, gpsfb.NMDS, "taxa", color = "taxonomy5", title = "plot_ordination, CCA, wUF")

> '?'(plot_ordination)

> p1

> p1 + facet_wrap(~taxonomy5, 3)

(p <- plot_heatmap(GP.chl.r, "NMDS", "bray", "taxa", "taxonomy5"))

> p2 <- plot_net(GP.chl.r)

> p2

# Network diagram
> g <- make_network(physeq1, type = "taxa",color = "taxonomy3", max.dist = 0.4)

> g

> plot_network(g, physeq1, type="taxa")

