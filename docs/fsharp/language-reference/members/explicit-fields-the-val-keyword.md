---
title: 'Pola jawne: val — Słowo kluczowe (F#)'
description: 'Więcej informacji na temat języka F # "val" słowo kluczowe, które jest używane do deklarowania lokalizację do przechowywania wartości w typie klasy lub struktury, bez inicjowania typu.'
ms.date: 05/16/2016
ms.openlocfilehash: 9cd06f7e90192be79490dd0ff67f118cce4339c3
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/14/2018
ms.locfileid: "45617373"
---
# <a name="explicit-fields-the-val-keyword"></a>Pola jawne: val — Słowo kluczowe

`val` — Słowo kluczowe jest używane do deklarowania lokalizację do przechowywania wartości w typie klasy lub struktury, bez jego inicjowania. Lokalizacje przechowywania, zadeklarowany w ten sposób są nazywane *pola jawne*. Używanie innego `val` — słowo kluczowe jest używana razem z `member` — słowo kluczowe do deklarowania automatycznie implementowanej właściwości. Aby uzyskać więcej informacji dotyczących automatycznie implementowanych właściwości, zobacz [właściwości](properties.md).

## <a name="syntax"></a>Składnia

```fsharp
val [ mutable ] [ access-modifier ] field-name : type-name
```

## <a name="remarks"></a>Uwagi

Zwykle sposobem zdefiniowania pola w typie klasy lub struktury jest użycie `let` powiązania. Jednak `let` powiązania musi zostać zainicjowany jako część konstruktora klasy, które nie zawsze jest możliwe, wymagane lub pożądane. Możesz użyć `val` — słowo kluczowe, jeśli chcesz, aby pola, które nie został zainicjowany.

Pola jawne może być statyczne lub niestatycznych. *Modyfikator dostępu* może być `public`, `private`, lub `internal`. Pola jawne są domyślnie publiczne. To różni się od `let` powiązania w klasach, które są zawsze prywatne.

[DefaultValue](https://msdn.microsoft.com/library/a3a3307b-8c05-441e-b109-245511614d58) atrybut jest wymagany na jawne pól w typach klasy, które mają podstawowy Konstruktor. Ten atrybut określa, że pole jest inicjowane od zera. Typ pola musi obsługiwać inicjowanie zero. Typ obsługuje inicjowania zero, jeśli jest to jeden z następujących czynności:

- Pierwotny typ, który ma wartość zero.

- Typ, który obsługuje wartości null, albo jako wartość normalna, jako wartość nietypowe lub jako reprezentację wartości. Obejmuje to klasy, krotek, rekordy, funkcje, interfejsy, typy odwołań platformy .NET, `unit` typu i dyskryminowanego typu złożenia.

- Typ wartości platformy .NET.

- Struktura, w których wszystkie pola obsługuje domyślną wartość zero.

Na przykład niezmienne pole o nazwie `someField` został skompilowany polem zapasowym na platformie .NET reprezentacji o nazwie `someField@`, i możesz uzyskać dostęp do wartości przechowywanej za pomocą właściwości o nazwie `someField`.

Modyfikowalne pola reprezentacja .NET skompilowanych jest polem .NET.

>[!WARNING]
`Note` Przestrzeń nazw .NET Framework `System.ComponentModel` zawiera atrybut, który ma taką samą nazwę. Aby uzyskać informacji na temat tego atrybutu, zobacz `System.ComponentModel.DefaultValueAttribute`.

Poniższy kod przedstawia użycie pola jawne i dla porównania `let` powiązania w klasie, która ma konstruktora podstawowego. Należy pamiętać, że `let`— pole związane `myInt1` jest prywatny. Gdy `let`— pola związanego `myInt1` jest wywoływany przez metodę elementu członkowskiego własny identyfikator `this` nie jest wymagana. Jednak gdy odwołujesz się do pola jawne `myInt2` i `myString`, własny identyfikator jest wymagany.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet6701.fs)]

Dane wyjściowe wyglądają następująco:

```
11 12 abc
30 def
```

Poniższy kod przedstawia użycie pola jawne w klasie, która nie ma konstruktora podstawowego. W tym przypadku `DefaultValue` atrybut nie jest wymagana, ale wszystkie pola muszą być zainicjowane w konstruktorach, które są zdefiniowane dla typu.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet6702.fs)]

Dane wyjściowe są `35 22`.

Poniższy kod przedstawia użycie pola jawne w strukturze. Ponieważ struktura jest typem wartości, automatycznie ma domyślnego konstruktora, która ustawia wartości pól do zera. W związku z tym `DefaultValue` atrybut nie jest wymagana.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet6703.fs)]

Dane wyjściowe są `11 xyz`.

Pola jawne nie są przeznaczone do użytku procedur. Ogólnie rzecz biorąc, gdy jest to możliwe należy używać `let` powiązania w klasie zamiast jawnego pola. Pola jawne są przydatne w niektórych scenariuszach współpracy, takie jak kiedy należy zdefiniować strukturę, która będzie używana w wywołaniu do natywnych interfejsów API lub w scenariuszach międzyoperacyjnego modelu COM wywołania platformy. Aby uzyskać więcej informacji, zobacz [funkcji zewnętrznych](../functions/external-functions.md). Innej sytuacji, w którym może być konieczne jawne pola jest podczas pracy z F # generatora kodu, który emituje klasy bez konstruktora podstawowego. Pola jawne są także przydatne zmienne statyczne wątku lub podobne konstrukcji. Aby uzyskać więcej informacji, zobacz `System.ThreadStaticAttribute`.

Gdy słowa kluczowe `member val` pojawiają się razem w definicji typu, jest on definicją automatycznie implementowanej właściwości. Aby uzyskać więcej informacji, zobacz [właściwości](properties.md).

## <a name="see-also"></a>Zobacz także

- [Właściwości](properties.md)
- [Elementy członkowskie](index.md)
- [`let` Powiązania w klasach](let-bindings-in-classes.md)
