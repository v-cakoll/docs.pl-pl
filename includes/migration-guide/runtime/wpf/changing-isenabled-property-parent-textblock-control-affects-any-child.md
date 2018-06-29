### <a name="changing-the-isenabled-property-of-the-parent-of-a-textblock-control-affects-any-child-controls"></a>Zmiana wartości właściwości IsEnabled nadrzędny blok tekstu formantu ma wpływ na wszystkie formanty podrzędne

|   |   |
|---|---|
|Szczegóły|Począwszy od programu .NET Framework 4.6.2, zmiana <xref:System.Windows.UIElement.IsEnabled?displayProperty=name> właściwości elementu nadrzędnego <xref:System.Windows.Controls.TextBlock?displayProperty=name> formantu ma wpływ na wszystkie formanty podrzędne (na przykład hiperłącza i przyciski) <xref:System.Windows.Controls.TextBlock?displayProperty=name> formantu. W programie .NET Framework 4.6.1 i wcześniejszych wersjach, kontrolki wewnątrz <xref:System.Windows.Controls.TextBlock?displayProperty=name> nie odzwierciedlała zawsze stan <xref:System.Windows.UIElement.IsEnabled?displayProperty=name> właściwości <xref:System.Windows.Controls.TextBlock?displayProperty=name> nadrzędnego.|
|Sugestia|Brak. Ta zmiana odpowiada oczekiwane zachowanie formanty <xref:System.Windows.Controls.TextBlock?displayProperty=name> formantu.|
|Zakres|Pomocnicza|
|Wersja|4.6.2|
|Typ|środowisko uruchomieniowe|
|Dotyczy interfejsów API|<ul><li><xref:System.Windows.UIElement.IsEnabled?displayProperty=nameWithType></li></ul>|

