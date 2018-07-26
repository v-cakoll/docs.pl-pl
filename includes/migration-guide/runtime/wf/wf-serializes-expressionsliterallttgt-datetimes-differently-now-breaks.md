### <a name="wf-serializes-expressionsliterallttgt-datetimes-differently-now-breaks-custom-xaml-parsers"></a>WF serializuje Expressions.Literal&lt;T&gt; Data/Godzina inaczej, teraz (przerywa niestandardowe analizatory XAML)

|   |   |
|---|---|
|Szczegóły|Skojarzone <xref:System.Windows.Markup.ValueSerializer> przekonwertuje obiekt <xref:System.DateTime?displayProperty=name> lub <xref:System.DateTimeOffset?displayProperty=name> obiektu, którego drugi i <xref:System.DateTime.Millisecond?displayProperty=name> składników jest różna od zera i (dla <xref:System.DateTime?displayProperty=name> wartość) którego <xref:System.DateTime.Kind> właściwość nie jest nieokreślona do elementu właściwości Składnia zamiast ciągu. Dzięki tej zmianie <xref:System.DateTime?displayProperty=name> i <xref:System.DateTimeOffset?displayProperty=name> wartości rundę. Niestandardowe analizatory języka XAML, które zakładają, że wejściowy kod XAML znajduje się w składni atrybutów, nie będą działać poprawnie.|
|Sugestia|Dzięki tej zmianie <xref:System.DateTime?displayProperty=name> i <xref:System.DateTimeOffset?displayProperty=name> wartości rundę. Niestandardowe analizatory języka XAML, które zakładają, że wejściowy kod XAML znajduje się w składni atrybutów, nie będą działać poprawnie.|
|Zakres|Krawędź|
|Wersja|4.5|
|Typ|Środowisko uruchomieniowe|

