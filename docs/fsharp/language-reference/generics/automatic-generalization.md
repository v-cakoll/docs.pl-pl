---
title: Automatyczna generalizacja
description: Dowiedz F# się, jak automatycznie uogólniać argumenty i typy funkcji, tak aby współpracowały z wieloma typami, gdy jest to możliwe.
ms.date: 05/16/2016
ms.openlocfilehash: 501749a190d9770cbcd9848e3d528cba32fe6762
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630624"
---
# <a name="automatic-generalization"></a>Automatyczna generalizacja

F#używa wnioskowania o typie do obliczenia typów funkcji i wyrażeń. W tym temacie opisano F# , jak program automatycznie uogólniuje argumenty i typy funkcji, tak aby współpracowały z wieloma typami, gdy jest to możliwe.

## <a name="automatic-generalization"></a>Automatyczna generalizacja

F# Kompilator, gdy wykonuje wnioskowanie o typie dla funkcji, określa, czy dany parametr może być ogólny. Kompilator sprawdza każdy parametr i określa, czy funkcja ma zależność od określonego typu parametru. Jeśli tak nie jest, typ jest wywnioskowany jako ogólny.

Poniższy przykład kodu ilustruje funkcję, którą kompilator wnioskuje za ogólny.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-3/snippet101.fs)]

Typ jest wywnioskowany `'a -> 'a -> 'a`jako.

Typ wskazuje, że jest to funkcja, która przyjmuje dwa argumenty tego samego nieznanego typu i zwraca wartość tego samego typu. Jedną z powodów, w których można użyć poprzedniej funkcji, jest to, że operator większości (`>`) jest sama jako ogólny. Operator większa niż jest sygnaturą `'a -> 'a -> bool`. Nie wszystkie operatory są ogólne i jeśli kod w funkcji używa typu parametru wraz z nieogólną funkcją lub operatorem, ten typ parametru nie może być uogólniony.

Ponieważ `max` jest ogólny, można go używać z typami takimi jak `int`, `float`, i tak dalej, jak pokazano w poniższych przykładach.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-3/snippet102.fs)]

Jednak te dwa argumenty muszą być tego samego typu. Sygnatura to `'a -> 'a -> 'a`, nie `'a -> 'b -> 'a`. W związku z tym Poniższy kod generuje błąd, ponieważ typy nie pasują do siebie.

```fsharp
// Error: type mismatch.
let biggestIntFloat = max 2.0 3
```

`max` Funkcja działa również z dowolnym typem, który obsługuje operator większości. Z tego względu można również użyć go w ciągu, jak pokazano w poniższym kodzie.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-3/snippet104.fs)]

## <a name="value-restriction"></a>Ograniczenie wartości

Kompilator wykonuje automatyczne uogólnianie tylko w przypadku kompletnych definicji funkcji, które mają jawne argumenty i w przypadku prostych niezmiennych wartości.

Oznacza to, że kompilator wystawia błąd w przypadku próby skompilowania kodu, który nie jest wystarczająco ograniczony do określonego typu, ale również nie jest możliwe jego uogólnienie. Komunikat o błędzie dotyczący tego problemu dotyczy tego ograniczenia dotyczącego automatycznego uogólniania wartości jako *ograniczenia wartości*.

Zazwyczaj błąd ograniczenia wartości występuje, gdy konstrukcja ma być ogólna, ale kompilator nie ma wystarczających informacji do jego uogólnienia lub gdy przypadkowo pominięto wystarczające informacje o typie w nieogólnej konstrukcji. Rozwiązaniem związanym z błędem ograniczenia wartości jest dostarczenie bardziej jawnych informacji w celu bardziej pełnego ograniczenia problemu wnioskowania o typie w jeden z następujących sposobów:

- Ogranicz typ jako nieogólny przez dodanie jawnej adnotacji typu do wartości lub parametru.

- Jeśli problem używa konstrukcji niemożliwej do uogólnienia w celu zdefiniowania funkcji ogólnej, takiej jak kompozycja funkcji lub nieukończone zastosowane argumenty funkcji rozwinięte, spróbuj ponownie napisać funkcję jako definicję zwykłej funkcji.

- Jeśli problem jest wyrażeniem, które jest zbyt złożone, aby było uogólnione, ustaw go w funkcji przez dodanie dodatkowego, nieużywanego parametru.

- Dodawanie jawnych parametrów typu ogólnego. Ta opcja jest rzadko używana.

- Poniższe przykłady kodu ilustrują poszczególne z tych scenariuszy.

Przypadek 1: Wyrażenie jest zbyt złożone. W tym przykładzie lista `counter` jest przeznaczona `int option ref`do, ale nie jest zdefiniowana jako prosta niezmienna wartość.

```fsharp
let counter = ref None
// Adding a type annotation fixes the problem:
let counter : int option ref = ref None
```

Przypadek 2: Definiowanie funkcji ogólnej przy użyciu konstrukcji nieuogólnieniowej. W tym przykładzie konstrukcja jest nieuogólnienia, ponieważ obejmuje częściowe stosowanie argumentów funkcji.

```fsharp
let maxhash = max << hash
// The following is acceptable because the argument for maxhash is explicit:
let maxhash obj = (max << hash) obj
```

Przypadek 3: Dodawanie dodatkowego, nieużywanego parametru. Ponieważ to wyrażenie nie jest wystarczająco proste dla generalizacji, kompilator wystawia błąd ograniczenia wartości.

```fsharp
let emptyList10 = Array.create 10 []
// Adding an extra (unused) parameter makes it a function, which is generalizable.
let emptyList10 () = Array.create 10 []
```

Przypadek 4: Dodawanie parametrów typu.

```fsharp
let arrayOf10Lists = Array.create 10 []
// Adding a type parameter and type annotation lets you write a generic value.
let arrayOf10Lists<'T> = Array.create 10 ([]:'T list)
```

W ostatnim przypadku wartość jest funkcją typu, która może służyć do tworzenia wartości wielu różnych typów, na przykład w następujący sposób:

```fsharp
let intLists = arrayOf10Lists<int>
let floatLists = arrayOf10Lists<float>
```

## <a name="see-also"></a>Zobacz także

- [Wnioskowanie o typie](../type-inference.md)
- [Typy ogólne](index.md)
- [Statycznie rozwiązywane parametry typu](statically-resolved-type-parameters.md)
- [Ograniczenia](constraints.md)
