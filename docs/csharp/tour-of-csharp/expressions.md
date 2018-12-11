---
title: C#Wyrażenia — Przewodnik po przykładzie C# języka
description: bloki konstrukcyjne są wyrażenia, argumenty operacji i operatory C# języka
ms.date: 11/06/2016
ms.assetid: 20d5eb10-7381-47b9-ad90-f1cc895aa27e
ms.openlocfilehash: 28e1d6952975c6932dc9ae40af28c7201d61d778
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/10/2018
ms.locfileid: "53154937"
---
# <a name="expressions"></a>Wyrażenia

*Wyrażenia* są konstruowane na podstawie *operandy* i *operatory*. Operatory wyrażenie wskazuje operacji do zastosowania do operandów. Przykłady operatorów `+`, `-`, `*`, `/`, i `new`. Przykładami operandy są literały, pola, zmienne lokalne i wyrażeń.

Gdy wyrażenie zawiera wiele operatorów *pierwszeństwo* operatorów określa kolejność, w jakiej są oceniane poszczególnych operatorach. Na przykład, wyrażenie `x + y * z` jest oceniane jako `x + (y * z)` ponieważ `*` operator ma wyższy priorytet niż `+` operatora.

Gdy argument odbywa się między dwa operatory o tym samym priorytecie *kojarzenie* operatorów określa kolejność, w której są wykonywane operacje:

*   Z wyjątkiem operatorów przypisania wszystkie operatory dwuargumentowe to *lewostronne*, co oznacza, że operacje są wykonywane od lewej do prawej. Na przykład `x + y + z` jest oceniane jako `(x + y) + z`.
*   Operatory przypisania i operator warunkowy (`?:`) są *zespolony z prawej*, co oznacza, że operacje są wykonywane od prawej do lewej. Na przykład `x = y = z` jest oceniane jako `x = (y = z)`.

Pierwszeństwo i kojarzenie mogą być kontrolowane za pomocą nawiasów. Na przykład `x + y * z` najpierw mnoży `y` przez `z` , a następnie dodaje wynik do `x`, ale `(x + y) * z` najpierw dodaje `x` i `y` i następnie mnoży wynik przez `z`.

Większość operatorów może być *przeciążone*. Przeciążanie operatora zezwala na implementacjami operatorów zdefiniowanych przez użytkownika, może być określony dla operacji, gdzie jeden lub oba operandy są typu klasy lub struktury zdefiniowany przez użytkownika.

Poniżej znajduje się podsumowanie C#firmy operatorów, najniższą listę kategorii operatora w kolejności od najwyższego do. Operatory w tej samej kategorii mają równy priorytet. W każdej z nich znajduje się lista wyrażeń w danej kategorii, oraz opis tego typu wyrażenia.

* Podstawowy
    - `x.m`: Dostęp do elementu członkowskiego
    - `x(...)`: Wywołanie metody i delegata
    - `x[...]`: Dostęp do tablicy i indeksatora
    - `x++`: Postinkrementacja
    - `x--`: Postdekrementacja
    - `new T(...)`: Utworzenie obiektu i delegata
    - `new T(...){...}`: Utworzenie obiektu za pomocą inicjatora
    - `new {...}`:  Inicjator obiektu anonimowego
    - `new T[...]`: Do utworzenia tablicy
    - `typeof(T)`: Uzyskaj <xref:System.Type> dla obiektu `T`
    - `checked(x)`: Obliczenie wyrażenia w kontekście sprawdzanym
    - `unchecked(x)`: Obliczenie wyrażenia w kontekście niesprawdzanym
    - `default(T)`: Uzyskanie wartości domyślnej typu `T`
    - `delegate {...}`: Funkcja anonimowa (metoda anonimowa)
* Jednoargumentowy
    - `+x`: Tożsamość
    - `-x`: Negacja
    - `!x`: Negacja logiczna
    - `~x`: Negacja bitowa
    - `++x`: Preinkrementacja
    - `--x`: Predekrementacja
    - `(T)x`: Jawnie przekonwertować `x` na typ `T`
    - `await x`: Asynchronicznie poczekaj, aż `x` do ukończenia
* Mnożenia
    - `x * y`: Mnożenie
    - `x / y`: Dzielenie
    - `x % y`: Reszta
* Dodatku
    - `x + y`: Dodawanie, łączenie ciągów, łączenie delegatów
    - `x – y`: Odejmowanie, usuwanie delegata
* Shift
    - `x << y`: Przesunięcie w lewo
    - `x >> y`: Przesunięcie w prawo
* Relacyjne i badania typu
    - `x < y`: Mniejsze niż
    - `x > y`: Większe niż
    - `x <= y`: Mniejsze niż lub równe
    - `x >= y`: Większe niż lub równe
    - `x is T`: Zwróć `true` Jeśli `x` jest `T`, `false` inaczej
    - `x as T`: Zwróć `x` wpisanych w formie `T`, lub `null` Jeśli `x` nie jest `T`
* Równość
    - `x == y`: Równa się
    - `x != y`: Nie równa się
* AND logiczne
    - `x & y`: Liczba całkowita bitowe i logicznych logiczne AND
* XOR logiczne
    - `x ^ y`: Bitowe XOR dla wartości całkowitych, logiczne XOR dla wartości binarnych
* OR logiczne
    - `x | y`: Bitowe OR dla wartości całkowitych, logiczne OR dla wartości binarnych
* AND warunkowe
    - `x && y`: Ocenia `y` tylko wtedy, gdy `x` nie jest `false`
* OR warunkowe
    - `x || y`: Ocenia `y` tylko wtedy, gdy `x` nie jest `true`
* Łączenie wartości null
    - `x ?? y`: Daje w wyniku `y` Jeśli `x` ma wartość null, aby `x` inaczej
* Warunkowe
    - `x ? y : z`: Ocenia `y` Jeśli `x` jest `true`, `z` Jeśli `x` jest `false`
* Przypisania lub funkcja anonimowa
    - `x = y`: Przypisanie
    - `x op= y`: Przydział złożony; obsługiwane operatory to
        - `*=`   `/=`   `%=`   `+=`   `-=`   `<<=`   `>>=`   `&=`  `^=`  `|=`
    - `(T x) => y`: Funkcja anonimowa (wyrażenie lambda)

>[!div class="step-by-step"]
>[Poprzednie](types-and-variables.md)
>[dalej](statements.md)