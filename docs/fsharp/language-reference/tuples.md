---
title: Krotki (F#)
description: "Więcej informacji na temat F # krotki, grupowanie bez nazwy, ale uporządkowanej wartości, prawdopodobnie różnych typów."
keywords: "Visual f #, f #, funkcjonalności programowania"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 35069073-9a82-410f-8dea-912e2a152e6d
ms.openlocfilehash: c6a0565ac7022928f5c2bdad5387d896c6c3d387
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="tuples"></a>Krotki

A *krotki* to grupa bez nazwy, ale uporządkowanej wartości, prawdopodobnie różnych typów.  Krotki może być typu odwołania lub struktury.

## <a name="syntax"></a>Składnia

```fsharp
(element, ... , element)
struct(element, ... ,element )
```
## <a name="remarks"></a>Uwagi
Każdy *elementu* w poprzednim składni może być dowolne prawidłowe wyrażenie F #.

## <a name="examples"></a>Przykłady
Przykładami krotek pary, triples i tak dalej, w tym samym lub różnych typów. Przykłady zostały przedstawione w poniższym kodzie.

[!code-fsharp[Main](../../../samples/snippets/fsharp/tuples/basic-examples.fsx#L6-L21)]
    
## <a name="obtaining-individual-values"></a>Uzyskiwanie poszczególne wartości
Umożliwia dopasowanie wzorca dostępu i przypisać nazwy dla spójnej kolekcji elementów, jak pokazano w poniższym kodzie.

[!code-fsharp[Main](../../../samples/snippets/fsharp/tuples/basic-examples.fsx#L27-L29)]

Można również deconstruct krotka za pomocą dopasowywania do wzorca poza `match` wyrażenia za pośrednictwem `let` powiązania:

[!code-fsharp[Main](../../../samples/snippets/fsharp/tuples/basic-examples.fsx#L34-L37)]

Lub może wzorzec dopasowywania w krotek jako dane wejściowe do funkcji:

[!code-fsharp[Main](../../../samples/snippets/fsharp/tuples/basic-examples.fsx#L43-L47)]

Tylko jeden element spójnej kolekcji, należy symbol wieloznaczny (podkreślenie) można uniknąć nową nazwę wartość, która nie ma potrzeby tworzenia.

[!code-fsharp[Main](../../../samples/snippets/fsharp/tuples/basic-examples.fsx#L53-L54)]

Kopiowanie elementów z krotka odwołania do krotka struktury również jest prosty:

[!code-fsharp[Main](../../../samples/snippets/fsharp/tuples/basic-examples.fsx#L62-L66)]

Funkcje `fst` i `snd` (odwoływać się tylko krotek) zwraca pierwsze i drugie elementy krotki, odpowiednio.

[!code-fsharp[Main](../../../samples/snippets/fsharp/tuples/basic-examples.fsx#L72-L73)]

Nie jest nie wbudowanych funkcji zwracającą trzeciego elementu trzykrotnie, ale łatwo zapisu jedną w następujący sposób.

[!code-fsharp[Main](../../../samples/snippets/fsharp/tuples/basic-examples.fsx#L78-L78)]

Ogólnie rzecz biorąc lepiej jest na potrzeby dopasowywania do wzorca dostęp do poszczególnych spójnej kolekcji elementów.

## <a name="using-tuples"></a>Przy użyciu spójnych kolekcji
Krotki zapewnić wygodny sposób wielu wartości zwracane przez funkcję, jak pokazano w poniższym przykładzie. W tym przykładzie przeprowadza dzielenie liczby całkowitej i zwraca zaokrąglony wynik operacji jako pierwszego elementu członkowskiego pary spójnej kolekcji, a reszta jako drugiego elementu członkowskiego pary.

[!code-fsharp[Main](../../../samples/snippets/fsharp/tuples/basic-examples.fsx#L83-L86)]

Krotek również może służyć jako argumenty funkcji, gdy chce się uniknąć niejawne currying argumentów funkcji, które jest implikowana przez zwykłe składnię.

[!code-fsharp[Main](../../../samples/snippets/fsharp/tuples/basic-examples.fsx#L88-L88)]

Zwykle składnia definiujący funkcję `let sum a b = a + b` umożliwia zdefiniowanie funkcja, która jest aplikacja częściowa pierwszego argumentu funkcji, jak pokazano w poniższym kodzie.

[!code-fsharp[Main](../../../samples/snippets/fsharp/tuples/basic-examples.fsx#L90-L94)]

Przy użyciu spójnych kolekcji jako parametr wyłącza currying. Aby uzyskać więcej informacji, zobacz "Częściowe aplikacji argumenty" w [funkcji](functions/index.md).

## <a name="names-of-tuple-types"></a>Nazwy typów spójnej kolekcji
Podczas pisania limit nazwę typu, który jest spójnej kolekcji, użyj `*` symbol do oddzielania elementów. Dla krotka składająca się z `int`, `float`, a `string`, takich jak `(10, 10.0, "ten")`, typu powinny być zapisane w następujący sposób.

```fsharp
int * float * string
```

## <a name="interoperation-with-c-tuples"></a>Współdziałanie z krotek C#

Do języka C# 7 wprowadza spójnych kolekcji.  Spójne kolekcje w C# i czy struktur i są równoważne krotek struktury w języku F #.  Jeśli potrzebujesz na potrzeby współdziałania z C# używa krotek, należy użyć krotek struktury.

Jest to łatwo zrobić.  Załóżmy, że trzeba przekazać krotka do klasy C# i korzystać z jej wynik, który jest także spójnych kolekcji:

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

W F # kodu można przekazać krotka struktury jako parametr i korzystać z wynik w postaci spójnej kolekcji struktury.

```fsharp
open TupleInterop

let struct (newX, newY) = Example.AddOneToXAndY(struct (1, 2))
// newX is now 2, and newY is now 3
```

### <a name="converting-between-reference-tuples-and-struct-tuples"></a>Konwertowanie pomiędzy krotek odwołania i krotek — struktura

Ponieważ krotek odwołania i struktury krotek dwóch zupełnie różnych reprezentacji podstawowych, nie są one umożliwiają niejawnej konwersji.  Oznacza to nie będzie kompilacji kodu, takie jak następujące:

[!code-fsharp[Main](../../../samples/snippets/fsharp/tuples/interop.fsx#L5-L12)]

Musi być wzorzec dopasowywania w jednej krotce i utworzyć drugi z elementów składowych.  Na przykład:

[!code-fsharp[Main](../../../samples/snippets/fsharp/tuples/interop.fsx#L18-L22)]

## <a name="compiled-form-of-reference-tuples"></a>Skompilowanej postaci krotek odwołania
W tej sekcji opisano formę krotek, gdy są one kompilowane.  Informacje w tym miejscu nie jest konieczne do odczytu, chyba że ma być przeznaczona dla programu .NET Framework 3.5 lub niższej.

Spójne kolekcje są kompilowane w obiektach jednego z kilku typów ogólnych, wszystkie nazwane `System.Tuple`, które są przeciążone w liczbie argumentów lub liczba parametrów typu. Typy spójnej kolekcji są wyświetlane w tym formularzu podczas przeglądania w innym języku, takich jak C# lub Visual Basic lub korzystając z narzędzia, które nie są znane konstrukcji F #. `Tuple` Typy zostały wprowadzone w programie .NET Framework 4. Jeśli aplikacja jest przeznaczona dla starszej wersji programu .NET Framework, kompilator używa wersji [System.Tuple](https://msdn.microsoft.com/library/5ac7953d-acdc-4a58-bfb7-c1f6406c0fa3) w wersji 2.0 biblioteki podstawowej F #. Typy w tej bibliotece są używane tylko dla aplikacji przeznaczonych dla 2.0, 3.0 i 3.5 wersje programu .NET Framework. Przekazywanie dalej typu jest używany do zapewniania zgodności plików binarnych między składnikami programu .NET Framework 2.0 i .NET Framework 4 F #.

### <a name="compiled-form-of-struct-tuples"></a>Skompilowanej postaci krotek — struktura

Struktura krotek (na przykład `struct (x, y)`), są różni się od krotek odwołania.  Są one kompilowane do <xref:System.ValueTuple> typu przeciążony przez argumentów lub liczba parametrów typu.  Są równoważne [C# 7 krotek](../../csharp/tuples.md) i [krotek 2017 Visual Basic](../../visual-basic/programming-guide/language-features/data-types/tuples.md)oraz współpraca dwukierunkowo.

## <a name="see-also"></a>Zobacz też
[Dokumentacja języka F #](index.md)

[Typy F #](fsharp-types.md)
