---
title: 'Instrukcje: Tworzenie wyrażenia Lambda (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- lambda expressions [Visual Basic]
- expressions [Visual Basic], lambda
ms.assetid: 3279bd5c-80f7-410a-a7ba-f7085ed36aa5
ms.openlocfilehash: e7302304fe6c44b0143d7f12ec272d597b313fdd
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54492426"
---
# <a name="how-to-create-a-lambda-expression-visual-basic"></a>Instrukcje: Tworzenie wyrażenia Lambda (Visual Basic)
A *wyrażenia lambda* jest funkcji lub podprocedury, który nie ma nazwy. Wyrażenie lambda może służyć wszędzie tam, gdzie typ obiektu delegowanego jest prawidłowy.  
  
### <a name="to-create-a-single-line-lambda-expression-function"></a>Aby utworzyć funkcję wyrażenia lambda pojedynczej linii  
  
1.  W każdej sytuacji, w których można użyć typu delegata, wpisz słowo kluczowe `Function`, jak w poniższym przykładzie:  
  
     `Dim add1 =`   `Function`  
  
2.  W nawiasach bezpośrednio po `Function`, typów parametrów funkcji. Zwróć uwagę, czy nie określisz nazwy po `Function`.  
  
     `Dim add1 = Function`   `(num As Integer)`  
  
3.  Po liście parametrów należy wpisać jedno wyrażenie jako treści funkcji. Wartość, która daje w wyniku wyrażenia jest wartość zwrócona przez funkcję. Nie używaj `As` klauzulę, aby określić typ zwracany.  
  
     [!code-vb[VbVbalrLambdas#1](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-create-a-lambda-expression_1.vb)]  
  
     Możesz wywołać Wyrażenie lambda przekazanie w argumencie liczby całkowitej.  
  
     [!code-vb[VbVbalrLambdas#2](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-create-a-lambda-expression_2.vb)]  
  
4.  Alternatywnie ten sam wynik odbywa się w poniższym przykładzie:  
  
     [!code-vb[VbVbalrLambdas#3](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-create-a-lambda-expression_3.vb)]  
  
### <a name="to-create-a-single-line-lambda-expression-subroutine"></a>Aby utworzyć procedurę wyrażenia lambda jednowierszowy  
  
1.  W każdej sytuacji, w których można użyć typu delegata, wpisz słowo kluczowe `Sub`, jak pokazano w poniższym przykładzie.  
  
     `Dim add1 =`   `Sub`  
  
2.  W nawiasach bezpośrednio po `Sub`, typów parametrów procedury. Zwróć uwagę, czy nie określisz nazwy po `Sub`.  
  
     `Dim add1 = Sub`   `(msg As String)`  
  
3.  Po liście parametrów wpisz pojedynczą instrukcję jako treść procedurę.  
  
     [!code-vb[VbVbalrLambdas#17](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-create-a-lambda-expression_4.vb)]  
  
     Możesz wywołać Wyrażenie lambda przekazanie argumentu ciągu.  
  
     [!code-vb[VbVbalrLambdas#18](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-create-a-lambda-expression_5.vb)]  
  
### <a name="to-create-a-multiline-lambda-expression-function"></a>Aby utworzyć funkcję wyrażenia lambda wielowierszowy  
  
1.  W każdej sytuacji, w których można użyć typu delegata, wpisz słowo kluczowe `Function`, jak pokazano w poniższym przykładzie.  
  
     `Dim add1 =`   `Function`  
  
2.  W nawiasach bezpośrednio po `Function`, typów parametrów funkcji. Zwróć uwagę, czy nie określisz nazwy po `Function`.  
  
     `Dim add1 = Function`   `(index As Integer)`  
  
3.  Naciśnij klawisz ENTER. `End Function` Instrukcji jest automatycznie dodawany.  
  
4.  W treści funkcji Dodaj następujący kod do tworzenia wyrażenia i zwraca wartość. Nie używaj `As` klauzulę, aby określić typ zwracany.  
  
     [!code-vb[VbVbalrLambdas#19](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-create-a-lambda-expression_6.vb)]  
  
     Możesz wywołać Wyrażenie lambda przekazanie w argumencie liczby całkowitej.  
  
     [!code-vb[VbVbalrLambdas#20](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-create-a-lambda-expression_7.vb)]  
  
### <a name="to-create-a-multiline-lambda-expression-subroutine"></a>Aby utworzyć procedurę wyrażenia lambda wielowierszowy  
  
1.  W każdej sytuacji, w których można użyć typu delegata, wpisz słowo kluczowe `Sub`, jak pokazano w poniższym przykładzie:  
  
     `Dim add1 =`   `Sub`  
  
2.  W nawiasach bezpośrednio po `Sub`, typów parametrów procedury. Zwróć uwagę, czy nie określisz nazwy po `Sub`.  
  
     `Dim add1 = Sub`  `(msg As String)`  
  
3.  Naciśnij klawisz ENTER. `End Sub` Instrukcji jest automatycznie dodawany.  
  
4.  W treści funkcji Dodaj następujący kod do wykonania, gdy jest wywoływana przez procedurę.  
  
     [!code-vb[VbVbalrLambdas#21](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-create-a-lambda-expression_8.vb)]  
  
     Możesz wywołać Wyrażenie lambda przekazanie argumentu ciągu.  
  
     [!code-vb[VbVbalrLambdas#22](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-create-a-lambda-expression_9.vb)]  
  
## <a name="example"></a>Przykład  
 Zazwyczaj jest używane, wyrażeń lambda do definiowania funkcji, które mogą być przekazywane jako argumentu dla parametru, którego typem jest `Delegate`. W poniższym przykładzie <xref:System.Diagnostics.Process.GetProcesses%2A> metoda zwraca tablicę procesów uruchomionych na komputerze lokalnym. <xref:System.Linq.Enumerable.Where%2A> Metody z <xref:System.Linq.Enumerable> klasa wymaga `Boolean` delegować jako argumentem. Wyrażenia lambda w przykładzie jest używany do tego celu. Zwraca `True` dla każdego procesu, który ma tylko jeden wątek, a te są zaznaczone w `filteredList`.  
  
 [!code-vb[VbVbalrLambdas#10](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-create-a-lambda-expression_10.vb)]  
  
 Poprzedni przykład jest równoważny z następującym kodem, które są zapisywane w [!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)] składni:  
  
 [!code-vb[VbVbalrLambdas#11](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-create-a-lambda-expression_11.vb)]  
  
## <a name="see-also"></a>Zobacz także
- <xref:System.Linq.Enumerable>
- [Wyrażenia lambda](./lambda-expressions.md)
- [Function, instrukcja](../../../../visual-basic/language-reference/statements/function-statement.md)
- [Sub, instrukcja](../../../../visual-basic/language-reference/statements/sub-statement.md)
- [Delegaty](../../../../visual-basic/programming-guide/language-features/delegates/index.md)
- [Instrukcje: Przekazywanie procedur do innej procedury w Visual Basic](../../../../visual-basic/programming-guide/language-features/delegates/how-to-pass-procedures-to-another-procedure.md)
- [Delegate, instrukcja](../../../../visual-basic/language-reference/statements/delegate-statement.md)
- [Wprowadzenie do LINQ w Visual Basic](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
