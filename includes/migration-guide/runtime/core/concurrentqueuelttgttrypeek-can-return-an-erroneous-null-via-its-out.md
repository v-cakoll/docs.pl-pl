### <a name="concurrentqueuelttgttrypeek-can-return-an-erroneous-null-via-its-out-parameter"></a>ConcurrentQueue&lt;T&gt;. Metody TryPeek może zwrócić błędne null za pośrednictwem jego parametru wyjściowego

|   |   |
|---|---|
|Szczegóły|W niektórych scenariuszach wielowątkowych <xref:System.Collections.Concurrent.ConcurrentQueue%601.TryPeek(%600@)?displayProperty=name> może zwrócić wartość true, ale wypełnić parametr out o wartości null (zamiast wartości poprawny, przybywającej).|
|Sugestia|Tego problemu w programie .NET Framework 4.5.1. Uaktualnianie do tej struktury rozwiąże problem.|
|Zakres|Główne|
|Wersja|4.5|
|Typ|Środowisko uruchomieniowe|
|Dotyczy interfejsów API|<ul><li><xref:System.Collections.Concurrent.ConcurrentQueue%601.TryPeek(%600@)?displayProperty=nameWithType></li></ul>|

