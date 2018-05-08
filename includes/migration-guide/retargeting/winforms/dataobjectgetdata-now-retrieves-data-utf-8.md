### <a name="dataobjectgetdata-now-retrieves-data-as-utf-8"></a>Teraz DataObject.GetData pobiera dane jako UTF-8

|   |   |
|---|---|
|Szczegóły|W przypadku aplikacji, które programem .NET Framework 4 lub działającymi w .NET Framework 4.5.1 lub starszych wersjach <code>DataObject.GetData</code> pobiera dane w formacie HTML jako ciąg ASCII. W związku z tym znaki spoza zestawu ASCII (znaki, których kodów ASCII są większe niż 0x7F) są reprezentowane przez dwa losowo wybranych znaków.<p/>Dla aplikacji przeznaczonych dla platformy .NET Framework 4.5 lub nowszy i uruchom na programie .NET Framework 4.5.2 <code>DataObject.GetData</code> pobiera dane w formacie HTML jako UTF-8, które reprezentuje znaków przekracza 0x7F poprawnie.|
|Sugestia|Jeśli zaimplementowano obejścia kodowania problemu z ciągami w formacie HTML (na przykład do jawnie kodowanie ciągu HTML pobrane ze Schowka przez przekazanie jej <xref:System.Text.UTF8Encoding.GetString(System.Byte[],System.Int32,System.Int32)?displayProperty=name>) i jest przekierowania aplikacji z wersji 4 do 4.5, który Obejście powinna zostać usunięta. Jeśli poprzednie działanie nie jest konieczne jakiegoś powodu, aplikacji można kierować programu .NET Framework 4.0 można pobrać tego zachowania.|
|Zakres|Krawędź|
|Wersja|4.5.2|
|Typ|Przekierowania|
|Dotyczy interfejsów API|<ul><li><xref:System.Windows.DataObject.GetData(System.String)?displayProperty=nameWithType></li><li><xref:System.Windows.DataObject.GetData(System.Type)?displayProperty=nameWithType></li><li><xref:System.Windows.DataObject.GetData(System.String,System.Boolean)?displayProperty=nameWithType></li></ul>|

