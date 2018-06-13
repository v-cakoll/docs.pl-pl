---
title: 'Pola jawne: val — Słowo kluczowe (F#)'
description: 'Dowiedz się więcej o F # "val" — słowo kluczowe, które służy do deklarowania lokalizację do przechowywania wartości w typie klasy lub struktury bez zainicjowania typu.'
ms.date: 05/16/2016
ms.openlocfilehash: 2bd1aae24a5823ddcd6bb8f121d8110f4a211a6a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33565824"
---
# <a name="explicit-fields-the-val-keyword"></a>Pola jawne: val — Słowo kluczowe

`val` — Słowo kluczowe służy do deklarowania lokalizację do przechowywania wartości w typie klasy lub struktury, bez jego inicjowania. Zadeklarowany w ten sposób lokalizacji przechowywania są nazywane *pola jawne*. Użycie innego `val` — słowo kluczowe jest używana razem z `member` słowo kluczowe, aby zadeklarować właściwości zaimplementowane automatycznie. Aby uzyskać więcej informacji na temat właściwości zaimplementowane automatycznie, zobacz [właściwości](properties.md).


## <a name="syntax"></a>Składnia

```fsharp
val [ mutable ] [ access-modifier ] field-name : type-name
```

## <a name="remarks"></a>Uwagi
Zwykły sposób, aby zdefiniować pól w typie klasy lub struktury jest użycie `let` powiązania. Jednak `let` powiązania musi zostać zainicjowany jako część konstruktora klasy, która nie jest zawsze możliwe, wymagane lub pożądane. Można użyć `val` — słowo kluczowe, jeśli chcesz pola, które nie jest zainicjowany.

Pola jawne mogą być statyczne lub statyczna. *Modyfikator dostępu* może być `public`, `private`, lub `internal`. Domyślnie pola jawne są publiczne. To różni się od `let` powiązania w klasach, które są zawsze prywatne.

[DefaultValue](https://msdn.microsoft.com/library/a3a3307b-8c05-441e-b109-245511614d58) atrybut jest wymagany dla pola jawne w typach klas, które mają podstawowego konstruktora. Ten atrybut określa, czy pole ustawiana jest wartość zero. Typ pola musi obsługiwać inicjowania zero. Typem obsługuje inicjowania zero, jeśli jest to jeden z następujących czynności:

- Pierwotny typ, który ma wartość zerową.

- Typ, który obsługuje wartość null albo jako wartość normalne, jako wartość nieprawidłowego lub jako reprezentację wartości. Dotyczy to również klas, krotek, rekordy, funkcji, interfejsów, typów referencyjnych .NET, `unit` typu i typy Unii rozłącznych.

- Typ wartości .NET.

- Struktury, którego wszystkie pola obsługiwać wartość domyślną wartość zero.


Na przykład modyfikować pola o nazwie `someField` został skompilowany polem zapasowym w ramach platformy .NET reprezentacja o nazwie `someField@`, uzyskasz dostęp do wartości przechowywanej za pomocą właściwości o nazwie `someField`.

Dla pola modyfikowalnego reprezentacja skompilowana .NET jest polem .NET.


>[!WARNING] 
`Note` Przestrzeń nazw .NET Framework `System.ComponentModel` zawiera atrybut, który ma taką samą nazwę. Informacje dla tego atrybutu, zobacz `System.ComponentModel.DefaultValueAttribute`.


Poniższy kod przedstawia użycie pola jawne oraz do porównania, `let` powiązania w klasie, która ma podstawowego konstruktora. Należy pamiętać, że `let`— pole powiązane `myInt1` jest prywatny. Gdy `let`— pole powiązane `myInt1` jest wywoływany przez metodę elementu członkowskiego własnego identyfikatora `this` nie jest wymagana. Jednak gdy utworzono odwołanie do pola jawne `myInt2` i `myString`, własnego identyfikatora jest wymagana.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet6701.fs)]

Wynik jest następujący:

```
11 12 abc
30 def
```

Poniższy kod przedstawia jawne pola w klasie, która nie ma podstawowego konstruktora. W takim przypadku `DefaultValue` atrybut nie jest wymagana, ale wszystkie pola muszą zostać zainicjowane w konstruktorach, które są zdefiniowane dla typu.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet6702.fs)]

Dane wyjściowe `35 22`.

Poniższy kod przedstawia jawne pola w strukturze. Ponieważ struktura jest typem wartości, automatycznie ma domyślny konstruktor, który ustawia wartości pól na zero. W związku z tym `DefaultValue` atrybut nie jest wymagana.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet6703.fs)]

Dane wyjściowe `11 xyz`.

Pola jawne nie są przeznaczone do użytku rutynowych. Ogólnie rzecz biorąc, gdy jest to możliwe należy używać `let` powiązania w klasie zamiast jawnego pola. Pola jawne są przydatne w niektórych scenariuszach współdziałanie, np. gdy są potrzebne do definiowania struktury, który będzie używany w platformie wywołania wywołania do natywnego API ani w zastosowaniach międzyoperacyjnego COM. Aby uzyskać więcej informacji, zobacz [funkcji zewnętrznych](../functions/external-functions.md). Innej sytuacji, w którym jawne pole może być konieczne jest podczas pracy z F # generatora kodu który emituje klas bez podstawowego konstruktora. Pola jawne są także przydatne zmienne statyczne dla wątku lub podobne konstrukcje. Aby uzyskać więcej informacji, zobacz `System.ThreadStaticAttribute`.

Gdy słowa kluczowe `member val` występować razem w definicji typu, jest automatycznie implementowanej właściwości definicji. Aby uzyskać więcej informacji, zobacz [właściwości](properties.md).


## <a name="see-also"></a>Zobacz też
[Właściwości](properties.md)

[Elementy członkowskie](index.md)

[`let` Powiązania w klasach](let-bindings-in-classes.md)
