---
title: Przegląd obsługi zdarzeń (formularze systemu Windows)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- Windows Forms, event handling
- event handling [Windows Forms], Windows Forms
- event handlers [Windows Forms], about event handlers
ms.assetid: 228112e1-1711-42ee-8ffa-ff3555bffe66
ms.openlocfilehash: 05acbfaf427060d015c2445360a7d73ebe97d070
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59186085"
---
# <a name="event-handlers-overview-windows-forms"></a>Przegląd obsługi zdarzeń (formularze systemu Windows)
Program obsługi zdarzeń jest metodą, która jest powiązana ze zdarzeniem. Gdy zdarzenie jest wywoływane, kod wewnątrz procedury obsługi zdarzeń jest wykonywany. Każdy program obsługi zdarzeń zawiera dwa parametry, które pozwalają na poprawnie obsłużyć zdarzenie. W poniższym przykładzie pokazano program obsługi zdarzeń dla <xref:System.Windows.Forms.Button> kontrolki <xref:System.Windows.Forms.Control.Click> zdarzeń.  
  
```vb  
Private Sub button1_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles button1.Click  
  
End Sub  
```  
  
```csharp  
private void button1_Click(object sender, System.EventArgs e)   
{  
  
}  
```  
  
```cpp  
private:  
  void button1_Click(System::Object ^ sender,  
    System::EventArgs ^ e)  
  {  
  
  }  
```  
  
 Pierwszy parametr`sender`, zawiera odwołanie do obiektu, który spowodował zdarzenie. Drugi parametr `e`, w powyższym przykładzie przekazuje obiekt określone zdarzenie, które jest obsługiwane. Odwołując się do właściwości obiektu (a czasami jego metod), można uzyskać informacje, takie jak lokalizacja myszy dla zdarzenia myszy lub danych przesyłanych w zdarzeniach przeciągania i upuszczania.  
  
 Zazwyczaj każde zdarzenie tworzy program obsługi zdarzeń z typem obiektu innego zdarzenia dla drugiego parametru. Niektóre procedury obsługi zdarzeń, takich jak te dotyczące <xref:System.Windows.Forms.Control.MouseDown> i <xref:System.Windows.Forms.Control.MouseUp> zdarzenia, mają ten sam typ obiektu, ich drugi parametr. Dla tych typów zdarzeń można użyć tego samego programu obsługi zdarzeń do obsługi zarówno zdarzeń.  
  
 Umożliwia także tę samą procedurę obsługi zdarzeń do obsługi tego samego zdarzenia dla różnych kontrolkach. Na przykład, jeśli istnieje grupa <xref:System.Windows.Forms.RadioButton> kontrolek w formularzu, można utworzyć jedną procedurą obsługi zdarzeń dla <xref:System.Windows.Forms.Control.Click> zdarzeń i mieć każdy formant <xref:System.Windows.Forms.Control.Click> zdarzenia powiązane z jedną procedurą obsługi zdarzeń. Aby uzyskać więcej informacji, zobacz [jak: Łączenie wielu zdarzeń jedną procedurą obsługi zdarzeń w formularzach Windows Forms](how-to-connect-multiple-events-to-a-single-event-handler-in-windows-forms.md).  
  
## <a name="see-also"></a>Zobacz także

- [Tworzenie programów obsługi zdarzeń w formularzach systemu Windows](creating-event-handlers-in-windows-forms.md)
- [Przegląd zdarzeń](events-overview-windows-forms.md)
