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
ms.openlocfilehash: 928917d25b5f3f97c4b8cdff85efdaa1957be41e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "79399316"
---
# <a name="c-keywords"></a>Słowa kluczowe języka C#

Słowa kluczowe są wstępnie zdefiniowane, zastrzeżone identyfikatory, które mają specjalne znaczenie do kompilatora. Nie można ich używać jako identyfikatorów w `@` programie, chyba że zawierają one prefiks. Na przykład `@if` jest prawidłowyidentyfikator, `if` ale `if` nie jest, ponieważ jest słowem kluczowym.  
  
 Pierwsza tabela w tym temacie zawiera listę słów kluczowych, które są zastrzeżone identyfikatory w dowolnej części programu C#. Druga tabela w tym temacie zawiera listę kontekstowych słów kluczowych w języku C#. Kontekstowe słowa kluczowe mają specjalne znaczenie tylko w ograniczonym kontekście programu i mogą być używane jako identyfikatory poza tym kontekstem. Ogólnie rzecz biorąc, ponieważ nowe słowa kluczowe są dodawane do języka C#, są dodawane jako kontekstowe słowa kluczowe, aby uniknąć zerwania programów napisanych we wcześniejszych wersjach.  
  
|||||  
|---|---|---|---|  
|[Abstrakcja](abstract.md)|[Jako](../operators/type-testing-and-cast.md#as-operator)|[base](base.md)|[bool](../builtin-types/bool.md)|  
|[Przerwy](break.md)|[Bajtów](../builtin-types/integral-numeric-types.md)|[Przypadku](switch.md)|[Złapać](try-catch.md)|  
|[char](../builtin-types/char.md)|[Sprawdzane](checked.md)|[Klasa](class.md)|[const](const.md)|  
|[Kontynuować](continue.md)|[decimal](../builtin-types/floating-point-numeric-types.md)|[Domyślny](default.md)|[delegate](../builtin-types/reference-types.md)|  
|[Zrobić](do.md)|[double](../builtin-types/floating-point-numeric-types.md)|[Innego](if-else.md)|[Enum](../builtin-types/enum.md)|  
|[Zdarzenie](event.md)|[explicit](../operators/user-defined-conversion-operators.md)|[Extern](extern.md)|[false](../builtin-types/bool.md)|  
|[Wreszcie](try-finally.md)|[Stałe](fixed-statement.md)|[float](../builtin-types/floating-point-numeric-types.md)|[for](for.md)|  
|[Foreach](foreach-in.md)|[Goto](goto.md)|[Jeśli](if-else.md)|[implicit](../operators/user-defined-conversion-operators.md)|  
|[Cala](in.md)|[int](../builtin-types/integral-numeric-types.md)|[Interfejs](interface.md)|[Wewnętrznego](internal.md)|
|[Jest](is.md)|[lock](lock-statement.md)|[long](../builtin-types/integral-numeric-types.md)|[Namespace](namespace.md)|
|[Nowy](../operators/new-operator.md)|[null](null.md)|[obiekt](../builtin-types/reference-types.md)|[Operator](../operators/operator-overloading.md)|
|[na zewnątrz](out.md)|[override](override.md)|[params](params.md)|[Prywatny](private.md)|
|[protected](protected.md)|[Publicznego](public.md)|[Readonly](readonly.md)|[ref](ref.md)|
|[return](return.md)|[Sbyte](../builtin-types/integral-numeric-types.md)|[sealed](sealed.md)|[short](../builtin-types/integral-numeric-types.md)||
[sizeof](../operators/sizeof.md)|[stackalloc](../operators/stackalloc.md)|[Statyczne](static.md)|[ciąg](../builtin-types/reference-types.md)|
|[Struct](../builtin-types/struct.md)|[Przełącznik](switch.md)|[względem tego ruchu](this.md)|[throw](throw.md)|
|[true](../builtin-types/bool.md)|[try](try-catch.md)|[typeof](../operators/type-testing-and-cast.md#typeof-operator)|[Uint](../builtin-types/integral-numeric-types.md)|
|[ulong](../builtin-types/integral-numeric-types.md)|[unchecked](unchecked.md)|[unsafe](unsafe.md)|[ushort](../builtin-types/integral-numeric-types.md)|
|[Za pomocą](using.md)|[za pomocą statycznego](using-static.md)|[virtual](virtual.md)|[void](../builtin-types/void.md)|
|[volatile](volatile.md)|[Podczas](while.md)|

## <a name="contextual-keywords"></a>Słowa kluczowe kontekstowe

 Kontekstowe słowo kluczowe służy do zapewnienia określonego znaczenia w kodzie, ale nie jest słowem zastrzeżonym w języku C#. Niektóre kontekstowe słowa kluczowe, `partial` `where`takie jak i , mają specjalne znaczenie w dwóch lub więcej kontekstach.  
  
||||  
|---|---|---|  
|[Dodaj](add.md)|[alias](extern-alias.md)|[ascending](ascending.md)|
|[async](async.md)|[await](../operators/await.md)|[Przez](by.md)|
|[descending](descending.md)|[Dynamiczne](../builtin-types/reference-types.md)|[equals](equals.md)|
|[Z](from-clause.md)|[get](get.md)|[Globalne](../operators/namespace-alias-qualifier.md)|
|[Grupa](group-clause.md)|[Do](into.md)|[join](join-clause.md)|
|[Niech](let-clause.md)|[nameof](../operators/nameof.md)|[Na](on.md)|
|[Orderby](orderby-clause.md)|[częściowe (typ)](partial-type.md)|[częściowe (metoda)](partial-method.md)|
|[Usunąć](remove.md)|[Wybierz](select-clause.md)|[Ustawić](set.md)|
|[niezarządzane (ograniczenie typu ogólnego)](where-generic-type-constraint.md)|[Wartość](value.md)|[Var](var.md)|
|[when (warunek filtru)](when.md)|[where (ograniczenie typu ogólnego)](where-generic-type-constraint.md)|[gdzie (klauzula zapytania)](where-clause.md)|
|[yield](yield.md)| | |
  
## <a name="see-also"></a>Zobacz też

- [Dokumentacja języka C#](../index.md)
