---
title: "Function — Instrukcja (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.Function
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
caps.latest.revision: "62"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 52e9210f9e715b6055e6ed199ef1aa4b919c6dd6
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
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
  
     Opcjonalny. Zobacz [listę atrybutów](attribute-list.md).  
  
-   `accessmodifier`  
  
     Opcjonalny. Może to być jedna z następujących czynności:  
  
    -   [Public](../../../visual-basic/language-reference/modifiers/public.md)  
  
    -   [Protected](../../../visual-basic/language-reference/modifiers/protected.md)  
  
    -   [Friend](../../../visual-basic/language-reference/modifiers/friend.md)  
  
    -   [Private](../../../visual-basic/language-reference/modifiers/private.md)  
  
    -   `Protected Friend`  
  
     Zobacz [poziomy w języku Visual Basic dostępu](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).  
  
-   `proceduremodifiers`  
  
     Opcjonalny. Może to być jedna z następujących czynności:  
  
    -   [Overloads](../../../visual-basic/language-reference/modifiers/overloads.md)  
  
    -   [Overrides](../../../visual-basic/language-reference/modifiers/overrides.md)  
  
    -   [Overridable](../../../visual-basic/language-reference/modifiers/overridable.md)  
  
    -   [NotOverridable](../../../visual-basic/language-reference/modifiers/notoverridable.md)  
  
    -   [MustOverride](../../../visual-basic/language-reference/modifiers/mustoverride.md)  
  
    -   `MustOverride Overrides`  
  
    -   `NotOverridable Overrides`  
  
-   `Shared`  
  
     Opcjonalny. Zobacz [udostępnionych](../../../visual-basic/language-reference/modifiers/shared.md).  
  
-   `Shadows`  
  
     Opcjonalny. Zobacz [Shadows](../../../visual-basic/language-reference/modifiers/shadows.md).  
  
-   `Async`  
  
     Opcjonalny. Zobacz [Async](../../../visual-basic/language-reference/modifiers/async.md).  
  
-   `Iterator`  
  
     Opcjonalny. Zobacz [Iterator](../../../visual-basic/language-reference/modifiers/iterator.md).  
  
-   `name`  
  
     Wymagany. Nazwa procedury. Zobacz [zadeklarowane nazwy elementów](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).  
  
-   `typeparamlist`  
  
     Opcjonalny. Lista parametrów typu ogólnego procedurę. Zobacz [typu listy](type-list.md).  
  
-   `parameterlist`  
  
     Opcjonalny. Lista nazwy zmiennych lokalnych reprezentujący parametry tej procedury. Zobacz [listy parametrów](parameter-list.md).  
  
-   `returntype`  
  
     Jeśli wymagane `Option Strict` jest `On`. Typ danych wartości zwracanej przez tę procedurę.  
  
-   `Implements`  
  
     Opcjonalny. Wskazuje, że ta procedura implementuje co najmniej jeden `Function` procedur, każdą z nich zdefiniowane w interfejsie zaimplementowany przez klasę lub strukturę zawierającego tę procedurę. Zobacz [implementuje instrukcji](implements-statement.md).  
  
-   `implementslist`  
  
     Jeśli wymagane `Implements` podano. Lista `Function` procedury implementowana.  
  
     `implementedprocedure [ , implementedprocedure ... ]`  
  
     Każdy `implementedprocedure` ma następujące składni i części:  
  
     `interface.definedname`  
  
    |Część|Opis|  
    |---|---|  
    |`interface`|Wymagany. Nazwa interfejsu implementowanego przez tej procedury zawierający klasy lub struktury.|  
    |`definedname`|Wymagany. Za pomocą którego procedura została określona w nazwie `interface`.|  
  
-   `Handles`  
  
     Opcjonalny. Wskazuje, że ta procedura może obsługiwać jeden lub więcej określonych zdarzeń. Zobacz [obsługuje](handles-clause.md).  
  
-   `eventlist`  
  
     Jeśli wymagane `Handles` podano. Lista zdarzeń, które obsługuje tę procedurę.  
  
     `eventspecifier [ , eventspecifier ... ]`  
  
     Każdy `eventspecifier` ma następujące składni i części:  
  
     `eventvariable.event`  
  
    |Część|Opis|  
    |---|---|  
    |`eventvariable`|Wymagany. Zmienna obiektu zadeklarowane z typem danych klasy lub struktury, który wywołuje zdarzenie.|  
    |`event`|Wymagany. Nazwa zdarzenia, które obsługuje tę procedurę.|  
  
-   `statements`  
  
     Opcjonalny. Blok instrukcji do wykonania w ramach tej procedury.  
  
-   `End Function`  
  
     Kończy definicję tej procedury.  
  
## <a name="remarks"></a>Uwagi  
 Cały kod wykonywalny musi znajdować się w procedurze. Każdej procedury z kolei jest zadeklarowany w obrębie klasy, struktury lub moduł, który jest określany jako zawierający klasy, struktury lub modułu.  
  
 Aby zwrócić wartość do wywołującego kodu, użyj `Function` procedury; w przeciwnym razie użyj `Sub` procedury.  
  
## <a name="defining-a-function"></a>Definiowanie funkcji  
 Można zdefiniować `Function` procedury tylko na poziomie modułu. W związku z tym kontekście deklaracji funkcji musi być klasą, strukturą, modułu lub interfejsu i nie może być plik źródłowy, przestrzeni nazw, procedurę lub blok. Aby uzyskać więcej informacji, zobacz [kontekst deklaracji i domyślne poziomy dostępu](declaration-contexts-and-default-access-levels.md).  
  
 `Function`Domyślnie procedur dostępu publicznego. Można dostosować ich poziomy dostępu z modyfikatorów dostępu.  
  
 A `Function` procedury mogą zadeklarować typ danych wartości, która zwraca procedury. Można określić dowolny typ danych lub nazwa wyliczenia, struktury, klasy lub interfejsu. Jeśli nie określisz `returntype` zwraca procedury parametru `Object`.  
  
 Jeśli ta procedura wykorzystuje `Implements` — słowo kluczowe, zawierające klasy lub struktury musi mieć również `Implements` instrukcji poniższą jego `Class` lub `Structure` instrukcji. `Implements` Instrukcja musi zawierać każdy interfejs, który jest określony w `implementslist`. Jednak nazwy za pomocą którego definiuje interfejs `Function` (w `definedname`) nie musi być zgodna z nazwą w tej procedurze (w `name`).  
  
> [!NOTE]
>  Wyrażenia lambda służy do definiowania wbudowane wyrażenia funkcji. Aby uzyskać więcej informacji, zobacz [wyrażenia funkcji](../../../visual-basic/language-reference/operators/function-expression.md) i [wyrażenia Lambda](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md).  
  
## <a name="returning-from-a-function"></a>Zwracanie z funkcji  
 Gdy `Function` procedura zwraca do kodu wywołującego, wykonanie będzie kontynuowane przy użyciu instrukcji następującej instrukcji, która wywołuje procedurę.  
  
 Aby zwrócić wartości z funkcji, można przypisać wartości do nazwy funkcji lub dołączyć go w `Return` instrukcji.  
  
 `Return` Instrukcji jednocześnie przypisuje wartość zwracaną i kończy działanie funkcji, jak przedstawiono na poniższym przykładzie.  
  
 [!code-vb[VbVbalrStatements#24](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/function-statement_1.vb)]  
  
 Poniższy przykład przypisuje wartość zwracaną nazwą funkcji `myFunction` , a następnie używa `Exit Function` instrukcji do zwrócenia.  
  
 [!code-vb[VbVbalrStatements#23](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/function-statement_2.vb)]  
  
 `Exit Function` i `Return` instrukcje powoduje natychmiastowe wyjście z `Function` procedury. Dowolną liczbę `Exit Function` i `Return` instrukcje mogą występować w dowolnym miejscu w procedurze, a można mieszać `Exit Function` i `Return` instrukcje.  
  
 Jeśli używasz `Exit Function` bez przypisywanie wartości do `name`, procedura zwraca wartość domyślna dla typu danych określonego w `returntype`. Jeśli `returntype` nie zostanie określona, zwraca procedury `Nothing`, która jest wartością domyślną dla `Object`.  
  
## <a name="calling-a-function"></a>Wywołanie funkcji  
 Należy wywołać `Function` procedury przy użyciu nazwę procedury, a następnie listy argumentów w nawiasach w wyrażeniu. Można pominąć nawiasów, tylko wtedy, gdy nie udostępnia żadnych argumentów. Jednak kod jest bardziej przejrzysta zawsze używać nawiasów.  
  
 Należy wywołać `Function` procedury taki sam sposób, że można wywołać żadnej biblioteki funkcji, takich jak `Sqrt`, `Cos`, lub `ChrW`.  
  
 Możesz także wywołać funkcję za pomocą `Call` — słowo kluczowe. W takim przypadku wartość zwracana jest ignorowana. Użycie `Call` — słowo kluczowe nie jest zalecana w większości przypadków. Aby uzyskać więcej informacji, zobacz [instrukcji Call](call-statement.md).  
  
 Visual Basic Reorganizuje czasami wyrażenia arytmetyczne, aby zwiększyć wydajność wewnętrznego. Z tego powodu nie można używać `Function` procedury w wyrażeniach arytmetycznych zmiany funkcji wartości zmiennych w jednym wyrażeniu.  
  
## <a name="async-functions"></a>Funkcje asynchroniczne  
 *Async* funkcja pozwala wywoływać funkcje asynchroniczne bez za pomocą jawnego wywołania zwrotne i ręcznie dzielenia kodu wielu funkcji lub wyrażenia lambda.  
  
 Po zaznaczeniu funkcji z [Async](../../../visual-basic/language-reference/modifiers/async.md) modyfikator, można użyć [Await](../../../visual-basic/language-reference/operators/await-operator.md) operatora w funkcji. Gdy kontrolować osiągnie `Await` wyrażenie w `Async` funkcji, zwraca sterowania do obiektu wywołującego i postępu w funkcji jest wstrzymana, aż do zakończenia oczekiwano zadań. Po zakończeniu zadania wykonywania można wznowić w funkcji.  
  
> [!NOTE]
>  `Async` Procedury zwraca do obiektu wywołującego po albo napotkaniu pierwszego oczekiwano obiekt, który nie został jeszcze ukończony lub pobiera na końcu `Async` procedury, w zależności od wykonane jako pierwsze.  
  
 `Async` Funkcja może mieć typ zwracany <xref:System.Threading.Tasks.Task%601> lub <xref:System.Threading.Tasks.Task>. Przykład `Async` funkcja, która ma typ zwracany <xref:System.Threading.Tasks.Task%601> podano poniżej.  
  
 `Async` Funkcji nie można zadeklarować żadnego [ByRef](../../../visual-basic/language-reference/modifiers/byref.md) parametrów.  
  
 A [Sub — instrukcja](sub-statement.md) również może być oznaczony przez `Async` modyfikator. To jest używany głównie dla programów obsługi zdarzeń, których nie można zwrócić wartość. `Async``Sub` Procedura nie jest oczekiwane oraz funkcji wywołującej `Async``Sub` procedury nie przechwytuje wyjątków, które są generowane przez `Sub` procedury.  
  
 Aby uzyskać więcej informacji na temat `Async` funkcji, zobacz [programowanie asynchroniczne z Async i Await](../../../visual-basic/programming-guide/concepts/async/index.md), [przepływ sterowania w aplikacjach asynchronicznych](../../../visual-basic/programming-guide/concepts/async/control-flow-in-async-programs.md), i [Async zwracać typów](../../../visual-basic/programming-guide/concepts/async/async-return-types.md).  
  
## <a name="iterator-functions"></a>Funkcje iteracyjne  
 *Iterator* funkcja wykonuje niestandardowych iteracji w kolekcji, takie jak listy lub tablicy. Korzysta z funkcji iteracyjnej [Yield](yield-statement.md) instrukcji, aby zwracany był każdy element jednym naraz. Gdy [Yield](yield-statement.md) osiągnięciu instrukcji zapamiętanych bieżącej lokalizacji w kodzie. Wykonanie jest uruchamiany ponownie z tej lokalizacji w następnym razem, gdy zostanie wywołana funkcja iteratora.  
  
 Wywołaj iteratora z kodu klienta przy użyciu [For Each... Następny](for-each-next-statement.md) instrukcji.  
  
 Może być zwracany typ funkcji iteracyjnej <xref:System.Collections.IEnumerable>, <xref:System.Collections.Generic.IEnumerable%601>, <xref:System.Collections.IEnumerator>, lub <xref:System.Collections.Generic.IEnumerator%601>.  
  
 Aby uzyskać więcej informacji, zobacz [Iteratory](../../programming-guide/concepts/iterators.md).  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie użyto `Function` instrukcji, aby zadeklarować nazwę, parametry i kod, który tworzą treści `Function` procedury. `ParamArray` Modyfikator włącza funkcję zaakceptować zmienną liczbę argumentów.  
  
 [!code-vb[VbVbalrStatements#25](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/function-statement_3.vb)]  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia wywoływanie funkcji zadeklarowany w poprzednim przykładzie.  
  
 [!code-vb[VbVbalrStatements#26](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/function-statement_4.vb)]  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie `DelayAsync` jest `Async``Function` mający typ zwracany <xref:System.Threading.Tasks.Task%601>. `DelayAsync`ma `Return` instrukcji, która zwraca liczbę całkowitą. W związku z tym funkcja deklaracja `DelayAsync` musi mieć typ zwracany `Task(Of Integer)`. Ponieważ typ zwracany jest `Task(Of Integer)`, oceny `Await` wyrażenie w `DoSomethingAsync` tworzy liczbą całkowitą. Zostało to przedstawione w tej instrukcji: `Dim result As Integer = Await delayTask`.  
  
 `startButton_Click` Procedura jest przykładem `Async Sub` procedury. Ponieważ `DoSomethingAsync` jest `Async` funkcji, zadanie dla wywołania `DoSomethingAsync` musi być oczekiwane, jak pokazano następująca instrukcja: `Await DoSomethingAsync()`. `startButton_Click``Sub` Procedury musi być zdefiniowany za pomocą `Async` modyfikator ponieważ ma ona `Await` wyrażenia.  
  
 [!code-vb[csAsyncMethod#1](../../../csharp/programming-guide/classes-and-structs/codesnippet/VisualBasic/function-statement_5.vb)]  
  
## <a name="see-also"></a>Zobacz też  
 [Sub, instrukcja](sub-statement.md)  
 [Procedury funkcji](../../../visual-basic/programming-guide/language-features/procedures/function-procedures.md)  
 [Lista parametrów](parameter-list.md)  
 [Dim, instrukcja](dim-statement.md)  
 [Call, instrukcja](call-statement.md)  
 [Z](of-clause.md)  
 [Tablice parametrów](../../../visual-basic/programming-guide/language-features/procedures/parameter-arrays.md)  
 [Instrukcje: używanie klasy ogólnej](../../../visual-basic/programming-guide/language-features/data-types/how-to-use-a-generic-class.md)  
 [Rozwiązywanie problemów z procedurami](../../../visual-basic/programming-guide/language-features/procedures/troubleshooting-procedures.md)  
 [Wyrażenia lambda](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)  
 [Function, wyrażenie](../../../visual-basic/language-reference/operators/function-expression.md)
