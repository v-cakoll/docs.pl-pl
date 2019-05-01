---
title: Wyrażenie jest wartością i dlatego nie może być elementem docelowym przypisania
ms.date: 07/20/2015
f1_keywords:
- bc30068
- vbc30068
helpviewer_keywords:
- BC30068
ms.assetid: d65141e1-f31e-4ac5-a3b8-0b2e02a71ebf
ms.openlocfilehash: 3027be6ee4ed3664b81c661b6a086a3604573833
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61802612"
---
# <a name="expression-is-a-value-and-therefore-cannot-be-the-target-of-an-assignment"></a>Wyrażenie jest wartością i dlatego nie może być elementem docelowym przypisania
Instrukcja próbuje przypisać wartość wyrażenia. W czasie wykonywania, można przypisać wartości tylko do zapisu zmiennej, właściwości lub elementu tablicy. W poniższym przykładzie pokazano, jak ten błąd może wystąpić.  
  
```  
Dim yesterday As Integer  
ReadOnly maximum As Integer = 45  
yesterday + 1 = DatePart(DateInterval.Day, Now)  
' The preceding line is an ERROR because of an expression on the left.  
maximum = 50  
' The preceding line is an ERROR because maximum is declared ReadOnly.  
```  
  
 Podobne przykłady można zastosować do właściwości i elementy tablicy.  
  
 **Bezpośredni dostęp.** Pośredni dostęp za pośrednictwem typu wartości można również wygenerować ten błąd. Należy wziąć pod uwagę poniższy przykład kodu, który próbuje ustawić wartość <xref:System.Drawing.Point> uzyskując pośrednio za pomocą <xref:System.Windows.Forms.Control.Location%2A>.  
  
```  
' Assume this code runs inside Form1.  
Dim exitButton As New System.Windows.Forms.Button()  
exitButton.Text = "Exit this form"  
exitButton.Location.X = 140  
' The preceding line is an ERROR because of no storage for Location.  
```  
  
 Ostatnią instrukcją poprzedni przykład nie powiedzie się, ponieważ powoduje to utworzenie tymczasowego alokacji dla <xref:System.Drawing.Point> zwracany przez strukturę <xref:System.Windows.Forms.Control.Location%2A> właściwości. Struktura jest typem wartości, a struktura tymczasowe nie są zachowywane po uruchomieniu instrukcji. Problem został rozwiązany przez deklarowanie i użycie zmiennej dla <xref:System.Windows.Forms.Control.Location%2A>, co powoduje utworzenie bardziej trwałych alokacji dla <xref:System.Drawing.Point> struktury. Poniższy przykład pokazuje kod, który można zastąpić ostatnią instrukcję w poprzednim przykładzie.  
  
```  
Dim exitLocation as New System.Drawing.Point(140, exitButton.Location.Y)  
exitButton.Location = exitLocation  
```  
  
 **Identyfikator błędu:** BC30068  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
- Jeśli instrukcja przypisuje wartość do wyrażenia, Zamień wyrażenia pojedynczej zmiennej zapisywalny, właściwości lub elementu tablicy.  
  
- Jeśli instrukcja sprawia, że pośredni dostęp za pośrednictwem typu wartości (zwykle struktura), należy utworzyć zmienną typu wartości.  
  
- Przypisz odpowiednią strukturę (lub innego typu wartości) do zmiennej.  
  
- Umożliwia dostęp do właściwości, aby przypisać wartość zmiennej.  
  
## <a name="see-also"></a>Zobacz także

- [Operatory i wyrażenia](../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)
- [Instrukcje](../../../visual-basic/programming-guide/language-features/statements.md)
- [Rozwiązywanie problemów z procedurami](../../../visual-basic/programming-guide/language-features/procedures/troubleshooting-procedures.md)
