---
title: "Porady: wyświetlanie większej niż jeden liczby miesięcy w formancie MonthCalendar formularzy systemu Windows"
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
- calendars [Windows Forms], formatting display
- examples [Windows Forms], calendar controls
- calendars [Windows Forms], multiple months
- MonthCalendar control [Windows Forms], formatting display
ms.assetid: d197caa2-38a5-4cb4-acc3-562130c2ace3
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 63cf236f93fa3352e536c71000f6bb110abf02fa
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-display-more-than-one-month-in-the-windows-forms-monthcalendar-control"></a>Porady: wyświetlanie większej niż jeden liczby miesięcy w formancie MonthCalendar formularzy systemu Windows
Formularze systemu Windows <xref:System.Windows.Forms.MonthCalendar> formant może wyświetlać do 12 miesięcy naraz. Domyślnie kontrolka ma wyświetlać tylko jeden miesiąc, ale można określić liczbę miesięcy są wyświetlane i sposób rozmieszczenia w formancie. Jeśli zmienisz wymiary kalendarza zostanie zmieniony rozmiar formantu, dlatego upewnij się, że jest za mało miejsca na formularzu dla nowych wymiarów.  
  
### <a name="to-display-multiple-months"></a>Aby wyświetlić wiele miesięcy  
  
-   Ustaw <xref:System.Windows.Forms.MonthCalendar.CalendarDimensions%2A> właściwości Liczba miesięcy do wyświetlenia w poziomie i w pionie.  
  
    ```vb  
    MonthCalendar1.CalendarDimensions = New System.Drawing.Size (3,2)  
    ```  
  
    ```csharp  
    monthCalendar1.CalendarDimensions = new System.Drawing.Size (3,2);  
    ```  
  
    ```cpp  
    monthCalendar1->CalendarDimensions = System::Drawing::Size (3,2);  
    ```  
  
## <a name="see-also"></a>Zobacz też  
 [MonthCalendar — formant](../../../../docs/framework/winforms/controls/monthcalendar-control-windows-forms.md)  
 [Porady: Wybieranie zakresu dat w formancie MonthCalendar formularzy systemu Windows](../../../../docs/framework/winforms/controls/how-to-select-a-range-of-dates-in-the-windows-forms-monthcalendar-control.md)  
 [Porady: Zmienianie wyglądu formantu MonthCalendar formularzy systemu Windows](../../../../docs/framework/winforms/controls/how-to-change-monthcalendar-control-appearance.md)
