---
title: 'Deklaracje importowania: open — Słowo kluczowe (F#)'
description: 'Dowiedz się więcej o deklaracje importowania F # oraz jak określić modułu lub przestrzeni nazw elementów, których można odwoływać się bez korzystania z w pełni kwalifikowaną nazwę.'
ms.date: 05/16/2016
ms.openlocfilehash: 29f09297993b347464f1572ac9ca24902c786f4d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33563535"
---
# <a name="import-declarations-the-open-keyword"></a>Deklaracje importowania: `open` — słowo kluczowe

> [!NOTE]
Interfejs API łącza odwołań w tym artykule spowoduje przejście do MSDN.  Dokumentacja interfejsu API docs.microsoft.com nie została ukończona.

*Deklaracja importu* Określa nazwę modułu lub przestrzeni nazw elementów, których można odwoływać się bez korzystania z w pełni kwalifikowaną nazwę.


## <a name="syntax"></a>Składnia

```fsharp
open module-or-namespace-name
```

## <a name="remarks"></a>Uwagi
Odwołanie do kodu przy użyciu w pełni kwalifikowana ścieżka przestrzeni nazw lub modułu zawsze można utworzyć kod, który jest trudna do zapisu, przeczytaj i konserwacji. Zamiast tego można użyć `open` — słowo kluczowe dla często używane moduły i przestrzenie nazw, dzięki czemu w przypadku odwołania członkiem tego modułu lub przestrzeni nazw, można użyć Krótka forma nazwy zamiast w pełni kwalifikowana nazwa. To słowo kluczowe jest podobny do `using` — słowo kluczowe języka C# `using namespace` w programie Visual C++ i `Imports` w języku Visual Basic.

Modułu lub przestrzeni nazw, pod warunkiem, musi być w tym samym projekcie lub przywoływanego projektu lub zestawu. Jeśli nie jest dostępne, można dodać odwołania do projektu, lub użyj `-reference` polecenia`-`wiersz opcji (lub jego skrót `-r`). Aby uzyskać więcej informacji, zobacz [— opcje kompilatora](compiler-options.md).

Deklaracja importu udostępnia nazwy w kodzie występującym w deklaracji, aż do końca otaczającej przestrzeni nazw, modułu lub pliku.

Korzystając z wielu deklaracji importu, powinna pojawić się w osobnych wierszach.

Poniższy kod przedstawia użycie `open` — słowo kluczowe w celu uproszczenia kodu.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6801.fs)]

Kompilator języka F # nie Emituj błędu lub ostrzeżenia, gdy niejednoznaczności występują po tej samej nazwie w więcej niż jeden Otwórz modułu lub przestrzeni nazw. Gdy występują niejednoznaczności, F # daje preferencje więcej ostatnio otwartą modułu lub przestrzeni nazw. Na przykład w poniższym kodzie `empty` oznacza `Seq.empty`, nawet jeśli `empty` znajduje się w obu `List` i `Seq` modułów.

```fsharp
open List
open Seq
printfn "%A" empty
```

Dlatego należy zachować ostrożność podczas takich jak otworzyć modułach ani przestrzeniach nazw `List` lub `Seq` zawierających elementy członkowskie, które mają identyczne nazwy; zamiast tego Rozważ użycie nazwy kwalifikowane. Należy unikać każdej sytuacji, w której jest zależny od kolejność deklaracje importowania kodu.


## <a name="namespaces-that-are-open-by-default"></a>Przestrzenie nazw, które są otwarte domyślnie
Niektórych przestrzeni nazw są tak często używane w kodzie języka F #, że otwarciu niejawnie bez konieczności deklaracji jawny import. W poniższej tabeli przedstawiono przestrzeni nazw, które są otwarte domyślnie.

|Przestrzeń nazw|Opis|
|---------|-----------|
|`Microsoft.FSharp.Core`|Zawiera podstawowe definicje typów F # dla wbudowanych typów, takie jak `int` i `float`.|
|`Microsoft.FSharp.Core.Operators`|Zawiera podstawowe operacje arytmetyczne, takie jak `+` i `*`.|
|`Microsoft.FSharp.Collections`|Zawiera klasy modyfikować kolekcji, takie jak `List` i `Array`.|
|`Microsoft.FSharp.Control`|Zawiera typy do sterowania konstrukcje, takie jak obliczanie leniwe i asynchroniczne przepływy pracy.|
|`Microsoft.FSharp.Text`|Zawiera funkcje sformatowany we/wy, takich jak `printf` funkcji.|

## <a name="autoopen-attribute"></a>AutoOpen — atrybut
Możesz zastosować `AutoOpen` atrybutu do zestawu, jeśli chcesz automatycznie otworzyć przestrzeni nazw lub modułu, gdy odwołuje się do zestawu. Można także zastosować `AutoOpen` atrybutu modułu do automatycznego otwierania tego modułu po otwarciu nadrzędnego modułu lub przestrzeni nazw. Aby uzyskać więcej informacji, zobacz [Core.autoopenattribute — klasa](https://msdn.microsoft.com/visualfsharpdocs/conceptual/core.autoopenattribute-class-%5bfsharp%5d).


## <a name="requirequalifiedaccess-attribute"></a>RequireQualifiedAccess — atrybut
Niektóre moduły, rekordy lub typy Unii mogą określać `RequireQualifiedAccess` atrybutu. Podając odniesienie elementy tych modułów, rekordy lub Unii należy użyć kwalifikowanej nazwy niezależnie od tego, czy obejmują deklaracja importu. Użycie tego atrybutu strategicznie dla typów, które definiują najczęściej używane nazwy, pomaga uniknąć konfliktów nazw i tym samym wprowadzić kod bardziej odporne na zmiany w bibliotekach. Aby uzyskać więcej informacji, zobacz [Core.requirequalifiedaccessattribute — klasa](https://msdn.microsoft.com/visualfsharpdocs/conceptual/core.requirequalifiedaccessattribute-class-%5Bfsharp%5D).


## <a name="see-also"></a>Zobacz też
[# Odwołanie — język](index.md)

[Przestrzenie nazw](namespaces.md)

[Moduły](modules.md)

