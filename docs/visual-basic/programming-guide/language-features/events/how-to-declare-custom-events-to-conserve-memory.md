---
title: 'Instrukcje: Deklarowanie zdarzeń niestandardowych w celu zachowywania pamięci (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- declaring events [Visual Basic], custom
- events [Visual Basic], custom
- custom events [Visual Basic]
ms.assetid: 87ebee87-260c-462f-979c-407874debd19
ms.openlocfilehash: 3bd58a09d016d818c4cc88c1d2527e81a95411e6
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/28/2019
ms.locfileid: "56967129"
---
# <a name="how-to-declare-custom-events-to-conserve-memory-visual-basic"></a>Instrukcje: Deklarowanie zdarzeń niestandardowych w celu zachowywania pamięci (Visual Basic)
Istnieje kilka sytuacji po ważne jest, że aplikacja niskich jej użycie pamięci. Zdarzenia niestandardowe Zezwól aplikacji na potrzeby pamięci tylko zdarzenia, które obsługuje.  
  
 Domyślnie gdy klasa deklaruje zdarzenie, kompilator przydziela pamięć dla pola do przechowywania informacji o zdarzeniach. Jeśli klasa ma wiele zdarzeń nieużywane, niepotrzebnie zajmowały pamięci.  
  
 Zamiast Domyślna implementacja zdarzeń, które zapewnia Visual Basic, można użyć zdarzeń niestandardowych do bardziej dokładnie zarządzać wykorzystaniem pamięci.  
  
## <a name="example"></a>Przykład  
 W tym przykładzie klasa używa jednego wystąpienia <xref:System.ComponentModel.EventHandlerList> klasy, przechowywane w `Events` pola do przechowywania informacji o zdarzeniach w użyciu. <xref:System.ComponentModel.EventHandlerList> Klasa jest klasą zoptymalizowane listy przeznaczone do przechowywania delegatów.  
  
 Wszystkie zdarzenia z użyciem klasy `Events` pola do śledzenia metod obsługi każdego zdarzenia.  
  
 [!code-vb[VbVbalrEvents#22](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#22)]  
  
## <a name="see-also"></a>Zobacz także
- <xref:System.ComponentModel.EventHandlerList>
- [Zdarzenia](../../../../visual-basic/programming-guide/language-features/events/index.md)
- [Instrukcje: Deklarowanie zdarzeń niestandardowych w celu unikania blokowania](../../../../visual-basic/programming-guide/language-features/events/how-to-declare-custom-events-to-avoid-blocking.md)
