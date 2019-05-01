---
title: Zdarzenia w formantach formularzy systemu Windows
ms.date: 03/30/2017
helpviewer_keywords:
- events [Windows Forms], custom controls (using code)
- custom controls [Windows Forms], events overview (using code)
ms.assetid: 7e3d1379-87aa-437c-afce-c99454eff30e
ms.openlocfilehash: 41ad95de7a65dbd0cb3a0d1af8f5c8cb00c1ccdd
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61971987"
---
# <a name="events-in-windows-forms-controls"></a>Zdarzenia w formantach formularzy systemu Windows
Formant programu Windows Forms dziedziczy więcej niż 60 zdarzenia z <xref:System.Windows.Forms.Control?displayProperty=nameWithType>. Obejmują one <xref:System.Windows.Forms.Control.Paint> zdarzenie, które powoduje formantu, który ma być rysowany, zdarzenia związane z wyświetlania okna, takie jak <xref:System.Windows.Forms.Control.Resize> i <xref:System.Windows.Forms.Control.Layout> zdarzeń i niskiego poziomu zdarzeń myszy i klawiatury. Niektóre zdarzenia niskiego poziomu są przekształcony przez <xref:System.Windows.Forms.Control> zdarzeniach semantycznych, takich jak <xref:System.Windows.Forms.Control.Click> i <xref:System.Windows.Forms.Control.DoubleClick>. Aby uzyskać szczegółowe informacje o zdarzeniach dziedziczone, zobacz <xref:System.Windows.Forms.Control>.  
  
 Jeśli niestandardową kontrolkę musi zastąpić funkcjonalność zdarzeń dziedziczone, zastąpić dziedziczonego `On` *EventName* metody zamiast dołączając delegata. Jeśli nie znasz modelu zdarzeń w programie .NET Framework, zobacz [Raising Events ze składnika](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/sh2e3k5z(v=vs.120)).  
  
## <a name="see-also"></a>Zobacz także

- [Przesłanianie metody OnPaint](overriding-the-onpaint-method.md)
- [Obsługa danych wejściowych użytkownika](handling-user-input.md)
- [Definiowanie zdarzenia](defining-an-event-in-windows-forms-controls.md)
- [Zdarzenia](../../../standard/events/index.md)
