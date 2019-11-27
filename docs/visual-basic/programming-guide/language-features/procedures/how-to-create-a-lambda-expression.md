---
title: 'Porady: tworzenie wyrażenia lambda'
ms.date: 07/20/2015
helpviewer_keywords:
- lambda expressions [Visual Basic]
- expressions [Visual Basic], lambda
ms.assetid: 3279bd5c-80f7-410a-a7ba-f7085ed36aa5
ms.openlocfilehash: bb0bdb3c10a7df2ca954fbdb9382a25bf805068d
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74349741"
---
# <a name="how-to-create-a-lambda-expression-visual-basic"></a>Porady: tworzenie wyrażenia lambda (Visual Basic)
*Wyrażenie lambda* jest funkcją lub podprocedurą, która nie ma nazwy. Wyrażenia lambda można użyć wszędzie tam, gdzie typ delegata jest prawidłowy.  
  
### <a name="to-create-a-single-line-lambda-expression-function"></a>Aby utworzyć jednowierszową funkcję wyrażenia lambda  
  
1. W każdej sytuacji, w której można użyć typu delegata, wpisz słowo kluczowe `Function`, jak w poniższym przykładzie:  
  
     `Dim add1 =`   `Function`  
  
2. W nawiasach, bezpośrednio po `Function`, wpisz parametry funkcji. Zwróć uwagę, że po `Function`nie określisz nazwy.  
  
     `Dim add1 = Function`   `(num As Integer)`  
  
3. Po liście parametrów wpisz pojedyncze wyrażenie jako treść funkcji. Wartością zwracaną przez wyrażenie jest wartość zwrócona przez funkcję. Nie używasz klauzuli `As` do określenia typu zwracanego.  
  
     [!code-vb[VbVbalrLambdas#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#1)]  
  
     Wyrażenie lambda jest wywoływane przez przekazanie argumentu w postaci liczby całkowitej.  
  
     [!code-vb[VbVbalrLambdas#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#2)]  
  
4. Alternatywnie, ten sam wynik jest realizowany przez następujący przykład:  
  
     [!code-vb[VbVbalrLambdas#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#3)]  
  
### <a name="to-create-a-single-line-lambda-expression-subroutine"></a>Aby utworzyć jednowierszową podprocedurę wyrażenia lambda  
  
1. W każdej sytuacji, w której można użyć typu delegata, wpisz słowo kluczowe `Sub`, jak pokazano w poniższym przykładzie.  
  
     `Dim add1 =`   `Sub`  
  
2. W nawiasach, bezpośrednio po `Sub`, wpisz parametry procedury podrzędnej. Zwróć uwagę, że po `Sub`nie określisz nazwy.  
  
     `Dim add1 = Sub`   `(msg As String)`  
  
3. Po liście parametrów wpisz pojedynczą instrukcję jako treść procedury podrzędnej.  
  
     [!code-vb[VbVbalrLambdas#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#17)]  
  
     Wyrażenie lambda jest wywoływane przez przekazanie argumentu ciągu.  
  
     [!code-vb[VbVbalrLambdas#18](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#18)]  
  
### <a name="to-create-a-multiline-lambda-expression-function"></a>Aby utworzyć wielowierszową funkcję wyrażenia lambda  
  
1. W każdej sytuacji, w której można użyć typu delegata, wpisz słowo kluczowe `Function`, jak pokazano w poniższym przykładzie.  
  
     `Dim add1 =`   `Function`  
  
2. W nawiasach, bezpośrednio po `Function`, wpisz parametry funkcji. Zwróć uwagę, że po `Function`nie określisz nazwy.  
  
     `Dim add1 = Function`   `(index As Integer)`  
  
3. Naciśnij klawisz ENTER. Instrukcja `End Function` jest automatycznie dodawana.  
  
4. W treści funkcji Dodaj następujący kod, aby utworzyć wyrażenie i zwrócić wartość. Nie używasz klauzuli `As` do określenia typu zwracanego.  
  
     [!code-vb[VbVbalrLambdas#19](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#19)]  
  
     Wyrażenie lambda jest wywoływane przez przekazanie argumentu w postaci liczby całkowitej.  
  
     [!code-vb[VbVbalrLambdas#20](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#20)]  
  
### <a name="to-create-a-multiline-lambda-expression-subroutine"></a>Aby utworzyć wielowierszową procedurę wyrażenia lambda  
  
1. W każdej sytuacji, w której można użyć typu delegata, wpisz słowo kluczowe `Sub`, jak pokazano w następującym przykładzie:  
  
     `Dim add1 =`   `Sub`  
  
2. W nawiasach, bezpośrednio po `Sub`, wpisz parametry procedury podrzędnej. Zwróć uwagę, że po `Sub`nie określisz nazwy.  
  
     `Dim add1 = Sub`  `(msg As String)`  
  
3. Naciśnij klawisz ENTER. Instrukcja `End Sub` jest automatycznie dodawana.  
  
4. W treści funkcji Dodaj następujący kod, aby wykonać po wywołaniu procedury podrzędnej.  
  
     [!code-vb[VbVbalrLambdas#21](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#21)]  
  
     Wyrażenie lambda jest wywoływane przez przekazanie argumentu ciągu.  
  
     [!code-vb[VbVbalrLambdas#22](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#22)]  
  
## <a name="example"></a>Przykład  
 Typowym zastosowaniem wyrażeń lambda jest zdefiniowanie funkcji, która może być przenoszona jako argument dla parametru, którego typ jest `Delegate`. W poniższym przykładzie metoda <xref:System.Diagnostics.Process.GetProcesses%2A> zwraca tablicę procesów uruchomionych na komputerze lokalnym. Metoda <xref:System.Linq.Enumerable.Where%2A> z klasy <xref:System.Linq.Enumerable> wymaga jako argumentu `Boolean` delegata. Wyrażenie lambda w przykładzie jest używane do tego celu. Zwraca `True` dla każdego procesu, który ma tylko jeden wątek, i są wybrane w `filteredList`.  
  
 [!code-vb[VbVbalrLambdas#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class4.vb#10)]  
  
 Poprzedni przykład jest odpowiednikiem poniższego kodu, który jest pisany w składni [!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)]:  
  
 [!code-vb[VbVbalrLambdas#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class5.vb#11)]  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Linq.Enumerable>
- [Wyrażenia lambda](./lambda-expressions.md)
- [Function, instrukcja](../../../../visual-basic/language-reference/statements/function-statement.md)
- [Sub, instrukcja](../../../../visual-basic/language-reference/statements/sub-statement.md)
- [Delegaci](../../../../visual-basic/programming-guide/language-features/delegates/index.md)
- [Instrukcje: przekazywanie procedur do innej procedury w Visual Basic](../../../../visual-basic/programming-guide/language-features/delegates/how-to-pass-procedures-to-another-procedure.md)
- [Delegate, instrukcja](../../../../visual-basic/language-reference/statements/delegate-statement.md)
- [Wprowadzenie do LINQ w Visual Basic](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
