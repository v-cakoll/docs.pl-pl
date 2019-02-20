---
title: Zdarzenia w formantach formularzy systemu Windows
ms.date: 03/30/2017
helpviewer_keywords:
- events [Windows Forms], custom controls (using code)
- custom controls [Windows Forms], events overview (using code)
ms.assetid: 7e3d1379-87aa-437c-afce-c99454eff30e
ms.openlocfilehash: 56de08f039fd4dee9dcc5a1b3f86cc0e8e577b43
ms.sourcegitcommit: acd8ed14fe94e9d4e3a7fb685fe83d05e941073c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/20/2019
ms.locfileid: "56442441"
---
# <a name="events-in-windows-forms-controls"></a>Zdarzenia w formantach formularzy systemu Windows
Formant programu Windows Forms dziedziczy więcej niż 60 zdarzenia z <xref:System.Windows.Forms.Control?displayProperty=nameWithType>. Obejmują one <xref:System.Windows.Forms.Control.Paint> zdarzenie, które powoduje formantu, który ma być rysowany, zdarzenia związane z wyświetlania okna, takie jak <xref:System.Windows.Forms.Control.Resize> i <xref:System.Windows.Forms.Control.Layout> zdarzeń i niskiego poziomu zdarzeń myszy i klawiatury. Niektóre zdarzenia niskiego poziomu są przekształcony przez <xref:System.Windows.Forms.Control> zdarzeniach semantycznych, takich jak <xref:System.Windows.Forms.Control.Click> i <xref:System.Windows.Forms.Control.DoubleClick>. Aby uzyskać szczegółowe informacje o zdarzeniach dziedziczone, zobacz <xref:System.Windows.Forms.Control>.  
  
 Jeśli niestandardową kontrolkę musi zastąpić funkcjonalność zdarzeń dziedziczone, zastąpić dziedziczonego `On` *EventName* metody zamiast dołączając delegata. Jeśli nie znasz modelu zdarzeń w programie .NET Framework, zobacz [Raising Events ze składnika](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/sh2e3k5z(v=vs.120)).  
  
## <a name="see-also"></a>Zobacz także
- [Przesłanianie metody OnPaint](../../../../docs/framework/winforms/controls/overriding-the-onpaint-method.md)
- [Obsługa danych wejściowych użytkownika](../../../../docs/framework/winforms/controls/handling-user-input.md)
- [Definiowanie zdarzenia](../../../../docs/framework/winforms/controls/defining-an-event-in-windows-forms-controls.md)
- [Zdarzenia](../../../../docs/standard/events/index.md)
