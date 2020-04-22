---
title: 'Deklaracje importowania: open — Słowo kluczowe'
description: Dowiedz się więcej o deklaracjach importu języka F# i o tym, jak określają one moduł lub obszar nazw, do których można odwoływać się bez użycia w pełni kwalifikowanej nazwy.
ms.date: 04/04/2019
ms.openlocfilehash: 0baef27c7dc3181b9da0defb1c793fec04269c09
ms.sourcegitcommit: 348bb052d5cef109a61a3d5253faa5d7167d55ac
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2020
ms.locfileid: "82021534"
---
# <a name="import-declarations-the-open-keyword"></a>Deklaracje importu: słowo `open` kluczowe

> [!NOTE]
> Łącza odwołania interfejsu API w tym artykule spowoduje, że przejdziesz do usługi MSDN.  Odwołanie docs.microsoft.com interfejsu API nie jest kompletne.

*Deklaracja importu* określa moduł lub obszar nazw, do których elementów można odwoływać się bez użycia w pełni kwalifikowanej nazwy.

## <a name="syntax"></a>Składnia

```fsharp
open module-or-namespace-name
```

## <a name="remarks"></a>Uwagi

Odwoływanie się do kodu przy użyciu w pełni kwalifikowanego obszaru nazw lub ścieżki modułu za każdym razem można utworzyć kod, który jest trudny do zapisania, odczytu i utrzymania. Zamiast tego można użyć `open` słowa kluczowego dla często używanych modułów i obszarów nazw, dzięki czemu podczas odwoływania się do członka tego modułu lub obszaru nazw można użyć krótkiej formy nazwy zamiast w pełni kwalifikowanej nazwy. To słowo kluczowe `using` jest podobne do `using namespace` słowa kluczowego w `Imports` języku C#, w języku Visual C++ i Visual Basic.

Dostarczony moduł lub obszar nazw musi znajdować się w tym samym projekcie lub w projekcie lub zestawie, do którego istnieje odwołanie. Jeśli tak nie jest, można dodać odwołanie do `-reference` projektu lub użyć opcji wiersza polecenia `-r`(lub jego skrótu). Aby uzyskać więcej informacji, zobacz [Opcje kompilatora](compiler-options.md).

Deklaracja importu udostępnia nazwy w kodzie następującym po deklaracji, aż do końca otaczającego obszaru nazw, modułu lub pliku.

W przypadku używania wielu deklaracji importu powinny one być wyświetlane w oddzielnych wierszach.

Poniższy kod przedstawia użycie `open` słowa kluczowego w celu uproszczenia kodu.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet6801.fs)]

Kompilator Języka F# nie emituje błędu ani ostrzeżenia, gdy wystąpią niejasności, gdy ta sama nazwa występuje w więcej niż jednym otwartym module lub obszarze nazw. Gdy wystąpią niejasności, F# daje pierwszeństwo nowo otwarty moduł lub obszar nazw. Na przykład w poniższym `empty` `Seq.empty`kodzie `empty` oznacza , nawet `List` `Seq` jeśli znajduje się w modułach i modułach.

```fsharp
open List
open Seq
printfn "%A" empty
```

W związku z tym należy zachować ostrożność podczas `List` `Seq` otwierania modułów lub obszarów nazw, takich jak lub które zawierają elementy członkowskie, które mają identyczne nazwy; zamiast tego należy rozważyć użycie kwalifikowanych nazw. Należy unikać sytuacji, w której kod jest zależny od kolejności deklaracji importowych.

## <a name="namespaces-that-are-open-by-default"></a>Obszary nazw, które są domyślnie otwarte

Niektóre przestrzenie nazw są tak często używane w kodzie Języka F#, że są otwierane niejawnie bez konieczności jawnej deklaracji importu. W poniższej tabeli przedstawiono obszary nazw, które są domyślnie otwarte.

|Przestrzeń nazw|Opis|
|---------|-----------|
|`Microsoft.FSharp.Core`|Zawiera podstawowe definicje typów F# dla `int` typów `float`wbudowanych, takich jak i .|
|`Microsoft.FSharp.Core.Operators`|Zawiera podstawowe operacje arytmetyczne, takie jak `+` i `*`.|
|`Microsoft.FSharp.Collections`|Zawiera niezmienne klasy kolekcji, takie jak `List` i `Array`.|
|`Microsoft.FSharp.Control`|Zawiera typy dla konstrukcji kontroli, takich jak ocena z opóźnieniem i przepływów pracy asynchronicznej.|
|`Microsoft.FSharp.Text`|Zawiera funkcje sformatowanego we/wy, takie jak `printf` funkcja.|

## <a name="autoopen-attribute"></a>Atrybut AutoOpen

Można zastosować `AutoOpen` atrybut do zestawu, jeśli chcesz automatycznie otworzyć obszar nazw lub moduł, gdy zbliża się do zestawu. Można również zastosować `AutoOpen` atrybut do modułu, aby automatycznie otworzyć ten moduł po otwarciu modułu nadrzędnego lub obszaru nazw. Aby uzyskać więcej informacji, zobacz [Core.AutoOpenAttribute Class](https://msdn.microsoft.com/visualfsharpdocs/conceptual/core.autoopenattribute-class-%5bfsharp%5d).

## <a name="requirequalifiedaccess-attribute"></a>Atrybut Wymagaj wykwalifikowanegoAkcesji

Niektóre moduły, rekordy lub typy `RequireQualifiedAccess` unii mogą określać atrybut. Podczas odwoływania się do elementów tych modułów, rekordów lub związków należy użyć nazwy kwalifikowanej, niezależnie od tego, czy jest do nich deklaracja importu. Jeśli używasz tego atrybutu strategicznie na typy, które definiują powszechnie używane nazwy, można uniknąć kolizji nazw i tym samym uczynić kod bardziej odporne na zmiany w bibliotekach. Aby uzyskać więcej informacji, zobacz [Core.RequireQualifiedAccessAttribute Class](https://msdn.microsoft.com/visualfsharpdocs/conceptual/core.requirequalifiedaccessattribute-class-%5Bfsharp%5D).

## <a name="see-also"></a>Zobacz też

- [Odwołanie do języka F#](index.md)
- [Namespaces](namespaces.md)
- [Moduły](modules.md)
