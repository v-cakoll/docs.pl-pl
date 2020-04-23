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
ms.openlocfilehash: 251046a8bd825a90d817965f9f747d08d4492197
ms.sourcegitcommit: 73aa9653547a1cd70ee6586221f79cc29b588ebd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2020
ms.locfileid: "82102037"
---
# <a name="c-keywords"></a>Słowa kluczowe języka C#

Słowa kluczowe są wstępnie zdefiniowane, zastrzeżone identyfikatory, które mają specjalne znaczenie dla kompilatora. Nie można ich używać jako identyfikatorów `@` w programie, chyba że zawierają one jako prefiks. Na przykład `@if` jest prawidłowym identyfikatorem, ale `if` nie dlatego, że `if` jest słowem kluczowym.  
  
 Pierwsza tabela w tym temacie zawiera listę słów kluczowych, które są zastrzeżone identyfikatory w dowolnej części programu C#. Druga tabela w tym temacie zawiera listę kontekstowych słów kluczowych w języku C#. Kontekstowe słowa kluczowe mają specjalne znaczenie tylko w ograniczonym kontekście programu i mogą być używane jako identyfikatory poza tym kontekstem. Ogólnie rzecz biorąc, jak nowe słowa kluczowe są dodawane do języka C#, są one dodawane jako kontekstowe słowa kluczowe w celu uniknięcia przerywania programów napisanych we wcześniejszych wersjach.  
  
|||||  
|---|---|---|---|  
|[Abstrakcja](abstract.md)|[Jako](../operators/type-testing-and-cast.md#as-operator)|[base](base.md)|[bool](../builtin-types/bool.md)|  
|[break](break.md)|[Bajtów](../builtin-types/integral-numeric-types.md)|[Przypadku](switch.md)|[Złapać](try-catch.md)|  
|[char](../builtin-types/char.md)|[Sprawdzane](checked.md)|[class](class.md)|[const](const.md)|  
|[continue](continue.md)|[decimal](../builtin-types/floating-point-numeric-types.md)|[default](default.md)|[delegate](../builtin-types/reference-types.md)|  
|[do](do.md)|[double](../builtin-types/floating-point-numeric-types.md)|[else](if-else.md)|[Enum](../builtin-types/enum.md)|  
|[event](event.md)|[explicit](../operators/user-defined-conversion-operators.md)|[extern](extern.md)|[False](../builtin-types/bool.md)|  
|[Wreszcie](try-finally.md)|[Stałe](fixed-statement.md)|[float](../builtin-types/floating-point-numeric-types.md)|[for](for.md)|  
|[Foreach](foreach-in.md)|[goto](goto.md)|[if](if-else.md)|[implicit](../operators/user-defined-conversion-operators.md)|  
|[in](in.md)|[int](../builtin-types/integral-numeric-types.md)|[interface](interface.md)|[internal](internal.md)|
|[is](is.md)|[lock](lock-statement.md)|[długi](../builtin-types/integral-numeric-types.md)|[namespace](namespace.md)|
|[Nowy](../operators/new-operator.md)|[wartość null](null.md)|[obiekt](../builtin-types/reference-types.md)|[Operator](../operators/operator-overloading.md)|
|[na zewnątrz](out.md)|[override](override.md)|[params](params.md)|[private](private.md)|
|[protected](protected.md)|[public](public.md)|[readonly](readonly.md)|[ref](ref.md)|
|[return](return.md)|[Sbyte](../builtin-types/integral-numeric-types.md)|[sealed](sealed.md)|[short](../builtin-types/integral-numeric-types.md)||
[sizeof](../operators/sizeof.md)|[stackalloc](../operators/stackalloc.md)|[static](static.md)|[ciąg](../builtin-types/reference-types.md)|
|[Struct](../builtin-types/struct.md)|[switch](switch.md)|[this](this.md)|[throw](throw.md)|
|[True](../builtin-types/bool.md)|[try](try-catch.md)|[typeof](../operators/type-testing-and-cast.md#typeof-operator)|[Uint](../builtin-types/integral-numeric-types.md)|
|[ulong](../builtin-types/integral-numeric-types.md)|[unchecked](unchecked.md)|[Niebezpieczne](unsafe.md)|[ushort](../builtin-types/integral-numeric-types.md)|
|[using](using.md)|[virtual](virtual.md)|[void](../builtin-types/void.md)|[volatile](volatile.md)|
|[while](while.md)|

## <a name="contextual-keywords"></a>Kontekstowe słowa kluczowe

 Kontekstowe słowo kluczowe służy do zapewnienia określonego znaczenia w kodzie, ale nie jest słowem zastrzeżonym w języku C#. Niektóre kontekstowe słowa kluczowe, `partial` `where`takie jak i , mają specjalne znaczenie w dwóch lub więcej kontekstach.  
  
||||  
|---|---|---|  
|[add](add.md)|[alias](extern-alias.md)|[ascending](ascending.md)|
|[async](async.md)|[await](../operators/await.md)|[by](by.md)|
|[descending](descending.md)|[dynamiczna](../builtin-types/reference-types.md)|[equals](equals.md)|
|[Z](from-clause.md)|[get](get.md)|[Globalne](../operators/namespace-alias-qualifier.md)|
|[Grupa](group-clause.md)|[into](into.md)|[Dołączyć](join-clause.md)|
|[Niech](let-clause.md)|[nameof](../operators/nameof.md)|[on](on.md)|
|[Orderby](orderby-clause.md)|[częściowe (typ)](partial-type.md)|[częściowe (metoda)](partial-method.md)|
|[remove](remove.md)|[Wybierz](select-clause.md)|[Ustawić](set.md)|
|[niezarządzane (ograniczenie typu ogólnego)](where-generic-type-constraint.md)|[value](value.md)|[var](var.md)|
|[when (warunek filtru)](when.md)|[where (ograniczenie typu ogólnego)](where-generic-type-constraint.md)|[gdzie (klauzula zapytania)](where-clause.md)|
|[yield](yield.md)| | |
  
## <a name="see-also"></a>Zobacz też

- [Dokumentacja języka C#](../index.md)
