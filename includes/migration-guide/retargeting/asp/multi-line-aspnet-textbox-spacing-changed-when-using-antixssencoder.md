### <a name="multi-line-aspnet-textbox-spacing-changed-when-using-antixssencoder"></a>Wielowierszowego pola tekstowego ASP.Net odstępy zmienić przy użyciu AntiXSSEncoder

|   |   |
|---|---|
|Szczegóły|.NET Framework 4.0, dodatkowe wiersze zostały wstawione między wierszami wielowierszowego pola tekstowego na ogłaszania zwrotnego, jeśli przy użyciu <xref:System.Web.Security.AntiXss.AntiXssEncoder?displayProperty=name>. W programie .NET Framework 4.5 te dodatkowe podziały wiersza nie są uwzględnione, ale tylko wtedy, gdy aplikacja sieci web jest przeznaczonych dla platformy .NET Framework 4.5|
|Sugestia|Należy pamiętać, że przekierować .NET Framework 4.5 4.0 aplikacje sieci web może mieć tekstu wielowierszowego pola zwiększona do wstawienia nie jest już dodatkowe podziały wiersza. Jeśli nie jest to pożądane, aplikacja może mieć stare zachowanie podczas uruchamiania na .NET Framework 4.5, wybierając programu .NET Framework 4.0.|
|Zakres|Pomocnicza|
|Wersja|4.5|
|Typ|Przekierowania|

