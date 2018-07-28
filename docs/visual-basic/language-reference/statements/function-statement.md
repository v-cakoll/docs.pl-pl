---
title: Function — Instrukcja (Visual Basic)
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
ms.openlocfilehash: b370e92aaab88a7f0d49f1de60b50fa6bbf1e161
ms.sourcegitcommit: 869b5832b667915ac4a5dd8c86b1109ed26b6c08
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2018
ms.locfileid: "39323017"
---
# <a name="function-statement-visual-basic"></a>Function — Instrukcja (Visual Basic)
Deklaruje nazwę, parametry i kod, który definiuje `Function` procedury.  
  
## <a name="syntax"></a>Składnia  
  
```  
[ <attributelist> ] [ accessmodifier ] [ proceduremodifiers ] [ Shared ] [ Shadows ] [ Async | Iterator ]  
Function name [ (Of typeparamlist) ] [ (parameterlist) ] [ As returntype ] [ Implements implementslist | Handles eventlist ]  
    [ statements ]  
    [ Exit Function ]  
    [ statements ]  
End Function  
```  
  
## <a name="parts"></a>Części  
  
-   `attributelist`  
  
     Opcjonalna. Zobacz [Lista atrybutów](attribute-list.md).  
  
-   `accessmodifier`  
  
     Opcjonalna. Może to być jeden z następujących elementów:  
  
    -   [Public](../../../visual-basic/language-reference/modifiers/public.md)  
  
    -   [Protected](../../../visual-basic/language-reference/modifiers/protected.md)  
  
    -   [Friend](../../../visual-basic/language-reference/modifiers/friend.md)  
  
    -   [Private](../../../visual-basic/language-reference/modifiers/private.md)  
  
    -   [Chronione Friend](../../language-reference/modifiers/protected-friend.md)

    - [Prywatny chroniony](../../language-reference/modifiers/private-protected.md)  
  
     Zobacz temat [Poziomy dostępu w języku Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).  
  
-   `proceduremodifiers`  
  
     Opcjonalna. Może to być jeden z następujących elementów:  
  
    -   [Overloads](../../../visual-basic/language-reference/modifiers/overloads.md)  
  
    -   [Overrides](../../../visual-basic/language-reference/modifiers/overrides.md)  
  
    -   [Overridable](../../../visual-basic/language-reference/modifiers/overridable.md)  
  
    -   [NotOverridable](../../../visual-basic/language-reference/modifiers/notoverridable.md)  
  
    -   [MustOverride](../../../visual-basic/language-reference/modifiers/mustoverride.md)  
  
    -   `MustOverride Overrides`  
  
    -   `NotOverridable Overrides`  
  
-   `Shared`  
  
     Opcjonalna. Zobacz [udostępnione](../../../visual-basic/language-reference/modifiers/shared.md).  
  
-   `Shadows`  
  
     Opcjonalna. Zobacz [Shadows](../../../visual-basic/language-reference/modifiers/shadows.md).  
  
-   `Async`  
  
     Opcjonalna. Zobacz [Async](../../../visual-basic/language-reference/modifiers/async.md).  
  
-   `Iterator`  
  
     Opcjonalna. Zobacz [iteratora](../../../visual-basic/language-reference/modifiers/iterator.md).  
  
-   `name`  
  
     Wymagane. Nazwa procedury. Zobacz temat[Zadeklarowane nazwy elementów](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).  
  
-   `typeparamlist`  
  
     Opcjonalna. Lista parametrów typu ogólnego procedury. Zobacz [Lista typów](type-list.md).  
  
-   `parameterlist`  
  
     Opcjonalna. Lista nazwy zmiennych lokalnych reprezentującą parametry tej procedury. Zobacz [listy parametrów](parameter-list.md).  
  
-   `returntype`  
  
     Jeśli wymagane `Option Strict` jest `On`. Typ danych wartości zwracanej przez tę procedurę.  
  
-   `Implements`  
  
     Opcjonalna. Wskazuje, że ta procedura implementuje co najmniej jeden `Function` procedury, każdy z nich zdefiniowane w interfejsie zaimplementowany przez klasę lub strukturę zawierającego tę procedurę. Zobacz [Implements, instrukcja](implements-statement.md).  
  
-   `implementslist`  
  
     Jeśli wymagane `Implements` podano. Lista `Function` procedury są wdrożone.  
  
     `implementedprocedure [ , implementedprocedure ... ]`  
  
     Każdy `implementedprocedure` ma następujące składni i części:  
  
     `interface.definedname`  
  
    |Część|Opis|  
    |---|---|  
    |`interface`|Wymagane. Nazwa interfejsu implementowany przez tej procedury zawierający klasy lub struktury.|  
    |`definedname`|Wymagane. Nazwa, za pomocą którego procedura jest zdefiniowany w `interface`.|  
  
-   `Handles`  
  
     Opcjonalna. Wskazuje, że ta procedura może obsługiwać jeden lub więcej określonych zdarzeń. Zobacz [obsługuje](handles-clause.md).  
  
-   `eventlist`  
  
     Jeśli wymagane `Handles` podano. Lista zdarzeń, które obsługuje tę procedurę.  
  
     `eventspecifier [ , eventspecifier ... ]`  
  
     Każdy `eventspecifier` ma następujące składni i części:  
  
     `eventvariable.event`  
  
    |Część|Opis|  
    |---|---|  
    |`eventvariable`|Wymagane. Zmienna obiektu zadeklarowane z typem danych klasy lub struktury, która wywołuje zdarzenia.|  
    |`event`|Wymagane. Nazwa zdarzenia, które obsługuje tę procedurę.|  
  
-   `statements`  
  
     Opcjonalna. Blok instrukcji do wykonania w ramach tej procedury.  
  
-   `End Function`  
  
     Kończy definicję tej procedury.  
  
## <a name="remarks"></a>Uwagi  
 Cały kod wykonywalny musi być wewnątrz procedury. Każdej procedury z kolei jest zadeklarowana w obrębie klasy, struktury lub modułu, który jest określany jako zawierającego klasy, struktury lub modułu.  
  
 Aby zwrócić wartości do kodu wywołującego, użyj `Function` procedury; w przeciwnym razie użyj `Sub` procedury.  
  
## <a name="defining-a-function"></a>Definiowanie funkcji  
 Można zdefiniować `Function` procedury tylko na poziomie modułu. W związku z tym kontekst deklaracji funkcji musi być klasy, struktury, modułem lub interfejsem, a nie może być plikiem źródłowym, przestrzeń nazw, procedurę lub blok. Aby uzyskać więcej informacji, zobacz [Kontekst deklaracji i domyślne poziomy dostępu](declaration-contexts-and-default-access-levels.md).  
  
 `Function` Domyślnie procedur dostępu publicznego. Poziomy dostępu można zmienić za pomocą modyfikatorów dostępu.  
  
 A `Function` procedury można zadeklarować typ danych wartości, która zwraca procedury. Można określić dowolny typ danych lub nazwa wyliczenia, strukturę, klasę lub interfejs. Jeśli nie określisz `returntype` parametr, procedura zwraca `Object`.  
  
 Jeśli ta procedura wykorzystuje `Implements` — słowo kluczowe, zawierający klasy lub struktury, również musi mieć `Implements` instrukcji, który następuje bezpośrednio po jego `Class` lub `Structure` instrukcji. `Implements` Instrukcja musi zawierać każdego interfejsu, który jest określony w `implementslist`. Jednak nazwy za pomocą którego interfejs definiuje `Function` (w `definedname`) nie musi być zgodna z nazwą w tej procedurze (w `name`).  
  
> [!NOTE]
>  Można użyć wyrażenia lambda do definiowania wbudowane wyrażenia funkcji. Aby uzyskać więcej informacji, zobacz [Function — wyrażenie](../../../visual-basic/language-reference/operators/function-expression.md) i [wyrażeń Lambda](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md).  
  
## <a name="returning-from-a-function"></a>Zwracanie z funkcji  
 Gdy `Function` procedury zwraca do kodu wywołującego, wykonywanie jest kontynuowane przy użyciu instrukcji, która następuje po instrukcji, która wywołuje procedurę.  
  
 Aby zwrócić wartości z funkcji, można przypisać wartość do nazwy funkcji lub uwzględnić go w `Return` instrukcji.  
  
 `Return` Instrukcji jednocześnie przypisuje wartość zwracaną i kończy działanie funkcji, co ilustruje poniższy przykład.  
  
 [!code-vb[VbVbalrStatements#24](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/function-statement_1.vb)]  
  
 Poniższy przykład przypisuje wartość zwracaną do nazwy funkcji `myFunction` , a następnie używa `Exit Function` instrukcji, aby zwrócić.  
  
 [!code-vb[VbVbalrStatements#23](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/function-statement_2.vb)]  
  
 `Exit Function` i `Return` instrukcji powodują natychmiastowego wyjścia z `Function` procedury. Dowolną liczbę `Exit Function` i `Return` instrukcji może występować w dowolnym miejscu w ramach procedury i możesz mieszać `Exit Function` i `Return` instrukcji.  
  
 Jeśli używasz `Exit Function` bez przypisywania wartości do `name`, procedura zwraca wartość domyślna dla typu danych, który jest określony w `returntype`. Jeśli `returntype` nie jest określona, zwraca procedury `Nothing`, która jest wartością domyślną dla `Object`.  
  
## <a name="calling-a-function"></a>Wywołanie funkcji  
 Należy wywołać `Function` procedury przy użyciu nazwy procedury, następuje lista argumentów w nawiasach w wyrażeniu. Nawiasy można pominąć, tylko wtedy, gdy nie udostępnia żadnych argumentów. Jednak kod jest bardziej czytelny, jeśli zawsze zawierać nawiasy.  
  
 Należy wywołać `Function` procedury taki sam sposób, że wywołać każdą bibliotekę funkcji, takich jak `Sqrt`, `Cos`, lub `ChrW`.  
  
 Można również wywołać funkcję za pomocą `Call` — słowo kluczowe. W takim przypadku zwracana wartość jest ignorowana. Korzystanie z `Call` — słowo kluczowe nie jest zalecane w większości przypadków. Aby uzyskać więcej informacji, zobacz [instrukcji Call](call-statement.md).  
  
 Visual Basic Reorganizuje czasami wyrażenia arytmetyczne, aby zwiększyć wydajność wewnętrznej. Z tego powodu nie można używać `Function` procedury w wyrażeniach arytmetycznych funkcja zmianę wartości zmiennych w jednym wyrażeniu.  
  
## <a name="async-functions"></a>Funkcje asynchroniczne  
 *Async* pozwala wywoływać funkcje asynchroniczne bez za pomocą jawnego wywołania zwrotne lub ręcznego podziału kodu na wielu funkcji lub wyrażenia lambda.  
  
 Po oznaczeniu funkcji z [Async](../../../visual-basic/language-reference/modifiers/async.md) modyfikator, można użyć [Await](../../../visual-basic/language-reference/operators/await-operator.md) operatora w funkcji. Gdy kontrola osiąga `Await` wyrażenia w `Async` funkcji, sterowanie powraca do obiektu wywołującego, a postęp w funkcji jest wstrzymana, dopóki nie zakończy się oczekiwane zadanie. Kiedy zadanie zostanie ukończone, wykonanie można wznowić w funkcji.  
  
> [!NOTE]
>  `Async` Po albo napotka pierwszego oczekiwane obiekt, który nie został jeszcze ukończony procedury powraca do obiektu wywołującego lub pobiera na końcu `Async` procedury, w zależności od tego nastąpi pierwsze.  
  
 `Async` Funkcji może mieć typ zwracany <xref:System.Threading.Tasks.Task%601> lub <xref:System.Threading.Tasks.Task>. Przykładem `Async` funkcję, która ma typ zwracany <xref:System.Threading.Tasks.Task%601> znajduje się poniżej.  
  
 `Async` Funkcji nie może deklarować [ByRef](../../../visual-basic/language-reference/modifiers/byref.md) parametrów.  
  
 A [Sub — instrukcja](sub-statement.md) również mogą być oznaczone `Async` modyfikator. To jest używany głównie dla procedury obsługi zdarzeń, których nie można zwrócić wartość. `Async` `Sub` Procedura nie może być oczekiwany, a obiekt wywołujący `Async` `Sub` procedura nie może przechwytywać wyjątki wyrzucane przez `Sub` procedury.  
  
 Aby uzyskać więcej informacji na temat `Async` funkcji, zobacz [Asynchronous Programming with Async and Await](../../../visual-basic/programming-guide/concepts/async/index.md), [Control Flow in Async Programs](../../../visual-basic/programming-guide/concepts/async/control-flow-in-async-programs.md), i [Async Return Types](../../../visual-basic/programming-guide/concepts/async/async-return-types.md).  
  
## <a name="iterator-functions"></a>Funkcje iteratora  
 *Iteratora* funkcja wykonuje niestandardowych iteracji w kolekcji, takie jak listy lub tablicy. Używa funkcji iteratora [uzyskanie](yield-statement.md) instrukcja zwraca każdy element w danym momencie. Gdy [uzyskanie](yield-statement.md) osiągnięciu instrukcji zapamiętanych bieżąca lokalizacja w kodzie. Wykonanie jest uruchamiane ponownie z tej lokalizacji w następnym razem, gdy zostanie wywołana funkcja iteratora.  
  
 Wywołujesz iterację z poziomu kodu klienta przy użyciu [For Each... Następny](for-each-next-statement.md) instrukcji.  
  
 Może być zwracany typ funkcji iteratora <xref:System.Collections.IEnumerable>, <xref:System.Collections.Generic.IEnumerable%601>, <xref:System.Collections.IEnumerator>, lub <xref:System.Collections.Generic.IEnumerator%601>.  
  
 Aby uzyskać więcej informacji, zobacz [Iteratory](../../programming-guide/concepts/iterators.md).  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie użyto `Function` instrukcję, aby zadeklarować nazwę, parametry i kod, który tworzą treści `Function` procedury. `ParamArray` Modyfikator umożliwia funkcji zaakceptować zmienną liczbę argumentów.  
  
 [!code-vb[VbVbalrStatements#25](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/function-statement_3.vb)]  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia wywoływanie funkcji zadeklarowanej w poprzednim przykładzie.  
  
 [!code-vb[VbVbalrStatements#26](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/function-statement_4.vb)]  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie `DelayAsync` jest `Async` `Function` zawierający typ zwracany <xref:System.Threading.Tasks.Task%601>. `DelayAsync` ma `Return` instrukcję, która zwraca liczbę całkowitą. W związku z tym funkcja deklaracji `DelayAsync` musi mieć typ zwracany `Task(Of Integer)`. Ponieważ typem zwracanym jest `Task(Of Integer)`, oceny `Await` wyrażenia w `DoSomethingAsync` tworzy liczbą całkowitą. Zostało to przedstawione w tej instrukcji: `Dim result As Integer = Await delayTask`.  
  
 `startButton_Click` Procedura to przykład `Async Sub` procedury. Ponieważ `DoSomethingAsync` jest `Async` funkcji, zadanie do wywołań `DoSomethingAsync` musi być oczekiwana, tak jak pokazano w następującej instrukcji: `Await DoSomethingAsync()`. `startButton_Click` `Sub` Procedury muszą być zdefiniowane przy użyciu `Async` modyfikator ponieważ ma ona `Await` wyrażenia.  
  
 [!code-vb[csAsyncMethod#1](../../../csharp/programming-guide/classes-and-structs/codesnippet/VisualBasic/function-statement_5.vb)]  
  
## <a name="see-also"></a>Zobacz też  
 [Sub, instrukcja](sub-statement.md)  
 [Procedury funkcji](../../../visual-basic/programming-guide/language-features/procedures/function-procedures.md)  
 [Lista parametrów](parameter-list.md)  
 [Dim, instrukcja](dim-statement.md)  
 [Call, instrukcja](call-statement.md)  
 [z](of-clause.md)  
 [Tablice parametrów](../../../visual-basic/programming-guide/language-features/procedures/parameter-arrays.md)  
 [Instrukcje: używanie klasy ogólnej](../../../visual-basic/programming-guide/language-features/data-types/how-to-use-a-generic-class.md)  
 [Rozwiązywanie problemów z procedurami](../../../visual-basic/programming-guide/language-features/procedures/troubleshooting-procedures.md)  
 [Wyrażenia lambda](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)  
 [Function, wyrażenie](../../../visual-basic/language-reference/operators/function-expression.md)
