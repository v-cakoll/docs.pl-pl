---
title: C#Wyrażenia — Przewodnik po przykładzie C# języka
description: bloki konstrukcyjne są wyrażenia, argumenty operacji i operatory C# języka
ms.date: 11/06/2016
ms.assetid: 20d5eb10-7381-47b9-ad90-f1cc895aa27e
ms.openlocfilehash: 682f98d51bf4eb3c1641297972afb86956e06d3e
ms.sourcegitcommit: 79066169e93d9d65203028b21983574ad9dcf6b4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/01/2019
ms.locfileid: "57212095"
---
# <a name="expressions"></a>Wyrażenia

*Wyrażenia* są konstruowane na podstawie *operandów* i *operatorów*. Operatory wyrażenia wskazują operacje do zastosowania dla operandów. Przykłady operatorów to `+`, `-`, `*`, `/`i `new`. Przykładami operandów są literały, pola, zmienne lokalne i wyrażenia.

Gdy wyrażenie zawiera wiele operatorów *pierwszeństwo* operatorów określa kolejność, w jakiej są oceniane poszczególne operatory. Na przykład, wyrażenie `x + y * z` jest oceniane jako `x + (y * z)`, ponieważ operator `*` ma wyższy priorytet niż operator `+`.

Gdy operand występuje między dwoma operatorami o tym samym priorytecie *asocjacyjność* operatorów określa kolejność, w której są wykonywane operacje:

*   Z wyjątkiem operatorów przypisania wszystkie operatory dwuargumentowe są *lewostronne*, co oznacza, że operacje są wykonywane od lewej do prawej. Na przykład `x + y + z` jest oceniane jako `(x + y) + z`.
*   Operatory przypisania i operator warunkowy (`?:`) są *prawostronne*, co oznacza, że operacje są wykonywane od prawej do lewej. Na przykład `x = y = z` jest oceniane jako `x = (y = z)`.

Pierwszeństwo i asocjacyjność mogą być kontrolowane za pomocą nawiasów. Na przykład `x + y * z` najpierw mnoży `y` przez `z` , a następnie dodaje wynik do `x`, ale `(x + y) * z` najpierw dodaje `x` i `y` i następnie wynik mnoży przez `z`.

Większość operatorów może być *przeciążona*. Przeciążanie operatora umożliwia określanie definiowanych przez użytkownika implementacji operatorów dla operacji, w których jeden lub oba operandy mają typ struktury lub klasy zdefiniowanej przez użytkownika.

Poniżej znajduje się podsumowanie operatorów języka C#. Kategorie operatorów wypisane są w kolejności pierwszeństwa od najwyższego do najniższego. Operatory w tej samej kategorii mają takie samo pierwszeństwo. Pod każdą z kategorii znajduje się lista wyrażeń znajdujących się w niej, wraz z opisem danego typu wyrażenia.

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
    - `(T)x`: Jawna konwersja `x` na typ `T`
    - `await x`: Asynchronicznie poczekaj na ukończenie `x`
* Mnożeniowy
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
* Równości
    - `x == y`: Równa się
    - `x != y`: Nie równa się
* Logicznego AND
    - `x & y`: Liczba całkowita bitowe i logicznych logiczne AND
* Logicznego XOR
    - `x ^ y`: Bitowe XOR dla wartości całkowitych, logiczne XOR dla wartości binarnych
* Logicznego OR
    - `x | y`: Bitowe OR dla wartości całkowitych, logiczne OR dla wartości binarnych
* Warunkowego AND
    - `x && y`: Ocenia `y` tylko wtedy, gdy `x` nie jest `false`
* Warunkowego OR
    - `x || y`: Ocenia `y` tylko wtedy, gdy `x` nie jest `true`
* Łączenia wartości null
    - `x ?? y`: Daje w wyniku `y` Jeśli `x` ma wartość null, aby `x` inaczej
* Warunkowe
    - `x ? y : z`: Ocenia `y` Jeśli `x` jest `true`, `z` Jeśli `x` jest `false`
* Przypisania lub funkcji anonimowej
    - `x = y`: Przypisanie
    - `x op= y`: Złożone przypisanie; obsługiwane operatory to
        - `*=`   `/=`   `%=`   `+=`   `-=`   `<<=`   `>>=`   `&=`  `^=`  `|=`
    - `(T x) => y`: Funkcja anonimowa (wyrażenie lambda)

> [!div class="step-by-step"]
> [Poprzednie](types-and-variables.md)
> [dalej](statements.md)