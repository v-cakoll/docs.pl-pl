---
title: 'Pola jawne: val — Słowo kluczowe'
description: Dowiedz się F# więcej o słowie kluczowym "Val", które jest używane do deklarowania lokalizacji do przechowywania wartości w typie klasy lub struktury bez inicjalizacji typu.
ms.date: 05/16/2016
ms.openlocfilehash: 2703d9a2734cfda1614a401ec24c6630ec31b2f1
ms.sourcegitcommit: 878ca7550b653114c3968ef8906da2b3e60e3c7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/02/2019
ms.locfileid: "71736838"
---
# <a name="explicit-fields-the-val-keyword"></a>Pola jawne: val — Słowo kluczowe

Słowo kluczowe `val` służy do deklarowania lokalizacji do przechowywania wartości w typie klasy lub struktury, bez jej inicjalizacji. Lokalizacje magazynu zadeklarowane w ten sposób są nazywane *jawnymi polami*. Inne użycie słowa kluczowego `val` jest w połączeniu ze słowem kluczowym `member` w celu zadeklarować właściwości, która jest implementowana. Aby uzyskać więcej informacji na temat właściwości, które są implementowane, zobacz [Właściwości](properties.md).

## <a name="syntax"></a>Składnia

```fsharp
val [ mutable ] [ access-modifier ] field-name : type-name
```

## <a name="remarks"></a>Uwagi

Typowym sposobem definiowania pól w klasie lub typie struktury jest użycie powiązania `let`. Jednakże powiązania `let` muszą być zainicjowane jako część konstruktora klasy, co nie zawsze jest możliwe, konieczne lub pożądane. Możesz użyć słowa kluczowego `val`, gdy chcesz, aby pole było niezainicjowane.

Jawne pola mogą być statyczne lub niestatyczne. *Modyfikatorem dostępu* może być `public`, `private` lub `internal`. Domyślnie jawne pola są publiczne. Różni się to od powiązań `let` w klasach, które są zawsze prywatne.

Atrybut [DefaultValue](https://msdn.microsoft.com/library/a3a3307b-8c05-441e-b109-245511614d58) jest wymagany w jawnych polach w typach klas, które mają Konstruktor podstawowy. Ten atrybut określa, że pole jest inicjowane na wartość zero. Typ pola musi obsługiwać inicjowanie o wartości zero. Typ obsługuje Inicjowanie zero, jeśli jest jedną z następujących:

- Typ pierwotny, który ma wartość zerową.
- Typ, który obsługuje wartość null, jako wartość normalną, jako wartość nietypową lub jako reprezentację wartości. Dotyczy to klas, krotek, rekordów, funkcji, interfejsów, typów odwołań platformy .NET, typu `unit` i typów Unii rozłącznych.
- Typ wartości .NET.
- Struktura, której pola wszystkie obsługują domyślną wartość zerową.

Na przykład niezmienne pole o nazwie `someField` ma pole zapasowe w reprezentacji skompilowanej .NET o nazwie `someField@` i uzyskuje dostęp do przechowywanej wartości przy użyciu właściwości o nazwie `someField`.

W przypadku pola modyfikowalnego skompilowana reprezentacja .NET jest polem platformy .NET.

> [!WARNING]
> .NET Framework przestrzeni nazw `System.ComponentModel` zawiera atrybut, który ma taką samą nazwę. Aby uzyskać informacje o tym atrybucie, zobacz <xref:System.ComponentModel.DefaultValueAttribute>.

Poniższy kod przedstawia użycie jawnych pól i, w przypadku porównania, powiązanie `let` w klasie, która ma Konstruktor podstawowy. Należy zauważyć, że pole @no__t -0-Bound `myInt1` jest prywatne. Jeśli do @no__t pola powiązanego z -0EM `myInt1` jest przywoływany z metody składowej, identyfikator własny `this` nie jest wymagany. Ale jeśli odwołujesz się do pól jawnie `myInt2` i `myString`, wymagany jest identyfikator samoobsługowy.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet6701.fs)]

Dane wyjściowe są następujące:

```console
11 12 abc
30 def
```

Poniższy kod przedstawia użycie jawnych pól w klasie, która nie ma konstruktora podstawowego. W takim przypadku atrybut `DefaultValue` nie jest wymagany, ale wszystkie pola muszą być zainicjowane w konstruktorach, które są zdefiniowane dla tego typu.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet6702.fs)]

Dane wyjściowe są `35 22`.

Poniższy kod przedstawia użycie jawnych pól w strukturze. Ponieważ struktura jest typem wartości, automatycznie ma Konstruktor bez parametrów, który ustawia wartości pól na zero. W związku z tym atrybut `DefaultValue` nie jest wymagany.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet6703.fs)]

Dane wyjściowe są `11 xyz`.

**Uważaj**, jeśli zamierzasz inicjować swoją strukturę przy użyciu pól `mutable` bez słowa kluczowego `mutable`, Twoje przypisania będą działać na kopii struktury, która zostanie odrzucona po przypisaniu. W związku z tym struktura nie ulegnie zmianie.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet6704.fs)]

Jawne pola nie są przeznaczone do rutynowego użycia. Ogólnie, jeśli jest to możliwe, należy użyć powiązania `let` w klasie zamiast w jawnym polu. Jawne pola są przydatne w niektórych scenariuszach współdziałania, na przykład w sytuacji, gdy trzeba zdefiniować strukturę, która będzie używana w wywołaniu wywołania platformy do natywnego interfejsu API lub w scenariuszach międzyoperacyjnych modelu COM. Aby uzyskać więcej informacji, zobacz [funkcje zewnętrzne](../functions/external-functions.md). Inną sytuacją, w której może być wymagane jawne pole, jest to, że podczas F# pracy z generatorem kodu, który emituje klasy bez konstruktora podstawowego. Jawne pola są również przydatne w przypadku zmiennych statycznych wątków lub podobnych konstrukcji. Aby uzyskać więcej informacji, zobacz `System.ThreadStaticAttribute`.

Gdy słowa kluczowe `member val` pojawiają się razem w definicji typu, jest to definicja automatycznie implementowanej właściwości. Aby uzyskać więcej informacji, zobacz [Właściwości](properties.md).

## <a name="see-also"></a>Zobacz także

- [Właściwości](properties.md)
- [Elementy członkowskie](index.md)
- [`let` powiązania w klasach](let-bindings-in-classes.md)
