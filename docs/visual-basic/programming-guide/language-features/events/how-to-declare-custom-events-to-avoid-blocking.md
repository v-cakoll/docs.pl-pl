---
title: 'Porady: deklarowanie zdarzeń niestandardowych w celu unikania blokowania'
ms.date: 07/20/2015
helpviewer_keywords:
- declaring events [Visual Basic], custom
- events [Visual Basic], custom
- custom events [Visual Basic]
ms.assetid: 998b6a90-67c5-4d2c-8b11-366d3e355505
ms.openlocfilehash: 8d73d9c4590afb33e7176f647069cafcb3a9d7d8
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74345148"
---
# <a name="how-to-declare-custom-events-to-avoid-blocking-visual-basic"></a>Porady: deklarowanie zdarzeń niestandardowych w celu unikania blokowania (Visual Basic)
Istnieją pewne sytuacje, w których należy pamiętać, że jedna procedura obsługi zdarzeń nie blokuje kolejnych programów obsługi zdarzeń. Zdarzenia niestandardowe umożliwiają zdarzeniom Asynchroniczne wywoływanie obsługi zdarzeń.  
  
 Domyślnie pole zapasowe magazynu dla deklaracji zdarzenia jest delegatem multiemisji, który szeregowo łączy wszystkie programy obsługi zdarzeń. Oznacza to, że jeśli jedna procedura obsługi zajmuje dużo czasu, program blokuje inne programy obsługi do momentu jego zakończenia. (Dobrze działające programy obsługi zdarzeń nigdy nie wykonują długotrwałych ani potencjalnie blokujących operacji).  
  
 Zamiast korzystać z domyślnej implementacji zdarzeń, które Visual Basic zapewnia, można użyć niestandardowego zdarzenia do wykonywania obsługi zdarzeń asynchronicznie.  
  
## <a name="example"></a>Przykład  
 W tym przykładzie metoda dostępu `AddHandler` dodaje delegata dla każdej procedury obsługi zdarzenia `Click` do <xref:System.Collections.ArrayList> przechowywanego w polu `EventHandlerList`.  
  
 Gdy kod wywołuje zdarzenie `Click`, metoda dostępu `RaiseEvent` wywołuje wszystkie delegatów obsługi zdarzeń asynchronicznie za pomocą metody <xref:System.Web.Services.Protocols.LogicalMethodInfo.BeginInvoke%2A>. Ta metoda wywołuje każdy program obsługi w wątku roboczym i zwraca natychmiast, dlatego programy obsługi nie mogą blokować siebie nawzajem.  
  
 [!code-vb[VbVbalrEvents#27](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#27)]  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Collections.ArrayList>
- <xref:System.Web.Services.Protocols.LogicalMethodInfo.BeginInvoke%2A>
- [Zdarzenia](../../../../visual-basic/programming-guide/language-features/events/index.md)
- [Instrukcje: deklarowanie zdarzeń niestandardowych w celu zachowywania pamięci](../../../../visual-basic/programming-guide/language-features/events/how-to-declare-custom-events-to-conserve-memory.md)
