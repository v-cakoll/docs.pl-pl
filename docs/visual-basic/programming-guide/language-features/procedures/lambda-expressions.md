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
ms.openlocfilehash: f3f963167e1b3633cc5fe6e1f435e374cd272cce
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74345972"
---
# <a name="lambda-expressions-visual-basic"></a>Lambda — Wyrażenia (Visual Basic)

*Wyrażenie lambda* jest funkcją lub podprocedurą bez nazwy, która może być używana wszędzie tam, gdzie delegat jest prawidłowy. Wyrażenia lambda mogą być funkcjami lub procedurami i mogą być jednowierszowe lub wielowierszowe. Można przekazać wartości z bieżącego zakresu do wyrażenia lambda.

> [!NOTE]
> Instrukcją `RemoveHandler` jest wyjątek. W parametrze delegata `RemoveHandler`nie można przekazać wyrażenia lambda.

Wyrażenia lambda można tworzyć za pomocą słowa kluczowego `Function` lub `Sub`, tak jak w przypadku tworzenia standardowej funkcji lub procedury podrzędnej. Jednak wyrażenia lambda są zawarte w instrukcji.

Poniższy przykład jest wyrażeniem lambda, które zwiększa jego argument i zwraca wartość. W przykładzie pokazano zarówno jednowierszowy, jak i wielowierszową składnię wyrażenia lambda dla funkcji.

[!code-vb[VbVbalrLambdas#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#14)]

Poniższy przykład jest wyrażeniem lambda, które zapisuje wartość w konsoli. W przykładzie pokazano zarówno jednowierszowe, jak i wielowierszowa składnia wyrażenia lambda dla procedury podrzędnej.

[!code-vb[VbVbalrLambdas#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#15)]

Zwróć uwagę, że w poprzednich przykładach wyrażenia lambda są przypisane do nazwy zmiennej. Za każdym razem, gdy odwołujesz się do zmiennej, wywołaj wyrażenie lambda. Można również zadeklarować i wywołać wyrażenie lambda w tym samym czasie, jak pokazano w poniższym przykładzie.

[!code-vb[VbVbalrLambdas#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#3)]

Wyrażenie lambda może być zwracane jako wartość wywołania funkcji (jak pokazano w przykładzie w sekcji [kontekstu](#context) w dalszej części tego tematu) lub przekazana jako argument do parametru, który przyjmuje typ delegata, jak pokazano w poniższym przykładzie.

[!code-vb[VbVbalrLambdas#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class2.vb#8)]

## <a name="lambda-expression-syntax"></a>Składnia wyrażenia lambda

Składnia wyrażenia lambda jest podobna do standardowej funkcji lub procedury podrzędnej. Różnice są następujące:

- Wyrażenie lambda nie ma nazwy.

- Wyrażenia lambda nie mogą mieć modyfikatorów, takich jak `Overloads` lub `Overrides`.

- Jednowierszowe funkcje lambda nie używają klauzuli `As` do wyznaczania typu zwracanego. Zamiast tego, typ jest wywnioskowany na podstawie wartości, do której szacuje się treść wyrażenia lambda. Na przykład jeśli treść wyrażenia lambda jest `cust.City = "London"`, jego typem zwracanym jest `Boolean`.

- W wielowierszowych funkcjach lambda można określić typ zwracany przy użyciu klauzuli `As` lub pominąć klauzulę `As`, aby typ zwracany został wywnioskowany. Gdy klauzula `As` jest pomijana dla wielowierszowej funkcji lambda, zwracany typ jest wywnioskowany jako typ dominujący ze wszystkich instrukcji `Return` w wielowierszowej funkcji lambda. *Typ dominujący* jest typem unikatowym, do którego można rozszerzyć wszystkie inne typy. Jeśli nie można określić tego unikatowego typu, typ dominujący jest typem unikatowym, do którego można zawęzić wszystkie inne typy w tablicy. Jeśli żaden z tych unikatowych typów nie może być określony, typ dominujący jest `Object`. W takim przypadku, jeśli `Option Strict` jest ustawiona na `On`, wystąpi błąd kompilatora.

     Na przykład, jeśli wyrażenia dostarczone do instrukcji `Return` zawierają wartości typu `Integer`, `Long`i `Double`, wynikiem tablicy jest typ `Double`. Zarówno `Integer`, jak i `Long` rozszerzać do `Double` i tylko `Double`. W związku z tym `Double` jest typem dominującym. Aby uzyskać więcej informacji, zobacz [rozszerzanie i zwężanie konwersji](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md).

- Treść funkcji jednowierszowej musi być wyrażeniem zwracającym wartość, a nie instrukcją. Brak instrukcji `Return` dla funkcji jednowierszowych. Wartość zwracana przez funkcję jednowierszową jest wartością wyrażenia w treści funkcji.

- Treść podprocedury jednowierszowej musi być instrukcją jednowierszową.

- Funkcje jednowierszowe i podprocedury nie zawierają instrukcji `End Function` ani `End Sub`.

- Można określić typ danych parametru wyrażenia lambda za pomocą słowa kluczowego `As` lub można wywnioskować typ danych parametru. Wszystkie parametry muszą mieć określone typy danych lub muszą zostać wywnioskowane.

- parametry `Optional` i `Paramarray` są niedozwolone.

- Parametry ogólne są niedozwolone.

## <a name="async-lambdas"></a>Lambdy asynchroniczne

Możesz łatwo tworzyć wyrażenia lambda i instrukcje, które zawierają asynchroniczne przetwarzanie przy użyciu słów kluczowych operatora [Async](../../../../visual-basic/language-reference/modifiers/async.md) i [await](../../../../visual-basic/language-reference/operators/await-operator.md) . Na przykład poniższy Windows Forms przykład zawiera procedurę obsługi zdarzeń, która wywołuje i czeka na metodę asynchroniczną, `ExampleMethodAsync`.

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

Tę samą procedurę obsługi zdarzeń można dodać przy użyciu asynchronicznego wyrażenia lambda w [instrukcji AddHandler](../../../../visual-basic/language-reference/statements/addhandler-statement.md). Aby dodać tę procedurę obsługi, Dodaj modyfikator `Async` przed listą parametrów lambda, jak pokazano w poniższym przykładzie.

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

Aby uzyskać więcej informacji na temat tworzenia i używania metod asynchronicznych, zobacz [programowanie asynchroniczne z Async i await](../../../../visual-basic/programming-guide/concepts/async/index.md).

## <a name="context"></a>Kontekst

Wyrażenie lambda udostępnia swój kontekst z zakresem, w którym jest zdefiniowany. Ma takie same prawa dostępu jak każdy kod zapisany w zakresie zawierającym. Obejmuje to dostęp do zmiennych składowych, funkcji, `Me`i parametrów oraz zmiennych lokalnych w zakresie zawierającym.

Dostęp do zmiennych lokalnych i parametrów w zakresie zawierającym może wykraczać poza okres istnienia tego zakresu. Tak długo, jak delegat odwołujący się do wyrażenia lambda nie jest dostępny do wyrzucania elementów bezużytecznych, zostanie zachowany dostęp do zmiennych w oryginalnym środowisku. W poniższym przykładzie zmienna `target` jest lokalna do `makeTheGame`, metoda, w której jest zdefiniowane wyrażenie lambda `playTheGame`. Zwróć uwagę, że zwrócone wyrażenie lambda przypisane do `takeAGuess` w `Main`nadal ma dostęp do zmiennej lokalnej `target`.

[!code-vb[VbVbalrLambdas#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class6.vb#12)]

Poniższy przykład demonstruje szeroki zakres praw dostępu zagnieżdżonego wyrażenia lambda. Gdy zwrócone wyrażenie lambda jest wykonywane z `Main` jako `aDel`, uzyskuje dostęp do następujących elementów:

- Pole klasy, w której jest zdefiniowany: `aField`

- Właściwość klasy, w której jest zdefiniowana: `aProp`

- Parametr metody `functionWithNestedLambda`, w którym jest zdefiniowany: `level1`

- Lokalna zmienna `functionWithNestedLambda`: `localVar`

- Parametr wyrażenia lambda, w którym jest zagnieżdżony: `level2`

 [!code-vb[VbVbalrLambdas#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class3.vb#9)]

## <a name="converting-to-a-delegate-type"></a>Konwertowanie na typ delegata

Wyrażenie lambda może być niejawnie konwertowane na zgodny typ delegata. Aby uzyskać informacje o ogólnych wymaganiach dotyczących zgodności, zobacz [swobodne przekształcenie delegata](../../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md). Na przykład poniższy kod ilustruje wyrażenie lambda, które niejawnie konwertuje do `Func(Of Integer, Boolean)` lub pasujący podpis delegata.

[!code-vb[VbVbalrLambdas#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#16)]

Poniższy przykład kodu przedstawia wyrażenie lambda, które niejawnie konwertuje do `Sub(Of Double, String, Double)` lub pasujący podpis delegata.

[!code-vb[VbVbalrLambdas#23](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/class7.vb#23)]

W przypadku przypisywania wyrażeń lambda do delegatów lub przekazywania ich jako argumentów do procedur, można określić nazwy parametrów, ale pomijać ich typy danych, dzięki czemu typy mają być pobierane z delegata.

## <a name="examples"></a>Przykłady

- W poniższym przykładzie zdefiniowano wyrażenie lambda, które zwraca `True`, jeśli argument nullable ma przypisaną wartość i `False`, jeśli jego wartość jest `Nothing`.

     [!code-vb[VbVbalrLambdas#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#4)]

- Poniższy przykład definiuje wyrażenie lambda zwracające indeks ostatniego elementu w tablicy.

     [!code-vb[VbVbalrLambdas#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#5)]

## <a name="see-also"></a>Zobacz także

- [Procedury](./index.md)
- [Wprowadzenie do LINQ w Visual Basic](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [Delegaci](../../../../visual-basic/programming-guide/language-features/delegates/index.md)
- [Function, instrukcja](../../../../visual-basic/language-reference/statements/function-statement.md)
- [Sub, instrukcja](../../../../visual-basic/language-reference/statements/sub-statement.md)
- [Typy wartości dopuszczających wartości null](../../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)
- [Instrukcje: przekazywanie procedur do innej procedury w Visual Basic](../../../../visual-basic/programming-guide/language-features/delegates/how-to-pass-procedures-to-another-procedure.md)
- [Instrukcje: tworzenie wyrażenia lambda](./how-to-create-a-lambda-expression.md)
- [Swobodna konwersja delegatów](../../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md)
