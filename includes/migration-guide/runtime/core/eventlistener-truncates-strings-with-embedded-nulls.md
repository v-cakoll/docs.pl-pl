### <a name="eventlistener-truncates-strings-with-embedded-nulls"></a>EventListener obcina ciągi z osadzonego na wartości null

|   |   |
|---|---|
|Szczegóły|<xref:System.Diagnostics.Tracing.EventListener?displayProperty=name> obcina ciągi z osadzonego na wartości null. Znaki Null nie są obsługiwane przez <xref:System.Diagnostics.Tracing.EventSource?displayProperty=name> klasy. Zmiana dotyczy tylko aplikacji, które używają <xref:System.Diagnostics.Tracing.EventListener?displayProperty=name> odczytać <xref:System.Diagnostics.Tracing.EventSource?displayProperty=name> danych w procesie oraz czy należy użyć znaków o wartości null jako ogranicznika.|
|Sugestia|<xref:System.Diagnostics.Tracing.EventSource?displayProperty=name> dane powinny zostać uaktualnione, jeśli jest to możliwe, aby nie używać osadzone znaki o wartości null.|
|Zakres|Krawędź|
|Wersja|4.5.1|
|Typ|Środowisko uruchomieniowe|
|Dotyczy interfejsów API|<ul><li><xref:System.Diagnostics.Tracing.EventListener.%23ctor?displayProperty=nameWithType></li><li><xref:System.Diagnostics.Tracing.EventListener.EnableEvents(System.Diagnostics.Tracing.EventSource,System.Diagnostics.Tracing.EventLevel)?displayProperty=nameWithType></li><li><xref:System.Diagnostics.Tracing.EventListener.EnableEvents(System.Diagnostics.Tracing.EventSource,System.Diagnostics.Tracing.EventLevel,System.Diagnostics.Tracing.EventKeywords)?displayProperty=nameWithType></li><li><xref:System.Diagnostics.Tracing.EventListener.EnableEvents(System.Diagnostics.Tracing.EventSource,System.Diagnostics.Tracing.EventLevel,System.Diagnostics.Tracing.EventKeywords,System.Collections.Generic.IDictionary{System.String,System.String})?displayProperty=nameWithType></li></ul>|

