---
title: Krotki (F#)
description: Więcej informacji na temat F# krotki, grupowanie bez nazwy, ale uporządkowane wartości, prawdopodobnie różnych typów.
ms.date: 05/16/2016
ms.openlocfilehash: e7628e4c4b538c2fe52fca25d2597b10fec28d1c
ms.sourcegitcommit: db8b83057d052c1f9f249d128b08d4423af0f7c2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/02/2018
ms.locfileid: "43749226"
---
# <a name="tuples"></a>Krotki

A *krotki* to zbiór wartości bez nazwy, ale uporządkowanym, prawdopodobnie różnych typów.  Kolekcje mogą być typami odwołań lub struktury.

## <a name="syntax"></a>Składnia

```fsharp
(element, ... , element)
struct(element, ... ,element )
```

## <a name="remarks"></a>Uwagi

Każdy *elementu* w poprzedniej składni może być dowolnym prawidłowym wyrażeniem języka F#.

## <a name="examples"></a>Przykłady

Przykładami krotek pary, trójek i tak dalej, tych samych lub różnych typów. Niektóre przykłady zostały zilustrowane w poniższym kodzie.

[!code-fsharp[Main](../../../samples/snippets/fsharp/tuples/basic-examples.fsx#L6-L21)]

## <a name="obtaining-individual-values"></a>Uzyskiwanie poszczególne wartości

Dopasowanie do wzorca można użyć dostępu i przypisać nazwy elementów krotki, jak pokazano w poniższym kodzie.

[!code-fsharp[Main](../../../samples/snippets/fsharp/tuples/basic-examples.fsx#L27-L29)]

Można również dekonstruować krotki za pomocą dopasowywania do wzorca poza `match` wyrażenia za pośrednictwem `let` powiązania:

[!code-fsharp[Main](../../../samples/snippets/fsharp/tuples/basic-examples.fsx#L34-L37)]

Lub można wzorca dopasowania krotek jako dane wejściowe do funkcji:

[!code-fsharp[Main](../../../samples/snippets/fsharp/tuples/basic-examples.fsx#L43-L47)]

Jeśli potrzebujesz tylko jeden element krotki symbol wieloznaczny (podkreślenie) można uniknąć, tworząc nową nazwę dla wartości, która nie ma potrzeby.

[!code-fsharp[Main](../../../samples/snippets/fsharp/tuples/basic-examples.fsx#L53-L54)]

Kopiowanie elementów z krotki odwołania do krotki struktury również jest prosty:

[!code-fsharp[Main](../../../samples/snippets/fsharp/tuples/basic-examples.fsx#L62-L66)]

Funkcje `fst` i `snd` (odwoływać się tylko krotek) zwraca pierwszy i drugi elementów krotki, odpowiednio.

[!code-fsharp[Main](../../../samples/snippets/fsharp/tuples/basic-examples.fsx#L72-L73)]

Nie ma wbudowanych funkcji zwracającą trzeci element triple, ale łatwe napisania jednego w następujący sposób.

[!code-fsharp[Main](../../../samples/snippets/fsharp/tuples/basic-examples.fsx#L78-L78)]

Ogólnie rzecz biorąc lepiej jest dostęp do elementów poszczególne krotki z za pomocą dopasowywania do wzorca.

## <a name="using-tuples"></a>Możliwość korzystania z krotek

Spójne kolekcje zapewniają wygodny sposób wielu wartości zwracane przez funkcję, jak pokazano w poniższym przykładzie. W tym przykładzie wykonuje dzielenie liczby całkowitej i zwraca zaokrąglony wynik operacji, ponieważ pierwszego elementu członkowskiego pary krotki, jak i resztę jako drugi element członkowski pary.

[!code-fsharp[Main](../../../samples/snippets/fsharp/tuples/basic-examples.fsx#L83-L86)]

Kolekcje można również jako argumenty funkcji uniknąć niejawne currying argumentów funkcji, które jest implikowane przez zwykłe składnię.

[!code-fsharp[Main](../../../samples/snippets/fsharp/tuples/basic-examples.fsx#L88-L88)]

Typowej składni do definiowania funkcji `let sum a b = a + b` pozwala na zdefiniowanie funkcja, która jest częściowym zastosowaniem pierwszy argument funkcji, jak pokazano w poniższym kodzie.

[!code-fsharp[Main](../../../samples/snippets/fsharp/tuples/basic-examples.fsx#L90-L94)]

Przy użyciu spójnych kolekcji jako parametr wyłącza currying. Aby uzyskać więcej informacji, zobacz "Częściowe stosowanie argumentów" w [funkcji](functions/index.md).

## <a name="names-of-tuple-types"></a>Nazwy typów krotki

Kiedy piszesz się nazwę typu, który jest spójną kolekcją, możesz użyć `*` symbol do oddzielania elementów. Dla spójną kolekcją, która składa się z `int`, `float`, a `string`, takich jak `(10, 10.0, "ten")`, typu, które powinny być zapisane w następujący sposób.

```fsharp
int * float * string
```

## <a name="interoperation-with-c-tuples"></a>Współdziałanie z Krotkami języka C#

C# 7.0 wprowadzono krotek języka.  Spójne kolekcje w języku C# są strukturami i są równoważne z krotek struktur w języku F#.  Jeśli musisz współdziałać z C#, należy użyć krotek struktur.

Jest to proste.  Załóżmy, że trzeba przekazać krotki do klasy C#, a następnie zużyć je jej wynik, który jest również spójnej kolekcji:

```csharp
namespace CSharpTupleInterop
{
    public static class Example
    {
        public static (int, int) AddOneToXAndY((int x, int y) a) =>
            (a.x + 1, a.y + 1);
    }
}
```

W F# kodzie można przekazać krotki struktury jako parametr i korzystać z wynik w postaci krotki struktury.

```fsharp
open TupleInterop

let struct (newX, newY) = Example.AddOneToXAndY(struct (1, 2))
// newX is now 2, and newY is now 3
```

### <a name="converting-between-reference-tuples-and-struct-tuples"></a>Konwertowanie pomiędzy krotek struktur i kolekcje odwołania

Ponieważ krotek struktur i kolekcje odwołanie całkowicie różnych reprezentacji podstawowych, nie są one niejawnej konwersji.  Oznacza to, że nie będzie kompilacji kodu, takie jak następujące:

[!code-fsharp[Main](../../../samples/snippets/fsharp/tuples/interop.fsx#L5-L12)]

Należy wzorca dopasowania po jednej krotce i konstruowania, pozostałe części składowe.  Na przykład:

[!code-fsharp[Main](../../../samples/snippets/fsharp/tuples/interop.fsx#L18-L22)]

## <a name="compiled-form-of-reference-tuples"></a>Skompilowanej formy krotek odwołania

W tej sekcji opisano formularza krotek, gdy są one skompilowane.  W tym miejscu nie są one niezbędne do odczytu, o ile nie są przeznaczone dla .NET Framework 3.5 lub niższą.

Kolekcje są kompilowane do jednego z kilku typów ogólnych, wszystkie nazwane obiekty `System.Tuple`, które są przeciążone na liczby argumentów lub liczbę parametrów typu. Typy krotek są wyświetlane w tym formularzu, podczas wyświetlania ich w innym języku, takich jak C# lub Visual Basic lub korzystając z narzędzia, która nie ma informacji o konstrukcje F#. `Tuple` Typy zostały wprowadzone w programie .NET Framework 4. Jeśli jest przeznaczony dla starszej wersji programu .NET Framework, kompilator używa wersji [System.Tuple](https://msdn.microsoft.com/library/5ac7953d-acdc-4a58-bfb7-c1f6406c0fa3) z podstawowej biblioteki języka F# w wersji 2.0. Typy w tej bibliotece są używane tylko w przypadku aplikacji przeznaczonych dla wersji 2.0, 3.0 i 3.5 wersje programu .NET Framework. Przekazywanie dalej typu jest używany w celu zapewnienia zgodność binarną między składnikami programu .NET Framework 2.0 i .NET Framework 4 F#.

### <a name="compiled-form-of-struct-tuples"></a>Skompilowanej formy krotek struktur

Krotek struktur (na przykład `struct (x, y)`), są różni się od krotek odwołania.  Są one kompilowane do <xref:System.ValueTuple> typu przeciążony przez liczby argumentów lub liczbę parametrów typu.  Są one równoważnymi [C# 7.0 krotek](../../csharp/tuples.md) i [krotek 2017 Visual Basic](../../visual-basic/programming-guide/language-features/data-types/tuples.md)oraz współpraca dwukierunkowo.

## <a name="see-also"></a>Zobacz także

- [Dokumentacja języka F#](index.md)
- [Typy F#](fsharp-types.md)
