---
title: "Lambda — Wyrażenia (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.LambdaFunction
helpviewer_keywords:
- functions [Visual Basic], lambda expressions
- lambda expressions [Visual Basic]
- expressions [Visual Basic], lambda
- inline functions [Visual Basic]
ms.assetid: 137064b0-3928-4bfa-ba71-c3f9cbd951e2
caps.latest.revision: "52"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 69ac88d295420277e99058d0f80a5ae1c2ce2e39
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="lambda-expressions-visual-basic"></a>Lambda — Wyrażenia (Visual Basic)
A *wyrażenia lambda* jest funkcją lub podprocedury bez nazwy, który może służyć wszędzie tam, gdzie delegata jest prawidłowy. Wyrażenia lambda można używać funkcji lub procedury i może być jednym lub wielu linii. Wyrażenie lambda, można przekazać wartości z bieżącego zakresu.  
  
> [!NOTE]
>  `RemoveHandler` Instrukcja jest wyjątek. Nie można przekazać wyrażenia lambda w dla parametru delegowanego `RemoveHandler`.  
  
 Tworzenie wyrażenia lambda za pomocą `Function` lub `Sub` — słowo kluczowe, tak samo jak tworzenie standardowych funkcji lub procedury. Jednak wyrażenia lambda znajdują się w instrukcji.  
  
 Poniższy przykład jest zwiększa jej argument, który zwraca wartość wyrażenia lambda. W przykładzie zarówno jeden wiersz i wielowierszowe składnia wyrażenia lambda dla funkcji.  
  
 [!code-vb[VbVbalrLambdas#14](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/lambda-expressions_1.vb)]  
  
 Poniższy przykład jest wyrażenie lambda, które zapisuje wartość do konsoli. W przykładzie zarówno jeden wiersz i wielowierszowe składnia wyrażenia lambda dla procedury.  
  
 [!code-vb[VbVbalrLambdas#15](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/lambda-expressions_2.vb)]  
  
 Zwróć uwagę, że w poprzednich przykładach wyrażenia lambda są przypisane do nazwy zmiennej. Odwołując się do zmiennej, można wywołać wyrażenia lambda. Można również deklarować i wywołać wyrażenia lambda w tym samym czasie, jak pokazano w poniższym przykładzie.  
  
 [!code-vb[VbVbalrLambdas#3](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/lambda-expressions_3.vb)]  
  
 Wyrażenia lambda, może być zwracany jako wartość wywołania funkcji (jak to pokazano w przykładzie w [kontekstu](#context) później w tym temacie), lub przekazany jako argument do parametru, który przyjmuje typ delegata, jak pokazano w poniższym przykład.  
  
 [!code-vb[VbVbalrLambdas#8](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/lambda-expressions_4.vb)]  
  
## <a name="lambda-expression-syntax"></a>Składnia wyrażenia lambda  
 Składnia wyrażenia lambda jest podobny do standardowych funkcji lub procedury. Różnice są następujące:  
  
-   Wyrażenia lambda nie ma nazwy.  
  
-   Wyrażenia lambda nie może mieć modyfikatorów, takich jak `Overloads` lub `Overrides`.  
  
-   Nie używaj funkcji lambda jednowierszowego `As` klauzuli, aby określić typ zwracany. Zamiast tego typu jest wywnioskowany na podstawie wartości, która daje w wyniku treści wyrażenia lambda. Na przykład, jeśli treść wyrażenia lambda jest `cust.City = "London"`, jego typem zwracanym jest `Boolean`.  
  
-   W wielowierszowym lambda funkcji, można określić zwracanego typu przy użyciu `As` klauzuli lub Pomiń `As` klauzuli tak, aby zwracany typ jest wywnioskowany. Gdy `As` klauzuli pominięto dla funkcji lambda wiele wierszy, zwracany typ jest wywnioskowany dominującą typem ze wszystkich `Return` instrukcje w funkcji lambda wiele wierszy. *Typu dominującą* jest typem unikatowy poszerzyć do innych typów. Nie można określić tego typu unikatowy, ten typ dominującej nie jest unikatowy typ, który wszystkie typy w tablicy można ograniczyć do. Jeśli żadna z tych typów unikatowy nie można ustalić, jest typu dominującą `Object`. W tym przypadku jeśli `Option Strict` ma ustawioną wartość `On`, wystąpi błąd kompilatora.  
  
     Na przykład, jeśli wyrażenia dostarczony do `Return` instrukcji zawierają wartości typu `Integer`, `Long`, i `Double`, wynikowy tablicy jest typu `Double`. Zarówno `Integer` i `Long` rozszerzane `Double` i tylko `Double`. W związku z tym `Double` jest dominującą typu. Aby uzyskać więcej informacji, zobacz [rozszerzanie i zwężanie konwersji](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md).  
  
-   Treść funkcji pojedynczej linii musi być wyrażenie zwracające wartość, nie instrukcję. Brak nie `Return` instrukcji dla funkcji jeden wiersz. Wartość zwrócona przez funkcję jeden wiersz jest wartość wyrażenia w treści funkcji.  
  
-   Treść podprocedury jeden wiersz musi być instrukcją jeden wiersz.  
  
-   Nie dołączaj jednowierszowego funkcje i podprocedury `End Function` lub `End Sub` instrukcji.  
  
-   Można określić typ danych parametru wyrażenia lambda za pomocą `As` można wywnioskować — słowo kluczowe lub typ danych parametru. Albo wszystkie parametry muszą określono można wywnioskować typów danych lub wszystkich.  
  
-   `Optional`i `Paramarray` parametry są niedozwolone.  
  
-   Parametry ogólne są niedozwolone.  
  
## <a name="async-lambdas"></a>Lambdy asynchroniczne  
 Można jednak łatwo tworzyć wyrażenia lambda i instrukcje zawierające przetwarzania asynchronicznego przy użyciu [Async](../../../../visual-basic/language-reference/modifiers/async.md) i [operatora Await](../../../../visual-basic/language-reference/operators/await-operator.md) słów kluczowych. Na przykład w poniższym przykładzie formularzy systemu Windows zawiera program obsługi zdarzeń, który wywołuje i oczekujące na metody asynchronicznej `ExampleMethodAsync`.  
  
```vb  
Public Class Form1  
  
    Async Sub Button1_Click(sender As Object, e As EventArgs) Handles Button1.Click  
        ' ExampleMethodAsync returns a Task.  
        Await ExampleMethodAsync()  
        TextBox1.Text = vbCrLf & "Control returned to button1_Click."  
    End Sub  
  
    Async Function ExampleMethodAsync() As Task  
        ' The following line simulates a task-returning asynchronous process.  
        Await Task.Delay(1000)  
    End Function  
  
End Class  
```  
  
 Można dodać tej procedury obsługi zdarzeń za pomocą asynchroniczne lambda w [AddHandler — instrukcja](../../../../visual-basic/language-reference/statements/addhandler-statement.md). Aby dodać ten program obsługi, Dodaj `Async` modyfikator przed listy parametrów lambda, jak przedstawiono na poniższym przykładzie.  
  
```vb  
Public Class Form1  
  
    Private Sub Form1_Load(sender As Object, e As EventArgs) Handles MyBase.Load  
        AddHandler Button1.Click,   
            Async Sub(sender1, e1)  
                ' ExampleMethodAsync returns a Task.  
                Await ExampleMethodAsync()  
                TextBox1.Text = vbCrLf & "Control returned to Button1_ Click."  
            End Sub  
    End Sub  
  
    Async Function ExampleMethodAsync() As Task  
        ' The following line simulates a task-returning asynchronous process.  
        Await Task.Delay(1000)  
    End Function  
  
End Class  
```  
  
 Aby uzyskać więcej informacji o sposobie tworzenia i używania metody asynchroniczne, zobacz [programowanie asynchroniczne z Async i Await](../../../../visual-basic/programming-guide/concepts/async/index.md).  
  
##  <a name="context"></a>Kontekst  
 Wyrażenia lambda udostępnia kontekst zakresu, w którym jest zdefiniowany. Ma te same prawa dostępu jako dowolny kod napisany w zawierający zakres. Obejmuje to dostęp do zmiennych Członkowskich, funkcje i subskrypcji, `Me`i parametrów i zmiennych lokalnych w zawierającym zasięgu.  
  
 Dostęp do zmiennych lokalnych i parametrów w zakresie zawierającym mogą wykraczać poza okres istnienia tego zakresu. Tak długo, jak delegata odwołujących się do wyrażenia lambda nie jest dostępny dla wyrzucanie elementów bezużytecznych, dostęp do zmiennych w oryginalne środowisko jest przechowywane. W poniższym przykładzie zmienna `target` jest lokalny dla `makeTheGame`, metody, w którym wyrażenie lambda `playTheGame` jest zdefiniowany. Należy pamiętać, że wyrażenie lambda zwrócony przypisane do `takeAGuess` w `Main`, ma nadal dostęp do zmiennej lokalnej `target`.  
  
 [!code-vb[VbVbalrLambdas#12](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/lambda-expressions_5.vb)]  
  
 W poniższym przykładzie pokazano szeroką gamę praw dostępu wyrażenia lambda zagnieżdżonych. Po wykonaniu wyrażenia lambda zwrócony z `Main` jako `aDel`, uzyskuje dostęp do tych elementów:  
  
-   To pole klasy, w którym jest zdefiniowany:`aField`  
  
-   Właściwość klasy, w którym jest zdefiniowana:`aProp`  
  
-   Parametr metody `functionWithNestedLambda`, w którym jest zdefiniowana:`level1`  
  
-   Zmienna lokalna o `functionWithNestedLambda`:`localVar`  
  
-   Parametr wyrażenia lambda, w którym jest zagnieżdżony:`level2`  
  
 [!code-vb[VbVbalrLambdas#9](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/lambda-expressions_6.vb)]  
  
## <a name="converting-to-a-delegate-type"></a>Konwertowanie na typ delegowany  
 Wyrażenia lambda można niejawnie przekonwertować na typ delegata zgodne. Aby uzyskać informacje ogólne wymagania dotyczące zgodności, zobacz [swobodna konwersja delegatów](../../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md). Na przykład poniższy przykładowy kod przedstawia wyrażenie lambda, które jawnie konwertuje `Func(Of Integer, Boolean)` lub zgodnego podpisu delegata.  
  
 [!code-vb[VbVbalrLambdas#16](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/lambda-expressions_7.vb)]  
  
 Poniższy przykład kodu pokazuje Wyrażenie lambda, które jawnie konwertuje `Sub(Of Double, String, Double)` lub zgodnego podpisu delegata.  
  
 [!code-vb[VbVbalrLambdas#23](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/lambda-expressions_8.vb)]  
  
 Podczas przypisywania do delegatów wyrażenia lambda lub przekazywane jako argumenty do procedur można określić nazwy parametrów, ale pominąć typy danych, umożliwiając typy pobrane z obiektem delegowanym.  
  
## <a name="examples"></a>Przykłady  
  
-   W poniższym przykładzie zdefiniowano wyrażenia lambda, która zwraca `True` Jeśli argument NULL ma przypisaną wartość i `False` jeśli jego wartość wynosi `Nothing`.  
  
     [!code-vb[VbVbalrLambdas#4](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/lambda-expressions_9.vb)]  
  
-   Poniższy przykład definiuje wyrażenie lambda, które zwraca indeks ostatniego elementu w tablicy.  
  
     [!code-vb[VbVbalrLambdas#5](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/lambda-expressions_10.vb)]  
  
## <a name="see-also"></a>Zobacz też  
 [Procedury](./index.md)  
 [Wprowadzenie do LINQ w Visual Basic](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)  
 [Obiekty delegowane](../../../../visual-basic/programming-guide/language-features/delegates/index.md)  
 [Function — instrukcja](../../../../visual-basic/language-reference/statements/function-statement.md)  
 [Sub — instrukcja](../../../../visual-basic/language-reference/statements/sub-statement.md)  
 [Typy dopuszczające wartości zerowe wartości](../../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)  
 [Porady: przekazywanie procedur do innej procedury w Visual Basic](../../../../visual-basic/programming-guide/language-features/delegates/how-to-pass-procedures-to-another-procedure.md)  
 [Porady: Tworzenie wyrażenia Lambda](./how-to-create-a-lambda-expression.md)  
 [Swobodna konwersja delegatów](../../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md)
