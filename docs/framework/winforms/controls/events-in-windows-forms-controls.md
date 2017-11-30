---
title: Zdarzenia w formantach formularzy systemu Windows
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- events [Windows Forms], custom controls (using code)
- custom controls [Windows Forms], events overview (using code)
ms.assetid: 7e3d1379-87aa-437c-afce-c99454eff30e
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: e568dd7fadea8af399a63aa95347f368b4e13a54
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="events-in-windows-forms-controls"></a>Zdarzenia w formantach formularzy systemu Windows
Formant formularzy systemu Windows dziedziczy więcej niż 60 zdarzeń z <xref:System.Windows.Forms.Control?displayProperty=nameWithType>. Obejmują one <xref:System.Windows.Forms.Control.Paint> zdarzeń, co powoduje, że formantu, który ma być rysowany, zdarzenia związane z wyświetlania okna, takich jak <xref:System.Windows.Forms.Control.Resize> i <xref:System.Windows.Forms.Control.Layout> zdarzenia i niskiego poziomu zdarzeń myszy i klawiatury. Niektóre zdarzenia niskiego poziomu są syntezatora przez <xref:System.Windows.Forms.Control> do semantycznego zdarzenia, takie jak <xref:System.Windows.Forms.Control.Click> i <xref:System.Windows.Forms.Control.DoubleClick>. Aby uzyskać szczegółowe informacje o zdarzeniach dziedziczone, zobacz <xref:System.Windows.Forms.Control>.  
  
 Jeśli formant niestandardowy musi przesłonić odziedziczonego zdarzeń funkcji, zastąpić dziedziczonego `On` *EventName* metody zamiast dołączanie delegata. Jeśli nie masz doświadczenia w obsłudze zdarzeń modelu w programie .NET Framework, zobacz [wywoływanie zdarzeń od składnika](http://msdn.microsoft.com/library/9aebf605-a87d-470b-b7c8-f9abfc8360a0).  
  
## <a name="see-also"></a>Zobacz też  
 [Zastępowanie metody OnPaint](../../../../docs/framework/winforms/controls/overriding-the-onpaint-method.md)  
 [Obsługa danych wejściowych użytkownika](../../../../docs/framework/winforms/controls/handling-user-input.md)  
 [Dodawanie zdarzenia](../../../../docs/framework/winforms/controls/defining-an-event-in-windows-forms-controls.md)  
 [Zdarzenia](../../../../docs/standard/events/index.md)
