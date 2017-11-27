---
title: "Wyrażenie jest wartością i dlatego nie może być elementem docelowym przypisania"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- bc30068
- vbc30068
helpviewer_keywords: BC30068
ms.assetid: d65141e1-f31e-4ac5-a3b8-0b2e02a71ebf
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: bec3e2d298160bd0b459dc3b7ef93b94648e439a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="expression-is-a-value-and-therefore-cannot-be-the-target-of-an-assignment"></a>Wyrażenie jest wartością i dlatego nie może być elementem docelowym przypisania
Instrukcja podejmuje próbę przypisania wartości dla wyrażenia. Można przypisać wartość tylko do zapisu zmienną, właściwością lub element tablicy w czasie wykonywania. Poniższy przykład przedstawia, jak ten błąd może wystąpić.  
  
```  
Dim yesterday As Integer  
ReadOnly maximum As Integer = 45  
yesterday + 1 = DatePart(DateInterval.Day, Now)  
' The preceding line is an ERROR because of an expression on the left.  
maximum = 50  
' The preceding line is an ERROR because maximum is declared ReadOnly.  
```  
  
 Podobne przykłady można zastosować do właściwości i elementów tablicy.  
  
 **Pośredni dostęp.** Pośredni dostęp do typu wartości można również generować tego błędu. Należy wziąć pod uwagę poniższy przykład kodu, który próbuje ustawić wartość <xref:System.Drawing.Point> uzyskując pośredni przez <xref:System.Windows.Forms.Control.Location%2A>.  
  
```  
' Assume this code runs inside Form1.  
Dim exitButton As New System.Windows.Forms.Button()  
exitButton.Text = "Exit this form"  
exitButton.Location.X = 140  
' The preceding line is an ERROR because of no storage for Location.  
```  
  
 Ostatnią instrukcją w poprzednim przykładzie nie powiedzie się, ponieważ spowoduje to utworzenie tymczasowego alokacji dla <xref:System.Drawing.Point> zwrócony przez strukturę <xref:System.Windows.Forms.Control.Location%2A> właściwości. Struktura jest typem wartości, a struktura tymczasowe nie są zachowywane po wykonaniu instrukcji. Problem został rozwiązany przez deklarowanie i użycie zmiennej <xref:System.Windows.Forms.Control.Location%2A>, co powoduje stałej alokacji dla <xref:System.Drawing.Point> struktury. Poniższy przykład przedstawia kod, który można zastąpić ostatniej instrukcji w poprzednim przykładzie.  
  
```  
Dim exitLocation as New System.Drawing.Point(140, exitButton.Location.Y)  
exitButton.Location = exitLocation  
```  
  
 **Identyfikator błędu:** BC30068  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
-   Jeśli instrukcja przypisuje wartość do wyrażenia, Zastąp wyrażenie pojedynczą zmienną zapisywalny, właściwość lub element tablicy.  
  
-   Jeśli instrukcja dokonuje bezpośredni dostęp do typu wartość (zazwyczaj struktury), Utwórz zmienną do przechowywania wartości typu.  
  
-   Przypisz odpowiednie struktury (lub innego typu wartość) do zmiennej.  
  
-   Umożliwia dostęp do właściwości, aby przypisać wartość zmiennej.  
  
## <a name="see-also"></a>Zobacz też  
 [Operatory i wyrażenia](../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)  
 [Instrukcje](../../../visual-basic/programming-guide/language-features/statements.md)  
 [Procedury rozwiązywania problemów](../../../visual-basic/programming-guide/language-features/procedures/troubleshooting-procedures.md)
