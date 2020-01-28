---
title: Zmień opóźnienie składnika ToolTip
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
ms.openlocfilehash: 8ab0b0760e8c82d752eaada19f14cae57fa63fdc
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76746590"
---
# <a name="how-to-change-the-delay-of-the-windows-forms-tooltip-component"></a>Porady: zmienianie opóźnienia składnika ToolTip formularzy systemu Windows
Istnieje wiele wartości opóźnienia, które można ustawić dla składnika <xref:System.Windows.Forms.ToolTip> Windows Forms. Jednostką miary dla wszystkich tych właściwości jest milisekund. Właściwość <xref:System.Windows.Forms.ToolTip.InitialDelay%2A> określa, jak długo użytkownik musi wskazywać w skojarzonym formancie ciąg etykietki narzędzia do wyświetlenia. Właściwość <xref:System.Windows.Forms.ToolTip.ReshowDelay%2A> ustawia liczbę milisekund, jaką zajmie kolejny ciąg etykietki narzędzia, gdy wskaźnik myszy zostanie przeniesiony z jednej etykietki narzędzia do innej. Właściwość <xref:System.Windows.Forms.ToolTip.AutoPopDelay%2A> określa długość czasu wyświetlania ciągu etykietki narzędzia. Można ustawić te wartości pojedynczo lub przez ustawienie wartości właściwości <xref:System.Windows.Forms.ToolTip.AutomaticDelay%2A>; inne właściwości opóźnienia są ustawiane na podstawie wartości przypisanej do właściwości <xref:System.Windows.Forms.ToolTip.AutomaticDelay%2A>. Na przykład, gdy <xref:System.Windows.Forms.ToolTip.AutomaticDelay%2A> jest ustawiona na wartość N, <xref:System.Windows.Forms.ToolTip.InitialDelay%2A> jest ustawiona na N, <xref:System.Windows.Forms.ToolTip.ReshowDelay%2A> jest ustawiona na wartość <xref:System.Windows.Forms.ToolTip.AutomaticDelay%2A> podzielona przez pięć (lub N/5), a <xref:System.Windows.Forms.ToolTip.AutoPopDelay%2A> jest ustawiona na wartość, która jest pięć razy większa niż wartość właściwości <xref:System.Windows.Forms.ToolTip.AutomaticDelay%2A> (lub 5N).  
  
### <a name="to-set-the-delay"></a>Aby ustawić opóźnienie  
  
1. Ustaw następujące właściwości, jak pokazano w tym przykładzie.  
  
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
- [Instrukcje: ustawienie elementu ToolTips dla kontrolek w formularzu systemu Windows w czasie projektowania](how-to-set-tooltips-for-controls-on-a-windows-form-at-design-time.md)
- [ToolTip, składnik](tooltip-component-windows-forms.md)
