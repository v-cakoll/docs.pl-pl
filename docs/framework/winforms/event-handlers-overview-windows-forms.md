---
title: Przegląd obsługi zdarzeń
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
ms.openlocfilehash: 10ba458197973ede35849a86fec35003f139b8d2
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76743496"
---
# <a name="event-handlers-overview-windows-forms"></a>Przegląd obsługi zdarzeń (formularze systemu Windows)
Program obsługi zdarzeń to metoda, która jest powiązana ze zdarzeniem. Po wywołaniu zdarzenia kod w ramach programu obsługi zdarzeń jest wykonywany. Każdy program obsługi zdarzeń zawiera dwa parametry, które umożliwiają prawidłowe obsłużenie zdarzenia. Poniższy przykład pokazuje procedurę obsługi zdarzeń dla zdarzenia <xref:System.Windows.Forms.Control.Click> formantu <xref:System.Windows.Forms.Button>.  
  
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
  
 Pierwszy parametr,`sender`, zawiera odwołanie do obiektu, który wywołał zdarzenie. Drugi parametr, `e`w powyższym przykładzie przekazuje obiekt specyficzny dla zdarzenia, które jest obsługiwane. Odwołując się do właściwości obiektu (i, czasami, jego metody), można uzyskać informacje takie jak lokalizacja myszy dla zdarzeń myszy lub danych transferowanych w zdarzeniach przeciągania i upuszczania.  
  
 Zwykle każde zdarzenie generuje procedurę obsługi zdarzeń z innym typem obiektu zdarzenia dla drugiego parametru. Niektóre programy obsługi zdarzeń, takie jak te dla zdarzeń <xref:System.Windows.Forms.Control.MouseDown> i <xref:System.Windows.Forms.Control.MouseUp>, mają ten sam typ obiektu dla drugiego parametru. W przypadku tych typów zdarzeń można użyć tego samego programu obsługi zdarzeń do obsługi obu zdarzeń.  
  
 Można również użyć tego samego programu obsługi zdarzeń, aby obsłużyć to samo zdarzenie dla różnych kontrolek. Na przykład jeśli masz grupę formantów <xref:System.Windows.Forms.RadioButton> na formularzu, można utworzyć pojedynczy program obsługi zdarzeń dla zdarzenia <xref:System.Windows.Forms.Control.Click> i mieć zdarzenie <xref:System.Windows.Forms.Control.Click> poszczególnych kontrolek powiązane z obsługą pojedynczego zdarzenia. Aby uzyskać więcej informacji, zobacz [jak: łączenie wielu zdarzeń z obsługą pojedynczego zdarzenia w Windows Forms](how-to-connect-multiple-events-to-a-single-event-handler-in-windows-forms.md).  
  
## <a name="see-also"></a>Zobacz także

- [Tworzenie procedur obsługi zdarzeń w formularzach Windows Forms](creating-event-handlers-in-windows-forms.md)
- [Przegląd zdarzeń](events-overview-windows-forms.md)
