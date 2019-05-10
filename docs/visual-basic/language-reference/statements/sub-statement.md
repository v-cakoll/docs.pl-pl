---
title: Sub — Instrukcja (Visual Basic)
ms.date: 05/12/2018
f1_keywords:
- vb.Sub
helpviewer_keywords:
- Public keyword [Visual Basic], Sub statements
- procedures [Visual Basic], creating
- declaring procedures [Visual Basic], Sub statement
- arguments [Visual Basic], Sub procedures
- As keyword [Visual Basic], Sub statements
- Optional keyword [Visual Basic], Sub statements
- declarations [Visual Basic], procedures
- Sub keyword [Visual Basic]
- Handles keyword [Visual Basic], Sub statements
- Protected Friend keyword [Visual Basic]
- ParamArray keyword [Visual Basic], Sub statements
- Implements keyword [Visual Basic], Sub statements
- Sub statement [Visual Basic]
- subroutines
- ByRef keyword [Visual Basic], Sub statements
- Sub procedures [Visual Basic], Sub statement
- recursive procedures
- Private keyword [Visual Basic], Sub statements
- Friend keyword [Visual Basic], Sub statements
- Exit statement [Visual Basic], Sub statements
- procedures [Visual Basic], Sub
- End keyword [Visual Basic], Sub statements
- ByVal keyword [Visual Basic], Sub statements
- Visual Basic code, Sub procedures
ms.assetid: e347d700-d06c-405b-b302-e9b1edb57dfc
ms.openlocfilehash: 00e2f313e283259ea44dd6da71530bed4bff31c5
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64751174"
---
# <a name="sub-statement-visual-basic"></a>Sub — Instrukcja (Visual Basic)

Deklaruje nazwę, parametry i kod, który definiuje `Sub` procedury.

## <a name="syntax"></a>Składnia

```
[ <attributelist> ] [ Partial ] [ accessmodifier ] [ proceduremodifiers ] [ Shared ] [ Shadows ] [ Async ]
Sub name [ (Of typeparamlist) ] [ (parameterlist) ] [ Implements implementslist | Handles eventlist ]
    [ statements ]
    [ Exit Sub ]
    [ statements ]
End Sub
```

## <a name="parts"></a>Części

- `attributelist`

  Opcjonalna. Zobacz [Lista atrybutów](attribute-list.md).

- `Partial`

  Opcjonalna. Wskazuje definicji metody częściowej. Zobacz [metod częściowych](../../../visual-basic/programming-guide/language-features/procedures/partial-methods.md).

- `accessmodifier`

  Opcjonalna. Może to być jeden z następujących elementów:

  - [Public](../modifiers/public.md)

  - [Protected](../modifiers/protected.md)

  - [Friend](../modifiers/friend.md)

  - [Private](../modifiers/private.md)

  - [Protected Friend](../../language-reference/modifiers/protected-friend.md)

  - [Private Protected](../../language-reference/modifiers/private-protected.md)

  Zobacz temat [Poziomy dostępu w języku Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).

- `proceduremodifiers`

  Opcjonalna. Może to być jeden z następujących elementów:

  - [Overloads](../modifiers/overloads.md)

  - [Overrides](../modifiers/overrides.md)

  - [Overridable](../modifiers/overridable.md)

  - [NotOverridable](../modifiers/notoverridable.md)

  - [MustOverride](../modifiers/mustoverride.md)

  - `MustOverride Overrides`

  - `NotOverridable Overrides`

- `Shared`

  Opcjonalna. Zobacz [udostępnione](../modifiers/shared.md).

- `Shadows`

  Opcjonalna. Zobacz [Shadows](../modifiers/shadows.md).

- `Async`

  Opcjonalna. Zobacz [Async](../modifiers/async.md).

- `name`

  Wymagana. Nazwa procedury. Zobacz [Zadeklarowane nazwy elementów](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md). Aby utworzyć procedurę konstruktora dla klasy, ustaw nazwę `Sub` procedury, aby `New` — słowo kluczowe. Aby uzyskać więcej informacji, zobacz [okres istnienia obiektów: Jak obiekty są tworzone i niszczone](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md).

- `typeparamlist`

  Opcjonalna. Lista parametrów typu ogólnego procedury. Zobacz [Lista typów](type-list.md).

- `parameterlist`

  Opcjonalna. Lista nazwy zmiennych lokalnych reprezentującą parametry tej procedury. Zobacz [listy parametrów](parameter-list.md).

- `Implements`

  Opcjonalna. Wskazuje, że ta procedura implementuje co najmniej jeden `Sub` procedury, każdy z nich zdefiniowane w interfejsie zaimplementowany przez klasę lub strukturę zawierającego tę procedurę. Zobacz [Implements, instrukcja](implements-statement.md).

- `implementslist`

  Jeśli wymagane `Implements` podano. Lista `Sub` procedury są wdrożone.

  `implementedprocedure [ , implementedprocedure ... ]`

  Każdy `implementedprocedure` ma następujące składni i części:

  `interface.definedname`

  |Część|Opis|
  |---|---|
  |`interface`|Wymagana. Nazwa interfejsu implementowany przez tej procedury zawierający klasy lub struktury.|
  |`definedname`|Wymagana. Nazwa, za pomocą którego procedura jest zdefiniowany w `interface`.|

- `Handles`

  Opcjonalna. Wskazuje, że ta procedura może obsługiwać jeden lub więcej określonych zdarzeń. Zobacz [obsługuje](handles-clause.md).

- `eventlist`

  Jeśli wymagane `Handles` podano. Lista zdarzeń, które obsługuje tę procedurę.

  `eventspecifier [ , eventspecifier ... ]`

  Każdy `eventspecifier` ma następujące składni i części:

  `eventvariable.event`

  |Część|Opis|
  |---|---|
  |`eventvariable`|Wymagana. Zmienna obiektu zadeklarowane z typem danych klasy lub struktury, która wywołuje zdarzenia.|
  |`event`|Wymagana. Nazwa zdarzenia, które obsługuje tę procedurę.|

- `statements`

  Opcjonalna. Blok instrukcji do uruchomienia w ramach tej procedury.

- `End Sub`

  Kończy definicję tej procedury.

## <a name="remarks"></a>Uwagi

Cały kod wykonywalny musi być wewnątrz procedury. Użyj `Sub` procedury, jeśli nie chcesz zwracać wartość do wywołującego kodu. Użyj `Function` procedury zwracać wartość.

## <a name="defining-a-sub-procedure"></a>Definiujący procedurę Sub

Można zdefiniować `Sub` procedury tylko na poziomie modułu. Kontekst deklaracji procedurę sub dlatego należy klasy, struktury, modułem lub interfejsem, a nie może być plikiem źródłowym, przestrzeń nazw, procedurę lub blok. Aby uzyskać więcej informacji, zobacz [Kontekst deklaracji i domyślne poziomy dostępu](declaration-contexts-and-default-access-levels.md).

`Sub` Domyślnie procedur dostępu publicznego. Modyfikatory dostępu można dostosować ich poziomy dostępu.

Jeśli w procedurze użyto `Implements` — słowo kluczowe, zawierający klasy lub struktury, musi mieć `Implements` instrukcji, który następuje bezpośrednio po jego `Class` lub `Structure` instrukcji. `Implements` Instrukcja musi zawierać każdego interfejsu, który jest określony w `implementslist`. Jednak nazwy za pomocą którego interfejs definiuje `Sub` (w `definedname`) nie musi być zgodna z nazwą w tej procedurze (w `name`).

## <a name="returning-from-a-sub-procedure"></a>Zwracanie z procedurę Sub

Gdy `Sub` procedury zwraca do kodu wywołującego, wykonywanie jest kontynuowane przy użyciu instrukcji następującej po instrukcji, która nazwała go.

W poniższym przykładzie pokazano zwracany `Sub` procedury.

```vb
Sub mySub(ByVal q As String)
    Return
End Sub
```

`Exit Sub` i `Return` instrukcji powodują natychmiastowego wyjścia z `Sub` procedury. Dowolną liczbę `Exit Sub` i `Return` instrukcji może występować w dowolnym miejscu w ramach procedury i możesz mieszać `Exit Sub` i `Return` instrukcji.

## <a name="calling-a-sub-procedure"></a>Wywoływanie procedury Sub

Należy wywołać `Sub` procedury przy użyciu nazwy procedury w instrukcji i postępuj zgodnie z tej nazwy z listą argumentów w nawiasach. Nawiasy można pominąć, tylko, jeśli nie podasz żadnych argumentów. Jednak kod jest bardziej czytelny, jeśli zawsze zawierać nawiasy.

A `Sub` procedury i `Function` procedury mogą mieć parametry i wykonać serię instrukcji. Jednak `Function` procedury zwraca wartość, a w `Sub` nie procedury. W związku z tym, nie można użyć `Sub` procedury w wyrażeniu.

Możesz użyć `Call` — słowo kluczowe po wywołaniu `Sub` procedura, ale że — słowo kluczowe nie jest zalecany dla większości zastosowań. Aby uzyskać więcej informacji, zobacz [instrukcji Call](call-statement.md).

Visual Basic Reorganizuje czasami wyrażenia arytmetyczne, aby zwiększyć wydajność wewnętrznej. Z tego powodu jeśli lista argumentów zawiera wyrażenia, które wywołują innych procedur, nie należy zakładać, że że te wyrażenia zostaną wywołane w określonej kolejności.

## <a name="async-sub-procedures"></a>Async Sub — procedury

Za pomocą funkcji asynchronicznych, można wywoływać funkcje asynchroniczne bez za pomocą jawnego wywołania zwrotne lub ręcznego podziału kodu na wielu funkcji lub wyrażenia lambda.

Po oznaczeniu procedury z [Async](../modifiers/async.md) modyfikator, można użyć [Await](../../../visual-basic/language-reference/operators/await-operator.md) operatora w procedurze. Gdy kontrola osiąga `Await` wyrażenia w `Async` procedury, sterowanie powraca do obiektu wywołującego, a postęp w procedurze jest wstrzymana, dopóki nie zakończy się oczekiwane zadanie. Kiedy zadanie zostanie ukończone, wykonanie można wznowić w procedurze.

> [!NOTE]
> `Async` Procedury powraca do obiektu wywołującego, po napotkaniu albo pierwszego oczekiwane obiekt, który nie został jeszcze ukończony lub na końcu `Async` procedury zostanie osiągnięty, zależnie co nastąpi wcześniej.

Można również oznaczyć [Function — instrukcja](function-statement.md) z `Async` modyfikator. `Async` Funkcji może mieć typ zwracany <xref:System.Threading.Tasks.Task%601> lub <xref:System.Threading.Tasks.Task>. Przykład później w tym temacie przedstawiono `Async` funkcję, która ma typ zwracany <xref:System.Threading.Tasks.Task%601>.

`Async` `Sub` procedury są głównie używane do obsługi zdarzeń, których nie można zwrócić wartość. `Async` `Sub` Procedura nie może być oczekiwany, a obiekt wywołujący `Async` `Sub` procedura nie może przechwytywać wyjątków, `Sub` zgłasza procedury.

`Async` Procedura nie może deklarować [ByRef](../modifiers/byref.md) parametrów.

Aby uzyskać więcej informacji na temat `Async` procedury, zobacz [Asynchronous Programming with Async and Await](../../../visual-basic/programming-guide/concepts/async/index.md), [Control Flow in Async Programs](../../../visual-basic/programming-guide/concepts/async/control-flow-in-async-programs.md), i [Async Return Types](../../../visual-basic/programming-guide/concepts/async/async-return-types.md).

## <a name="example"></a>Przykład

W poniższym przykładzie użyto `Sub` instrukcji, aby zdefiniować nazwę, parametry i kod, który tworzą treści `Sub` procedury.

[!code-vb[VbVbalrStatements#58](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#58)]

## <a name="example"></a>Przykład

W poniższym przykładzie `DelayAsync` jest `Async` `Function` zawierający typ zwracany <xref:System.Threading.Tasks.Task%601>. `DelayAsync` ma `Return` instrukcję, która zwraca liczbę całkowitą. W związku z tym, funkcja deklaracji `DelayAsync` musi mieć typ zwracany `Task(Of Integer)`. Ponieważ typem zwracanym jest `Task(Of Integer)`, oceny `Await` wyrażenia w `DoSomethingAsync` tworzy liczbą całkowitą, co pokazuje poniższa instrukcja: `Dim result As Integer = Await delayTask`.

`startButton_Click` Procedura to przykład `Async Sub` procedury. Ponieważ `DoSomethingAsync` jest `Async` funkcji, zadanie do wywołań `DoSomethingAsync` musi być oczekiwana, co pokazuje poniższa instrukcja: `Await DoSomethingAsync()`. `startButton_Click` `Sub` Procedury muszą być zdefiniowane przy użyciu `Async` modyfikator ponieważ ma ona `Await` wyrażenia.

[!code-vb[csAsyncMethod#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/csasyncmethod/vb/mainwindow.xaml.vb#1)]

## <a name="see-also"></a>Zobacz także

- [Implements, instrukcja](implements-statement.md)
- [Function, instrukcja](function-statement.md)
- [Lista parametrów](parameter-list.md)
- [Dim, instrukcja](dim-statement.md)
- [Call, instrukcja](call-statement.md)
- [z](of-clause.md)
- [Tablice parametrów](../../../visual-basic/programming-guide/language-features/procedures/parameter-arrays.md)
- [Instrukcje: używanie klasy ogólnej](../../../visual-basic/programming-guide/language-features/data-types/how-to-use-a-generic-class.md)
- [Rozwiązywanie problemów z procedurami](../../../visual-basic/programming-guide/language-features/procedures/troubleshooting-procedures.md)
- [Metody częściowe](../../../visual-basic/programming-guide/language-features/procedures/partial-methods.md)
