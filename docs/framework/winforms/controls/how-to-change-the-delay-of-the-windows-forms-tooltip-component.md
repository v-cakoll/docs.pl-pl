---
title: "Porady: zmienianie opóźnienia składnika ToolTip formularzy systemu Windows"
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
- ToolTip component [Windows Forms], delay values
- tooltips [Windows Forms], delay values
- examples [Windows Forms], tooltips
ms.assetid: 08979ba7-dd84-477b-ab17-8d06e759be99
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 48bb8c08fa02a54f9bfd3febbe99f683fd68d7f8
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-change-the-delay-of-the-windows-forms-tooltip-component"></a>Porady: zmienianie opóźnienia składnika ToolTip formularzy systemu Windows
Istnieje wiele wartości opóźnienia, które można ustawić dla formularzy systemu Windows <xref:System.Windows.Forms.ToolTip> składnika. Jednostka miary tych właściwości to milisekund. <xref:System.Windows.Forms.ToolTip.InitialDelay%2A> Właściwość określa, jak długo użytkownik musi wskazywać na skojarzonym formancie ciągu etykietki narzędzia i pojawienie się. <xref:System.Windows.Forms.ToolTip.ReshowDelay%2A> Właściwość ustawia liczbę milisekund zajmuje kolejnych ciągów ToolTip są wyświetlane jako wskaźnik myszy są przenoszone z jednego formantu ToolTip skojarzonych na inny. <xref:System.Windows.Forms.ToolTip.AutoPopDelay%2A> Właściwość określa długość czasu jest wyświetlany ciąg etykietki narzędzia. Wartości te można ustawiać indywidualnie lub przez ustawienie wartości <xref:System.Windows.Forms.ToolTip.AutomaticDelay%2A> właściwości; opóźnienie, na wartość przypisana do właściwości są ustawione na podstawie <xref:System.Windows.Forms.ToolTip.AutomaticDelay%2A> właściwości. Na przykład, jeśli <xref:System.Windows.Forms.ToolTip.AutomaticDelay%2A> ma ustawioną wartość N, <xref:System.Windows.Forms.ToolTip.InitialDelay%2A> ma ustawioną wartość N, <xref:System.Windows.Forms.ToolTip.ReshowDelay%2A> ma ustawioną wartość <xref:System.Windows.Forms.ToolTip.AutomaticDelay%2A> podzielony przez pięć (lub N/5) i <xref:System.Windows.Forms.ToolTip.AutoPopDelay%2A> ma ustawioną wartość, która jest pięć razy wartość <xref:System.Windows.Forms.ToolTip.AutomaticDelay%2A> właściwości (lub 5 n).  
  
### <a name="to-set-the-delay"></a>Aby ustawić opóźnienie  
  
1.  Ustaw następujące właściwości, jak pokazano w poniższym przykładzie.  
  
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
  
## <a name="see-also"></a>Zobacz też  
 [Informacje o składniku ToolTip](../../../../docs/framework/winforms/controls/tooltip-component-overview-windows-forms.md)  
 [Porady: ustawienie elementu ToolTips dla formantów w formularzu systemu Windows w czasie projektowania](../../../../docs/framework/winforms/controls/how-to-set-tooltips-for-controls-on-a-windows-form-at-design-time.md)  
 [ToolTip — składnik](../../../../docs/framework/winforms/controls/tooltip-component-windows-forms.md)
