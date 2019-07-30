---
title: Krotki
description: Dowiedz się F# więcej na temat krotki, grupowania nienazwanych, ale uporządkowanych wartości, prawdopodobnie różnych typów.
ms.date: 05/16/2016
ms.openlocfilehash: 7a15d7e0c6c9b42118dd75066f02cbb2e05335fc
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630241"
---
# <a name="tuples"></a>Krotki

*Krotka* to grupa nienazwanych, ale uporządkowanych wartości, prawdopodobnie różnych typów.  Krotki mogą być typami referencyjnymi lub strukturami.

## <a name="syntax"></a>Składnia

```fsharp
(element, ... , element)
struct(element, ... ,element )
```

## <a name="remarks"></a>Uwagi

Każdy *element* w poprzedniej składni może być dowolnym prawidłowym F# wyrażeniem.

## <a name="examples"></a>Przykłady

Przykłady krotek obejmują pary, potrójne i tak dalej, o tych samych lub różnych typach. Przykłady przedstawiono w poniższym kodzie.

[!code-fsharp[Main](~/samples/snippets/fsharp/tuples/basic-examples.fsx#L6-L21)]

## <a name="obtaining-individual-values"></a>Uzyskiwanie pojedynczych wartości

Możesz użyć dopasowania wzorca, aby uzyskać dostęp i przypisać nazwy dla elementów krotki, jak pokazano w poniższym kodzie.

[!code-fsharp[Main](~/samples/snippets/fsharp/tuples/basic-examples.fsx#L27-L29)]

Możesz również odtworzyć krotkę przez dopasowanie wzorca poza `match` wyrażeniem za pośrednictwem `let` powiązania:

[!code-fsharp[Main](~/samples/snippets/fsharp/tuples/basic-examples.fsx#L34-L37)]

Lub można dopasować do wzorca spójnych krotek jako dane wejściowe do funkcji:

[!code-fsharp[Main](~/samples/snippets/fsharp/tuples/basic-examples.fsx#L43-L47)]

Jeśli potrzebujesz tylko jednego elementu krotki, symbol wieloznaczny (podkreślenie) można użyć, aby uniknąć tworzenia nowej nazwy dla niepotrzebnej wartości.

[!code-fsharp[Main](~/samples/snippets/fsharp/tuples/basic-examples.fsx#L53-L54)]

Kopiowanie elementów z krotki referencyjnej do krotki struktury jest również proste:

[!code-fsharp[Main](~/samples/snippets/fsharp/tuples/basic-examples.fsx#L62-L66)]

Funkcje `fst` i`snd` (tylko krotki referencyjne) zwracają odpowiednio pierwszy i drugi element spójnej kolekcji.

[!code-fsharp[Main](~/samples/snippets/fsharp/tuples/basic-examples.fsx#L72-L73)]

Nie istnieje Wbudowana funkcja, która zwraca trzeci element trzykrotności, ale można ją łatwo napisać w następujący sposób.

[!code-fsharp[Main](~/samples/snippets/fsharp/tuples/basic-examples.fsx#L78-L78)]

Ogólnie rzecz biorąc lepiej jest używać dopasowywania wzorców w celu uzyskania dostępu do poszczególnych elementów krotki.

## <a name="using-tuples"></a>Używanie krotek

Krotki zapewniają wygodny sposób zwracania wielu wartości z funkcji, jak pokazano w poniższym przykładzie. Ten przykład wykonuje dzielenie liczby całkowitej i zwraca zaokrąglony wynik operacji jako pierwszy element członkowski pary krotek i resztę jako drugi element członkowski pary.

[!code-fsharp[Main](~/samples/snippets/fsharp/tuples/basic-examples.fsx#L83-L86)]

Krotki mogą być również używane jako argumenty funkcji, gdy chcesz uniknąć niejawnego currying argumentów funkcji, które są implikowane przez normalną składnię funkcji.

[!code-fsharp[Main](~/samples/snippets/fsharp/tuples/basic-examples.fsx#L88-L88)]

Zwykła Składnia służąca do definiowania funkcji `let sum a b = a + b` umożliwia zdefiniowanie funkcji, która jest częściową aplikacją pierwszego argumentu funkcji, jak pokazano w poniższym kodzie.

[!code-fsharp[Main](~/samples/snippets/fsharp/tuples/basic-examples.fsx#L90-L94)]

Użycie krotki jako parametru powoduje wyłączenie currying. Aby uzyskać więcej informacji, zobacz "częściowe stosowanie argumentów" w [funkcjach](./functions/index.md).

## <a name="names-of-tuple-types"></a>Nazwy typów krotek

Podczas wpisywania nazwy typu, który jest krotką, należy użyć `*` symbolu do oddzielenia elementów. Dla krotki, która składa się `int`z `float`, a, i `string`a, takich `(10, 10.0, "ten")`jak, typ zostałby zapisany w następujący sposób.

```fsharp
int * float * string
```

## <a name="interoperation-with-c-tuples"></a>Współdziałanie C# z krotkami

C#7,0 wprowadza krotki do języka.  Krotki w C# są strukturami i są odpowiednikami krotek struktury w F#.  Jeśli musisz współpracować z programem C#, musisz użyć krotek struktury.

Jest to bardzo proste.  Załóżmy na przykład, że musisz przekazać krotkę do C# klasy, a następnie użyć jej wyniku, która jest również krotką:

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

W F# kodzie można następnie przekazać krotkę struktury jako parametr i użyć wyniku jako krotki struktury.

```fsharp
open TupleInterop

let struct (newX, newY) = Example.AddOneToXAndY(struct (1, 2))
// newX is now 2, and newY is now 3
```

### <a name="converting-between-reference-tuples-and-struct-tuples"></a>Konwertowanie między Krotekmi referencyjnymi a krotkami struktury

Ponieważ krotki referencyjne i krotek struktury mają zupełnie inną reprezentację podstawową, nie są one niejawnie konwertowane.  Oznacza to, że kod, taki jak następujące, nie zostanie skompilowany:

[!code-fsharp[Main](~/samples/snippets/fsharp/tuples/interop.fsx#L5-L12)]

Musisz dopasować wzorzec dla jednej krotki i utworzyć drugą z częściami elementów.  Na przykład:

[!code-fsharp[Main](~/samples/snippets/fsharp/tuples/interop.fsx#L18-L22)]

## <a name="compiled-form-of-reference-tuples"></a>Skompilowana forma kolekcji referencyjnych

W tej sekcji opisano formę krotek, gdy są one kompilowane.  Informacje w tym miejscu nie są niezbędne do odczytania, chyba że jest przeznaczony .NET Framework 3,5 lub niższy.

Krotki są kompilowane do obiektów jednego z kilku typów ogólnych, wszystkie nazwane `System.Tuple`, które są przeciążone dla liczby argumentów lub liczby parametrów typu. Typy krotek są wyświetlane w tym formularzu podczas wyświetlania ich z innego języka, takiego jak C# lub Visual Basic, lub podczas korzystania z narzędzia, które nie ma informacji o F# konstrukcjach. `Tuple` Typy zostały wprowadzone w .NET Framework 4. Jeśli obiektem docelowym jest wcześniejsza wersja .NET Framework, kompilator używa wersji elementu [System. krotka](https://msdn.microsoft.com/library/5ac7953d-acdc-4a58-bfb7-c1f6406c0fa3) z wersji 2,0 biblioteki F# podstawowej. Typy w tej bibliotece są używane tylko dla aplikacji przeznaczonych dla wersji 2,0, 3,0 i 3,5 .NET Framework. Przekazywanie typu jest używane w celu zapewnienia zgodności binarnej między składnikami .NET Framework F# 2,0 i .NET Framework 4.

### <a name="compiled-form-of-struct-tuples"></a>Skompilowana forma krotek struktury

Krotki struktury (na przykład `struct (x, y)`) różnią się zasadniczo od krotek odwołania.  Są one kompilowane w <xref:System.ValueTuple> typie, przeciążonym przez liczbę argumentów lub liczbie parametrów typu.  Są one równoważne z [ C# 7,0 krotkami](../../csharp/tuples.md) i [Visual Basic 2017 krotek](../../visual-basic/programming-guide/language-features/data-types/tuples.md)i współdziałają dwukierunkowo.

## <a name="see-also"></a>Zobacz także

- [Dokumentacja języka F#](index.md)
- [Typy F#](fsharp-types.md)
