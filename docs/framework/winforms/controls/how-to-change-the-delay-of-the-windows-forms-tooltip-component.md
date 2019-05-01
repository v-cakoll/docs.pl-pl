---
title: 'Instrukcje: zmienianie opóźnienia składnika ToolTip formularzy systemu Windows'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- ToolTip component [Windows Forms], delay values
- tooltips [Windows Forms], delay values
- examples [Windows Forms], tooltips
ms.assetid: 08979ba7-dd84-477b-ab17-8d06e759be99
ms.openlocfilehash: cf257cccd272c16c3d7c3d403456265444fc8ac8
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61781241"
---
# <a name="how-to-change-the-delay-of-the-windows-forms-tooltip-component"></a>Instrukcje: zmienianie opóźnienia składnika ToolTip formularzy systemu Windows
Istnieje wiele wartości opóźnienia, które można ustawić dla formularzy Windows <xref:System.Windows.Forms.ToolTip> składnika. Jednostka miary dla tych właściwości jest milisekund. <xref:System.Windows.Forms.ToolTip.InitialDelay%2A> Właściwość określa, jak długo użytkownik musi wskazywać na jest skojarzony formant ciąg etykietki narzędzi są wyświetlane. <xref:System.Windows.Forms.ToolTip.ReshowDelay%2A> Właściwość ustawia liczbę milisekund zajmuje kolejne parametry etykietki narzędzia wyświetlany jako myszy przesuwa się z jednego formantu skojarzone ToolTip do innego. <xref:System.Windows.Forms.ToolTip.AutoPopDelay%2A> Właściwość określa długość czasu, jest wyświetlany ciąg etykietki narzędzia. Wartości te można ustawić indywidualnie lub przez ustawienie wartości <xref:System.Windows.Forms.ToolTip.AutomaticDelay%2A> właściwości; opóźnienie, właściwości jest ustawiona na podstawie wartości przypisanej do <xref:System.Windows.Forms.ToolTip.AutomaticDelay%2A> właściwości. Na przykład, gdy <xref:System.Windows.Forms.ToolTip.AutomaticDelay%2A> jest ustawiona na wartość N, <xref:System.Windows.Forms.ToolTip.InitialDelay%2A> jest równa się N, <xref:System.Windows.Forms.ToolTip.ReshowDelay%2A> jest ustawiona na wartość <xref:System.Windows.Forms.ToolTip.AutomaticDelay%2A> podzielona przez pięć (lub N na dobę, 5) i <xref:System.Windows.Forms.ToolTip.AutoPopDelay%2A> jest ustawiona na wartość, która jest pięciokrotnie wartość <xref:System.Windows.Forms.ToolTip.AutomaticDelay%2A> właściwości (lub 5 n).  
  
### <a name="to-set-the-delay"></a>Aby ustawić opóźnienie  
  
1. Ustaw następujące właściwości, jak pokazano w poniższym przykładzie.  
  
    ```vb  
    ToolTip1.InitialDelay = 500  
    ToolTip1.ReshowDelay = 100  
    ToolTip1.AutoPopDelay = 5000  
    ```  
  
    ```csharp  
    ToolTip1.InitialDelay = 500;  
    ToolTip1.ReshowDelay = 100;  
    ToolTip1.AutoPopDelay = 5000;  
    ```  
  
    ```cpp  
    toolTip1->InitialDelay = 500;  
    toolTip1->ReshowDelay = 100;  
    toolTip1->AutoPopDelay = 5000;  
    ```  
  
## <a name="see-also"></a>Zobacz także

- [ToolTip, składnik — omówienie](tooltip-component-overview-windows-forms.md)
- [Instrukcje: Ustawienie elementu ToolTips dla formantów w formularzu Windows w czasie projektowania](how-to-set-tooltips-for-controls-on-a-windows-form-at-design-time.md)
- [ToolTip, składnik](tooltip-component-windows-forms.md)
