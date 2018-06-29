### <a name="sqlbulkcopy-uses-destination-column-encoding-for-strings"></a>SqlBulkCopy używa docelowej kolumny kodowanie dla ciągów

|   |   |
|---|---|
|Szczegóły|Podczas wstawiania danych do kolumny, <xref:System.Data.SqlClient.SqlBulkCopy?displayProperty=name> używa kodowania kolumna docelowa, a nie domyślne kodowanie <code>VARCHAR</code> i <code>CHAR</code> typów. Ta zmiana eliminuje możliwość uszkodzenia danych na skutek użycia domyślnego kodowania w sytuacji, gdy w kolumnie docelowej nie jest używane kodowanie domyślne. W rzadkich przypadkach istniejącej aplikacji może zgłoszenia wyjątku SqlException, jeśli dane, które jest zbyt duży, aby mieścił się w kolumnie docelowej powoduje zmianę w kodowaniu.|
|Sugestia|Oczekuje, że <xref:System.Data.SqlClient.SqlBulkCopy?displayProperty=name> już spowoduje uszkodzenie danych z powodu kodowania różnice. Jeśli ciągi w pobliżu limit rozmiaru kolumny docelowej są kopiowane, może być konieczne albo wstępnie kodowania danych (ma zostać skopiowany do sprawdzenia, czy dane zmieści się w kolumnie docelowej) lub przechwycić <xref:System.Data.SqlClient.SqlException?displayProperty=name>s.|
|Zakres|Krawędź|
|Wersja|4.5|
|Typ|środowisko uruchomieniowe|
|Dotyczy interfejsów API|<ul><li><xref:System.Data.SqlClient.SqlBulkCopy?displayProperty=nameWithType></li><li><xref:System.Data.SqlClient.SqlBulkCopy.%23ctor(System.Data.SqlClient.SqlConnection)?displayProperty=nameWithType></li></ul>|

