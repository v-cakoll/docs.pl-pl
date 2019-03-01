---
title: 'Instrukcje: Deklarowanie zdarzeń niestandardowych w celu unikania blokowania (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- declaring events [Visual Basic], custom
- events [Visual Basic], custom
- custom events [Visual Basic]
ms.assetid: 998b6a90-67c5-4d2c-8b11-366d3e355505
ms.openlocfilehash: fe8775a15ce5149cf307879ab31e2ec0a8ba8f47
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/28/2019
ms.locfileid: "56965179"
---
# <a name="how-to-declare-custom-events-to-avoid-blocking-visual-basic"></a>Instrukcje: Deklarowanie zdarzeń niestandardowych w celu unikania blokowania (Visual Basic)
Istnieją kilka okoliczności, gdy jest ważne, że jedna procedura obsługi zdarzeń blokuje obsługi kolejnych zdarzeń. Zdarzenia niestandardowe umożliwiają zdarzenia asynchroniczne wywoływanie swoich programów obsługi zdarzeń.  
  
 Domyślnie pole Magazyn zapasowy deklaracji zdarzenia jest multiemisji delegat, który łączy szeregowo wszystkich procedur obsługi zdarzeń. Oznacza to, że jeśli jeden program obsługi zajmuje dużo czasu, blokuje innych programów obsługi przed zakończeniem tego procesu. (Procedury obsługi zdarzeń dobrze działające nigdy nie należy wykonywać operacji długotrwałej lub mogącego powodować blokowanie.)  
  
 Zamiast Domyślna implementacja zdarzeń, które zapewnia Visual Basic, można użyć niestandardowego zdarzenia asynchroniczne wykonywanie procedur obsługi zdarzeń.  
  
## <a name="example"></a>Przykład  
 W tym przykładzie `AddHandler` akcesor dodaje delegata dla każdego program obsługi `Click` zdarzenia <xref:System.Collections.ArrayList> przechowywane w `EventHandlerList` pola.  
  
 Gdy kod wywołuje `Click` zdarzenia `RaiseEvent` akcesor wywołuje wszystkie delegatów obsługi zdarzeń asynchronicznie za pomocą <xref:System.Web.Services.Protocols.LogicalMethodInfo.BeginInvoke%2A> metody. Ta metoda wywołuje każdy program obsługi w wątku roboczego i zwraca wynik natychmiast, więc obsługi nie można zablokować siebie nawzajem.  
  
 [!code-vb[VbVbalrEvents#27](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#27)]  
  
## <a name="see-also"></a>Zobacz także
- <xref:System.Collections.ArrayList>
- <xref:System.Web.Services.Protocols.LogicalMethodInfo.BeginInvoke%2A>
- [Zdarzenia](../../../../visual-basic/programming-guide/language-features/events/index.md)
- [Instrukcje: Deklarowanie zdarzeń niestandardowych w celu zachowywania pamięci](../../../../visual-basic/programming-guide/language-features/events/how-to-declare-custom-events-to-conserve-memory.md)
