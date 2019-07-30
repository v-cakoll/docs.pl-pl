---
title: 'Deklaracje importowania: słowo kluczowe open'
description: Dowiedz F# się więcej na temat deklaracji importu i sposobu określania modułu lub przestrzeni nazw, których elementy można odwołać bez używania w pełni kwalifikowanej nazwy.
ms.date: 04/04/2019
ms.openlocfilehash: 816bac551692c3397290f64c6267ee22e4ce90fb
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630578"
---
# <a name="import-declarations-the-open-keyword"></a>Deklaracje importowania: słowo kluczowe `open`

> [!NOTE]
> Linki do odwołań do interfejsów API w tym artykule przeprowadzą Cię do subskrypcji MSDN.  Dokumentacja interfejsu API docs.microsoft.com nie została ukończona.

*Deklaracja importu* określa moduł lub przestrzeń nazw, których elementy można odwoływać bez używania w pełni kwalifikowanej nazwy.

## <a name="syntax"></a>Składnia

```fsharp
open module-or-namespace-name
```

## <a name="remarks"></a>Uwagi

Odwoływanie się do kodu przy użyciu w pełni kwalifikowanej przestrzeni nazw lub ścieżki modułu za każdym razem, gdy program może utworzyć kod, który jest trudno pisać, czytać i konserwować. Zamiast tego można użyć `open` słowa kluczowego dla często używanych modułów i przestrzeni nazw, aby podczas odwoływania się do elementu członkowskiego tego modułu lub przestrzeni nazw można użyć krótkiej formy nazwy zamiast w pełni kwalifikowanej nazwy. To słowo kluczowe jest podobne do `using` słowa kluczowego `using namespace` C#w, C++w wizualizacji i `Imports` w Visual Basic.

Dostarczony moduł lub przestrzeń nazw muszą znajdować się w tym samym projekcie lub w przywoływanym projekcie lub zestawie. Jeśli tak nie jest, można dodać odwołanie do projektu lub użyć `-reference` opcji wiersza polecenia`-` `-r`(lub jego skrótu). Aby uzyskać więcej informacji, zobacz [Opcje kompilatora](compiler-options.md).

Deklaracja importu udostępnia nazwy dostępne w kodzie, który następuje po deklaracji, do końca otaczającej przestrzeni nazw, modułu lub pliku.

Jeśli używasz wielu deklaracji importu, powinny one pojawiać się w osobnych wierszach.

Poniższy kod ilustruje użycie `open` słowa kluczowego w celu uproszczenia kodu.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet6801.fs)]

F# Kompilator nie emituje błędu lub ostrzeżenia, gdy niejasności wystąpi, gdy ta sama nazwa występuje w więcej niż jednym otwartym module lub przestrzeni nazw. Gdy wystąpi niejasności, F# zapewnia preferencję dla ostatnio otwartego modułu lub przestrzeni nazw. Na przykład, w poniższym kodzie, `empty` oznacza `Seq.empty`, `empty` chociaż znajduje się zarówno `List` w module, jak i `Seq` .

```fsharp
open List
open Seq
printfn "%A" empty
```

W związku z tym należy zachować ostrożność podczas otwierania modułów lub `List` przestrzeni `Seq` nazw, takich jak lub zawierających składowe o identycznych nazwach. zamiast tego należy rozważyć użycie kwalifikowanych nazw. Należy unikać każdej sytuacji, w której kod jest zależny od kolejności deklaracji importu.

## <a name="namespaces-that-are-open-by-default"></a>Obszary nazw, które są domyślnie otwarte

Niektóre przestrzenie nazw są często używane F# w kodzie, który są otwierane niejawnie bez potrzeby jawnej deklaracji importu. W poniższej tabeli przedstawiono obszary nazw, które są domyślnie otwarte.

|Przestrzeń nazw|Opis|
|---------|-----------|
|`Microsoft.FSharp.Core`|Zawiera podstawowe F# definicje typów dla typów wbudowanych, takich jak `int` i. `float`|
|`Microsoft.FSharp.Core.Operators`|Zawiera podstawowe operacje arytmetyczne, `+` takie `*`jak i.|
|`Microsoft.FSharp.Collections`|Zawiera niezmienne klasy kolekcji, `List` takie `Array`jak i.|
|`Microsoft.FSharp.Control`|Zawiera typy dla konstrukcji kontroli, takich jak Ocena z opóźnieniem i asynchroniczne przepływy pracy.|
|`Microsoft.FSharp.Text`|Zawiera funkcje dla sformatowanych operacji we/wy `printf` , takich jak funkcja.|

## <a name="autoopen-attribute"></a>AutoOpen — atrybut

Można zastosować `AutoOpen` atrybut do zestawu, jeśli chcesz automatycznie otworzyć przestrzeń nazw lub moduł, gdy odwołanie do zestawu. Można również zastosować `AutoOpen` atrybut do modułu, aby automatycznie otworzyć ten moduł po otwarciu modułu nadrzędnego lub przestrzeni nazw. Aby uzyskać więcej informacji, zobacz [Klasa Core.](https://msdn.microsoft.com/visualfsharpdocs/conceptual/core.autoopenattribute-class-%5bfsharp%5d)AutoOpenAttribute.

## <a name="requirequalifiedaccess-attribute"></a>RequireQualifiedAccess — atrybut

Niektóre moduły, rekordy lub typy Unii mogą określać `RequireQualifiedAccess` atrybut. Gdy odwołujesz się do elementów tych modułów, rekordów lub Unii, musisz użyć kwalifikowanej nazwy bez względu na to, czy dołączysz deklarację importu. Jeśli ten atrybut jest używany strategicznie dla typów, które definiują często używane nazwy, można uniknąć kolizji nazw, a tym samym zwiększyć odporność kodu na zmiany w bibliotekach. Aby uzyskać więcej informacji, zobacz [Klasa Core. RequireQualifiedAccessAttribute —](https://msdn.microsoft.com/visualfsharpdocs/conceptual/core.requirequalifiedaccessattribute-class-%5Bfsharp%5D).

## <a name="see-also"></a>Zobacz także

- [Dokumentacja języka F#](index.md)
- [Przestrzenie nazw](namespaces.md)
- [Moduły](modules.md)
