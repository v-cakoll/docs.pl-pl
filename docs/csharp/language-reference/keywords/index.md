---
title: Słowa kluczowe języka C#
ms.date: 03/07/2017
f1_keywords:
- cs.keywords
helpviewer_keywords:
- keywords [C#]
- C# language, keywords
- Visual C#, keywords
- '@ keyword'
ms.assetid: e929b0f2-4b92-4d37-8060-23d323b098ad
ms.openlocfilehash: 91dbe36efd58c2455df5b38ac4bc6b1b56bc452f
ms.sourcegitcommit: 93762e1a0dae1b5f64d82eebb7b705a6d566d839
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/27/2019
ms.locfileid: "74552182"
---
# <a name="c-keywords"></a>Słowa kluczowe języka C#

Słowa kluczowe są wstępnie zdefiniowanymi, zarezerwowanymi identyfikatorami, które mają specjalne znaczenie dla kompilatora. Nie mogą być używane jako identyfikatory w programie, chyba że zawierają `@` jako prefiks. Na przykład `@if` jest prawidłowym identyfikatorem, ale `if` nie jest, ponieważ `if` jest słowem kluczowym.  
  
 W pierwszej tabeli w tym temacie wymieniono słowa kluczowe, które są zarezerwowane identyfikatory w C# dowolnej części programu. W drugiej tabeli w tym temacie wymieniono kontekstowe słowa C#kluczowe w. Kontekstowe słowa kluczowe mają specjalne znaczenie tylko w ograniczonym kontekście programu i mogą być używane jako identyfikatory poza tym kontekstem. Ogólnie rzecz biorąc, w miarę dodawania nowych słów C# kluczowych do języka są one dodawane jako kontekstowe słowa kluczowe, aby uniknąć przerywania programów pisanych we wcześniejszych wersjach.  
  
|||||  
|---|---|---|---|  
|[abstract](abstract.md)|[as](../operators/type-testing-and-cast.md#as-operator)|[base](base.md)|[bool](../builtin-types/bool.md)|  
|[break](break.md)|[byte](../builtin-types/integral-numeric-types.md)|[case](switch.md)|[efektywn](try-catch.md)|  
|[char](../builtin-types/char.md)|[checked](checked.md)|[class](class.md)|[const](const.md)|  
|[continue](continue.md)|[decimal](../builtin-types/floating-point-numeric-types.md)|[default](default.md)|[delegate](../builtin-types/reference-types.md)|  
|[do](do.md)|[double](../builtin-types/floating-point-numeric-types.md)|[Przejmi](if-else.md)|[enum](enum.md)|  
|[event](event.md)|[explicit](../operators/user-defined-conversion-operators.md)|[extern](extern.md)|[false](../builtin-types/bool.md)|  
|[finally](try-finally.md)|[FIXED](fixed-statement.md)|[float](../builtin-types/floating-point-numeric-types.md)|[for](for.md)|  
|[spowodował](foreach-in.md)|[goto](goto.md)|[przypadku](if-else.md)|[implicit](../operators/user-defined-conversion-operators.md)|  
|[in](in.md)|[int](../builtin-types/integral-numeric-types.md)|[interface](interface.md)|[internal](internal.md)|
|[is](is.md)|[lock](lock-statement.md)|[long](../builtin-types/integral-numeric-types.md)|[namespace](namespace.md)|
|[new](../operators/new-operator.md)|[null](null.md)|[object](../builtin-types/reference-types.md)|[operator](../operators/operator-overloading.md)|
|[out](out.md)|[override](override.md)|[params](params.md)|[private](private.md)|
|[protected](protected.md)|[public](public.md)|[readonly](readonly.md)|[ref](ref.md)|
|[return](return.md)|[sbyte](../builtin-types/integral-numeric-types.md)|[sealed](sealed.md)|[short](../builtin-types/integral-numeric-types.md)||
[sizeof](../operators/sizeof.md)|[stackalloc](../operators/stackalloc.md)|[static](static.md)|[string](../builtin-types/reference-types.md)|
|[struct](struct.md)|[switch](switch.md)|[this](this.md)|[throw](throw.md)|
|[true](../builtin-types/bool.md)|[spróbował](try-catch.md)|[typeof](../operators/type-testing-and-cast.md#typeof-operator)|[uint](../builtin-types/integral-numeric-types.md)|
|[ulong](../builtin-types/integral-numeric-types.md)|[unchecked](unchecked.md)|[unsafe](unsafe.md)|[ushort](../builtin-types/integral-numeric-types.md)|
|[using](using.md)|[Używanie static](using-static.md)|[virtual](virtual.md)|[void](void.md)|
|[volatile](volatile.md)|[while](while.md)|

## <a name="contextual-keywords"></a>Kontekstowe słowa kluczowe

 Kontekstowe słowo kluczowe jest używane do zapewnienia określonego znaczenia w kodzie, ale nie jest to słowo zastrzeżone w C#. Niektóre kontekstowe słowa kluczowe, takie jak `partial` i `where`, mają specjalne znaczenie w co najmniej dwóch kontekstach.  
  
||||  
|---|---|---|  
|[add](add.md)|[Użyj](extern-alias.md)|[ascending](ascending.md)|
|[async](async.md)|[await](../operators/await.md)|[by](by.md)|
|[descending](descending.md)|[dynamic](../builtin-types/reference-types.md)|[equals](equals.md)|
|[wniosek](from-clause.md)|[get](get.md)|[global](../operators/namespace-alias-qualifier.md)|
|[Group](group-clause.md)|[into](into.md)|[Złącza](join-clause.md)|
|[wpuść](let-clause.md)|[nameof](../operators/nameof.md)|[on](on.md)|
|[OrderBy](orderby-clause.md)|[częściowy (typ)](partial-type.md)|[częściowe (Metoda)](partial-method.md)|
|[remove](remove.md)|[zaznaczenia](select-clause.md)|[set](set.md)|
|[niezarządzane (ograniczenie typu ogólnego)](where-generic-type-constraint.md)|[value](value.md)|[var](var.md)|
|[when (warunek filtru)](when.md)|[where (ograniczenie typu ogólnego)](where-generic-type-constraint.md)|[WHERE (klauzula zapytania)](where-clause.md)|
|[yield](yield.md)| | |
  
## <a name="see-also"></a>Zobacz także

- [C#odwoła](../index.md)
