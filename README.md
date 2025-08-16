To use in codespaces, hover over the green code tab, select 'codespaces' and activate. Once everything installs and loads (could be some time, perhaps 10 minutes), to use RStudio Server go to the ports tab in VScode. Hover over the Forwarded Address column in the 8787 row and click the globe. The username and password are both "rstudio".

To pull up the R notebook, go to File>Open File and input /workspaces/enrichment_class/enrichment_cluster_profiler.Rmd

Be aware if you do nothing in the VS Code view for 30 minutes, the R Studio will time out.Possible options to prevent this are running `watch -n 1000 ls` in the terminal of the VS Code view, or going to the Github main page, clicking on your avatar in the right-hand corner, selecting "Settings", then finding "Codespaces" on the left-hand menu bar. Finally, you can set the idle time allowed.

Then you'll be ready to start!
