### <a name="flowdocument-may-show-an-extra-line-of-text"></a>FlowDocument mogą być wyświetlane dodatkowe wiersza tekstu

|   |   |
|---|---|
|Szczegóły|W niektórych przypadkach <xref:System.Windows.Documents.FlowDocument> elementu wyświetli dodatkowy wiersz tekstu uruchomionej na środowisko .NET Framework 4.5, w porównaniu do sposób wyświetlania po uruchomieniu programu .NET Framework 4.0. Istnieją żadne znane przypadki zmiany powodujące tekst mają być wyświetlane nieprawidłowo lub illegibly, ale może spowodować, że tekst, który wcześniej został pominięty <xref:System.Windows.Documents.FlowDocument>do wyświetlenia.|
|Sugestia|W niektórych przypadkach zmniejszenie o jeden element wyświetlania PageHeight właściwości można przywrócić poprzedniego liczbę wierszy wyświetlanych.|
|Zakres|Krawędź|
|Wersja|4.5|
|Typ|Środowisko uruchomieniowe|
|Dotyczy interfejsów API|<ul><li><xref:System.Windows.Documents.FlowDocument.%23ctor?displayProperty=nameWithType></li><li><xref:System.Windows.Documents.FlowDocument.%23ctor(System.Windows.Documents.Block)?displayProperty=nameWithType></li><li><xref:System.Windows.Controls.FlowDocumentReader.%23ctor?displayProperty=nameWithType></li><li><xref:System.Windows.Controls.FlowDocumentPageViewer.%23ctor?displayProperty=nameWithType></li><li><xref:System.Windows.Controls.Primitives.DocumentPageView.%23ctor?displayProperty=nameWithType></li></ul>|

