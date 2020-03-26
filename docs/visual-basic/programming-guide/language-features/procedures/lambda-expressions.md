---
title: Wyrażenia lambda
ms.date: 07/20/2015
f1_keywords:
- vb.LambdaFunction
helpviewer_keywords:
- functions [Visual Basic], lambda expressions
- lambda expressions [Visual Basic]
- expressions [Visual Basic], lambda
- inline functions [Visual Basic]
ms.assetid: 137064b0-3928-4bfa-ba71-c3f9cbd951e2
ms.openlocfilehash: 1827eb5630ed217527de25fc9d9c2bb8994b9aff
ms.sourcegitcommit: 99b153b93bf94d0fecf7c7bcecb58ac424dfa47c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2020
ms.locfileid: "80249672"
---
# <a name="lambda-expressions-visual-basic"></a>Lambda — Wyrażenia (Visual Basic)

Wyrażenie *lambda* jest funkcją lub podprocedury bez nazwy, która może być używana wszędzie tam, gdzie delegat jest prawidłowy. Wyrażenia Lambda mogą być funkcjami lub podprocedury i mogą być jednowierszowe lub wieloliniowe. Wartości z bieżącego zakresu można przekazać do wyrażenia lambda.

> [!NOTE]
> Instrukcja `RemoveHandler` jest wyjątkiem. Nie można przekazać wyrażenia lambda dla `RemoveHandler`parametru delegata .

Wyrażenia lambda można tworzyć `Function` przy `Sub` użyciu słowa kluczowego lub, tak jak tworzysz standardową funkcję lub podprocedury. Jednak wyrażenia lambda są uwzględniane w instrukcji.

Poniższy przykład jest wyrażenie lambda, który zwiększa jego argument i zwraca wartość. W przykładzie przedstawiono składnię wyrażenia lambda jedno- i wielowierszowego dla funkcji.

[!code-vb[VbVbalrLambdas#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#14)]

Poniższy przykład jest wyrażenie lambda, który zapisuje wartość do konsoli. W przykładzie przedstawiono składnię wyrażenia lambda jedno- i wielowierszowego dla podprocedury.

[!code-vb[VbVbalrLambdas#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#15)]

Należy zauważyć, że w poprzednich przykładach wyrażenia lambda są przypisane do nazwy zmiennej. Za każdym razem, gdy odwołujesz się do zmiennej, wywołujesz wyrażenie lambda. Można również zadeklarować i wywołać wyrażenie lambda w tym samym czasie, jak pokazano w poniższym przykładzie.

[!code-vb[VbVbalrLambdas#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#3)]

Wyrażenie lambda może być zwracane jako wartość wywołania funkcji (jak pokazano w przykładzie w sekcji Kontekst w dalszej części tego [tematu)](#context) lub przekazywane jako argument do parametru, który przyjmuje typ delegata, jak pokazano w poniższym przykładzie.

[!code-vb[VbVbalrLambdas#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class2.vb#8)]

## <a name="lambda-expression-syntax"></a>Składnia wyrażenia lambda

Składnia wyrażenia lambda przypomina składność funkcji standardowej lub podprocedury. Różnice są następujące:

- Wyrażenie lambda nie ma nazwy.

- Wyrażenia Lambda nie mogą mieć `Overloads` modyfikatorów, takich jak lub `Overrides`.

- Funkcje lambda jednowierszowe `As` nie używają klauzuli do wyznaczenia typu zwracanego. Zamiast tego typ jest wywnioskowany z wartości, która jest oceniana przez obiekt wyrażenia lambda. Na przykład, jeśli treść wyrażenia lambda jest `cust.City = "London"`, `Boolean`jego typem zwracany jest .

- W wielowierszowych funkcjach lambda można określić typ `As` zwracany przy `As` użyciu klauzuli lub pominąć klauzulę, tak aby wywnioskować typ zwracany. Gdy `As` klauzula jest pominięta dla funkcji lambda wielowierszowej, typ zwracany jest `Return` wnioskowany jako typ dominujący ze wszystkich instrukcji w funkcji lambda wielowierszowej. *Typ dominujący* jest typem unikatowym, do który można poszerzyć wszystkie inne typy. Jeśli nie można określić tego typu unikatowego, typ dominujący jest typem unikatowym, do który można zawęzić wszystkie inne typy w tablicy. Jeśli żaden z tych unikatowych typów nie `Object`może być określony, typem dominującym jest . W takim przypadku, `Option Strict` jeśli `On`jest ustawiona na , występuje błąd kompilatora.

     Na przykład, jeśli wyrażenia dostarczone `Return` do instrukcji `Integer`zawierają `Long`wartości `Double`typu , i , `Double`wynikowa tablica jest typu . Zarówno `Integer` `Long` i `Double` poszerzyć `Double`do i tylko . W związku `Double` z tym jest typem dominującym. Aby uzyskać więcej informacji, zobacz [Rozszerzanie i zawężanie konwersji](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md).

- Treść funkcji jednowierszowej musi być wyrażeniem, które zwraca wartość, a nie instrukcją. Nie ma `Return` instrukcji dla funkcji jednowierszowych. Wartość zwracana przez funkcję jednowierszową jest wartością wyrażenia w treści funkcji.

- Treść podprocedury jednowierszowej musi być instrukcją jednowierszową.

- Funkcje jednowierszowe i podprocedury nie zawierają `End Function` instrukcji ani `End Sub` instrukcji.

- Można określić typ danych parametru wyrażenia lambda za pomocą `As` słowa kluczowego lub typ danych parametru można wywnioskować. Wszystkie parametry muszą mieć określone typy danych lub wszystkie muszą być wywnioskowane.

- `Optional`i `Paramarray` parametry nie są dozwolone.

- Parametry ogólne nie są dozwolone.

## <a name="async-lambdas"></a>Lambdy asynchroniczne

Można łatwo tworzyć wyrażenia lambda i instrukcje, które zawierają przetwarzanie asynchroniczne przy użyciu [async](../../../../visual-basic/language-reference/modifiers/async.md) i [await operator](../../../../visual-basic/language-reference/operators/await-operator.md) słów kluczowych. Na przykład poniższy przykład formularzy systemu Windows zawiera program obsługi zdarzeń, który wywołuje metodę asynchronizową i oczekuje na metodę asynchronizowania. `ExampleMethodAsync`

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

Ten sam program obsługi zdarzeń można dodać przy użyciu lambda asynchronii w [Instrukcji AddHandler](../../../../visual-basic/language-reference/statements/addhandler-statement.md). Aby dodać ten program `Async` obsługi, dodaj modyfikator przed listą parametrów lambda, jak pokazano w poniższym przykładzie.

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

Aby uzyskać więcej informacji na temat tworzenia i używania metod [asynchronicznych, zobacz Programowanie asynchroniczne za pomocą asynchronii i Await](../../../../visual-basic/programming-guide/concepts/async/index.md).

## <a name="context"></a>Kontekst

Wyrażenie lambda udostępnia swój kontekst z zakresem, w którym jest zdefiniowany. Ma takie same prawa dostępu, jak każdy kod napisany w zakresie zawierającym. Obejmuje to dostęp do zmiennych członkowskich, funkcji i subs oraz `Me`parametrów i zmiennych lokalnych w zakresie zawierającym.

Dostęp do zmiennych lokalnych i parametrów w zakresie zawierającym może wykraczać poza okres istnienia tego zakresu. Tak długo, jak delegat odnoszący się do wyrażenia lambda nie jest dostępny do wyrzucania elementów bezużytecznych, dostęp do zmiennych w środowisku oryginalnym jest zachowywany. W poniższym przykładzie zmienna `target` jest lokalna do `makeTheGame`, `playTheGame` metoda, w której wyrażenie lambda jest zdefiniowany. Należy zauważyć, że zwrócone wyrażenie `takeAGuess` lambda, przypisane do w `Main`programie , nadal ma dostęp do zmiennej `target`lokalnej .

[!code-vb[VbVbalrLambdas#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class6.vb#12)]

W poniższym przykładzie przedstawiono szeroki zakres praw dostępu wyrażenia lambda zagnieżdżone. Gdy zwrócone wyrażenie lambda `Main` `aDel`jest wykonywane z as , uzyskuje dostęp do tych elementów:

- Pole klasy, w której jest zdefiniowane:`aField`

- Właściwość klasy, w której jest zdefiniowana:`aProp`

- Parametr metody, `functionWithNestedLambda`w którym jest zdefiniowany:`level1`

- Zmienna lokalna: `functionWithNestedLambda``localVar`

- Parametr wyrażenia lambda, w którym jest zagnieżdżony:`level2`

 [!code-vb[VbVbalrLambdas#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class3.vb#9)]

## <a name="converting-to-a-delegate-type"></a>Konwertowanie na typ delegata

Wyrażenie lambda można niejawnie przekonwertować na zgodny typ delegata. Aby uzyskać informacje na temat ogólnych wymagań dotyczących zgodności, zobacz [Zrelaksowana konwersja delegata](../../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md). Na przykład w poniższym przykładzie kodu pokazano wyrażenie lambda, które niejawnie konwertuje do `Func(Of Integer, Boolean)` lub pasujące podpis delegata.

[!code-vb[VbVbalrLambdas#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#16)]

Poniższy przykład kodu pokazuje wyrażenie lambda, `Sub(Of Double, String, Double)` które niejawnie konwertuje do lub pasujące podpis delegata.

[!code-vb[VbVbalrLambdas#23](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/class7.vb#23)]

Po przypisaniu wyrażeń lambda do delegatów lub przekazać je jako argumenty do procedur, można określić nazwy parametrów, ale pominąć ich typy danych, pozwalając typy być pobierane od pełnomocnika.

## <a name="examples"></a>Przykłady

- Poniższy przykład definiuje wyrażenie lambda, które zwraca, `True` jeśli argument typu wartości `False` nullable `Nothing`ma przypisaną wartość, a jeśli jego wartość jest .

     [!code-vb[VbVbalrLambdas#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#4)]

- Poniższy przykład definiuje wyrażenie lambda, który zwraca indeks ostatniego elementu w tablicy.

     [!code-vb[VbVbalrLambdas#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#5)]

## <a name="see-also"></a>Zobacz też

- [Procedury](./index.md)
- [Wprowadzenie do LINQ w Visual Basic](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [Delegaty](../../../../visual-basic/programming-guide/language-features/delegates/index.md)
- [Instrukcja funkcji](../../../../visual-basic/language-reference/statements/function-statement.md)
- [Sub, instrukcja](../../../../visual-basic/language-reference/statements/sub-statement.md)
- [Typy o wartości zerowalnej](../../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)
- [Porady: przekazywanie procedur do innej procedury w Visual Basic](../../../../visual-basic/programming-guide/language-features/delegates/how-to-pass-procedures-to-another-procedure.md)
- [Porady: tworzenie wyrażenia lambda](./how-to-create-a-lambda-expression.md)
- [Swobodna konwersja delegatów](../../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md)
