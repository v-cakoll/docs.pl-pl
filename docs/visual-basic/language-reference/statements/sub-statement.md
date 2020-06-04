---
title: Sub, instrukcja
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
ms.openlocfilehash: e50b79c31c92ac116d6c82bcececba3340894d74
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84404177"
---
# <a name="sub-statement-visual-basic"></a>Sub — Instrukcja (Visual Basic)

Deklaruje nazwę, parametry i kod definiujący `Sub` procedurę.

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

  Opcjonalny. Zobacz [listę atrybutów](attribute-list.md).

- `Partial`

  Opcjonalny. Wskazuje definicję metody częściowej. Zobacz [metody częściowe](../../programming-guide/language-features/procedures/partial-methods.md).

- `accessmodifier`

  Opcjonalny. Może być jedną z następujących czynności:

  - [Społeczeństwo](../modifiers/public.md)

  - [Chronione](../modifiers/protected.md)

  - [Osoby](../modifiers/friend.md)

  - [Użytek](../modifiers/private.md)

  - [Protected Friend](../modifiers/protected-friend.md)

  - [Prywatne chronione](../modifiers/private-protected.md)

  Zobacz [poziomy dostępu w Visual Basic](../../programming-guide/language-features/declared-elements/access-levels.md).

- `proceduremodifiers`

  Opcjonalny. Może być jedną z następujących czynności:

  - [Przeciążenia](../modifiers/overloads.md)

  - [Przesłonięcia](../modifiers/overrides.md)

  - [Overridable](../modifiers/overridable.md)

  - [NotOverridable](../modifiers/notoverridable.md)

  - [MustOverride](../modifiers/mustoverride.md)

  - `MustOverride Overrides`

  - `NotOverridable Overrides`

- `Shared`

  Opcjonalny. Zobacz [udostępnianie](../modifiers/shared.md).

- `Shadows`

  Opcjonalny. Zobacz [Shadows](../modifiers/shadows.md).

- `Async`

  Opcjonalny. Zobacz [Async](../modifiers/async.md).

- `name`

  Wymagany. Nazwa procedury. Zobacz [zadeklarowane nazwy elementów](../../programming-guide/language-features/declared-elements/declared-element-names.md). Aby utworzyć procedurę konstruktora dla klasy, należy ustawić nazwę `Sub` procedury dla `New` słowa kluczowego. Aby uzyskać więcej informacji, zobacz [okres istnienia obiektu: sposób tworzenia i zniszczenia obiektów](../../programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md).

- `typeparamlist`

  Opcjonalny. Lista parametrów typu dla procedury ogólnej. Zobacz [Lista typów](type-list.md).

- `parameterlist`

  Opcjonalny. Lista nazw zmiennych lokalnych reprezentujących parametry tej procedury. Zobacz [listę parametrów](parameter-list.md).

- `Implements`

  Opcjonalny. Wskazuje, że ta procedura implementuje jedną lub więcej `Sub` procedur, każda zdefiniowana w interfejsie implementowanym przez tę procedurę zawierającą klasę lub strukturę. Zobacz [instrukcja Implements](implements-statement.md).

- `implementslist`

  Wymagane, jeśli `Implements` jest podany. Lista `Sub` implementowanych procedur.

  `implementedprocedure [ , implementedprocedure ... ]`

  Każda `implementedprocedure` z nich ma następującą składnię i części:

  `interface.definedname`

  |Część|Opis|
  |---|---|
  |`interface`|Wymagany. Nazwa interfejsu implementowanego przez tę procedurę zawierającą klasę lub strukturę.|
  |`definedname`|Wymagany. Nazwa, przez którą procedura jest zdefiniowana `interface` .|

- `Handles`

  Opcjonalny. Wskazuje, że ta procedura może obsłużyć jedno lub więcej konkretnych zdarzeń. Zobacz [Handles](handles-clause.md).

- `eventlist`

  Wymagane, jeśli `Handles` jest podany. Lista zdarzeń, których dotyczy ta procedura.

  `eventspecifier [ , eventspecifier ... ]`

  Każda `eventspecifier` z nich ma następującą składnię i części:

  `eventvariable.event`

  |Część|Opis|
  |---|---|
  |`eventvariable`|Wymagany. Zmienna obiektu zadeklarowana z typem danych klasy lub struktury, która wywołuje zdarzenie.|
  |`event`|Wymagany. Nazwa zdarzenia, którego dotyczy ta procedura.|

- `statements`

  Opcjonalny. Blok instrukcji do uruchomienia w ramach tej procedury.

- `End Sub`

  Kończy definicję tej procedury.

## <a name="remarks"></a>Uwagi

Cały kod wykonywalny musi znajdować się wewnątrz procedury. Użyj `Sub` procedury, gdy nie chcesz zwracać wartości do kodu wywołującego. Użyj `Function` procedury, jeśli chcesz zwrócić wartość.

## <a name="defining-a-sub-procedure"></a>Definiowanie procedury Sub

Procedurę można zdefiniować `Sub` tylko na poziomie modułu. Kontekst deklaracji procedury Sub musi, dlatego, być klasą, strukturą, modułem lub interfejsem i nie może być plikiem źródłowym, przestrzenią nazw, procedurą lub blokiem. Aby uzyskać więcej informacji, zobacz [konteksty deklaracji i domyślne poziomy dostępu](declaration-contexts-and-default-access-levels.md).

`Sub`procedury domyślne do dostępu publicznego. Poziomy dostępu można dostosować za pomocą modyfikatorów dostępu.

Jeśli procedura używa `Implements` słowa kluczowego, Klasa lub struktura, która musi występować `Implements` bezpośrednio po `Class` `Structure` instrukcji or. `Implements`Instrukcja musi zawierać wszystkie interfejsy, które są określone w `implementslist` . Jednak nazwa, za pomocą której interfejs definiuje `Sub` (w), `definedname` nie musi być zgodna z nazwą tej procedury (w programie `name` ).

## <a name="returning-from-a-sub-procedure"></a>Powrót z procedury Sub

Gdy `Sub` procedura zwraca kod wywołujący, wykonywanie jest kontynuowane za pomocą instrukcji po instrukcji, która go wywołała.

Poniższy przykład przedstawia powrót z `Sub` procedury.

```vb
Sub mySub(ByVal q As String)
    Return
End Sub
```

`Exit Sub`Instrukcje i `Return` powodują natychmiastowe wyjście z `Sub` procedury. Dowolna liczba `Exit Sub` `Return` instrukcji i może występować w dowolnym miejscu procedury i można mieszać i wypełniać `Exit Sub` `Return` instrukcje.

## <a name="calling-a-sub-procedure"></a>Wywoływanie procedury Sub

Należy wywołać `Sub` procedurę przy użyciu nazwy procedury w instrukcji, a następnie po tej nazwie z listą argumentów w nawiasach. Nawiasy można pominąć tylko wtedy, gdy nie podasz żadnych argumentów. Jednak kod jest bardziej czytelny, jeśli zawsze zawiera nawiasy.

`Sub`Procedura i `Function` procedura mogą mieć parametry i wykonywać serie instrukcji. Jednak `Function` procedura zwraca wartość, a `Sub` procedura nie jest. W związku z tym nie można użyć `Sub` procedury w wyrażeniu.

Możesz użyć `Call` słowa kluczowego podczas wywoływania `Sub` procedury, ale nie jest to zalecane w przypadku większości użycia. Aby uzyskać więcej informacji, zobacz [wywoływanie instrukcji](call-statement.md).

Visual Basic czasami ponownie rozmieszcza wyrażenia arytmetyczne w celu zwiększenia wydajności wewnętrznej. Z tego powodu, jeśli lista argumentów zawiera wyrażenia, które wywołują inne procedury, nie należy zakładać, że te wyrażenia będą wywoływane w określonej kolejności.

## <a name="async-sub-procedures"></a>Procedury podrzędne Async

Za pomocą funkcji asynchronicznej można wywoływać funkcje asynchroniczne bez używania jawnych wywołań zwrotnych lub ręcznie podzielić kod w wielu funkcjach lub wyrażeniach lambda.

Jeśli oznaczesz procedurę za pomocą modyfikatora [asynchronicznego](../modifiers/async.md) , możesz użyć operatora [await](../operators/await-operator.md) w procedurze. Gdy kontrolka osiągnie `Await` wyrażenie w `Async` procedurze, sterowanie powraca do obiektu wywołującego, a postęp w procedurze jest zawieszony do momentu zakończenia zadania oczekiwania. Po zakończeniu zadania wykonanie może zostać wznowione w procedurze.

> [!NOTE]
> `Async`Procedura powraca do obiektu wywołującego, gdy wystąpił pierwszy oczekujący obiekt, który nie został jeszcze ukończony lub `Async` osiągnięto koniec procedury, w zależności od tego, co się dzieje.

Można także oznaczyć [instrukcję Function](function-statement.md) z `Async` modyfikatorem. `Async`Funkcja może mieć zwracany typ <xref:System.Threading.Tasks.Task%601> lub <xref:System.Threading.Tasks.Task> . Przykład w dalszej części tego tematu pokazuje `Async` funkcję, która ma zwracany typ <xref:System.Threading.Tasks.Task%601> .

`Async``Sub`procedury są używane głównie dla programów obsługi zdarzeń, w których nie można zwrócić wartości. `Async` `Sub` Nie można oczekiwać procedury, a obiekt wywołujący `Async` `Sub` procedury nie może przechwytywać wyjątków, które `Sub` procedura zgłasza.

`Async`Procedura nie może zadeklarować żadnych parametrów [ByRef](../modifiers/byref.md) .

Aby uzyskać więcej informacji na temat `Async` procedur, zobacz [programowanie asynchroniczne przy użyciu asynchronicznych i oczekujących](../../programming-guide/concepts/async/index.md), [przepływu sterowania w programach asynchronicznych](../../programming-guide/concepts/async/control-flow-in-async-programs.md)i [asynchronicznych typów zwracanych](../../programming-guide/concepts/async/async-return-types.md).

## <a name="example"></a>Przykład

Poniższy przykład używa instrukcji, `Sub` Aby zdefiniować nazwę, parametry i kod, który stanowi treść `Sub` procedury.

[!code-vb[VbVbalrStatements#58](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#58)]

## <a name="example"></a>Przykład

W poniższym przykładzie `DelayAsync` jest to, `Async` `Function` który ma zwracany typ <xref:System.Threading.Tasks.Task%601> . `DelayAsync`zawiera `Return` instrukcję zwracającą liczbę całkowitą. W związku z tym, deklaracja funkcji `DelayAsync` musi mieć typ zwracany `Task(Of Integer)` . Ponieważ typem zwracanym jest `Task(Of Integer)` , obliczanie `Await` wyrażenia w `DoSomethingAsync` tworzy liczbę całkowitą, jak pokazano w poniższej instrukcji: `Dim result As Integer = Await delayTask` .

`startButton_Click`Procedura jest przykładem `Async Sub` procedury. Ponieważ `DoSomethingAsync` jest `Async` funkcją, zadanie dla wywołania `DoSomethingAsync` musi być oczekiwane, jak pokazano w poniższej instrukcji: `Await DoSomethingAsync()` . `startButton_Click` `Sub` Procedura musi być zdefiniowana z `Async` modyfikatorem, ponieważ ma `Await` wyrażenie.

[!code-vb[csAsyncMethod#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/csasyncmethod/vb/mainwindow.xaml.vb#1)]

## <a name="see-also"></a>Zobacz też

- [Implements — Instrukcja](implements-statement.md)
- [Function, instrukcja](function-statement.md)
- [Lista parametrów](parameter-list.md)
- [Dim, instrukcja](dim-statement.md)
- [Call, instrukcja](call-statement.md)
- [Z](of-clause.md)
- [Parameter — Tablice](../../programming-guide/language-features/procedures/parameter-arrays.md)
- [Instrukcje: Używanie klasy ogólnej](../../programming-guide/language-features/data-types/how-to-use-a-generic-class.md)
- [Rozwiązywanie problemów z procedurami](../../programming-guide/language-features/procedures/troubleshooting-procedures.md)
- [Metody częściowe](../../programming-guide/language-features/procedures/partial-methods.md)
