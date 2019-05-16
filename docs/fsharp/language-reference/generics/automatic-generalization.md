---
title: Automatyczna generalizacja
description: Dowiedz się, jak F# automatycznie stanowi uogólnienie argumentów i typy funkcji, tak że każde działa z wieloma typami, gdy jest to możliwe.
ms.date: 05/16/2016
ms.openlocfilehash: 8fc61b5e0c227474a5e913b37f4c0dad9b235a6f
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2019
ms.locfileid: "65641871"
---
# <a name="automatic-generalization"></a>Automatyczna generalizacja

F#używa typu wnioskowania, aby ocenić typy funkcje i wyrażenia. W tym temacie opisano sposób F# automatycznie stanowi uogólnienie argumentów i typy funkcji, tak że każde działa z wieloma typami, gdy jest to możliwe.

## <a name="automatic-generalization"></a>Automatyczna generalizacja

F# Kompilator, podczas wykonywania wnioskowanie o typie dla funkcji określa, czy określony parametr może być ogólny. Kompilator sprawdza każdy parametr i określa, czy funkcja zależny od określonego typu parametru. Jeśli nie, typ jest wnioskowany jako ogólnego.

Poniższy przykładowy kod przedstawia funkcję, która kompilator wnioskuje się ogólnego.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-3/snippet101.fs)]

Typ jest wnioskowany jako `'a -> 'a -> 'a`.

Typ wskazuje, że jest to funkcja, która przyjmuje dwa argumenty nieznanego tego samego typu i zwraca wartość tego samego typu. Jedną z przyczyn, które mogą być poprzednim funkcji ogólnego jest to, że większa-than-operator (`>`) jest sam ogólny. Większą-niż operator ma podpis `'a -> 'a -> bool`. Nie wszystkie operatory są ogólne, a jeśli typ parametru funkcji nieogólnego lub operator korzysta z kodu w funkcji, nie mogą być uogólnione typu parametru.

Ponieważ `max` jest ogólny, może służyć z typami takich jak `int`, `float`i tak dalej, jak pokazano w poniższych przykładach.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-3/snippet102.fs)]

Jednak dwa argumenty muszą być tego samego typu. Podpis jest `'a -> 'a -> 'a`, a nie `'a -> 'b -> 'a`. W związku z tym poniższy kod powoduje błąd, ponieważ typy nie są zgodne.

```fsharp
// Error: type mismatch.
let biggestIntFloat = max 2.0 3
```

`max` Funkcja działa także w przypadku dowolnego typu, który obsługuje większą-niż operator. W związku z tym można również użyć tego na ciąg, jak pokazano w poniższym kodzie.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-3/snippet104.fs)]

## <a name="value-restriction"></a>Ograniczenie dotyczące wartości

Kompilator wykonuje automatyczna Generalizacja tylko definicje pełne funkcji, które mają jawnych argumentów i prostych wartości niezmienne.

Oznacza to, że kompilator generuje błąd, Jeśli spróbujesz skompilować kod, który nie jest wystarczająco ograniczony do określonego typu, ale nie jest również generalizacji. Komunikat o błędzie w przypadku tego problemu, który odwołuje się do tego ograniczenia na automatyczna Generalizacja wartości jako *wartość ograniczenia*.

Zazwyczaj błąd ograniczenia wartości występuje, gdy chcesz konstrukcję być rodzajowy, ale kompilator ma za mało informacji w celu uogólnienia go, lub przypadkowo pominąć wystarczających informacji o typie w konstrukcji nierodzajowych. Rozwiązanie do błąd ograniczenia wartości jest zapewnienie dokładniejsze informacje, aby dokładniej ograniczyć problem wnioskowania typu, w jednym z następujących sposobów:

- Ograniczenie typ, który ma być nierodzajowych, dodając adnotację jawnego typu wartości lub parametr.

- Jeśli ten problem za pomocą konstrukcji nongeneralizable do definiowania ogólnych funkcji, takich jak kompozycja funkcji lub nie w pełni zastosowane argumenty funkcji rozwinięte, próbę ponownego zapisywania pełnią definicji zwykłej funkcji.

- Problem jest wyrażenie, które jest zbyt złożona, aby być uogólniony, aby ją do funkcji, dodając parametr dodatkowych, nieużywane.

- Dodaj parametry jawnego typu ogólnego. Ta opcja jest rzadko używana.

- Poniższe przykłady kodu ilustrują każdego z tych scenariuszy.

Przypadek 1: Zbyt złożone wyrażenie. W tym przykładzie lista `counter` ma być `int option ref`, ale nie jest zdefiniowany jako wartość typu prostego niezmienne.

```fsharp
let counter = ref None
// Adding a type annotation fixes the problem:
let counter : int option ref = ref None
```

Przypadek 2: Za pomocą konstrukcji nongeneralizable, aby zdefiniować funkcję ogólną. W tym przykładzie konstrukcja jest nongeneralizable, ponieważ spowodowałoby to częściowe stosowanie argumentów funkcji.

```fsharp
let maxhash = max << hash
// The following is acceptable because the argument for maxhash is explicit:
let maxhash obj = (max << hash) obj
```

Przypadek 3: Dodawanie dodatkowych, nieużywanych parametrów. To wyrażenie nie jest wystarczająco prosty Generalizacja, kompilator generuje błąd ograniczenia wartości.

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

W ostatnim przypadku wartość staje się funkcji typu, który może służyć do tworzenia wartości wiele różnych typów, na przykład w następujący sposób:

```fsharp
let intLists = arrayOf10Lists<int>
let floatLists = arrayOf10Lists<float>
```

## <a name="see-also"></a>Zobacz także

- [Wnioskowanie o typie](../type-inference.md)
- [Typy ogólne](index.md)
- [Statycznie rozwiązywane parametry typu](statically-resolved-type-parameters.md)
- [Ograniczenia](constraints.md)
