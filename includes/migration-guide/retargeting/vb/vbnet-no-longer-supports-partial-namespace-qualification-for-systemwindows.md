### <a name="vbnet-no-longer-supports-partial-namespace-qualification-for-systemwindows-apis"></a>VB.NET nie obsługuje już kwalifikacji częściowe przestrzeń nazw dla interfejsów API System.Windows

|   |   |
|---|---|
|Szczegóły|Począwszy od wersji 4.5.2 .NET, projektach VB.NET nie można określić interfejsy API System.Windows z częściowo kwalifikowana przestrzeni nazw. Na przykład odwołujących się do <code>Windows.Forms.DialogResult</code> zakończy się niepowodzeniem. Zamiast tego kodu musi odwoływać się do w pełni kwalifikowana nazwa (<xref:System.Windows.Forms.DialogResult>) lub importowanie określonych przestrzeni nazw i odwoływać się tylko do <xref:System.Windows.Forms.DialogResult?displayProperty=name>.|
|Sugestia|Kod powinien zostać zaktualizowany do odwoływania się do <code>System.Windows</code> interfejsów API proste nazwy (i importowania odpowiednich przestrzeni nazw) albo w pełni kwalifikowane nazwy.|
|Zakres|Pomocnicza|
|Wersja|4.5.2|
|Typ|Przekierowania|

