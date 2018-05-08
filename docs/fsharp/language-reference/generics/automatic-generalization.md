---
title: Automatyczna generalizacja (F#)
description: 'Dowiedz się, jak F # automatycznie stanowi uogólnienie argumentów i typy funkcji, aby mogły działać z różnymi typami, gdy jest to możliwe.'
ms.date: 05/16/2016
ms.openlocfilehash: 858c8bab4a1a37f44a700744e70ebfa8a5abf12c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="automatic-generalization"></a>Automatyczna generalizacja

F # używa wnioskowanie o typie w celu oceny typów wyrażeń i funkcji. W tym temacie opisano, jak F # automatycznie stanowi uogólnienie argumentów i typy funkcji, aby mogły działać z różnymi typami, gdy jest to możliwe.


## <a name="automatic-generalization"></a>Automatyczna generalizacja
Kompilator języka F # podczas wykonywania wnioskowanie o typie dla funkcji, określa, czy dany parametr może być rodzajowy. Kompilator sprawdza każdego parametru i określa, czy funkcja ma zależność na określony typ parametru. Jeśli nie, typu jest wywnioskowany, aby wartość była ogólna.

Poniższy przykładowy kod przedstawia funkcję, która wnioskuje kompilator, aby wartość była ogólna.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-3/snippet101.fs)]

Typ jest wywnioskowany jako `'a -> 'a -> 'a`.

Typ wskazuje, że jest to funkcja, która przyjmuje dwa argumenty nieznanego typu tego samego i zwraca wartość tego samego typu. Jedną z przyczyn, które mogą być poprzedniej funkcji ogólnego jest to, że większa — niż — operator (`>`) jest rodzajowy. Większa-niż operator ma podpis `'a -> 'a -> bool`. Nie wszystkie operatory są ogólne, a jeśli kod w funkcji korzysta z typem parametru razem z funkcji nierodzajową lub operator, nie można uogólnić typu parametru.

Ponieważ `max` jest ogólny, można z typami takich jak `int`, `float`i tak dalej, jak pokazano w poniższych przykładach.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-3/snippet102.fs)]

Jednak dwa argumenty muszą być tego samego typu. Podpis jest `'a -> 'a -> 'a`, a nie `'a -> 'b -> 'a`. W związku z tym poniższy kod tworzy błąd, ponieważ typy są niezgodne.

```fsharp
// Error: type mismatch.
let biggestIntFloat = max 2.0 3
```

`max` Funkcja działa także w przypadku dowolnego typu, który obsługuje większą-niż operator. W związku z tym można również użyć tego na ciąg, jak pokazano w poniższym kodzie.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-3/snippet104.fs)]
    
## <a name="value-restriction"></a>Wartość ograniczenia
Kompilator wykonuje automatyczna Generalizacja tylko w definicji funkcji pełną, które mają jawne argumenty i proste modyfikować wartości.

Oznacza to, że kompilator generuje błąd, Jeśli spróbujesz skompilować kod, który nie jest wystarczająco ograniczone do określonego typu, ale nie jest również generalizacji. Komunikat o błędzie w przypadku tego problemu, który odwołuje się do tego ograniczenia automatyczna Generalizacja wartości jako *wartość ograniczenia*.

Zazwyczaj błąd ograniczenie wartości występuje, gdy konstrukcji, aby wartość była ogólna a kompilator ma za mało informacji do uogólnienia go lub jeśli pominięto przypadkowo wystarczających informacji o typie w nierodzajowe konstrukcji. Rozwiązania pod kątem błędów ograniczeń wartość ma na celu dostarczenie dokładniejsze informacje do dokładniejszego ograniczyć problem wnioskowania typu, w jednym z następujących sposobów:


- Ograniczenie typu jako nierodzajowe przez dodanie jawną adnotację typu wartości lub parametr.

- Jeśli ten problem przy użyciu konstrukcji nongeneralizable do definiowania ogólnych funkcji, takich jak kompozycja funkcji lub nie w pełni stosowane argumenty curried funkcji, spróbuj przepisywania funkcji jako definicji zwykłej funkcji.

- Problem jest wyrażenie jest zbyt złożone, aby być uogólniony, aby go do funkcji przez dodanie parametru dodatkowe, nieużywane.

- Dodaj parametry jawnego typu ogólnego. Ta opcja jest rzadko używana.

- Poniższe przykłady kodu przedstawiają każdego z tych scenariuszy.

Przypadek 1: Zbyt złożone wyrażenie. W tym przykładzie listy `counter` ma być `int option ref`, ale nie jest zdefiniowany jako niezmienialny wartość prostą.

```fsharp
let counter = ref None
// Adding a type annotation fixes the problem:
let counter : int option ref = ref None
```

Przypadek 2: Przy użyciu konstrukcji nongeneralizable do definiowania ogólnych funkcji. W tym przykładzie konstrukcja jest nongeneralizable, ponieważ spowodowałoby to aplikacja częściowa argumentów funkcji.

```fsharp
let maxhash = max << hash
// The following is acceptable because the argument for maxhash is explicit:
let maxhash obj = (max << hash) obj
```

Przypadek 3: Dodanie dodatkowych, nieużywane parametru. To wyrażenie nie jest wystarczająco prosty generalizacji, kompilator generuje błąd ograniczenie wartości.

```fsharp
let emptyList10 = Array.create 10 []
// Adding an extra (unused) parameter makes it a function, which is generalizable.
let emptyList10 () = Array.create 10 []
```

W przypadku 4: Dodawanie parametrów typu.

```fsharp
let arrayOf10Lists = Array.create 10 []
// Adding a type parameter and type annotation lets you write a generic value.
let arrayOf10Lists<'T> = Array.create 10 ([]:'T list)
```

W ostatnim przypadku wartość staje się typ funkcji, które mogą służyć do tworzenia wartości wielu różnych typów, na przykład w następujący sposób:

```fsharp
let intLists = arrayOf10Lists<int>
let floatLists = arrayOf10Lists<float>
```

## <a name="see-also"></a>Zobacz też
[Wnioskowanie o typie](../type-inference.md)

[Typy ogólne](index.md)

[Statycznie rozwiązywane parametry typu](statically-resolved-type-parameters.md)

[Ograniczenia](constraints.md)

