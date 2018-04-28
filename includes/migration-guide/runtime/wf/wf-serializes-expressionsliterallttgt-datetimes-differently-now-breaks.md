### <a name="wf-serializes-expressionsliterallttgt-datetimes-differently-now-breaks-custom-xaml-parsers"></a>WF serializuje Expressions.Literal&lt;T&gt; dat i godzin inaczej teraz (dzieli niestandardowych XAML analizatory składni)

|   |   |
|---|---|
|Szczegóły|Skojarzony <xref:System.Windows.Markup.ValueSerializer> przekonwertuje obiektu <xref:System.DateTime?displayProperty=name> lub <xref:System.DateTimeOffset?displayProperty=name> obiekt, którego drugi i <xref:System.DateTime.Millisecond?displayProperty=name> składników jest różna od zera i (dla <xref:System.DateTime?displayProperty=name> wartość) którego <xref:System.DateTime.Kind> właściwość nie jest nieokreślony do właściwości elementu Składnia zamiast ciągu. Ta zmiana umożliwia <xref:System.DateTime?displayProperty=name> i <xref:System.DateTimeOffset?displayProperty=name> można wysyłać, zwracać wartości. Niestandardowe analizatory języka XAML, które zakładają, że wejściowy kod XAML znajduje się w składni atrybutów, nie będą działać poprawnie.|
|Sugestia|Ta zmiana umożliwia <xref:System.DateTime?displayProperty=name> i <xref:System.DateTimeOffset?displayProperty=name> można wysyłać, zwracać wartości. Niestandardowe analizatory języka XAML, które zakładają, że wejściowy kod XAML znajduje się w składni atrybutów, nie będą działać poprawnie.|
|Zakres|Krawędź|
|Wersja|4.5|
|Typ|Środowisko uruchomieniowe|

