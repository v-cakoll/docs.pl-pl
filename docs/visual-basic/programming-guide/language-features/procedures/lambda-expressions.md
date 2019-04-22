---
title: Lambda — Wyrażenia (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.LambdaFunction
helpviewer_keywords:
- functions [Visual Basic], lambda expressions
- lambda expressions [Visual Basic]
- expressions [Visual Basic], lambda
- inline functions [Visual Basic]
ms.assetid: 137064b0-3928-4bfa-ba71-c3f9cbd951e2
ms.openlocfilehash: c43739e098a91d54d300fa7074d1563da179c0e9
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "58832115"
---
# <a name="lambda-expressions-visual-basic"></a>Lambda — Wyrażenia (Visual Basic)
A *wyrażenia lambda* jest funkcji lub podprocedury bez nazwy, który może służyć wszędzie tam, gdzie obiekt delegowany jest prawidłowy. Wyrażenia lambda może być funkcji lub podprocedury i może być w jednym lub wielu linii. Wyrażenie lambda można przekazać wartości z bieżącego zakresu.  
  
> [!NOTE]
>  `RemoveHandler` Instrukcja jest wyjątek. Nie można przekazać wyrażenia lambda w parametrze delegata `RemoveHandler`.  
  
 Tworzenie wyrażenia lambda przy użyciu `Function` lub `Sub` — słowo kluczowe, podobnie jak tworzenie standardowej funkcji lub podprocedury. Jednak wyrażenia lambda są uwzględnione w instrukcji.  
  
 Poniższy przykład jest wyrażenie lambda, która zwiększa jej argument i zwraca wartość. W przykładzie pokazano oba jeden wiersz i wielowierszowe składnia wyrażenia lambda dla funkcji.  
  
 [!code-vb[VbVbalrLambdas#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#14)]  
  
 Poniższy przykład jest wyrażenie lambda, która zapisuje wartości do konsoli. W przykładzie pokazano oba jeden wiersz i wielowierszowe składnia wyrażenia lambda do procedurę.  
  
 [!code-vb[VbVbalrLambdas#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#15)]  
  
 Należy zauważyć, że w poprzednich przykładach wyrażenia lambda są przypisane do nazwy zmiennej. Zawsze, gdy odwołujesz się do zmiennej, można wywołać wyrażenia lambda. Można również zadeklarować i wywołać Wyrażenie lambda, w tym samym czasie, jak pokazano w poniższym przykładzie.  
  
 [!code-vb[VbVbalrLambdas#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#3)]  
  
 Wyrażenia lambda mogą być zwracane jako wartość wywołania funkcji (jak pokazano w przykładzie w [kontekstu](#context) w dalszej części tego tematu), lub przekazany jako argument do parametru, która przyjmuje typ delegata, jak pokazano w poniższym przykład.  
  
 [!code-vb[VbVbalrLambdas#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class2.vb#8)]  
  
## <a name="lambda-expression-syntax"></a>Składnia wyrażenia lambda  
 Składnia wyrażenia lambda przypomina standardowej funkcji lub podprocedury. Różnice są następujące:  
  
-   Wyrażenie lambda nie ma nazwy.  
  
-   Wyrażenia lambda nie może mieć modyfikatorów, takich jak `Overloads` lub `Overrides`.  
  
-   Nie należy używać funkcji lambda jednowierszowego `As` klauzuli, aby określić typ zwracany. Zamiast tego typ jest wnioskowany z wartości, która daje w wyniku treść wyrażenia lambda. Na przykład, jeśli treść wyrażenia lambda jest `cust.City = "London"`, jego typem zwracanym jest `Boolean`.  
  
-   W przypadku funkcji lambda wielowierszowe można określić typ zwracany za pomocą `As` klauzuli lub Pomiń `As` klauzuli tak, aby zwracany typ jest wnioskowany. Gdy `As` klauzuli zostanie pominięty dla funkcji lambda wielowierszowego, zwracany typ jest wnioskowany jako typ dominujący ze wszystkich `Return` instrukcji w funkcji lambda wiele wierszy. *Typ dominujący* to unikatowy typ, który poszerzyć do innych typów. Jeżeli nie można ustalić tego typu unikatowego, Typ dominujący to unikatowy typ, który można zawęzić wszystkie typy w tablicy. Jeśli żadna z tych typów unikatowych nie można ustalić, typem dominującym jest `Object`. W takim przypadku `Option Strict` ustawiono `On`, występuje błąd kompilatora.  
  
     Na przykład, jeśli wyrażenie dostarczone do `Return` instrukcji zawierają wartości typu `Integer`, `Long`, i `Double`, tablica wynikowa jest typu `Double`. Zarówno `Integer` i `Long` mogą zostać poszerzone do `Double` i tylko `Double`. W związku z tym `Double` jest typem dominującym. Aby uzyskać więcej informacji, zobacz [rozszerzanie i zwężanie konwersji](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md).  
  
-   Treść funkcji pojedynczej linii musi być wyrażenie zwracające wartość nie instrukcję. Istnieje nie `Return` poufności informacji dla funkcji pojedynczej linii. Wartość zwrócona przez funkcję jednowierszowego jest wartość wyrażenia w treści funkcji.  
  
-   Treść procedury jeden wiersz musi być instrukcją jeden wiersz.  
  
-   Nie dołączaj jednowierszowego, funkcje i procedur `End Function` lub `End Sub` instrukcji.  
  
-   Typ danych parametru wyrażenia lambda można określić za pomocą `As` można wywnioskować — słowo kluczowe lub typ danych parametru. Musi mieć określony albo wszystkie parametry można wywnioskować typów danych lub wszystkich.  
  
-   `Optional` i `Paramarray` parametry nie są dozwolone.  
  
-   Parametry ogólne nie są dozwolone.  
  
## <a name="async-lambdas"></a>Lambdy asynchroniczne  
 Możesz łatwo tworzyć wyrażenia lambda i instrukcje, które zawierają Przetwarzanie asynchroniczne przy użyciu [Async](../../../../visual-basic/language-reference/modifiers/async.md) i [operatora Await](../../../../visual-basic/language-reference/operators/await-operator.md) słów kluczowych. Na przykład, poniższy przykład Windows Forms zawiera program obsługi zdarzeń, który wywołuje i czeka na metodę asynchroniczną `ExampleMethodAsync`.  
  
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
  
 Można dodać tę samą procedurę obsługi zdarzeń, używając lambdy asynchronicznej w [AddHandler — instrukcja](../../../../visual-basic/language-reference/statements/addhandler-statement.md). Aby dodać ten program obsługi `Async` modyfikator przed listą parametrów lambda, co ilustruje poniższy przykład.  
  
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
  
 Aby uzyskać więcej informacji na temat sposobu tworzenia i używania metod asynchronicznych, zobacz [Asynchronous Programming with Async and Await](../../../../visual-basic/programming-guide/concepts/async/index.md).  
  
## <a name="context"></a> Kontekst  
 Wyrażenie lambda udostępnia kontekst zakresu, w którym jest zdefiniowana. Ma on te same prawa dostępu, jak każdy kod napisany w zakresie zawierającym. Obejmuje to dostęp do zmiennych składowych, funkcje i subskrypcji, `Me`oraz parametry i zmienne lokalne w zakresie zawierającym.  
  
 Dostęp do zmiennych lokalnych i parametrów w zakresie zawierającym mogą wykraczać poza okres istnienia tego zakresu. Tak długo, jak obiekt delegowany odwołujące się do wyrażenia lambda nie jest dostępna dla wyrzucania elementów bezużytecznych, dostęp do zmiennych w środowisku, oryginalnym są zachowywane. W poniższym przykładzie zmienna `target` jest lokalną grupą `makeTheGame`, metody, w którym wyrażenie lambda `playTheGame` jest zdefiniowana. Należy zauważyć, że wyrażenie lambda zwrócone przypisane do `takeAGuess` w `Main`, wciąż ma dostęp do zmiennej lokalnej `target`.  
  
 [!code-vb[VbVbalrLambdas#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class6.vb#12)]  
  
 W poniższym przykładzie pokazano szeroką gamę prawa dostępu zagnieżdżonym wyrażeniem lambda. Gdy wyrażenie lambda zwracany jest wykonywany z `Main` jako `aDel`, uzyskuje dostęp do tych elementów:  
  
-   Pole klasy, w którym jest zdefiniowany: `aField`  
  
-   Właściwość klasy, w którym jest zdefiniowany: `aProp`  
  
-   Parametr metody `functionWithNestedLambda`, w którym jest zdefiniowana: `level1`  
  
-   Zmienna lokalna o `functionWithNestedLambda`: `localVar`  
  
-   Parametr wyrażenia lambda, w którym jest zagnieżdżona: `level2`  
  
 [!code-vb[VbVbalrLambdas#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class3.vb#9)]  
  
## <a name="converting-to-a-delegate-type"></a>Konwertowanie do typu delegata  
 Wyrażenia lambda mogą być niejawnie konwertowane na typ delegata zgodne. Aby uzyskać informacje na temat ogólnych wymagań dotyczących zgodności, zobacz [swobodna konwersja delegatów](../../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md). Na przykład, poniższy przykład kodu pokazuje Wyrażenie lambda, która niejawnie konwertuje `Func(Of Integer, Boolean)` lub pasujący podpis delegata.  
  
 [!code-vb[VbVbalrLambdas#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#16)]  
  
 Poniższy przykład kodu pokazuje Wyrażenie lambda, która niejawnie konwertuje `Sub(Of Double, String, Double)` lub pasujący podpis delegata.  
  
 [!code-vb[VbVbalrLambdas#23](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/class7.vb#23)]  
  
 Podczas przypisywania wyrażenia lambda do delegatów i przekazywane jako argumenty do procedur, można określić nazwy parametrów, ale Pomiń typy danych, umożliwiając typy podejmowane na podstawie obiektu delegowanego.  
  
## <a name="examples"></a>Przykłady  
  
-   W poniższym przykładzie zdefiniowano Wyrażenie lambda, które zwraca `True` Jeśli przypisaną wartością argumentu dopuszcza wartości null i `False` gdy jego wartość jest `Nothing`.  
  
     [!code-vb[VbVbalrLambdas#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#4)]  
  
-   W poniższym przykładzie zdefiniowano Wyrażenie lambda, które zwraca indeks ostatniego elementu w tablicy.  
  
     [!code-vb[VbVbalrLambdas#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#5)]  
  
## <a name="see-also"></a>Zobacz także

- [Procedury](./index.md)
- [Wprowadzenie do LINQ w Visual Basic](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [Delegaty](../../../../visual-basic/programming-guide/language-features/delegates/index.md)
- [Function, instrukcja](../../../../visual-basic/language-reference/statements/function-statement.md)
- [Sub, instrukcja](../../../../visual-basic/language-reference/statements/sub-statement.md)
- [Typy wartości dopuszczających wartości null](../../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)
- [Instrukcje: Przekazywanie procedur do innej procedury w Visual Basic](../../../../visual-basic/programming-guide/language-features/delegates/how-to-pass-procedures-to-another-procedure.md)
- [Instrukcje: Tworzenie wyrażenia Lambda](./how-to-create-a-lambda-expression.md)
- [Swobodna konwersja delegatów](../../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md)
