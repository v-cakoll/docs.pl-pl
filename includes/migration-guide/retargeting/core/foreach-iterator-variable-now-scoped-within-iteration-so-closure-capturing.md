### <a name="foreach-iterator-variable-is-now-scoped-within-the-iteration-so-closure-capturing-semantics-are-different-in-c5"></a>Zmienna sterująca w instrukcji foreach zakres to teraz w iteracji, więc semantyki przechwytywania zamknięcia są inne (C# 5)

|   |   |
|---|---|
|Szczegóły|Począwszy od C# 5 (Visual Studio 2012) <code>foreach</code> iteratora zmienne zakresu w iteracji. Może to spowodować przerwy, jeśli kod został wcześniej w zależności od zmienne, które mają nie być zawarta w <code>foreach</code>na zamknięcie. Objaw ta zmiana jest, że zmienna sterująca przekazany do delegata jest traktowana jako wartość ma w tym czasie delegat jest tworzony, zamiast wartości, które ma w czasie, który jest wywoływany delegat.|
|Sugestia|Najlepiej, jeśli kod powinien zostać zaktualizowany oczekiwać nowe zachowanie kompilatora. Jeśli stary semantyki są wymagane, można zastąpić zmienna sterująca oddzielne zmiennej, która jawnie znajduje się poza zakresem pętli.|
|Zakres|Główne|
|Wersja|4.5|
|Typ|Przekierowania|

