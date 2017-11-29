---
title: "C# wyrażeń — samouczek języka C#"
description: "wyrażenia, argumentów i operatory są blokami konstrukcyjnymi języka C#"
keywords: ".NET, csharp, wyrażenia, operatora, operandu"
author: BillWagner
ms.author: wiwagn
ms.date: 11/06/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: 20d5eb10-7381-47b9-ad90-f1cc895aa27e
ms.openlocfilehash: 7b7e321e6554818924a8a2b68afa4c787807bcba
ms.sourcegitcommit: bbde43da655ae7bea1977f7af7345eb87bd7fd5f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/21/2017
---
# <a name="expressions"></a>Wyrażenia

*Wyrażenia* są tworzone na podstawie *operandy* i *operatory*. Operatory wyrażenia wskazują, jakie operacje, aby zastosować do argumentów operacji. Przykłady operatory `+`, `-`, `*`, `/`, i `new`. Przykładami operandy literały, pola, zmienne lokalne i wyrażenia.

Jeśli wyrażenie zawiera wiele operatorów *pierwszeństwo* operatorów decyduje o kolejności, w jakiej są oceniane poszczególne operatory. Na przykład, wyrażenie `x + y * z` jest szacowana jako `x + (y * z)` ponieważ `*` operator ma wyższy priorytet niż `+` operatora.

Po wystąpieniu operand między dwa operatory o tym samym priorytecie *kojarzenie* operatorów decyduje o kolejności, w którym wykonywane są operacje:

*   Z wyjątkiem operatory przypisania są wszystkie operatory binarne *lewostronne*, co oznacza, że operacje są wykonywane od lewej do prawej. Na przykład `x + y + z` jest szacowana jako `(x + y) + z`.
*   Operatory przypisania i operator warunkowy (`?:`) są *łączny prawo*, co oznacza, że operacje są wykonywane od prawej do lewej. Na przykład `x = y = z` jest szacowana jako `x = (y = z)`.

Priorytet i łączność można sterować za pomocą nawiasów. Na przykład `x + y * z` najpierw mnoży `y` przez `z` , a następnie dodaje wynik do `x`, ale `(x + y) * z` najpierw dodaje `x` i `y` , a następnie mnoży wynik przez `z`.

Większość operatorów może być *przeciążony*. Przeładowanie operatora pozwala implementacje zdefiniowany przez użytkownika operator może być określony dla operacji skutkującej jeden lub oba argumenty operacji typu klasy lub struktury zdefiniowane przez użytkownika.

Poniżej przedstawiono podsumowanie C# dla operatorów, wyświetlanie kategorii operatora w kolejności od najwyższego malejąco. Operatory w tej samej kategorii mają taki sam priorytet. W każdej z nich znajduje się lista wyrażeń w tej kategorii, oraz opis tego typu wyrażenia.

* podstawowy
    - `x.m`: Dostęp do elementu członkowskiego
    - `x(...)`: Wywołanie metody a obiektem delegowanym
    - `x[...]`: Tablica i dostęp indeksatora
    - `x++`: Przyrost po
    - `x--`: Zmniejszenie po
    - `new T(...)`: Obiekt, a następnie delegatem tworzenia
    - `new T(...){...}`: Tworzenie obiektów za pomocą inicjatora
    - `new {...}`: Inicjator obiektu anonimowe
    - `new T[...]`: Do utworzenia tablicy
    - `typeof(T)`: Uzyskanie <xref:System.Type> obiekt do`T`
    - `checked(x)`: Obliczyć wyrażenia w kontekście zaznaczenia
    - `unchecked(x)`: Obliczyć wyrażenia w kontekście unchecked
    - `default(T)`: Wartość domyślna typu uzyskać`T`
    - `delegate {...}`: Anonimowy — funkcja (metody anonimowej)
* Jednoargumentowe
    - `+x`: Tożsamości
    - `-x`: Negacji
    - `!x`: Logiczna Negacja
    - `~x`: Bitową negację
    - `++x`: Przyrost wstępnego
    - `--x`: Zmniejszenie wstępnego
    - `(T)x`: Jawnie przekonwertować `x` na typ`T`
    - `await x`: Poczekaj asynchronicznie `x` do ukończenia
* Mnożenia
    - `x * y`: Mnożenia
    - `x / y`: Dzielenie
    - `x % y`: Pozostałe
* Dodatku
    - `x + y`: Dodawanie, ciągów, kombinacja delegata
    - `x – y`: Odejmowania, usunięcie delegata
* SHIFT
    - `x << y`: Przesunięcia w lewo
    - `x >> y`: Przesuń w prawo
* Relacyjna i testowania typu
    - `x < y`: Mniejsza niż
    - `x > y`: Większa niż
    - `x <= y`: Mniejsza niż lub równe
    - `x >= y`: Większe lub równe
    - `x is T`: Zwracany `true` Jeśli `x` jest `T`, `false` inaczej
    - `x as T`: Zwracany `x` typu `T`, lub `null` Jeśli `x` nie jest`T`
* Równość
    - `x == y`: Równe
    - `x != y`: Nie jest równy
* AND logiczne
    - `x & y`: Liczba całkowita bitowe i logicznych logiczny AND
* XOR logiczne
    - `x ^ y`: Liczba całkowita iloczynu bitowego XOR, logiczna XOR logiczne
* OR logiczne
    - `x | y`: Liczba całkowita bitowe lub logiczna operatora logicznego OR
* AND warunkowe
    - `x && y`: Oblicza `y` tylko wtedy, gdy `x` nie jest`false`
* OR warunkowe
    - `x || y`: Oblicza `y` tylko wtedy, gdy `x` nie jest`true`
* Łączenie wartości null
    - `x ?? y`: Daje w wyniku `y` Jeśli `x` ma wartość null, aby `x` inaczej
* Warunkowe
    - `x ? y : z`: Oblicza `y` Jeśli `x` jest `true`, `z` Jeśli `x` jest`false`
* Przypisanie ani funkcji anonimowej
    - `x = y`: Przypisania
    - `x op= y`: Przydział złożony; Operatory obsługiwane są
        - `*=`   `/=`   `%=`   `+=`   `-=`   `<<=`   `>>=`   `&=`  `^=`  `|=`
    - `(T x) => y`: Funkcja anonimowe (wyrażenia lambda)

>[!div class="step-by-step"]
[Poprzednie](types-and-variables.md)
[dalej](statements.md)
