---
title: Zdarzenia w kontrolkach
ms.date: 03/30/2017
helpviewer_keywords:
- events [Windows Forms], custom controls (using code)
- custom controls [Windows Forms], events overview (using code)
ms.assetid: 7e3d1379-87aa-437c-afce-c99454eff30e
ms.openlocfilehash: c60713917b9c84aa7fad50fb1c81fc9252149ad6
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76745757"
---
# <a name="events-in-windows-forms-controls"></a>Zdarzenia w formantach formularzy systemu Windows
Formant Windows Forms dziedziczy więcej niż 60 zdarzeń z <xref:System.Windows.Forms.Control?displayProperty=nameWithType>. Obejmują one zdarzenie <xref:System.Windows.Forms.Control.Paint>, które powoduje narysowanie kontrolki, zdarzenia związane z wyświetlaniem okna, takie jak zdarzenia <xref:System.Windows.Forms.Control.Resize> i <xref:System.Windows.Forms.Control.Layout> oraz zdarzenia myszy i klawiatury niskiego poziomu. Niektóre zdarzenia niskiego poziomu są syntezą <xref:System.Windows.Forms.Control> do zdarzeń semantycznych, takich jak <xref:System.Windows.Forms.Control.Click> i <xref:System.Windows.Forms.Control.DoubleClick>. Aby uzyskać szczegółowe informacje o zdarzeniach dziedziczonych, zobacz <xref:System.Windows.Forms.Control>.  
  
 Jeśli kontrolka niestandardowa musi przesłonić funkcję dziedziczonego zdarzenia, Przesłoń dziedziczonej metody `On`*EventName* zamiast dołączać delegata. Jeśli nie znasz modelu zdarzeń w .NET Framework, zobacz Wywoływanie [zdarzeń ze składnika](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/sh2e3k5z(v=vs.120)).  
  
## <a name="see-also"></a>Zobacz także

- [Przesłanianie metody OnPaint](overriding-the-onpaint-method.md)
- [Obsługa danych wejściowych użytkownika](handling-user-input.md)
- [Definiowanie zdarzenia](defining-an-event-in-windows-forms-controls.md)
- [Zdarzenia](../../../standard/events/index.md)
