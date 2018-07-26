### <a name="entity-framework-version-must-match-the-net-framework-version"></a>Entity Framework w wersji musi odpowiadać wersji programu .NET Framework

|   |   |
|---|---|
|Szczegóły|Programu entity framework w wersji powinny zostać dopasowane do wersji programu .NET framework. Entity Framework 5 jest zalecane dla platformy .NET Framework 4.5. Istnieje kilka znanych problemów z programem EF 4.x w projekcie programu .NET Framework 4.5 wokół <xref:System.ComponentModel.DataAnnotations>. W .NET 4.5 te zostały przeniesione do innego zestawu, dzięki czemu nie występują problemy, określająca, które adnotacje do użycia.|
|Sugestia|Uaktualnianie do programu Entity Framework 5 dla programu .NET Framework 4.5|
|Zakres|Główne|
|Wersja|4.5|
|Typ|Trwa przekierowywanie|

