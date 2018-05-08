### <a name="il-ret-not-allowed-in-a-try-region"></a>IL ret nie są dozwolone w regionie try

|   |   |
|---|---|
|Szczegóły|W przeciwieństwie do kompilatora just in time JIT64 RyuJIT (używane w programie .NET Framework 4.6) nie zezwala na IL ret instrukcji w regionie try. Zwracanie z obszarem spróbuj jest niedozwolone w specyfikacji ECMA-335, a nie znane zarządzanych kompilator generuje takie IL. Jednak kompilatora JIT64 będzie wykonywać takie IL, jeśli jest ona generowana za pomocą odbicia emisji.|
|Sugestia|Jeśli aplikacja generuje IL zawierający ret opcode w regionie try, aplikacji mogą odnosić się do programu .NET Framework 4.5 JIT stary i uniknąć tego podziału. Alternatywnie wygenerowanego IL może zostać zaktualizowany do zwracania po try region.|
|Zakres|Krawędź|
|Wersja|4.6|
|Typ|Przekierowania|

