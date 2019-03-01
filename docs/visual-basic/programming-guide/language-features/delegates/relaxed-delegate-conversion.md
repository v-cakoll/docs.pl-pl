---
title: Swobodna konwersja delegatów (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- relaxed delegate conversion [Visual Basic]
- delegates [Visual Basic], relaxed conversion
- conversions [Visual Basic], relaxed delegate
ms.assetid: 64f371d0-5416-4f65-b23b-adcbf556e81c
ms.openlocfilehash: 96941754f17326893437cdcf83c588880e010cc0
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/28/2019
ms.locfileid: "56979514"
---
# <a name="relaxed-delegate-conversion-visual-basic"></a>Swobodna konwersja delegatów (Visual Basic)
Swobodna konwersja delegatów umożliwia przypisywanie subskrypcji i funkcji do delegatów lub programów obsługi, nawet wtedy, gdy ich podpisy nie są identyczne. W związku z tym powiązania do obiektów delegowanych staje się spójne z powiązaniem już dozwolone w przypadku wywołania metody.  
  
## <a name="parameters-and-return-type"></a>Parametry oraz zwracany typ  
 Zamiast podpisu dokładne dopasowanie, swobodna konwersja wymaga spełnienia następujących warunków podczas `Option Strict` ustawiono `On`:  
  
-   Konwersję rozszerzającą musi istnieć typ danych każdego parametru na typ danych w odpowiadającym jej parametrze w funkcji przypisane lub `Sub`. W poniższym przykładzie, delegat `Del1` ma jeden parametr `Integer`. Parametr `m` w przypisanych lambda wyrażenia muszą mieć typ danych, dla którego jest konwersją rozszerzającą z `Integer`, takich jak `Long` lub `Double`.  
  
     [!code-vb[VbVbalrRelaxedDelegates#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrRelaxedDelegates/VB/Module1.vb#1)]  
  
     [!code-vb[VbVbalrRelaxedDelegates#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrRelaxedDelegates/VB/Module1.vb#2)]  
  
     Konwersje zawężające są dozwolone tylko wtedy, gdy `Option Strict` ustawiono `Off`.  
  
     [!code-vb[VbVbalrRelaxedDelegates#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrRelaxedDelegates/VB/Module2.vb#8)]  
  
-   Konwersję rozszerzającą musi istnieć w odwrotnym kierunku ze zwracanego typu funkcji przypisane lub `Sub` zwracany typ delegata. W poniższych przykładach treści każde wyrażenie lambda przypisane musi być typu danych, która rozszerza się na `Integer` ponieważ zwracany typ metody `del1` jest `Integer`.  
  
     [!code-vb[VbVbalrRelaxedDelegates#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrRelaxedDelegates/VB/Module1.vb#3)]  
  
 Jeśli `Option Strict` ustawiono `Off`, rozszerzanie ograniczeń zostanie usunięta w obu kierunkach.  
  
 [!code-vb[VbVbalrRelaxedDelegates#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrRelaxedDelegates/VB/Module2.vb#4)]  
  
## <a name="omitting-parameter-specifications"></a>Pominięcie specyfikacji parametru  
 Obniżone delegaty umożliwiają również całkowicie pominąć parametr specyfikacji w przypisanej metodzie:  
  
 [!code-vb[VbVbalrRelaxedDelegates#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrRelaxedDelegates/VB/Module1.vb#5)]  
  
 [!code-vb[VbVbalrRelaxedDelegates#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrRelaxedDelegates/VB/Module1.vb#6)]  
  
 Należy pamiętać, nie można określić niektóre parametry i pominąć innych użytkowników.  
  
 [!code-vb[VbVbalrRelaxedDelegates#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrRelaxedDelegates/VB/Module1.vb#15)]  
  
 Zdolność do pominięcia parametrów jest przydatne w sytuacji, takich jak definiowanie program obsługi zdarzeń, w której kilka parametrów złożone są zaangażowane. Argumenty, które mają niektóre procedury obsługi zdarzeń nie są używane. Zamiast tego program obsługi bezpośrednio uzyskuje dostęp do stanu kontrolki, w którym zdarzenie jest zarejestrowany i ignoruje argumenty. Obniżone delegaty umożliwiają pominięcie argumentów w takich deklaracji, gdy brak wyniku niejednoznaczności. W poniższym przykładzie w pełni określonej metody `OnClick` może być napisany `RelaxedOnClick`.  
  
```vb  
Sub OnClick(ByVal sender As Object, ByVal e As EventArgs) Handles b.Click  
    MessageBox.Show("Hello World from" + b.Text)  
End Sub  
  
Sub RelaxedOnClick() Handles b.Click  
    MessageBox.Show("Hello World from" + b.Text)  
End Sub  
```  
  
## <a name="addressof-examples"></a>Przykłady AddressOf  
 Wyrażenia lambda są używane w poprzednich przykładach ułatwia Zobacz relacje typów. Jednak sam złagodzenie są dozwolone dla przypisania delegata, które używają `AddressOf`, `Handles`, lub `AddHandler`.  
  
 W poniższym przykładzie funkcje `f1`, `f2`, `f3`, i `f4` wszystkie można przypisać do `Del1`.  
  
 [!code-vb[VbVbalrRelaxedDelegates#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrRelaxedDelegates/VB/Module1.vb#1)]  
  
 [!code-vb[VbVbalrRelaxedDelegates#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrRelaxedDelegates/VB/Module1.vb#7)]  
  
 [!code-vb[VbVbalrRelaxedDelegates#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrRelaxedDelegates/VB/Module1.vb#9)]  
  
 Poniższy przykład jest prawidłowy tylko wtedy, gdy `Option Strict` ustawiono `Off`.  
  
 [!code-vb[VbVbalrRelaxedDelegates#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrRelaxedDelegates/VB/Module2.vb#14)]  
  
## <a name="dropping-function-returns"></a>Upuszczanie zwraca — funkcja  
 Swobodna konwersja delegatów umożliwia przypisanie funkcja `Sub` delegata, efektywnie ignorowanie wartości zwracanej funkcji. Jednak nie można przypisać `Sub` delegata funkcji. W poniższym przykładzie adresu funkcji `doubler` jest przypisany do `Sub` delegować `Del3`.  
  
 [!code-vb[VbVbalrRelaxedDelegates#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrRelaxedDelegates/VB/Module1.vb#10)]  
  
 [!code-vb[VbVbalrRelaxedDelegates#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrRelaxedDelegates/VB/Module1.vb#11)]  
  
## <a name="see-also"></a>Zobacz także
- [Wyrażenia lambda](../../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)
- [Rozszerzanie i zwężanie konwersji](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
- [Delegaty](../../../../visual-basic/programming-guide/language-features/delegates/index.md)
- [Instrukcje: Przekazywanie procedur do innej procedury w Visual Basic](../../../../visual-basic/programming-guide/language-features/delegates/how-to-pass-procedures-to-another-procedure.md)
- [Wnioskowanie o typie lokalnym](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
- [Option Strict, instrukcja](../../../../visual-basic/language-reference/statements/option-strict-statement.md)
