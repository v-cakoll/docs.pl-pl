### <a name="null-coalescer-values-are-not-visible-in-debugger-until-one-step-later"></a>Wartości null coalescer nie są widoczne w debugerze, dopóki jeden krok później

|   |   |
|---|---|
|Szczegóły|Usterki w programie .NET Framework 4.5 powoduje, że wartości ustawione za pośrednictwem o wartości null operacji łączącego nie powinny być widoczne w debugerze natychmiast po zakończeniu operacji przypisania jest wykonywany podczas uruchamiania na 64-bitowej wersji Framework.|
|Sugestia|Przechodzenie krok po kroku jeden dodatkowy czas w debugerze spowoduje, że lokalne/pola. wartość do zaktualizowania poprawnie. Ponadto ten problem został rozwiązany w .NET Framework 4.6; Uaktualnianie do wersji Framework powinno rozwiązać problem.|
|Zakres|Krawędź|
|Wersja|4.5|
|Typ|Środowisko uruchomieniowe|

