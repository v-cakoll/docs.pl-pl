---
title: "Przegląd obsługi zdarzeń (formularze systemu Windows)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- Windows Forms, event handling
- event handling [Windows Forms], Windows Forms
- event handlers [Windows Forms], about event handlers
ms.assetid: 228112e1-1711-42ee-8ffa-ff3555bffe66
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 7353f3ab4513d8331b1d38cb01ad16c7d3cde165
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="event-handlers-overview-windows-forms"></a>Przegląd obsługi zdarzeń (formularze systemu Windows)
Program obsługi zdarzeń jest to metoda, która jest powiązany ze zdarzeniem. Gdy zdarzenie jest zgłaszane, wykonywany jest kod wewnątrz obsługi zdarzeń. Każdy program obsługi zdarzeń zawiera dwa parametry, które umożliwiają obsługę zdarzenia poprawnie. W poniższym przykładzie przedstawiono program obsługi zdarzeń dla <xref:System.Windows.Forms.Button> formantu <xref:System.Windows.Forms.Control.Click> zdarzeń.  
  
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
  
 Pierwszy parametr`sender`, zawiera odwołanie do obiektu, który wywołał zdarzenie. Drugi parametr `e`, w powyższym przykładzie przekazuje obiekt określone zdarzenie, które jest obsługiwane. Za pomocą odwołań do właściwości obiektu (i jego metody), możesz uzyskać informacje, takie jak lokalizacja myszy dla zdarzenia myszy lub danych przesyłanych w przeciągania i upuszczania.  
  
 Zazwyczaj każde zdarzenie tworzy program obsługi zdarzeń typu inny obiekt zdarzenia dla drugiego parametru. Niektóre programy obsługi zdarzeń, takich jak te dotyczące <xref:System.Windows.Forms.Control.MouseDown> i <xref:System.Windows.Forms.Control.MouseUp> zdarzenia, mają ten sam typ obiektu dla ich drugiego parametru. W przypadku tych typów zdarzeń można użyć tej procedury obsługi zdarzeń do obsługi zarówno zdarzeń.  
  
 Umożliwia także tej procedury obsługi zdarzeń do obsługi tego samego zdarzenia dla inne formanty. Na przykład, jeśli istnieje grupa <xref:System.Windows.Forms.RadioButton> formantów w formularzu, można utworzyć jednym programem obsługi zdarzeń dla <xref:System.Windows.Forms.Control.Click> zdarzeń i każdej kontrolki <xref:System.Windows.Forms.Control.Click> zdarzenia powiązane z obsługą jednego zdarzenia. Aby uzyskać więcej informacji, zobacz [porady: łączenie wielu zdarzeń pojedynczego obsługi zdarzeń w formularzach systemu Windows](../../../docs/framework/winforms/how-to-connect-multiple-events-to-a-single-event-handler-in-windows-forms.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Tworzenie programów obsługi zdarzeń w formularzach systemu Windows](../../../docs/framework/winforms/creating-event-handlers-in-windows-forms.md)  
 [Przegląd zdarzeń](../../../docs/framework/winforms/events-overview-windows-forms.md)
