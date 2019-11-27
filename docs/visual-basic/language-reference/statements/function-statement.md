---
title: Function — Instrukcja
ms.date: 05/12/2018
f1_keywords:
- vb.Function
helpviewer_keywords:
- procedures [Visual Basic], creating
- Function procedures [Visual Basic], Function statement syntax
- functions [Visual Basic], function procedures
- ParamArray keyword [Visual Basic], Function statements
- Private keyword [Visual Basic], Function statements
- declarations [Visual Basic], procedures
- procedures [Visual Basic], declaration
- Public keyword [Visual Basic], in Function statement
- ByVal keyword [Visual Basic], Function statements
- procedures [Visual Basic], recursive
- Implements keyword [Visual Basic], Function statements
- procedures [Visual Basic], returning values
- Exit statement [Visual Basic], in Function procedures
- recursive procedures
- As keyword [Visual Basic], in Function statement
- Optional keyword [Visual Basic], Function statements
- Function statement [Visual Basic]
- Visual Basic code, Function procedures
- procedures [Visual Basic], function
- ByRef keyword [Visual Basic], Function statements
- Friend keyword [Visual Basic], Function statements
- End keyword [Visual Basic], Function statements
- Handles keyword [Visual Basic], Function statements
ms.assetid: a4497077-0f46-4ede-a27f-9e8670df52b9
ms.openlocfilehash: 8140c7e6267e66c69c20d413a11d04372400c581
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74345918"
---
# <a name="function-statement-visual-basic"></a>Function — Instrukcja (Visual Basic)

Deklaruje nazwę, parametry i kod definiujący procedurę `Function`.

## <a name="syntax"></a>Składnia

```vb
[ <attributelist> ] [ accessmodifier ] [ proceduremodifiers ] [ Shared ] [ Shadows ] [ Async | Iterator ]
Function name [ (Of typeparamlist) ] [ (parameterlist) ] [ As returntype ] [ Implements implementslist | Handles eventlist ]
    [ statements ]
    [ Exit Function ]
    [ statements ]
End Function
```

## <a name="parts"></a>Części

- `attributelist`

  Opcjonalna. Zobacz [listę atrybutów](attribute-list.md).

- `accessmodifier`

  Opcjonalna. Może to być jeden z następujących modyfikatorów dostępu:

  - [Public](../../../visual-basic/language-reference/modifiers/public.md)

  - [Protected](../../../visual-basic/language-reference/modifiers/protected.md)

  - [Friend](../../../visual-basic/language-reference/modifiers/friend.md)

  - [Private](../../../visual-basic/language-reference/modifiers/private.md)

  - [Protected Friend](../../language-reference/modifiers/protected-friend.md)

  - [Private Protected](../../language-reference/modifiers/private-protected.md)

  Zobacz [poziomy dostępu w Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).

- `proceduremodifiers`

  Opcjonalna. Może to być jeden z następujących modyfikatorów dostępu:

  - [Overloads](../../../visual-basic/language-reference/modifiers/overloads.md)

  - [Overrides](../../../visual-basic/language-reference/modifiers/overrides.md)

  - [Overridable](../../../visual-basic/language-reference/modifiers/overridable.md)

  - [NotOverridable](../../../visual-basic/language-reference/modifiers/notoverridable.md)

  - [MustOverride](../../../visual-basic/language-reference/modifiers/mustoverride.md)

  - `MustOverride Overrides`

  - `NotOverridable Overrides`

- `Shared`

  Opcjonalna. Zobacz [udostępnianie](../../../visual-basic/language-reference/modifiers/shared.md).

- `Shadows`

  Opcjonalna. Zobacz [Shadows](../../../visual-basic/language-reference/modifiers/shadows.md).

- `Async`

  Opcjonalna. Zobacz [Async](../../../visual-basic/language-reference/modifiers/async.md).

- `Iterator`

  Opcjonalna. Zobacz [iterator](../../../visual-basic/language-reference/modifiers/iterator.md).

- `name`

  Wymagana. Nazwa procedury. Zobacz [zadeklarowane nazwy elementów](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).

- `typeparamlist`

  Opcjonalna. Lista parametrów typu dla procedury ogólnej. Zobacz [Lista typów](type-list.md).

- `parameterlist`

  Opcjonalna. Lista nazw zmiennych lokalnych reprezentujących parametry tej procedury. Zobacz [listę parametrów](parameter-list.md).

- `returntype`

  Wymagane, jeśli `Option Strict` jest `On`. Typ danych wartości zwracanej przez tę procedurę.

- `Implements`

  Opcjonalna. Wskazuje, że ta procedura implementuje co najmniej jedną `Function` procedury, każda z nich zdefiniowana w interfejsie zaimplementowanym przez tę procedurę zawierającą klasę lub strukturę. Zobacz [instrukcja Implements](implements-statement.md).

- `implementslist`

  Wymagane, jeśli podano `Implements`. Lista implementowanych procedur `Function`.

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

  Opcjonalna. Blok instrukcji do wykonania w ramach tej procedury.

- `End Function`

  Kończy definicję tej procedury.

## <a name="remarks"></a>Uwagi

Cały kod wykonywalny musi znajdować się wewnątrz procedury. Każda procedura z kolei jest zadeklarowana w obrębie klasy, struktury lub modułu, który jest nazywany klasą zawierającą, strukturą lub modułem.

Aby zwrócić wartość do kodu wywołującego, użyj procedury `Function`ej; w przeciwnym razie użyj procedury `Sub`.

## <a name="defining-a-function"></a>Definiowanie funkcji

Procedurę `Function` można zdefiniować tylko na poziomie modułu. W związku z tym kontekst deklaracji dla funkcji musi być klasą, strukturą, modułem lub interfejsem i nie może być plikiem źródłowym, przestrzenią nazw, procedurą lub blokiem. Aby uzyskać więcej informacji, zobacz [konteksty deklaracji i domyślne poziomy dostępu](declaration-contexts-and-default-access-levels.md).

`Function` procedury domyślne do dostępu publicznego. Poziomy dostępu modułów można dostosować za pomocą modyfikatorów dostępu.

Procedura `Function` może deklarować typ danych wartości zwracanej przez procedurę. Można określić dowolny typ danych lub nazwę wyliczenia, struktury, klasy lub interfejsu. Jeśli nie określisz parametru `returntype`, procedura zwróci `Object`.

Jeśli ta procedura używa słowa kluczowego `Implements`, Klasa lub struktura, która zawiera, musi również mieć instrukcję `Implements`, która bezpośrednio następuje po instrukcji `Class` lub `Structure`. Instrukcja `Implements` musi zawierać każdy interfejs, który jest określony w `implementslist`. Jednak nazwa, za pomocą której interfejs definiuje `Function` (w `definedname`), nie musi być zgodna z nazwą tej procedury (w `name`).

> [!NOTE]
> Można użyć wyrażeń lambda do definiowania wyrażeń funkcji w tekście. Aby uzyskać więcej informacji, zobacz [wyrażenie funkcji](../../../visual-basic/language-reference/operators/function-expression.md) i [wyrażenia lambda](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md).

## <a name="returning-from-a-function"></a>Zwracanie z funkcji

Gdy procedura `Function` powraca do kodu wywołującego, wykonywanie jest kontynuowane za pomocą instrukcji, która następuje po instrukcji, która wywołała procedurę.

Aby zwrócić wartość z funkcji, można przypisać wartość do nazwy funkcji lub dołączyć ją do instrukcji `Return`.

Instrukcja `Return` równocześnie przypisuje wartość zwracaną i opuszcza funkcję, jak pokazano w poniższym przykładzie.

[!code-vb[VbVbalrStatements#24](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#24)]

Poniższy przykład przypisuje wartość zwracaną do nazwy funkcji `myFunction` a następnie używa instrukcji `Exit Function` do zwrócenia.

[!code-vb[VbVbalrStatements#23](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#23)]

Instrukcje `Exit Function` i `Return` powodują natychmiastowe wyjście z procedury `Function`. Dowolna liczba instrukcji `Exit Function` i `Return` może występować w dowolnym miejscu procedury i można mieszać instrukcje `Exit Function` i `Return`.

Jeśli używasz `Exit Function` bez przypisywania wartości do `name`, procedura zwróci wartość domyślną dla typu danych określonego w `returntype`. Jeśli nie określono `returntype`, procedura zwraca `Nothing`, która jest wartością domyślną dla `Object`.

## <a name="calling-a-function"></a>Wywołanie funkcji

Procedurę `Function` można wywołać przy użyciu nazwy procedury, a następnie listy argumentów w nawiasach w wyrażeniu. Nawiasy można pominąć tylko wtedy, gdy nie podasz żadnych argumentów. Jednak kod jest bardziej czytelny, jeśli zawsze zawiera nawiasy.

Należy wywołać procedurę `Function` w taki sam sposób, jak w przypadku każdej funkcji biblioteki, takiej jak `Sqrt`, `Cos`lub `ChrW`.

Możesz również wywołać funkcję za pomocą słowa kluczowego `Call`. W takim przypadku zwracana wartość jest ignorowana. Użycie słowa kluczowego `Call` nie jest zalecane w większości przypadków. Aby uzyskać więcej informacji, zobacz [wywoływanie instrukcji](call-statement.md).

Visual Basic czasami ponownie rozmieszcza wyrażenia arytmetyczne w celu zwiększenia wydajności wewnętrznej. Z tego powodu nie należy używać procedury `Function` w wyrażeniu arytmetycznym, gdy funkcja zmienia wartość zmiennych w tym samym wyrażeniu.

## <a name="async-functions"></a>Funkcje asynchroniczne

Funkcja *Async* umożliwia wywoływanie funkcji asynchronicznych bez użycia jawnych wywołań zwrotnych lub Ręczne dzielenie kodu w wielu funkcjach lub wyrażeniach lambda.

Jeśli oznaczesz funkcję z modyfikatorem [Async](../../../visual-basic/language-reference/modifiers/async.md) , możesz użyć operatora [await](../../../visual-basic/language-reference/operators/await-operator.md) w funkcji. Gdy kontrolka osiągnie wyrażenie `Await` w funkcji `Async`, sterowanie powraca do obiektu wywołującego, a postęp w funkcji jest zawieszony do momentu ukończenia zadania. Po zakończeniu zadania wykonywanie może zostać wznowione w funkcji.

> [!NOTE]
> Procedura `Async` powraca do obiektu wywołującego, gdy napotka on pierwszy oczekujący obiekt, który nie został jeszcze ukończony, lub znajduje się na końcu procedury `Async`, zależnie od tego, co nastąpi wcześniej.

Funkcja `Async` może mieć zwracany typ <xref:System.Threading.Tasks.Task%601> lub <xref:System.Threading.Tasks.Task>. Przykład funkcji `Async`, która ma zwracany typ <xref:System.Threading.Tasks.Task%601> jest podany poniżej.

Funkcja `Async` nie może deklarować żadnych parametrów [ByRef](../../../visual-basic/language-reference/modifiers/byref.md) .

[Instrukcja sub](sub-statement.md) może być również oznaczona modyfikatorem `Async`. Jest to używane głównie dla programów obsługi zdarzeń, w których nie można zwrócić wartości. Nie można oczekiwać `Async` procedury `Sub`, a obiekt wywołujący procedury `Async` `Sub` nie może przechwytywać wyjątków, które są zgłaszane przez procedurę `Sub`.

Aby uzyskać więcej informacji na temat funkcji `Async`, zobacz [programowanie asynchroniczne z asynchroniczne i await](../../../visual-basic/programming-guide/concepts/async/index.md), [przepływ sterowania w programach asynchronicznych](../../../visual-basic/programming-guide/concepts/async/control-flow-in-async-programs.md)i [asynchroniczne typy zwracane](../../../visual-basic/programming-guide/concepts/async/async-return-types.md).

## <a name="iterator-functions"></a>Funkcje iteratora

Funkcja *iteratora* wykonuje niestandardową iterację w kolekcji, na przykład listę lub tablicę. Funkcja iteratora używa instrukcji [Yield](yield-statement.md) do zwrócenia każdego elementu w danym momencie. Po osiągnięciu instrukcji [Yield](yield-statement.md) bieżąca lokalizacja w kodzie jest zapamiętywana. Wykonanie jest uruchamiane ponownie z tej lokalizacji przy następnym wywołaniu funkcji iteratora.

Należy wywołać iterator z kodu klienta przy użyciu [for each... Next](for-each-next-statement.md) — instrukcja.

Zwracanym typem funkcji iteratora może być <xref:System.Collections.IEnumerable>, <xref:System.Collections.Generic.IEnumerable%601>, <xref:System.Collections.IEnumerator>lub <xref:System.Collections.Generic.IEnumerator%601>.

Aby uzyskać więcej informacji, zobacz [Iteratory](../../programming-guide/concepts/iterators.md).

## <a name="example"></a>Przykład

Poniższy przykład używa instrukcji `Function`, aby zadeklarować nazwę, parametry i kod, który stanowi treść procedury `Function`. Modyfikator `ParamArray` włącza funkcję do akceptowania zmiennej liczby argumentów.

[!code-vb[VbVbalrStatements#25](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#25)]

## <a name="example"></a>Przykład

Poniższy przykład wywołuje funkcję zadeklarowaną w poprzednim przykładzie.

[!code-vb[VbVbalrStatements#26](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#26)]

## <a name="example"></a>Przykład

W poniższym przykładzie `DelayAsync` jest `Async` `Function`, który ma zwracany typ <xref:System.Threading.Tasks.Task%601>. `DelayAsync` zawiera instrukcję `Return`, która zwraca liczbę całkowitą. W związku z tym deklaracja funkcji `DelayAsync` musi mieć typ zwracany `Task(Of Integer)`. Ponieważ zwracany typ jest `Task(Of Integer)`, obliczenia `Await` wyrażenia w `DoSomethingAsync` tworzą liczbę całkowitą. Przedstawiono to w tej instrukcji: `Dim result As Integer = Await delayTask`.

Procedura `startButton_Click` jest przykładem procedury `Async Sub`owej. Ponieważ `DoSomethingAsync` jest funkcją `Async`, zadanie dla wywołania `DoSomethingAsync` musi być oczekiwane, jak pokazano w poniższej instrukcji: `Await DoSomethingAsync()`. Procedura `startButton_Click` `Sub` musi być zdefiniowana za pomocą modyfikatora `Async`, ponieważ ma wyrażenie `Await`.

[!code-vb[csAsyncMethod#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/csasyncmethod/vb/mainwindow.xaml.vb#1)]

## <a name="see-also"></a>Zobacz także

- [Sub, instrukcja](sub-statement.md)
- [Procedury funkcji](../../../visual-basic/programming-guide/language-features/procedures/function-procedures.md)
- [Lista parametrów](parameter-list.md)
- [Dim, instrukcja](dim-statement.md)
- [Call, instrukcja](call-statement.md)
- [Z](of-clause.md)
- [Tablice parametrów](../../../visual-basic/programming-guide/language-features/procedures/parameter-arrays.md)
- [Instrukcje: używanie klasy ogólnej](../../../visual-basic/programming-guide/language-features/data-types/how-to-use-a-generic-class.md)
- [Rozwiązywanie problemów z procedurami](../../../visual-basic/programming-guide/language-features/procedures/troubleshooting-procedures.md)
- [Wyrażenia lambda](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)
- [Function, wyrażenie](../../../visual-basic/language-reference/operators/function-expression.md)
