---
title: 'Deklaracje importowania: Open — słowo kluczowe'
description: Dowiedz się więcej o F# zaimportować deklaracje i jak określić modułu lub przestrzeni nazw elementów, których możesz odwoływać się bez korzystania z w pełni kwalifikowanej nazwy.
ms.date: 04/04/2019
ms.openlocfilehash: ad64190c3243c57a185f3b864270fca80590f079
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61937504"
---
# <a name="import-declarations-the-open-keyword"></a>Deklaracje importowania: `open` — Słowo kluczowe

> [!NOTE]
> Łączy dokumentacja interfejsu API, w tym artykule spowoduje przejście do MSDN.  Dokumentacja interfejsu API w witrynie docs.microsoft.com nie została ukończona.

*Deklaracja importu* określa modułu lub przestrzeni nazw elementów, których możesz odwoływać się bez korzystania z w pełni kwalifikowanej nazwy.

## <a name="syntax"></a>Składnia

```fsharp
open module-or-namespace-name
```

## <a name="remarks"></a>Uwagi

Odwoływanie się do kodu przy użyciu w pełni kwalifikowana ścieżka przestrzeni nazw lub module każdym razem, gdy można tworzyć kod, który jest trudny do zapisu, odczytu i obsługa. Zamiast tego można użyć `open` — słowo kluczowe dla często używanych modułów i przestrzeni nazw, dzięki czemu Gdy odwołujesz się członkiem tego modułu lub przestrzeni nazw, a nie w pełni kwalifikowana nazwa, można użyć krótkiej formy o nazwie. This — słowo kluczowe jest podobny do `using` — słowo kluczowe w języku C# `using namespace` w programie Visual C++ i `Imports` w języku Visual Basic.

W tym samym projekcie lub w przywoływanego projektu lub zestawu, modułu lub przestrzeni nazw, pod warunkiem musi być. Jeśli nie jest dostępne, można dodać odwołania do projektu lub użyj `-reference` polecenia`-`opcji (lub jego skrót `-r`). Aby uzyskać więcej informacji, zobacz [opcje kompilatora](compiler-options.md).

Deklaracja importu udostępnia nazwy w kodzie, który następuje po deklaracji, aż do końcowego otaczającej przestrzeni nazw, modułu lub pliku.

Korzystając z wielu deklaracji importu, powinna zostać wyświetlona w osobnych wierszach.

Poniższy kod przedstawia użycie `open` — słowo kluczowe w celu uproszczenia kodu.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6801.fs)]

F# Kompilator nie generuje błąd lub ostrzeżenie przypadku niejednoznaczności wystąpienia sytuacji takiej samej nazwie w więcej niż jeden otwarty modułu lub przestrzeni nazw. Gdy występują niejasności, F# preferuje bardziej ostatnio otwieranych modułu lub przestrzeni nazw. Na przykład w poniższym kodzie `empty` oznacza `Seq.empty`, nawet jeśli `empty` znajduje się w obu `List` i `Seq` modułów.

```fsharp
open List
open Seq
printfn "%A" empty
```

W związku z tym, należy zachować ostrożność podczas takich jak otwierania modułów i przestrzeni nazw `List` lub `Seq` zawierających elementy członkowskie, które mają identyczne nazwy; zamiast tego Rozważ użycie kwalifikowanej nazwy. Należy unikać każdej sytuacji, w której kod jest zależny od kolejności deklaracji importu.

## <a name="namespaces-that-are-open-by-default"></a>Przestrzenie nazw, które są domyślnie otwarty

Niektóre przestrzenie nazw, dlatego często są używane w F# kodu, że są one otwarte niejawnie bez konieczności deklaracji jawny import. W poniższej tabeli przedstawiono przestrzenie nazw, które są domyślnie otwarty.

|Przestrzeń nazw|Opis|
|---------|-----------|
|`Microsoft.FSharp.Core`|Zawiera podstawowe F# wpisz definicje dla typów wbudowanych, taką jak `int` i `float`.|
|`Microsoft.FSharp.Core.Operators`|Zawiera podstawowe operacje arytmetyczne, takie jak `+` i `*`.|
|`Microsoft.FSharp.Collections`|Zawiera klasy kolekcji niezmienialnej, takie jak `List` i `Array`.|
|`Microsoft.FSharp.Control`|Zawiera typy dla konstrukcji kontrolki, takie jak obliczanie z opóźnieniem i asynchroniczne przepływy pracy.|
|`Microsoft.FSharp.Text`|Zawiera funkcje dla sformatowane we/wy, takich jak `printf` funkcji.|

## <a name="autoopen-attribute"></a>AutoOpen — atrybut

Można zastosować `AutoOpen` atrybut do zestawu, jeśli chcesz automatycznie otworzyć przestrzeni nazw lub module, gdy odwołuje się do zestawu. Można również zastosować `AutoOpen` atrybutu modułu, aby automatycznie otworzyć ten moduł, po otwarciu moduł nadrzędny lub przestrzeni nazw. Aby uzyskać więcej informacji, zobacz [Core.autoopenattribute — klasa](https://msdn.microsoft.com/visualfsharpdocs/conceptual/core.autoopenattribute-class-%5bfsharp%5d).

## <a name="requirequalifiedaccess-attribute"></a>Requirequalifiedaccess — atrybut

Niektóre moduły, rekordów lub typy Unii mogą określać `RequireQualifiedAccess` atrybutu. Gdy odwołujesz się elementy te moduły, rekordów lub Unii, należy użyć kwalifikowanej nazwy, niezależnie od tego, czy obejmują deklaracji importu. Użycie tego atrybutu strategicznie dla typów, które definiują najczęściej używane nazwy, pomagają uniknąć konfliktów nazw, a tym samym wprowadzić kod bardziej odporne na zmiany w bibliotekach. Aby uzyskać więcej informacji, zobacz [Core.requirequalifiedaccessattribute — klasa](https://msdn.microsoft.com/visualfsharpdocs/conceptual/core.requirequalifiedaccessattribute-class-%5Bfsharp%5D).

## <a name="see-also"></a>Zobacz także

- [Dokumentacja języka F#](index.md)
- [Przestrzenie nazw](namespaces.md)
- [Moduły](modules.md)
