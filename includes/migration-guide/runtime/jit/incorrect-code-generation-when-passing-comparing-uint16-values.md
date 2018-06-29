### <a name="incorrect-code-generation-when-passing-and-comparing-uint16-values"></a>Nieprawidłowo wygenerowany kod podczas przekazywanie i porównywanie wartości UInt16

|   |   |
|---|---|
|Szczegóły|Z powodu zmian wprowadzonych w programie .NET Framework 4.7, w niektórych przypadkach kod wygenerowany przez kompilator JIT aplikacji uruchomionych na .NET Framework 4.7 niepoprawnie porównuje dwa <code>T:System.UInt16</code> wartości. Aby uzyskać więcej informacji, zobacz [11508 # problem: ciche Generowanie nieprawidłowego kodu podczas przekazywanie i porównywanie argumentów ushort](https://github.com/dotnet/coreclr/issues/11508) w witrynie GitHub.com.|
|Sugestia|Jeśli wystąpią problemy dotyczące porównywania wartości bez znaku 16-bitowe w .NET Framework 4.7, uaktualnienie do programu .NET Framework 4.7.1.|
|Zakres|Krawędź|
|Wersja|4.7|
|Typ|środowisko uruchomieniowe|

