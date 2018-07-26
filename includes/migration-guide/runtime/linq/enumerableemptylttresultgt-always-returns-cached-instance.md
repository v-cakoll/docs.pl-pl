### <a name="enumerableemptylttresultgt-always-returns-cached-instance"></a>Enumerable.Empty&lt;TResult&gt; zawsze zwraca buforowane wystąpienie

|   |   |
|---|---|
|Szczegóły|Począwszy od programu .NET Framework 4.5, <xref:System.Linq.Enumerable.Empty%60%601> zawsze zwraca buforowane wystąpienie wewnętrzne <xref:System.Collections.Generic.IEnumerable%601>. Wcześniej <xref:System.Linq.Enumerable.Empty%60%601> będzie buforować pustą <xref:System.Collections.Generic.IEnumerable%601> w czasie, interfejs API został wywołany, co oznacza, że w niektórych sytuacjach, w którym <xref:System.Linq.Enumerable.Empty%60%601> wywołano szybko i jednocześnie, różne wystąpienia tego typu mogą być zwracane dla różnych wywołań INTERFEJS API.|
|Sugestia|Ponieważ poprzednie zachowanie jest deterministyczna, kod jest mało prawdopodobne, zależą od niej. Jednak w mało prawdopodobnym przypadku enumerables puste są porównywane i powinny być czasem nierównej, jawnych tablic pusty należy utworzyć (<code>new T[0]</code>) zamiast <xref:System.Linq.Enumerable.Empty%60%601>.|
|Zakres|Krawędź|
|Wersja|4.5|
|Typ|Środowisko uruchomieniowe|
|Dotyczy interfejsów API|<ul><li><xref:System.Linq.Enumerable.Empty%60%601?displayProperty=nameWithType></li></ul>|

