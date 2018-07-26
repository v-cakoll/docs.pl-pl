### <a name="changing-the-isenabled-property-of-the-parent-of-a-textblock-control-affects-any-child-controls"></a>Zmiana właściwości IsEnabled elementu nadrzędnego formant TextBlock wpływa formanty podrzędne

|   |   |
|---|---|
|Szczegóły|Począwszy od programu .NET Framework 4.6.2, zmieniając <xref:System.Windows.UIElement.IsEnabled?displayProperty=name> właściwości elementu nadrzędnego <xref:System.Windows.Controls.TextBlock?displayProperty=name> kontroli ma wpływ na formanty podrzędne (takie jak hiperłącza i przyciski) z <xref:System.Windows.Controls.TextBlock?displayProperty=name> kontroli. W .NET Framework 4.6.1 i wcześniejszych wersjach, kontroluje wewnątrz <xref:System.Windows.Controls.TextBlock?displayProperty=name> nie zawsze odzwierciedlają stan <xref:System.Windows.UIElement.IsEnabled?displayProperty=name> właściwość <xref:System.Windows.Controls.TextBlock?displayProperty=name> nadrzędnej.|
|Sugestia|Brak. Ta zmiana jest zgodny z oczekiwane zachowanie formanty <xref:System.Windows.Controls.TextBlock?displayProperty=name> kontroli.|
|Zakres|Pomocnicza|
|Wersja|4.6.2|
|Typ|Środowisko uruchomieniowe|
|Dotyczy interfejsów API|<ul><li><xref:System.Windows.UIElement.IsEnabled?displayProperty=nameWithType></li></ul>|

