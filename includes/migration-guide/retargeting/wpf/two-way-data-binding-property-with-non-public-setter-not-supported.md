### <a name="two-way-data-binding-to-a-property-with-a-non-public-setter-is-not-supported"></a>Dwukierunkowego powiązania danych właściwości setter niepublicznych nie jest obsługiwane.

|   |   |
|---|---|
|Szczegóły|Próba powiązania danych właściwości bez publicznej metody ustawiającej nigdy nie było obsługiwanym scenariuszem. Począwszy od programu .NET Framework 4.5.1, w tym scenariuszu zgłosi <xref:System.InvalidOperationException?displayProperty=name>. Należy pamiętać, że ten nowy będą tylko wyjątek dla aplikacji, które w szczególności dla środowiska .NET Framework 4.5.1. Jeśli aplikacja jest przeznaczony dla platformy .NET Framework 4.5, wywołanie będzie dozwolone. Jeśli aplikacja nie wskazuje konkretnej wersji .NET Framework, powiązanie będą traktowane jako jednokierunkowe.|
|Sugestia|Aplikacja powinny zostać uaktualnione do Użyj powiązania jednokierunkowe lub publicznie uwidacznia metody ustawiającej właściwość. Alternatywnie przeznaczonych dla platformy .NET Framework 4.5 spowoduje, że aplikacja starego zachowują się.|
|Zakres|Pomocnicza|
|Wersja|4.5.1|
|Typ|Przekierowania|
|Dotyczy interfejsów API|<ul><li><xref:System.Windows.Data.BindingMode.TwoWay?displayProperty=nameWithType></li></ul>|

