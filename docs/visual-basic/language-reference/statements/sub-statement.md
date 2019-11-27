---
title: Sub — Instrukcja
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
ms.openlocfilehash: da498a5e0a3633eb98882aaed145fcd21ab169fd
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74346440"
---
# <a name="sub-statement-visual-basic"></a>Sub — Instrukcja (Visual Basic)

Deklaruje nazwę, parametry i kod definiujący procedurę `Sub`.

## <a name="syntax"></a>Składnia

```vb
[ <attributelist> ] [ Partial ] [ accessmodifier ] [ proceduremodifiers ] [ Shared ] [ Shadows ] [ Async ]
Sub name [ (Of typeparamlist) ] [ (parameterlist) ] [ Implements implementslist | Handles eventlist ]
    [ statements ]
    [ Exit Sub ]
    [ statements ]
End Sub
```

## <a name="parts"></a>Części

- `attributelist`

  Opcjonalna. Zobacz [listę atrybutów](attribute-list.md).

- `Partial`

  Opcjonalna. Wskazuje definicję metody częściowej. Zobacz [metody częściowe](../../../visual-basic/programming-guide/language-features/procedures/partial-methods.md).

- `accessmodifier`

  Opcjonalna. Może to być jeden z następujących modyfikatorów dostępu:

  - [Public](../modifiers/public.md)

  - [Protected](../modifiers/protected.md)

  - [Friend](../modifiers/friend.md)

  - [Private](../modifiers/private.md)

  - [Protected Friend](../../language-reference/modifiers/protected-friend.md)

  - [Private Protected](../../language-reference/modifiers/private-protected.md)

  Zobacz [poziomy dostępu w Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).

- `proceduremodifiers`

  Opcjonalna. Może to być jeden z następujących modyfikatorów dostępu:

  - [Overloads](../modifiers/overloads.md)

  - [Overrides](../modifiers/overrides.md)

  - [Overridable](../modifiers/overridable.md)

  - [NotOverridable](../modifiers/notoverridable.md)

  - [MustOverride](../modifiers/mustoverride.md)

  - `MustOverride Overrides`

  - `NotOverridable Overrides`

- `Shared`

  Opcjonalna. Zobacz [udostępnianie](../modifiers/shared.md).

- `Shadows`

  Opcjonalna. Zobacz [Shadows](../modifiers/shadows.md).

- `Async`

  Opcjonalna. Zobacz [Async](../modifiers/async.md).

- `name`

  Wymagana. Nazwa procedury. Zobacz [zadeklarowane nazwy elementów](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md). Aby utworzyć procedurę konstruktora dla klasy, należy ustawić nazwę procedury `Sub` na słowo kluczowe `New`. Aby uzyskać więcej informacji, zobacz [okres istnienia obiektu: sposób tworzenia i zniszczenia obiektów](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md).

- `typeparamlist`

  Opcjonalna. Lista parametrów typu dla procedury ogólnej. Zobacz [Lista typów](type-list.md).

- `parameterlist`

  Opcjonalna. Lista nazw zmiennych lokalnych reprezentujących parametry tej procedury. Zobacz [listę parametrów](parameter-list.md).

- `Implements`

  Opcjonalna. Wskazuje, że ta procedura implementuje co najmniej jedną `Sub` procedury, każda z nich zdefiniowana w interfejsie zaimplementowanym przez tę procedurę zawierającą klasę lub strukturę. Zobacz [instrukcja Implements](implements-statement.md).

- `implementslist`

  Wymagane, jeśli podano `Implements`. Lista implementowanych procedur `Sub`.

  `implementedprocedure [ , implementedprocedure ... ]`

  Każda `implementedprocedure` ma następującą składnię i części:

  `interface.definedname`

  |Części|Opis|
  |---|---|
  |`interface`|Wymagana. Nazwa interfejsu implementowanego przez tę procedurę zawierającą klasę lub strukturę.|
  |`definedname`|Wymagana. Nazwa, przez którą procedura jest definiowana w `interface`.|

- `Handles`

  Opcjonalna. Wskazuje, że ta procedura może obsłużyć jedno lub więcej konkretnych zdarzeń. Zobacz [Handles](handles-clause.md).

- `eventlist`

  Wymagane, jeśli podano `Handles`. Lista zdarzeń, których dotyczy ta procedura.

  `eventspecifier [ , eventspecifier ... ]`

  Każda `eventspecifier` ma następującą składnię i części:

  `eventvariable.event`

  |Części|Opis|
  |---|---|
  |`eventvariable`|Wymagana. Zmienna obiektu zadeklarowana z typem danych klasy lub struktury, która wywołuje zdarzenie.|
  |`event`|Wymagana. Nazwa zdarzenia, którego dotyczy ta procedura.|

- `statements`

  Opcjonalna. Blok instrukcji do uruchomienia w ramach tej procedury.

- `End Sub`

  Kończy definicję tej procedury.

## <a name="remarks"></a>Uwagi

Cały kod wykonywalny musi znajdować się wewnątrz procedury. Użyj procedury `Sub`, jeśli nie chcesz zwracać wartości do kodu wywołującego. Użyj procedury `Function`, jeśli chcesz zwrócić wartość.

## <a name="defining-a-sub-procedure"></a>Definiowanie procedury Sub

Procedurę `Sub` można zdefiniować tylko na poziomie modułu. Kontekst deklaracji procedury Sub musi, dlatego, być klasą, strukturą, modułem lub interfejsem i nie może być plikiem źródłowym, przestrzenią nazw, procedurą lub blokiem. Aby uzyskać więcej informacji, zobacz [konteksty deklaracji i domyślne poziomy dostępu](declaration-contexts-and-default-access-levels.md).

`Sub` procedury domyślne do dostępu publicznego. Poziomy dostępu można dostosować za pomocą modyfikatorów dostępu.

Jeśli procedura używa słowa kluczowego `Implements`, zawierająca klasę lub strukturę musi mieć instrukcję `Implements`, która natychmiast następuje po `Class` lub `Structure` instrukcji. Instrukcja `Implements` musi zawierać każdy interfejs, który jest określony w `implementslist`. Jednak nazwa, za pomocą której interfejs definiuje `Sub` (w `definedname`), nie musi być zgodna z nazwą tej procedury (w `name`).

## <a name="returning-from-a-sub-procedure"></a>Powrót z procedury Sub

Gdy `Sub` procedura zwraca kod wywołujący, wykonywanie jest kontynuowane za pomocą instrukcji po instrukcji, która go wywołała.

Poniższy przykład przedstawia zwrot z procedury `Sub`.

```vb
Sub mySub(ByVal q As String)
    Return
End Sub
```

Instrukcje `Exit Sub` i `Return` powodują natychmiastowe wyjście z procedury `Sub`. Dowolna liczba instrukcji `Exit Sub` i `Return` może występować w dowolnym miejscu procedury i można mieszać instrukcje `Exit Sub` i `Return`.

## <a name="calling-a-sub-procedure"></a>Wywoływanie procedury Sub

Procedurę `Sub` można wywołać przy użyciu nazwy procedury w instrukcji, a następnie po tej nazwie z listą argumentów w nawiasach. Nawiasy można pominąć tylko wtedy, gdy nie podasz żadnych argumentów. Jednak kod jest bardziej czytelny, jeśli zawsze zawiera nawiasy.

Procedura `Sub` i procedura `Function` mogą mieć parametry i wykonywać serie instrukcji. Jednak procedura `Function` zwraca wartość, a procedura `Sub`a nie. W związku z tym nie można użyć `Sub` procedury w wyrażeniu.

Można użyć słowa kluczowego `Call` podczas wywoływania procedury `Sub`, ale nie jest to zalecane w przypadku większości użycia. Aby uzyskać więcej informacji, zobacz [wywoływanie instrukcji](call-statement.md).

Visual Basic czasami ponownie rozmieszcza wyrażenia arytmetyczne w celu zwiększenia wydajności wewnętrznej. Z tego powodu, jeśli lista argumentów zawiera wyrażenia, które wywołują inne procedury, nie należy zakładać, że te wyrażenia będą wywoływane w określonej kolejności.

## <a name="async-sub-procedures"></a>Procedury podrzędne Async

Za pomocą funkcji asynchronicznej można wywoływać funkcje asynchroniczne bez używania jawnych wywołań zwrotnych lub ręcznie podzielić kod w wielu funkcjach lub wyrażeniach lambda.

Jeśli oznaczesz procedurę za pomocą modyfikatora [asynchronicznego](../modifiers/async.md) , możesz użyć operatora [await](../../../visual-basic/language-reference/operators/await-operator.md) w procedurze. Gdy kontrolka osiągnie wyrażenie `Await` w procedurze `Async`, sterowanie powraca do obiektu wywołującego, a postęp w procedurze jest zawieszony do momentu ukończenia zadania. Po zakończeniu zadania wykonanie może zostać wznowione w procedurze.

> [!NOTE]
> Procedura `Async` powraca do obiektu wywołującego, gdy wystąpił pierwszy oczekujący obiekt, który nie został jeszcze ukończony lub osiągnięto koniec procedury `Async`, w zależności od tego, co się dzieje.

Można także oznaczyć [instrukcję Function](function-statement.md) z modyfikatorem `Async`. Funkcja `Async` może mieć zwracany typ <xref:System.Threading.Tasks.Task%601> lub <xref:System.Threading.Tasks.Task>. Przykład w dalszej części tego tematu pokazuje funkcję `Async`, która ma zwracany typ <xref:System.Threading.Tasks.Task%601>.

procedury `Sub` `Async` są używane głównie dla programów obsługi zdarzeń, w których nie można zwrócić wartości. Nie można oczekiwać `Async` procedury `Sub`, a obiekt wywołujący procedury `Async` `Sub` nie może przechwytywać wyjątków, które zgłasza procedura `Sub`.

Procedura `Async` nie może zadeklarować żadnych parametrów [ByRef](../modifiers/byref.md) .

Aby uzyskać więcej informacji na temat procedur `Async`, zobacz [programowanie asynchroniczne z asynchroniczne i await](../../../visual-basic/programming-guide/concepts/async/index.md), [przepływ sterowania w programach asynchronicznych](../../../visual-basic/programming-guide/concepts/async/control-flow-in-async-programs.md)i [asynchroniczne typy zwracane](../../../visual-basic/programming-guide/concepts/async/async-return-types.md).

## <a name="example"></a>Przykład

Poniższy przykład używa instrukcji `Sub`, aby zdefiniować nazwę, parametry i kod, który stanowi treść procedury `Sub`.

[!code-vb[VbVbalrStatements#58](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#58)]

## <a name="example"></a>Przykład

W poniższym przykładzie `DelayAsync` jest `Async` `Function`, który ma zwracany typ <xref:System.Threading.Tasks.Task%601>. `DelayAsync` zawiera instrukcję `Return`, która zwraca liczbę całkowitą. W związku z tym deklaracja funkcji `DelayAsync` musi mieć typ zwracany `Task(Of Integer)`. Ponieważ zwracany typ jest `Task(Of Integer)`, Obliczanie wyrażenia `Await` w `DoSomethingAsync` tworzy liczbę całkowitą, jak pokazano w poniższej instrukcji: `Dim result As Integer = Await delayTask`.

Procedura `startButton_Click` jest przykładem procedury `Async Sub`owej. Ponieważ `DoSomethingAsync` jest funkcją `Async`, zadanie dla wywołania `DoSomethingAsync` musi być oczekiwane, jak pokazano w poniższej instrukcji: `Await DoSomethingAsync()`. Procedura `startButton_Click` `Sub` musi być zdefiniowana za pomocą modyfikatora `Async`, ponieważ ma wyrażenie `Await`.

[!code-vb[csAsyncMethod#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/csasyncmethod/vb/mainwindow.xaml.vb#1)]

## <a name="see-also"></a>Zobacz także

- [Implements, instrukcja](implements-statement.md)
- [Function, instrukcja](function-statement.md)
- [Lista parametrów](parameter-list.md)
- [Dim, instrukcja](dim-statement.md)
- [Call, instrukcja](call-statement.md)
- [Z](of-clause.md)
- [Tablice parametrów](../../../visual-basic/programming-guide/language-features/procedures/parameter-arrays.md)
- [Instrukcje: używanie klasy ogólnej](../../../visual-basic/programming-guide/language-features/data-types/how-to-use-a-generic-class.md)
- [Rozwiązywanie problemów z procedurami](../../../visual-basic/programming-guide/language-features/procedures/troubleshooting-procedures.md)
- [Metody częściowe](../../../visual-basic/programming-guide/language-features/procedures/partial-methods.md)
