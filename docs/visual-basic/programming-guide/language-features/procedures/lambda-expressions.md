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
ms.openlocfilehash: 54a9c0cf275a67c77748c32771c3c5dcbdb916d7
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84406706"
---
# <a name="lambda-expressions-visual-basic"></a>Lambda — Wyrażenia (Visual Basic)

*Wyrażenie lambda* jest funkcją lub podprocedurą bez nazwy, która może być używana wszędzie tam, gdzie delegat jest prawidłowy. Wyrażenia lambda mogą być funkcjami lub procedurami i mogą być jednowierszowe lub wielowierszowe. Można przekazać wartości z bieżącego zakresu do wyrażenia lambda.

> [!NOTE]
> `RemoveHandler`Instrukcja to wyjątek. W parametrze delegata elementu nie można przekazać wyrażenia lambda `RemoveHandler` .

Wyrażenia lambda można tworzyć za pomocą `Function` `Sub` słowa kluczowego or, tak jak w przypadku tworzenia standardowej funkcji lub procedury podrzędnej. Jednak wyrażenia lambda są zawarte w instrukcji.

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

- Wyrażenia lambda nie mogą mieć modyfikatorów, takich jak `Overloads` lub `Overrides` .

- Jednowierszowe funkcje lambda nie używają `As` klauzuli do wyznaczania typu zwracanego. Zamiast tego, typ jest wywnioskowany na podstawie wartości, do której szacuje się treść wyrażenia lambda. Na przykład jeśli treść wyrażenia lambda jest `cust.City = "London"` , jego typem zwracanym jest `Boolean` .

- W wielowierszowych funkcjach lambda można określić typ zwracany przy użyciu `As` klauzuli lub pominąć `As` klauzulę, tak aby typ zwracany został wywnioskowany. Gdy `As` klauzula jest pomijana dla wielowierszowej funkcji lambda, zwracany typ jest wywnioskowany jako typ dominujący ze wszystkich `Return` instrukcji w wielowierszowej funkcji lambda. *Typ dominujący* jest typem unikatowym, do którego można rozszerzyć wszystkie inne typy. Jeśli nie można określić tego unikatowego typu, typ dominujący jest typem unikatowym, do którego można zawęzić wszystkie inne typy w tablicy. Jeśli nie można określić żadnego z tych unikatowych typów, typ dominujący to `Object` . W tym przypadku, jeśli `Option Strict` jest ustawiona na `On` , wystąpi błąd kompilatora.

     Na przykład, jeśli wyrażenia dostarczone do `Return` instrukcji zawierają wartości typu `Integer` , `Long` , i `Double` , Tablica wyników jest typu `Double` . Obie `Integer` i `Long` rozszerzają się `Double` tylko do i `Double` . W związku `Double` z tym jest typem dominującym. Aby uzyskać więcej informacji, zobacz [rozszerzanie i zwężanie konwersji](../data-types/widening-and-narrowing-conversions.md).

- Treść funkcji jednowierszowej musi być wyrażeniem zwracającym wartość, a nie instrukcją. Brak `Return` instrukcji dla funkcji jednowierszowych. Wartość zwracana przez funkcję jednowierszową jest wartością wyrażenia w treści funkcji.

- Treść podprocedury jednowierszowej musi być instrukcją jednowierszową.

- Funkcje jednowierszowe i podprocedury nie zawierają `End Function` `End Sub` instrukcji or.

- Można określić typ danych parametru wyrażenia lambda za pomocą `As` słowa kluczowego lub można wywnioskować typ danych parametru. Wszystkie parametry muszą mieć określone typy danych lub muszą zostać wywnioskowane.

- `Optional``Paramarray`Parametry i są niedozwolone.

- Parametry ogólne są niedozwolone.

## <a name="async-lambdas"></a>Lambdy asynchroniczne

Możesz łatwo tworzyć wyrażenia lambda i instrukcje, które zawierają asynchroniczne przetwarzanie przy użyciu słów kluczowych operatora [Async](../../../language-reference/modifiers/async.md) i [await](../../../language-reference/operators/await-operator.md) . Na przykład poniższy Windows Forms przykład zawiera procedurę obsługi zdarzeń, która wywołuje i czeka na metodę asynchroniczną `ExampleMethodAsync` .

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

Tę samą procedurę obsługi zdarzeń można dodać przy użyciu asynchronicznego wyrażenia lambda w [instrukcji AddHandler](../../../language-reference/statements/addhandler-statement.md). Aby dodać tę procedurę obsługi, Dodaj `Async` modyfikator przed listą parametrów lambda, jak pokazano w poniższym przykładzie.

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

Aby uzyskać więcej informacji na temat tworzenia i używania metod asynchronicznych, zobacz [programowanie asynchroniczne z Async i await](../../concepts/async/index.md).

## <a name="context"></a>Kontekst

Wyrażenie lambda udostępnia swój kontekst z zakresem, w którym jest zdefiniowany. Ma takie same prawa dostępu jak każdy kod zapisany w zakresie zawierającym. Obejmuje to dostęp do zmiennych składowych, funkcji i `Me` parametrów, a także zmiennych lokalnych w zakresie zawierającym.

Dostęp do zmiennych lokalnych i parametrów w zakresie zawierającym może wykraczać poza okres istnienia tego zakresu. Tak długo, jak delegat odwołujący się do wyrażenia lambda nie jest dostępny do wyrzucania elementów bezużytecznych, zostanie zachowany dostęp do zmiennych w oryginalnym środowisku. W poniższym przykładzie zmienna `target` jest lokalna do `makeTheGame` , metoda, w której `playTheGame` jest zdefiniowane wyrażenie lambda. Zwróć uwagę, że zwrócone wyrażenie lambda przypisane do `takeAGuess` w `Main` , nadal ma dostęp do zmiennej lokalnej `target` .

[!code-vb[VbVbalrLambdas#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class6.vb#12)]

Poniższy przykład demonstruje szeroki zakres praw dostępu zagnieżdżonego wyrażenia lambda. Gdy zwrócone wyrażenie lambda jest wykonywane z `Main` AS `aDel` , uzyskuje dostęp do następujących elementów:

- Pole klasy, w której jest zdefiniowany:`aField`

- Właściwość klasy, w której jest zdefiniowana:`aProp`

- Parametr metody `functionWithNestedLambda` , w której jest zdefiniowany:`level1`

- Zmienna lokalna `functionWithNestedLambda` :`localVar`

- Parametr wyrażenia lambda, w którym jest zagnieżdżony:`level2`

 [!code-vb[VbVbalrLambdas#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class3.vb#9)]

## <a name="converting-to-a-delegate-type"></a>Konwertowanie na typ delegata

Wyrażenie lambda może być niejawnie konwertowane na zgodny typ delegata. Aby uzyskać informacje o ogólnych wymaganiach dotyczących zgodności, zobacz [swobodne przekształcenie delegata](../delegates/relaxed-delegate-conversion.md). Na przykład poniższy kod ilustruje wyrażenie lambda, które niejawnie konwertuje do `Func(Of Integer, Boolean)` lub pasujący podpis delegata.

[!code-vb[VbVbalrLambdas#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#16)]

Poniższy przykład kodu przedstawia wyrażenie lambda, które niejawnie konwertuje do `Sub(Of Double, String, Double)` lub pasujący podpis delegata.

[!code-vb[VbVbalrLambdas#23](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/class7.vb#23)]

W przypadku przypisywania wyrażeń lambda do delegatów lub przekazywania ich jako argumentów do procedur, można określić nazwy parametrów, ale pomijać ich typy danych, dzięki czemu typy mają być pobierane z delegata.

## <a name="examples"></a>Przykłady

- W poniższym przykładzie zdefiniowano wyrażenie lambda, które zwraca `True` , jeśli argument typu wartości null ma przypisaną wartość i `False` jeśli jego wartość to `Nothing` .

     [!code-vb[VbVbalrLambdas#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#4)]

- Poniższy przykład definiuje wyrażenie lambda zwracające indeks ostatniego elementu w tablicy.

     [!code-vb[VbVbalrLambdas#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#5)]

## <a name="see-also"></a>Zobacz też

- [Procedury](./index.md)
- [Wprowadzenie do LINQ w Visual Basic](../linq/introduction-to-linq.md)
- [Delegaci](../delegates/index.md)
- [Function, instrukcja](../../../language-reference/statements/function-statement.md)
- [Sub, instrukcja](../../../language-reference/statements/sub-statement.md)
- [Typy wartości null](../data-types/nullable-value-types.md)
- [Porady: przekazywanie procedur do innej procedury w Visual Basic](../delegates/how-to-pass-procedures-to-another-procedure.md)
- [Porady: tworzenie wyrażenia lambda](./how-to-create-a-lambda-expression.md)
- [Swobodna konwersja delegatów](../delegates/relaxed-delegate-conversion.md)
