---
title: 'Porady: tworzenie wyrażenia lambda (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- lambda expressions [Visual Basic]
- expressions [Visual Basic], lambda
ms.assetid: 3279bd5c-80f7-410a-a7ba-f7085ed36aa5
ms.openlocfilehash: f437166bc5206b4145d6508aa2131ec94d6eca95
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33653549"
---
# <a name="how-to-create-a-lambda-expression-visual-basic"></a>Porady: tworzenie wyrażenia lambda (Visual Basic)
A *wyrażenia lambda* funkcji lub procedury, która nie ma nazwy. Wyrażenia lambda można tam, gdzie typ delegata jest prawidłowy.  
  
### <a name="to-create-a-single-line-lambda-expression-function"></a>Aby utworzyć funkcja wyrażenia lambda jeden wiersz  
  
1.  W każdej sytuacji, w których można użyć typu delegata, wpisz słowo kluczowe `Function`, jak w poniższym przykładzie:  
  
     `Dim add1 =`   `Function`  
  
2.  W nawiasach bezpośrednio po `Function`, wpisz parametry funkcji. Zwróć uwagę, że nie należy określać nazwy po `Function`.  
  
     `Dim add1 = Function`   `(num As Integer)`  
  
3.  Po liście parametrów wpisz jedno wyrażenie jako treści funkcji. Wartość, która daje w wyniku wyrażenia jest wartość zwrócona przez funkcję. Nie używaj `As` klauzuli, aby określić typ zwracany.  
  
     [!code-vb[VbVbalrLambdas#1](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-create-a-lambda-expression_1.vb)]  
  
     Należy wywołać wyrażenia lambda przekazując argument liczby całkowitej.  
  
     [!code-vb[VbVbalrLambdas#2](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-create-a-lambda-expression_2.vb)]  
  
4.  Alternatywnie takiego samego wyniku odbywa się przy następującym przykładzie:  
  
     [!code-vb[VbVbalrLambdas#3](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-create-a-lambda-expression_3.vb)]  
  
### <a name="to-create-a-single-line-lambda-expression-subroutine"></a>Aby utworzyć podprocedury wyrażenia lambda jeden wiersz  
  
1.  W każdej sytuacji, w których można użyć typu delegata, wpisz słowo kluczowe `Sub`, jak pokazano w poniższym przykładzie.  
  
     `Dim add1 =`   `Sub`  
  
2.  W nawiasach bezpośrednio po `Sub`, wpisz parametry procedury. Zwróć uwagę, że nie należy określać nazwy po `Sub`.  
  
     `Dim add1 = Sub`   `(msg As String)`  
  
3.  Po liście parametrów wpisać jednej instrukcji w treści procedury.  
  
     [!code-vb[VbVbalrLambdas#17](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-create-a-lambda-expression_4.vb)]  
  
     Należy wywołać wyrażenia lambda przekazując argument ciągu.  
  
     [!code-vb[VbVbalrLambdas#18](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-create-a-lambda-expression_5.vb)]  
  
### <a name="to-create-a-multiline-lambda-expression-function"></a>Aby utworzyć funkcja wyrażenie wielowierszowych wyrażeń lambda  
  
1.  W każdej sytuacji, w których można użyć typu delegata, wpisz słowo kluczowe `Function`, jak pokazano w poniższym przykładzie.  
  
     `Dim add1 =`   `Function`  
  
2.  W nawiasach bezpośrednio po `Function`, wpisz parametry funkcji. Zwróć uwagę, że nie należy określać nazwy po `Function`.  
  
     `Dim add1 = Function`   `(index As Integer)`  
  
3.  Naciśnij klawisz ENTER. `End Function` Instrukcja jest automatycznie dodawany.  
  
4.  W treści funkcji Dodaj następujący kod do tworzenia wyrażenia i zwraca wartość. Nie używaj `As` klauzuli, aby określić typ zwracany.  
  
     [!code-vb[VbVbalrLambdas#19](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-create-a-lambda-expression_6.vb)]  
  
     Należy wywołać wyrażenia lambda przekazując argument liczby całkowitej.  
  
     [!code-vb[VbVbalrLambdas#20](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-create-a-lambda-expression_7.vb)]  
  
### <a name="to-create-a-multiline-lambda-expression-subroutine"></a>Aby utworzyć podprocedury wyrażenie wielowierszowych wyrażeń lambda  
  
1.  W każdej sytuacji, w których można użyć typu delegata, wpisz słowo kluczowe `Sub`, jak pokazano w poniższym przykładzie:  
  
     `Dim add1 =`   `Sub`  
  
2.  W nawiasach bezpośrednio po `Sub`, wpisz parametry procedury. Zwróć uwagę, że nie należy określać nazwy po `Sub`.  
  
     `Dim add1 = Sub`  `(msg As String)`  
  
3.  Naciśnij klawisz ENTER. `End Sub` Instrukcja jest automatycznie dodawany.  
  
4.  W treści funkcji Dodaj następujący kod do wykonania po wywołaniu procedury.  
  
     [!code-vb[VbVbalrLambdas#21](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-create-a-lambda-expression_8.vb)]  
  
     Należy wywołać wyrażenia lambda przekazując argument ciągu.  
  
     [!code-vb[VbVbalrLambdas#22](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-create-a-lambda-expression_9.vb)]  
  
## <a name="example"></a>Przykład  
 Zazwyczaj wyrażeń lambda jest używane do definiowania funkcji, która może zostać przekazane za jako argumentu dla parametru o typie `Delegate`. W poniższym przykładzie <xref:System.Diagnostics.Process.GetProcesses%2A> metoda zwraca tablicę procesów uruchomionych na komputerze lokalnym. <xref:System.Linq.Enumerable.Where%2A> Metody z <xref:System.Linq.Enumerable> wymaga klasy `Boolean` delegata jako jej argument. Wyrażenia lambda, w tym przykładzie jest używany do tego celu. Zwraca `True` dla każdego procesu, który ma tylko jeden wątek, a te są zaznaczone w `filteredList`.  
  
 [!code-vb[VbVbalrLambdas#10](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-create-a-lambda-expression_10.vb)]  
  
 Poprzedni przykład jest odpowiednikiem następujący kod, który jest zapisywany w [!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)] składni:  
  
 [!code-vb[VbVbalrLambdas#11](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-create-a-lambda-expression_11.vb)]  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Linq.Enumerable>  
 [Wyrażenia lambda](./lambda-expressions.md)  
 [Function, instrukcja](../../../../visual-basic/language-reference/statements/function-statement.md)  
 [Sub, instrukcja](../../../../visual-basic/language-reference/statements/sub-statement.md)  
 [Delegaci](../../../../visual-basic/programming-guide/language-features/delegates/index.md)  
 [Porady: przekazywanie procedur do innej procedury w Visual Basic](../../../../visual-basic/programming-guide/language-features/delegates/how-to-pass-procedures-to-another-procedure.md)  
 [Delegate, instrukcja](../../../../visual-basic/language-reference/statements/delegate-statement.md)  
 [Wprowadzenie do LINQ w Visual Basic](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
