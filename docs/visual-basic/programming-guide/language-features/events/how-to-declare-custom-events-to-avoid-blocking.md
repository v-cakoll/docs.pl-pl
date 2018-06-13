---
title: 'Porady: deklarowanie zdarzeń niestandardowych w celu unikania blokowania (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- declaring events [Visual Basic], custom
- events [Visual Basic], custom
- custom events [Visual Basic]
ms.assetid: 998b6a90-67c5-4d2c-8b11-366d3e355505
ms.openlocfilehash: 3cb66aed71195d2fd2335fbd59cc499b3dbf808e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33646929"
---
# <a name="how-to-declare-custom-events-to-avoid-blocking-visual-basic"></a>Porady: deklarowanie zdarzeń niestandardowych w celu unikania blokowania (Visual Basic)
Istnieją kilka okoliczności, gdy należy pamiętać, że jedna procedura obsługi zdarzeń blokuje obsługi kolejnych zdarzeń. Zdarzenia niestandardowe umożliwiają zdarzenia asynchroniczne wywoływanie jej obsługi zdarzeń.  
  
 Domyślnie pole magazynu zapasowego deklaracji zdarzenia jest multiemisji delegata, który kolejno łączy obsługi zdarzeń. Oznacza to, że jeśli jednej procedury obsługi trwa długo, blokuje innych programów obsługi dopóki nie ukończy. (Procedury obsługi zdarzeń dobrze działające nigdy nie należy wykonywać operacje długie lub potencjalnie blokujące.)  
  
 Zamiast Domyślna implementacja zdarzeń, które zapewnia Visual Basic, niestandardowe zdarzenia można używać do wykonywania programów obsługi zdarzeń asynchronicznie.  
  
## <a name="example"></a>Przykład  
 W tym przykładzie `AddHandler` akcesor dodaje delegowanie dla każdego obsługi `Click` zdarzenia <xref:System.Collections.ArrayList> przechowywane w `EventHandlerList` pola.  
  
 Gdy kod generuje `Click` zdarzeń, `RaiseEvent` akcesor wywołuje wszystkie delegatów obsługi zdarzeń asynchronicznie za pomocą <xref:System.Web.Services.Protocols.LogicalMethodInfo.BeginInvoke%2A> metody. Ta metoda wywołuje każdy program obsługi na wątku roboczego i zwraca natychmiast, więc obsługi nie można zablokować siebie nawzajem.  
  
 [!code-vb[VbVbalrEvents#27](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/how-to-declare-custom-events-to-avoid-blocking_1.vb)]  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Collections.ArrayList>  
 <xref:System.Web.Services.Protocols.LogicalMethodInfo.BeginInvoke%2A>  
 [Zdarzenia](../../../../visual-basic/programming-guide/language-features/events/index.md)  
 [Instrukcje: deklarowanie zdarzeń niestandardowych w celu zachowywania pamięci](../../../../visual-basic/programming-guide/language-features/events/how-to-declare-custom-events-to-conserve-memory.md)
