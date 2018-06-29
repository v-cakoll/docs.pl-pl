### <a name="eventlistener-truncates-strings-with-embedded-nulls"></a>Ciągi zawierające osadzone wartości obcina odbiornika danych

|   |   |
|---|---|
|Szczegóły|<xref:System.Diagnostics.Tracing.EventListener?displayProperty=name> obcina ciągi zawierające osadzone wartości. Znaki Null nie są obsługiwane przez <xref:System.Diagnostics.Tracing.EventSource?displayProperty=name> klasy. Dotyczy tylko aplikacji korzystających z <xref:System.Diagnostics.Tracing.EventListener?displayProperty=name> odczytać <xref:System.Diagnostics.Tracing.EventSource?displayProperty=name> dane w procesie i znaki null jako ograniczników.|
|Sugestia|<xref:System.Diagnostics.Tracing.EventSource?displayProperty=name> dane powinny zostać uaktualnione, jeśli to możliwe, aby nie używać osadzonych znaków wartości null.|
|Zakres|Krawędź|
|Wersja|4.5.1|
|Typ|środowisko uruchomieniowe|
|Dotyczy interfejsów API|<ul><li><xref:System.Diagnostics.Tracing.EventListener.%23ctor?displayProperty=nameWithType></li><li><xref:System.Diagnostics.Tracing.EventListener.EnableEvents(System.Diagnostics.Tracing.EventSource,System.Diagnostics.Tracing.EventLevel)?displayProperty=nameWithType></li><li><xref:System.Diagnostics.Tracing.EventListener.EnableEvents(System.Diagnostics.Tracing.EventSource,System.Diagnostics.Tracing.EventLevel,System.Diagnostics.Tracing.EventKeywords)?displayProperty=nameWithType></li><li><xref:System.Diagnostics.Tracing.EventListener.EnableEvents(System.Diagnostics.Tracing.EventSource,System.Diagnostics.Tracing.EventLevel,System.Diagnostics.Tracing.EventKeywords,System.Collections.Generic.IDictionary{System.String,System.String})?displayProperty=nameWithType></li></ul>|

