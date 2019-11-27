---
title: 'Porady: deklarowanie zdarzeń niestandardowych w celu zachowywania pamięci'
ms.date: 07/20/2015
helpviewer_keywords:
- declaring events [Visual Basic], custom
- events [Visual Basic], custom
- custom events [Visual Basic]
ms.assetid: 87ebee87-260c-462f-979c-407874debd19
ms.openlocfilehash: 3cc2d3ea57f1a8daf704c2c929baf3f2acf78c17
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74345130"
---
# <a name="how-to-declare-custom-events-to-conserve-memory-visual-basic"></a>Porady: deklarowanie zdarzeń niestandardowych w celu zachowywania pamięci (Visual Basic)
Istnieje kilka okoliczności, w których ważna jest niska użycie pamięci przez aplikację. Zdarzenia niestandardowe umożliwiają aplikacji używanie pamięci tylko dla zdarzeń, które obsługuje.  
  
 Domyślnie, gdy Klasa deklaruje zdarzenie, kompilator przydziela pamięć dla pola do przechowywania informacji o zdarzeniu. Jeśli klasa ma wiele nieużywanych zdarzeń, niepotrzebnie zajmują pamięć.  
  
 Zamiast korzystać z domyślnej implementacji zdarzeń, które Visual Basic zapewnia, można użyć niestandardowych zdarzeń do szczegółowego zarządzania użyciem pamięci.  
  
## <a name="example"></a>Przykład  
 W tym przykładzie Klasa używa jednego wystąpienia klasy <xref:System.ComponentModel.EventHandlerList>, która jest przechowywana w polu `Events`, do przechowywania informacji o zdarzeniach w użyciu. Klasa <xref:System.ComponentModel.EventHandlerList> jest zoptymalizowaną klasą listy zaprojektowaną do przechowywania delegatów.  
  
 Wszystkie zdarzenia w klasie używają pola `Events`, aby śledzić, które metody obsługują każde zdarzenie.  
  
 [!code-vb[VbVbalrEvents#22](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#22)]  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.ComponentModel.EventHandlerList>
- [Zdarzenia](../../../../visual-basic/programming-guide/language-features/events/index.md)
- [Instrukcje: deklarowanie zdarzeń niestandardowych w celu unikania blokowania](../../../../visual-basic/programming-guide/language-features/events/how-to-declare-custom-events-to-avoid-blocking.md)
