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
ms.openlocfilehash: 19126eb8bb78643ca1b91a0ddf537033d19cc698
ms.sourcegitcommit: 34593b4d0be779699d38a9949d6aec11561657ec
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/11/2019
ms.locfileid: "66833224"
---
# <a name="c-keywords"></a>Słowa kluczowe języka C#

Słowa kluczowe są wstępnie zdefiniowane, zarezerwowane identyfikatorów, które mają specjalne znaczenie dla kompilatora. Nie można ich używać jako identyfikatorów w programach, chyba że zawierają one `@` jako prefiksu. Na przykład `@if` jest prawidłowym identyfikatorem, ale `if` jest niezgodny, ponieważ `if` jest słowem kluczowym.  
  
 W pierwszej tabeli, w tym temacie wymieniono słowa kluczowe, które są zarezerwowanymi identyfikatorami w dowolnej części programu w języku C#. W drugiej tabeli, w tym temacie wymieniono kontekstowych słów kluczowych w języku C#. Kontekstowe słowa kluczowe mają specjalne znaczenie tylko w kontekście ograniczony program i mogą być używane jako identyfikatory poza tym kontekstem. Ogólnie rzecz biorąc podczas dodawania nowych słów kluczowych języka C#, zostaną dodane jako kontekstowymi słowami kluczowymi Aby uniknąć dzielenia programy napisane w starszych wersjach.  
  
|||||  
|---|---|---|---|  
|[abstract](abstract.md)|[as](as.md)|[base](base.md)|[bool](bool.md)|  
|[break](break.md)|[byte](byte.md)|[case](switch.md)|[catch](try-catch.md)|  
|[char](char.md)|[checked](checked.md)|[class](class.md)|[const](const.md)|  
|[continue](continue.md)|[decimal](decimal.md)|[default](default.md)|[delegate](delegate.md)|  
|[do](do.md)|[double](double.md)|[else](if-else.md)|[enum](enum.md)|  
|[event](event.md)|[explicit](explicit.md)|[extern](extern.md)|[false](false-literal.md)|  
|[finally](try-finally.md)|[Stała](fixed-statement.md)|[float](float.md)|[for](for.md)|  
|[Instrukcja foreach](foreach-in.md)|[goto](goto.md)|[if](if-else.md)|[implicit](implicit.md)|  
|[in](in.md)|[int](int.md)|[interface](interface.md)|[internal](internal.md)|
|[is](is.md)|[lock](lock-statement.md)|[long](long.md)|[namespace](namespace.md)|
|[new](new.md)|[null](null.md)|[object](object.md)|[operator](operator.md)|
|[out](out.md)|[override](override.md)|[params](params.md)|[private](private.md)|
|[protected](protected.md)|[public](public.md)|[readonly](readonly.md)|[ref](ref.md)|
|[return](return.md)|[sbyte](sbyte.md)|[sealed](sealed.md)|[short](short.md)||
[sizeof](sizeof.md)|[stackalloc](../operators/stackalloc.md)|[static](static.md)|[string](string.md)|
|[struct](struct.md)|[switch](switch.md)|[this](this.md)|[throw](throw.md)|
|[true](true-literal.md)|[try](try-catch.md)|[typeof](typeof.md)|[uint](uint.md)|
|[ulong](ulong.md)|[unchecked](unchecked.md)|[unsafe](unsafe.md)|[ushort](ushort.md)|
|[using](using.md)|[Przy użyciu statycznej](using-static.md)|[virtual](virtual.md)|[void](void.md)|
|[volatile](volatile.md)|[while](while.md)|

## <a name="contextual-keywords"></a>Kontekstowe słowa kluczowe

 Kontekstowe słowo kluczowe służy do zapewnienia określone znaczenie w kodzie, ale nie jest wyrazem zastrzeżonym w języku C#. Niektóre kontekstowych słów kluczowych, takich jak `partial` i `where`, mają specjalne znaczenie w co najmniej dwóch kontekstów.  
  
||||  
|---|---|---|  
|[add](add.md)|[alias](extern-alias.md)|[ascending](ascending.md)|
|[async](async.md)|[await](await.md)|[by](by.md)|
|[descending](descending.md)|[dynamic](dynamic.md)|[equals](equals.md)|
|[from](from-clause.md)|[get](get.md)|[global](global.md)|
|[Grupy](group-clause.md)|[into](into.md)|[join](join-clause.md)|
|[Let](let-clause.md)|[nameof](nameof.md)|[on](on.md)|
|[orderby](orderby-clause.md)|[Partial (typ)](partial-type.md)|[Partial (metoda)](partial-method.md)|
|[remove](remove.md)|[select](select-clause.md)|[set](set.md)|
|[value](value.md)|[var](var.md)|[when (warunek filtru)](when.md)|
|[where (ograniczenie typu ogólnego)](where-generic-type-constraint.md)|[gdzie (klauzula zapytania)](where-clause.md)|[yield](yield.md)|
  
## <a name="see-also"></a>Zobacz także

- [C#Odwołanie](../index.md)
