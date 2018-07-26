### <a name="multi-line-aspnet-textbox-spacing-changed-when-using-antixssencoder"></a>Wielowierszowe pole tekstowe ASP.Net odstępy zmieniany, gdy za pomocą AntiXSSEncoder

|   |   |
|---|---|
|Szczegóły|W programie .NET Framework 4.0 dodatkowe wiersze zostały wstawione między wierszami wielowierszowego pola tekstowego na odświeżenie strony, jeśli za pomocą <xref:System.Web.Security.AntiXss.AntiXssEncoder?displayProperty=name>. Te dodatkowe podziały wiersza .NET Framework 4.5, nie są uwzględnione, ale tylko wtedy, gdy aplikacja sieci web jest przeznaczony dla .NET Framework 4.5|
|Sugestia|Należy pamiętać, że 4.0 aplikacji sieci web, ukierunkowany na .NET Framework 4.5 może mieć pól tekstu wielowierszowego ulepszony, aby nie jest już wstawić dodatkowe podziały wiersza. Jeśli nie jest to pożądane, aplikacja może mieć stare zachowanie podczas uruchamiania na .NET Framework 4.5, przeznaczonych dla programu .NET Framework 4.0.|
|Zakres|Pomocnicza|
|Wersja|4.5|
|Typ|Trwa przekierowywanie|

