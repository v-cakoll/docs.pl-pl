### <a name="listsort-algorithm-changed"></a>Algorytm list.sort — zmienione

|   |   |
|---|---|
|Szczegóły|W programie .NET Framework 4.5 <xref:System.Collections.Generic.List%601?displayProperty=name>przez algorytm sortowania został zmieniony (jako introspective sortowania zamiast szybkiego sortowania). <xref:System.Collections.Generic.List%601?displayProperty=name>w sortowania nigdy nie było stabilny, ale ta zmiana może spowodować różnych scenariuszy do sortowania w sposób niestabilny. Oznacza to, że po prostu, że elementy równoważne może sortować w różnej kolejności w kolejnych wywołaniach interfejsu API.|
|Sugestia|Ponieważ starego algorytm sortowania również niestabilny (jeśli są w sposób nieco inny), nie powinien być nie kod, który jest zależny od elementów równoważne zawsze sortowanie w określonej kolejności. W przypadku wystąpienia kodu, który zależności i Trwa szczęście z zachowaniem starego kodu powinny zostać uaktualnione do używania porównania, która będzie sposób sortowania elementów w odpowiedni sposób.|
|Zakres|Przezroczyste|
|Wersja|4.5|
|Typ|środowisko uruchomieniowe|
|Dotyczy interfejsów API|<ul><li><xref:System.Collections.Generic.List%601.Sort?displayProperty=nameWithType></li><li><xref:System.Collections.Generic.List%601.Sort(System.Collections.Generic.IComparer{%600})?displayProperty=nameWithType></li><li><xref:System.Collections.Generic.List%601.Sort(System.Comparison{%600})?displayProperty=nameWithType></li><li><xref:System.Collections.Generic.List%601.Sort(System.Int32,System.Int32,System.Collections.Generic.IComparer{%600})?displayProperty=nameWithType></li></ul>|

