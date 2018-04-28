### <a name="enumerableemptylttresultgt-always-returns-cached-instance"></a>Enumerable.Empty&lt;TResult&gt; zawsze zwraca buforowane wystąpienie

|   |   |
|---|---|
|Szczegóły|W programie .NET 4.5, <xref:System.Linq.Enumerable.Empty%60%601> zawsze zwraca buforowane wystąpienie wewnętrzny <xref:System.Collections.Generic.IEnumerable%601>. Wcześniej <xref:System.Linq.Enumerable.Empty%60%601> może buforować pustą <xref:System.Collections.Generic.IEnumerable%601> w czasie wywołano interfejsu API, co oznacza, że w niektórych sytuacjach, w którym <xref:System.Linq.Enumerable.Empty%60%601> została wywołana szybko i jednocześnie, różnych wystąpień tego typu mogą być zwracane dla różnych wywołań INTERFEJS API.|
|Sugestia|Ponieważ poprzednie jest deterministyczna, kod jest mało prawdopodobne zależą od niej. Jednak w przypadku mało prawdopodobne, że puste elementy wyliczalne są porównywane i powinny być czasem nierówne, jawne puste tablice należy utworzyć (<code>new T[0]</code>) zamiast <xref:System.Linq.Enumerable.Empty%60%601>.|
|Zakres|Krawędź|
|Wersja|4.5|
|Typ|Środowisko uruchomieniowe|
|Dotyczy interfejsów API|<ul><li><xref:System.Linq.Enumerable.Empty%60%601?displayProperty=nameWithType></li></ul>|

