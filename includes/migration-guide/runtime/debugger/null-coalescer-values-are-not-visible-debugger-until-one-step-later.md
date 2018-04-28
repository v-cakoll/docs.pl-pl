### <a name="null-coalescer-values-are-not-visible-in-debugger-until-one-step-later"></a>Wartości null coalescer nie są widoczne w debugerze, dopóki krok później

|   |   |
|---|---|
|Szczegóły|Usterki w programie .NET Framework 4.5 powoduje, że wartości ustawione za pomocą wartości null operacji łączącego nie powinny być widoczne w debugerze natychmiast po operacji przypisania jest wykonywany podczas uruchamiania w 64-bitowej wersji platformy.|
|Sugestia|Wykonywanie krok po kroku jeden dodatkowy czas w debugerze spowoduje, że lokalny/pola. wartość zaktualizowania poprawnie. Ponadto ten problem został rozwiązany w .NET Framework 4.6; Uaktualnianie do tej wersji platformy powinno rozwiązać problem.|
|Zakres|Krawędź|
|Wersja|4.5|
|Typ|Środowisko uruchomieniowe|

