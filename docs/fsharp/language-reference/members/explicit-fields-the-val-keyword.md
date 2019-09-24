---
title: 'Pola jawne: Val — słowo kluczowe'
description: Dowiedz się F# więcej o słowie kluczowym "Val", które jest używane do deklarowania lokalizacji do przechowywania wartości w typie klasy lub struktury bez inicjalizacji typu.
ms.date: 05/16/2016
ms.openlocfilehash: fe339e33dae27ae226022a68dd8247d1ab1994b3
ms.sourcegitcommit: 56f1d1203d0075a461a10a301459d3aa452f4f47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/24/2019
ms.locfileid: "71216477"
---
# <a name="explicit-fields-the-val-keyword"></a>Pola jawne: Val — słowo kluczowe

`val` Słowo kluczowe jest używane do deklarowania lokalizacji do przechowywania wartości w typie klasy lub struktury, bez jej inicjalizacji. Lokalizacje magazynu zadeklarowane w ten sposób są nazywane *jawnymi polami*. Inne użycie `val` słowa kluczowego jest w połączeniu `member` ze słowem kluczowym w celu zadeklarować właściwości, która jest implementowana. Aby uzyskać więcej informacji na temat właściwości, które są implementowane, zobacz [Właściwości](properties.md).

## <a name="syntax"></a>Składnia

```fsharp
val [ mutable ] [ access-modifier ] field-name : type-name
```

## <a name="remarks"></a>Uwagi

Typowym sposobem definiowania pól w klasie lub typie struktury jest użycie `let` powiązania. `let` Jednakże powiązania muszą być zainicjowane jako część konstruktora klasy, co nie zawsze jest możliwe, konieczne lub pożądane. Możesz użyć `val` słowa kluczowego, gdy chcesz, aby pole, które jest niezainicjowane.

Jawne pola mogą być statyczne lub niestatyczne. *Modyfikatorem dostępu* może być `public`, `private`, lub `internal`. Domyślnie jawne pola są publiczne. Różni się to `let` od powiązań w klasach, które są zawsze prywatne.

Atrybut [DefaultValue](https://msdn.microsoft.com/library/a3a3307b-8c05-441e-b109-245511614d58) jest wymagany w jawnych polach w typach klas, które mają Konstruktor podstawowy. Ten atrybut określa, że pole jest inicjowane na wartość zero. Typ pola musi obsługiwać inicjowanie o wartości zero. Typ obsługuje Inicjowanie zero, jeśli jest jedną z następujących:

- Typ pierwotny, który ma wartość zerową.

- Typ, który obsługuje wartość null, jako wartość normalną, jako wartość nietypową lub jako reprezentację wartości. Obejmuje to klasy, krotki, rekordy, funkcje, interfejsy, typy odwołań platformy .NET, `unit` typ i typy Unii rozłącznych.

- Typ wartości .NET.

- Struktura, której pola wszystkie obsługują domyślną wartość zerową.

Na przykład niezmienne pole o nazwie `someField` ma pole zapasowe w skompilowanej reprezentacji .NET o nazwie `someField@`i uzyskuje dostęp do przechowywanej wartości przy użyciu właściwości `someField`o nazwie.

W przypadku pola modyfikowalnego skompilowana reprezentacja .NET jest polem platformy .NET.

>[!WARNING]
>Przestrzeń nazw `System.ComponentModel` .NET Framework zawiera atrybut, który ma taką samą nazwę. Informacje o tym atrybucie można znaleźć w `System.ComponentModel.DefaultValueAttribute`temacie.

Poniższy kod przedstawia użycie jawnych pól i, w przypadku porównania, `let` powiązanie w klasie, która ma Konstruktor podstawowy. Zwróć uwagę, `let`że pole `myInt1` -powiązane jest prywatne. Gdy odwołanie do pola `myInt1` jest powiązane z metody składowej, jego identyfikator `this` samodzielny nie jest wymagany. `let` Ale w przypadku odwoływania się do jawnych `myString`pól `myInt2` i, wymagany jest sam identyfikator.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet6701.fs)]

Wynik jest następujący:

```console
11 12 abc
30 def
```

Poniższy kod przedstawia użycie jawnych pól w klasie, która nie ma konstruktora podstawowego. W tym przypadku `DefaultValue` atrybut nie jest wymagany, ale wszystkie pola muszą być zainicjowane w konstruktorach, które są zdefiniowane dla tego typu.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet6702.fs)]

Dane wyjściowe to `35 22`.

Poniższy kod przedstawia użycie jawnych pól w strukturze. Ponieważ struktura jest typem wartości, automatycznie ma konstruktora domyślnego, który ustawia wartości pól na zero. W związku z `DefaultValue` tym atrybut nie jest wymagany.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet6703.fs)]

Dane wyjściowe to `11 xyz`.

**Uważaj**, jeśli zamierzasz zainicjować strukturę przy użyciu `mutable` pól bez `mutable` słowa kluczowego, przypisania będą działać na kopii struktury, która zostanie odrzucona po przypisaniu. W związku z tym struktura nie ulegnie zmianie.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet6704.fs)]

Jawne pola nie są przeznaczone do rutynowego użycia. Ogólnie rzecz biorąc, gdy jest to możliwe, `let` należy użyć powiązania w klasie zamiast pola jawnego. Jawne pola są przydatne w niektórych scenariuszach współdziałania, na przykład w sytuacji, gdy trzeba zdefiniować strukturę, która będzie używana w wywołaniu wywołania platformy do natywnego interfejsu API lub w scenariuszach międzyoperacyjnych modelu COM. Aby uzyskać więcej informacji, zobacz [funkcje zewnętrzne](../functions/external-functions.md). Inną sytuacją, w której może być wymagane jawne pole, jest to, że podczas F# pracy z generatorem kodu, który emituje klasy bez konstruktora podstawowego. Jawne pola są również przydatne w przypadku zmiennych statycznych wątków lub podobnych konstrukcji. Aby uzyskać więcej informacji, zobacz `System.ThreadStaticAttribute`.

Gdy słowa kluczowe `member val` są wyświetlane razem w definicji typu, jest to definicja automatycznie implementowanej właściwości. Aby uzyskać więcej informacji, zobacz [Właściwości](properties.md).

## <a name="see-also"></a>Zobacz także

- [Właściwości](properties.md)
- [Elementy członkowskie](index.md)
- [`let`Powiązania w klasach](let-bindings-in-classes.md)
