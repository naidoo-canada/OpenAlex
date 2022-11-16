library(tidyverse)
library(treemapify)

dataDir <- '/Users/rnaidoo/Documents/Canada-Secure/GAC/2022_MDRID/Projects_data/OpenAlex/works_ES_first_auth/CA_col/'
graphicsDir <- '/Users/rnaidoo/Documents/Canada-Secure/GAC/2022_MDRID/Projects/OpenAlex/Concept_Treemap/graphics/'

concept_level <- '5'

#Prepare Data
concepts_fn <- paste0(dataDir, 'works_by_concept_', concept_level, '_ES-CA.csv')
df_conc <- read.csv(concepts_fn) %>%
  rename(citations = cited_by_count) %>%
  top_n(50)

#Treemap Plot
title_str <- 'Spain-Canada academic collaborations by concepts (top-50)'
subtitle_str <- paste0('Concept level ', concept_level)
p <- ggplot(df_conc, aes(area=publications, fill=publications, label=concept)) +
  geom_treemap(start='topleft') +
  geom_treemap_text(colour = '#ededed', #c(rep("white", 6), "#ff96a4", rep("white", 9)
                    place = "centre",
                    size = 32,
                    grow = FALSE,
                    start='topleft') +
  scale_fill_gradient(low = '#AD1519', high = '#FABD00') + #blue ('#030933', '#235ee8', '#c7dfff), #green ('#033311', '#008751', '#ff96a4), #red ('#260601', 'E8112D', 'E8112D), #yellow ('#bf4200', '#F99915', '#F9D615')
  labs(title=title_str, subtitle=subtitle_str) +
  theme(
    plot.title = element_text(hjust=0, size=18, face='bold', family='sans', margin=margin(0,0,6,0)),
    plot.subtitle = element_text(hjust=0, size=12, family='sans', margin=margin(0,0,6,0)),
    #legend.title = element_text(hjust=0, size=10, face='bold', family='sans', margin=margin(0,0,10,0)),
  )
ggsave(filename=paste0(graphicsDir, 'ES-CA_concept_', concept_level, '.png'), plot=p, width=15, height=15)
