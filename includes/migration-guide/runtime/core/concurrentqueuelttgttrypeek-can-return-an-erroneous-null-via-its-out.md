### <a name="concurrentqueuelttgttrypeek-can-return-an-erroneous-null-via-its-out-parameter"></a>ConcurrentQueue&lt;T&gt;. TryPeek może zwrócić poproszenie o wartości null za pośrednictwem jego parametru ze specyfikatorem out

|   |   |
|---|---|
|Szczegóły|W niektórych przypadkach wielowątkowych <xref:System.Collections.Concurrent.ConcurrentQueue%601.TryPeek(%600@)?displayProperty=name> może zwrócić wartość true, ale wypełnić parametr out o wartości null (a nie wartość poprawny, podejrzeć).|
|Sugestia|Ten problem został rozwiązany w .NET Framework 4.5.1. Uaktualnienie do tej struktury rozwiąże problem.|
|Zakres|Główne|
|Wersja|4.5|
|Typ|Środowisko uruchomieniowe|
|Dotyczy interfejsów API|<ul><li><xref:System.Collections.Concurrent.ConcurrentQueue%601.TryPeek(%600@)?displayProperty=nameWithType></li></ul>|

