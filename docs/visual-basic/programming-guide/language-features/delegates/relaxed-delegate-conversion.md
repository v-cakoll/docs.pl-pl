---
title: Swobodna konwersja delegatów
ms.date: 07/20/2015
helpviewer_keywords:
- relaxed delegate conversion [Visual Basic]
- delegates [Visual Basic], relaxed conversion
- conversions [Visual Basic], relaxed delegate
ms.assetid: 64f371d0-5416-4f65-b23b-adcbf556e81c
ms.openlocfilehash: ffb242842553382ba26121333c38fc65eaa168a9
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74345217"
---
# <a name="relaxed-delegate-conversion-visual-basic"></a>Swobodna konwersja delegatów (Visual Basic)
Swobodna konwersja delegatów umożliwia przypisanie funkcji do delegatów lub programów obsługi nawet wtedy, gdy ich podpisy nie są identyczne. W związku z tym powiązanie z delegatami jest spójne z powiązaniem, które jest już dozwolone dla wywołań metod.  
  
## <a name="parameters-and-return-type"></a>Parametry i zwracany typ  
 W przypadku dokładnego dopasowania podpisu przeprowadzona konwersja wymaga spełnienia następujących warunków, gdy `Option Strict` jest ustawiona na `On`:  
  
- Konwersja rozszerzająca musi istnieć z typu danych każdego parametru delegata na typ danych odpowiadającego mu parametru przypisanej funkcji lub `Sub`. W poniższym przykładzie delegat `Del1` ma jeden parametr, `Integer`. Parametr `m` w przypisanych wyrażeniach lambda musi mieć typ danych, dla którego istnieje konwersja rozszerzająca z `Integer`, taka jak `Long` lub `Double`.  
  
     [!code-vb[VbVbalrRelaxedDelegates#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrRelaxedDelegates/VB/Module1.vb#1)]  
  
     [!code-vb[VbVbalrRelaxedDelegates#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrRelaxedDelegates/VB/Module1.vb#2)]  
  
     Konwersje zawężające są dozwolone tylko wtedy, gdy `Option Strict` jest ustawiona na `Off`.  
  
     [!code-vb[VbVbalrRelaxedDelegates#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrRelaxedDelegates/VB/Module2.vb#8)]  
  
- Konwersja rozszerzająca musi istnieć w odwrotnym kierunku od typu zwracanego przypisanej funkcji lub `Sub` do zwracanego typu delegata. W poniższych przykładach treść każdego przypisanego wyrażenia lambda musi być Szacowana do typu danych, który poszerza do `Integer`, ponieważ typ zwracany `del1` jest `Integer`.  
  
     [!code-vb[VbVbalrRelaxedDelegates#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrRelaxedDelegates/VB/Module1.vb#3)]  
  
 Jeśli `Option Strict` jest ustawiona na `Off`, ograniczenie rozszerzania zostanie usunięte w obu kierunkach.  
  
 [!code-vb[VbVbalrRelaxedDelegates#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrRelaxedDelegates/VB/Module2.vb#4)]  
  
## <a name="omitting-parameter-specifications"></a>Pomijanie specyfikacji parametrów  
 W przypadku delegatów swobodnych można również całkowicie pominąć specyfikacje parametrów w przypisanej metodzie:  
  
 [!code-vb[VbVbalrRelaxedDelegates#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrRelaxedDelegates/VB/Module1.vb#5)]  
  
 [!code-vb[VbVbalrRelaxedDelegates#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrRelaxedDelegates/VB/Module1.vb#6)]  
  
 Należy pamiętać, że nie można określić niektórych parametrów i pominąć innych.  
  
 [!code-vb[VbVbalrRelaxedDelegates#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrRelaxedDelegates/VB/Module1.vb#15)]  
  
 Możliwość pominięcia parametrów jest przydatna w sytuacji, takiej jak Definiowanie procedury obsługi zdarzeń, w której występuje kilka złożonych parametrów. Argumenty niektórych programów obsługi zdarzeń nie są używane. Zamiast tego program obsługi bezpośrednio uzyskuje dostęp do stanu kontrolki, w której zdarzenie jest zarejestrowane, i ignoruje argumenty. W przypadku delegatów swobodnych można pominąć argumenty w takich deklaracjach, gdy nie niejasności wyników. W poniższym przykładzie w pełni określoną metodę `OnClick` można zapisać jako `RelaxedOnClick`.  
  
```vb  
Sub OnClick(ByVal sender As Object, ByVal e As EventArgs) Handles b.Click  
    MessageBox.Show("Hello World from" + b.Text)  
End Sub  
  
Sub RelaxedOnClick() Handles b.Click  
    MessageBox.Show("Hello World from" + b.Text)  
End Sub  
```  
  
## <a name="addressof-examples"></a>Przykłady AddressOf  
 Wyrażenia lambda są używane w poprzednich przykładach, aby można było łatwo zobaczyć relacje typu. Jednak te same złagodzenia są dozwolone dla przypisań delegatów korzystających `AddressOf`, `Handles`lub `AddHandler`.  
  
 W poniższym przykładzie funkcje `f1`, `f2`, `f3`i `f4` można przypisać do `Del1`.  
  
 [!code-vb[VbVbalrRelaxedDelegates#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrRelaxedDelegates/VB/Module1.vb#1)]  
  
 [!code-vb[VbVbalrRelaxedDelegates#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrRelaxedDelegates/VB/Module1.vb#7)]  
  
 [!code-vb[VbVbalrRelaxedDelegates#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrRelaxedDelegates/VB/Module1.vb#9)]  
  
 Poniższy przykład jest prawidłowy tylko wtedy, gdy `Option Strict` jest ustawiona na `Off`.  
  
 [!code-vb[VbVbalrRelaxedDelegates#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrRelaxedDelegates/VB/Module2.vb#14)]  
  
## <a name="dropping-function-returns"></a>Funkcja upuszczania zwraca  
 Swobodna konwersja delegatów umożliwia przypisanie funkcji do `Sub` delegata, co w efekcie ignorowanie wartości zwracanej funkcji. Nie można jednak przypisać `Sub` do delegata funkcji. W poniższym przykładzie adres funkcji `doubler` jest przypisany do `Sub` delegata `Del3`.  
  
 [!code-vb[VbVbalrRelaxedDelegates#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrRelaxedDelegates/VB/Module1.vb#10)]  
  
 [!code-vb[VbVbalrRelaxedDelegates#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrRelaxedDelegates/VB/Module1.vb#11)]  
  
## <a name="see-also"></a>Zobacz także

- [Wyrażenia lambda](../../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)
- [Rozszerzanie i zwężanie konwersji](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
- [Delegaci](../../../../visual-basic/programming-guide/language-features/delegates/index.md)
- [Instrukcje: przekazywanie procedur do innej procedury w Visual Basic](../../../../visual-basic/programming-guide/language-features/delegates/how-to-pass-procedures-to-another-procedure.md)
- [Wnioskowanie o typie lokalnym](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
- [Option Strict, instrukcja](../../../../visual-basic/language-reference/statements/option-strict-statement.md)
