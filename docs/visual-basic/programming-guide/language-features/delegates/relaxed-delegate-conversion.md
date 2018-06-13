---
title: Swobodna konwersja delegatów (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- relaxed delegate conversion [Visual Basic]
- delegates [Visual Basic], relaxed conversion
- conversions [Visual Basic], relaxed delegate
ms.assetid: 64f371d0-5416-4f65-b23b-adcbf556e81c
ms.openlocfilehash: c4a41bf74716a6ea7d3c1139651834acccf27657
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33650832"
---
# <a name="relaxed-delegate-conversion-visual-basic"></a>Swobodna konwersja delegatów (Visual Basic)
Swobodna konwersja delegatów umożliwia przypisanie subskrypcji i funkcji do delegatów lub obsługi, nawet wtedy, gdy ich podpisów nie są identyczne. W związku z tym powiązanie do obiektów delegowanych staje się spójne z powiązaniem już dozwolone dla wywołań metod.  
  
## <a name="parameters-and-return-type"></a>Parametry oraz zwracany typ  
 Zamiast podpisu dokładnego dopasowania, swobodna konwersja wymaga spełnienia następujących warunków podczas `Option Strict` ma ustawioną wartość `On`:  
  
-   Konwersję rozszerzającą musi istnieć od każdego parametru delegowanego typu danych na typ danych odpowiadającego mu parametru funkcji przypisanej lub `Sub`. W poniższym przykładzie, delegat `Del1` ma jeden parametr `Integer`. Parametr `m` w przypisanej lambda wyrażenia musi mieć typ danych, dla którego jest konwersję rozszerzającą z `Integer`, takich jak `Long` lub `Double`.  
  
     [!code-vb[VbVbalrRelaxedDelegates#1](../../../../visual-basic/programming-guide/language-features/delegates/codesnippet/VisualBasic/relaxed-delegate-conversion_1.vb)]  
  
     [!code-vb[VbVbalrRelaxedDelegates#2](../../../../visual-basic/programming-guide/language-features/delegates/codesnippet/VisualBasic/relaxed-delegate-conversion_2.vb)]  
  
     Konwersji zawężającej są dozwolone tylko wtedy, gdy `Option Strict` ma ustawioną wartość `Off`.  
  
     [!code-vb[VbVbalrRelaxedDelegates#8](../../../../visual-basic/programming-guide/language-features/delegates/codesnippet/VisualBasic/relaxed-delegate-conversion_3.vb)]  
  
-   Konwersję rozszerzającą musi istnieć w przeciwnym kierunku z zwracany typ funkcji przypisanej lub `Sub` na zwracany typ delegata. W poniższych przykładach treści każde wyrażenie lambda przypisanej musi być typem danych rozszerzająca do `Integer` ponieważ zwracany typ funkcji `del1` jest `Integer`.  
  
     [!code-vb[VbVbalrRelaxedDelegates#3](../../../../visual-basic/programming-guide/language-features/delegates/codesnippet/VisualBasic/relaxed-delegate-conversion_4.vb)]  
  
 Jeśli `Option Strict` ma ustawioną wartość `Off`, rozszerzanie ograniczenie zostało usunięte w obu kierunkach.  
  
 [!code-vb[VbVbalrRelaxedDelegates#4](../../../../visual-basic/programming-guide/language-features/delegates/codesnippet/VisualBasic/relaxed-delegate-conversion_5.vb)]  
  
## <a name="omitting-parameter-specifications"></a>Pominięcie specyfikacji parametru  
 Swobodna delegatów pozwalają również całkowicie pominąć specyfikacje parametru w metodzie przypisanej:  
  
 [!code-vb[VbVbalrRelaxedDelegates#5](../../../../visual-basic/programming-guide/language-features/delegates/codesnippet/VisualBasic/relaxed-delegate-conversion_6.vb)]  
  
 [!code-vb[VbVbalrRelaxedDelegates#6](../../../../visual-basic/programming-guide/language-features/delegates/codesnippet/VisualBasic/relaxed-delegate-conversion_7.vb)]  
  
 Należy pamiętać, nie można określić niektóre parametry i Pomiń innych użytkowników.  
  
 [!code-vb[VbVbalrRelaxedDelegates#15](../../../../visual-basic/programming-guide/language-features/delegates/codesnippet/VisualBasic/relaxed-delegate-conversion_8.vb)]  
  
 Pomiń parametry jest przydatne w sytuacji, takie jak Definiowanie obsługi zdarzeń, w którym są związane z kilku parametrów złożonych. Argumenty do niektórych programów obsługi zdarzeń nie są używane. Zamiast tego program obsługi bezpośredni dostęp do stanu formantu, na którym zdarzenie jest zarejestrowany i ignoruje argumentów. Swobodna delegatów umożliwiają Pomiń argumentów oświadczenia, jeśli żadnego wyniku niejednoznaczności. W poniższym przykładzie pełni określonej metody `OnClick` można przepisany `RelaxedOnClick`.  
  
```vb  
Sub OnClick(ByVal sender As Object, ByVal e As EventArgs) Handles b.Click  
    MessageBox.Show("Hello World from" + b.Text)  
End Sub  
  
Sub RelaxedOnClick() Handles b.Click  
    MessageBox.Show("Hello World from" + b.Text)  
End Sub  
```  
  
## <a name="addressof-examples"></a>Przykłady AddressOf  
 Wyrażenia lambda są używane w poprzednich przykładach ułatwia Zobacz relacje typu. Jednak sam złagodzenie są dozwolone dla przypisania delegata, które używają `AddressOf`, `Handles`, lub `AddHandler`.  
  
 W poniższym przykładzie funkcje `f1`, `f2`, `f3`, i `f4` wszystkie można przypisać do `Del1`.  
  
 [!code-vb[VbVbalrRelaxedDelegates#1](../../../../visual-basic/programming-guide/language-features/delegates/codesnippet/VisualBasic/relaxed-delegate-conversion_1.vb)]  
  
 [!code-vb[VbVbalrRelaxedDelegates#7](../../../../visual-basic/programming-guide/language-features/delegates/codesnippet/VisualBasic/relaxed-delegate-conversion_9.vb)]  
  
 [!code-vb[VbVbalrRelaxedDelegates#9](../../../../visual-basic/programming-guide/language-features/delegates/codesnippet/VisualBasic/relaxed-delegate-conversion_10.vb)]  
  
 Poniższy przykład jest prawidłowe tylko w przypadku `Option Strict` ma ustawioną wartość `Off`.  
  
 [!code-vb[VbVbalrRelaxedDelegates#14](../../../../visual-basic/programming-guide/language-features/delegates/codesnippet/VisualBasic/relaxed-delegate-conversion_11.vb)]  
  
## <a name="dropping-function-returns"></a>Porzucanie zwraca — funkcja  
 Swobodna konwersja delegatów umożliwia przypisanie funkcji, aby `Sub` delegata, efektywnie ignorowanie zwracana wartość funkcji. Jednak nie można przypisać `Sub` do delegata funkcji. W poniższym przykładzie adresu funkcji `doubler` jest przypisany do `Sub` delegować `Del3`.  
  
 [!code-vb[VbVbalrRelaxedDelegates#10](../../../../visual-basic/programming-guide/language-features/delegates/codesnippet/VisualBasic/relaxed-delegate-conversion_12.vb)]  
  
 [!code-vb[VbVbalrRelaxedDelegates#11](../../../../visual-basic/programming-guide/language-features/delegates/codesnippet/VisualBasic/relaxed-delegate-conversion_13.vb)]  
  
## <a name="see-also"></a>Zobacz też  
 [Wyrażenia lambda](../../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)  
 [Rozszerzanie i zwężanie konwersji](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)  
 [Delegaci](../../../../visual-basic/programming-guide/language-features/delegates/index.md)  
 [Porady: przekazywanie procedur do innej procedury w Visual Basic](../../../../visual-basic/programming-guide/language-features/delegates/how-to-pass-procedures-to-another-procedure.md)  
 [Wnioskowanie o typie lokalnym](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)  
 [Option Strict, instrukcja](../../../../visual-basic/language-reference/statements/option-strict-statement.md)
