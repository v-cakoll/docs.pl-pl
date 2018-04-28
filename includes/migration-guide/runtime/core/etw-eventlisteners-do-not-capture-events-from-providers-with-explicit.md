### <a name="etw-eventlisteners-do-not-capture-events-from-providers-with-explicit-keywords-like-the-tpl-provider"></a>ETW EventListeners nie Przechwytywanie zdarzeń od dostawców jawne słów kluczowych (na przykład dostawca TPL)

|   |   |
|---|---|
|Szczegóły|EventListeners ETW za pomocą maski puste — słowo kluczowe nie jest poprawnie przechwycona zdarzeń od dostawców jawne słów kluczowych. W programie .NET Framework 4.5 dostawcy TPL rozpoczęcia, dostarczanie jawne słów kluczowych i wyzwalane ten problem. W .NET Framework 4.6 EventListeners zostały zaktualizowane do już ten problem.|
|Sugestia|Aby obejść ten problem, Zamień wywołań <xref:System.Diagnostics.Tracing.EventListener.EnableEvents(System.Diagnostics.Tracing.EventSource,System.Diagnostics.Tracing.EventLevel)> wywołania przeciążenia EnableEvents, które jawnie określa &quot;dowolnego słowa kluczowe&quot; maski do użycia: <code>EnableEvents(eventSource, level, unchecked((EventKeywords)0xFFFFffffFFFFffff))</code>. Alternatywnie ten problem został rozwiązany w .NET Framework 4.6 i mogą być kierowane przez uaktualnienie do tej wersji programu .NET Framework.|
|Zakres|Krawędź|
|Wersja|4.5|
|Typ|Środowisko uruchomieniowe|
|Dotyczy interfejsów API|<ul><li><xref:System.Diagnostics.Tracing.EventListener.EnableEvents(System.Diagnostics.Tracing.EventSource,System.Diagnostics.Tracing.EventLevel)?displayProperty=nameWithType></li></ul>|

