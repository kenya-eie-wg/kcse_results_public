dadaab_subtotals <- dadaab %>% 
  filter(grade %out% c("X", "Y", "U", "P", "--")) %>% 
  group_by(year) %>% 
  summarise(count = n())

papers_graded <- dadaab %>% 
  filter(grade %out% c("X", "Y", "U", "P", "--")) %>% 
  group_by(subject, year) %>%
  summarise(count = n()) %>% 
  filter(subject %out% c("biology_for_the_blind", 
                         "maths_b", 
                         "general_science")) %>% 
  ggplot(aes(x = year, y = count, fill = subject))  + 
  geom_col() + 
  geom_text(aes(year, count, label = comma(count), fill = NULL), 
            data = dadaab_subtotals, 
            vjust = -1) + 
  scale_y_continuous(labels = comma) + 
  labs(title = "Number of papers graded per year per subject in Dadaab")

ggplotly(papers_graded)