---
title: Zdarzenia w formantach formularzy systemu Windows
ms.date: 03/30/2017
helpviewer_keywords:
- events [Windows Forms], custom controls (using code)
- custom controls [Windows Forms], events overview (using code)
ms.assetid: 7e3d1379-87aa-437c-afce-c99454eff30e
ms.openlocfilehash: d18938565c302be085b7ac51f878d83ae5ab533d
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/05/2018
ms.locfileid: "43746772"
---
# <a name="events-in-windows-forms-controls"></a>Zdarzenia w formantach formularzy systemu Windows
Formant programu Windows Forms dziedziczy więcej niż 60 zdarzenia z <xref:System.Windows.Forms.Control?displayProperty=nameWithType>. Obejmują one <xref:System.Windows.Forms.Control.Paint> zdarzenie, które powoduje formantu, który ma być rysowany, zdarzenia związane z wyświetlania okna, takie jak <xref:System.Windows.Forms.Control.Resize> i <xref:System.Windows.Forms.Control.Layout> zdarzeń i niskiego poziomu zdarzeń myszy i klawiatury. Niektóre zdarzenia niskiego poziomu są przekształcony przez <xref:System.Windows.Forms.Control> zdarzeniach semantycznych, takich jak <xref:System.Windows.Forms.Control.Click> i <xref:System.Windows.Forms.Control.DoubleClick>. Aby uzyskać szczegółowe informacje o zdarzeniach dziedziczone, zobacz <xref:System.Windows.Forms.Control>.  
  
 Jeśli niestandardową kontrolkę musi zastąpić funkcjonalność zdarzeń dziedziczone, zastąpić dziedziczonego `On` *EventName* metody zamiast dołączając delegata. Jeśli nie znasz modelu zdarzeń w programie .NET Framework, zobacz [Raising Events ze składnika](https://msdn.microsoft.com/library/9aebf605-a87d-470b-b7c8-f9abfc8360a0).  
  
## <a name="see-also"></a>Zobacz też  
 [Przesłanianie metody OnPaint](../../../../docs/framework/winforms/controls/overriding-the-onpaint-method.md)  
 [Obsługa danych wejściowych użytkownika](../../../../docs/framework/winforms/controls/handling-user-input.md)  
 [Definiowanie zdarzenia](../../../../docs/framework/winforms/controls/defining-an-event-in-windows-forms-controls.md)  
 [Zdarzenia](../../../../docs/standard/events/index.md)
