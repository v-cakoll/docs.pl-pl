---
title: Przegląd programów obsługi zdarzeń
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
ms.openlocfilehash: ffec8a9f8e080dec78152e62e00e2dceefbdaab0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79141695"
---
# <a name="event-handlers-overview-windows-forms"></a>Przegląd obsługi zdarzeń (formularze systemu Windows)
Program obsługi zdarzeń jest metodą, która jest powiązana ze zdarzeniem. Gdy zdarzenie jest wywoływane, kod w programie obsługi zdarzeń jest wykonywany. Każdy program obsługi zdarzeń zawiera dwa parametry, które umożliwiają prawidłowe obsługę zdarzenia. W poniższym przykładzie pokazano <xref:System.Windows.Forms.Button> program <xref:System.Windows.Forms.Control.Click> obsługi zdarzeń dla zdarzenia formantu.  
  
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
  
 Pierwszy parametr`sender`, zawiera odwołanie do obiektu, który wywołał zdarzenie. Drugi parametr, `e`w powyższym przykładzie, przekazuje obiekt specyficzny dla zdarzenia, które jest obsługiwane. Odwołując się do właściwości obiektu (i czasami jego metod), można uzyskać informacje, takie jak lokalizacja myszy dla zdarzeń myszy lub dane przesyłane w zdarzeniach przeciągania i upuszczania.  
  
 Zazwyczaj każde zdarzenie tworzy program obsługi zdarzeń z innym typem obiektu zdarzenia dla drugiego parametru. Niektóre programy obsługi zdarzeń, takie <xref:System.Windows.Forms.Control.MouseDown> <xref:System.Windows.Forms.Control.MouseUp> jak te dla i zdarzeń, mają ten sam typ obiektu dla ich drugiego parametru. Dla tego typu zdarzeń można użyć tego samego programu obsługi zdarzeń do obsługi obu zdarzeń.  
  
 Można również użyć tego samego programu obsługi zdarzeń do obsługi tego samego zdarzenia dla różnych formantów. Na przykład jeśli masz grupę formantów w formularzu, można <xref:System.Windows.Forms.Control.Click> utworzyć jeden program obsługi <xref:System.Windows.Forms.Control.Click> zdarzeń dla zdarzenia i mają każde zdarzenie formantu powiązane z obsługi pojedynczego <xref:System.Windows.Forms.RadioButton> zdarzenia. Aby uzyskać więcej informacji, zobacz [Jak: Łączenie wielu zdarzeń z pojedynczym programem obsługi zdarzeń w formularzach systemu Windows](how-to-connect-multiple-events-to-a-single-event-handler-in-windows-forms.md).  
  
## <a name="see-also"></a>Zobacz też

- [Tworzenie procedur obsługi zdarzeń w formularzach Windows Forms](creating-event-handlers-in-windows-forms.md)
- [Przegląd zdarzeń](events-overview-windows-forms.md)
