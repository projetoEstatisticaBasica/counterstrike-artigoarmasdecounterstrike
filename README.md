# counterstrike-artigoarmasdecounterstrike
este repositorio estuda inumeras partidas , dados, armas e etc de counter strike

# Carregar pacotes necessários
```r
library(ggplot2)
library(dplyr)
```
# Criar dataframe
```r
data <- data.frame(
  Weapon = c("AK-47", "M4A1-S", "AWP", "M4A1", "USP-S", "Desert Eagle", "Glock-18", 
             "Galil AR", "FAMAS", "P90", "SG 553", "MP9", "AUG", "MAC-10", "MP7", 
             "P250", "Tec-9", "XM1014", "G3SG1", "P2000"),
  KPR = c(1.2, 1.1, 1.6, 1.2, 0.9, 0.9, 0.9, 1.1, 1.0, 1.0, 1.2, 0.8, 1.3, 0.8, 1.0, 
          0.7, 0.8, 1.0, 1.9, 0.8),
  HS_Percent = c(17.8, 14.6, 14.5, 18.0, 21.2, 28.5, 17.8, 18.1, 18.9, 10.0, 13.8, 
                 12.5, 12.7, 11.4, 9.0, 18.2, 14.9, 10.9, 15.1, 13.9),
  Chest_Percent = c(59.4, 60.3, 68.7, 60.6, 63.5, 58.7, 65.5, 57.6, 58.7, 58.3, 59.7, 
                    62.4, 61.4, 60.3, 59.1, 63.3, 63.2, 59.3, 61.3, 67.0),
  Leg_Percent = c(16.7, 18.3, 10.1, 15.5, 10.5, 9.0, 11.8, 18.4, 16.9, 24.1, 18.8, 
                  18.1, 18.5, 21.2, 24.0, 13.0, 15.6, 22.0, 15.5, 13.3),
  Total_Kills = c(370567, 181934, 164754, 104012, 94958, 84197, 83899, 63215, 50834, 
                  27907, 27572, 25846, 25335, 20285, 15535, 12575, 11796, 10428, 9289, 8306)
)
```

# Estatísticas descritivas
summary(data)


# KPR por arma
```r
ggplot(data, aes(x = reorder(Weapon, -KPR), y = KPR)) +
  geom_bar(stat = "identity") +
  coord_flip() +
  labs(title = "Kills Per Round (KPR) por Arma", x = "Arma", y = "KPR") +
  theme_minimal()
```

# Porcentagem de headshots por arma
```r
ggplot(data, aes(x = reorder(Weapon, -HS_Percent), y = HS_Percent)) +
  geom_bar(stat = "identity", fill = "midnightblue") +
  coord_flip() +
  labs(title = "Porcentagem de Headshots por Arma", x = "Arma", y = "HS %") +
  theme_minimal()
```

# Distribuição dos tiros (peito e pernas)
```r
ggplot(data, aes(x = reorder(Weapon, -Chest_Percent), y = Chest_Percent)) +
  geom_bar(stat = "identity", fill = "lightgreen") +
  coord_flip() +
  labs(title = "Porcentagem de Tiros no Peito por Arma", x = "Arma", y = "Chest %") +
  theme_minimal()
 ```
```r
ggplot(data, aes(x = reorder(Weapon, -Leg_Percent), y = Leg_Percent)) +
  geom_bar(stat = "identity", fill = "darkred") +
  coord_flip() +
  labs(title = "Porcentagem de Tiros nas Pernas por Arma", x = "Arma", y = "Leg %") +
  theme_minimal()
```
