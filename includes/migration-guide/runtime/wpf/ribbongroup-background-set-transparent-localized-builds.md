### <a name="ribbongroup-background-is-set-to-transparent-in-localized-builds"></a>Tło RibbonGroup ustawiono przezroczyste w kompilacjach zlokalizowanych

|   |   |
|---|---|
|Szczegóły|<xref:System.Windows.Controls.Ribbon.RibbonGroup?displayProperty=name> tło zlokalizowanego w przypadku kompilacji zawsze został rysowane z przezroczystym pędzla, co spowoduje niską możliwości interfejsu użytkownika. Problem jest rozwiązany w .NET Framework 4,7 poprawka WPF, aktualizując zlokalizowanych zasobów dla <xref:System.Windows.Controls.Ribbon.RibbonGroup?displayProperty=name>, co zapewnia z kolei, że wybrano poprawny pędzla.|
|Sugestia|Uaktualnij do platformy .NET Framework 4.7|
|Zakres|Krawędź|
|Wersja|4.6.2|
|Typ|Środowisko uruchomieniowe|

