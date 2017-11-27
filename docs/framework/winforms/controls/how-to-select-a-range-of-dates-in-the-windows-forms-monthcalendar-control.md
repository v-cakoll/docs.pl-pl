---
title: 'Porady: wybieranie zakresu dat w formancie MonthCalendar formularzy systemu Windows'
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
- dates [Windows Forms], selecting range in calendar controls
- examples [Windows Forms], calendar controls
- calendars [Windows Forms], selecting date range
- MonthCalendar control [Windows Forms], selecting date range
ms.assetid: 95d9ab95-b0f8-4c19-9f63-b5cd4593a5d0
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 7d6a8d156e6e9a8c5331bd3db1c8e584be5ac154
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-select-a-range-of-dates-in-the-windows-forms-monthcalendar-control"></a>Porady: wybieranie zakresu dat w formancie MonthCalendar formularzy systemu Windows
Ważna cecha formularzy systemu Windows <xref:System.Windows.Forms.MonthCalendar> formant jest, że użytkownik może wybrać zakres dat. Ta funkcja jest ulepszoną funkcję wyboru daty <xref:System.Windows.Forms.DateTimePicker> określanie tylko umożliwia użytkownikowi wybranie wartość jednej daty/godziny. Możesz ustawić zakresu dat lub pobrać wybranego zakresu określonego przez tego użytkownika za pomocą właściwości <xref:System.Windows.Forms.MonthCalendar> formantu. W poniższym przykładzie pokazano, jak ustawić wybranego zakresu.  
  
### <a name="to-select-a-range-of-dates"></a>Aby wybrać zakres dat  
  
1.  Utwórz <xref:System.DateTime> obiekty reprezentujące imię i nazwisko daty w zakresie.  
  
    ```vb  
    Dim projectStart As Date = New DateTime(2001, 2, 13)  
    Dim projectEnd As Date = New DateTime(2001, 2, 28)  
    ```  
  
    ```csharp  
    DateTime projectStart = new DateTime(2001, 2, 13);  
    DateTime projectEnd = new DateTime(2001, 2, 28);  
    ```  
  
    ```cpp  
    DateTime projectStart = DateTime(2001, 2, 13);  
    DateTime projectEnd = DateTime(2001, 2, 28);  
    ```  
  
2.  Ustaw <xref:System.Windows.Forms.MonthCalendar.SelectionRange%2A> właściwości.  
  
    ```vb  
    MonthCalendar1.SelectionRange = New SelectionRange(projectStart, projectEnd)  
    ```  
  
    ```csharp  
    monthCalendar1.SelectionRange = new SelectionRange(projectStart, projectEnd);  
    ```  
  
    ```cpp  
    monthCalendar1->SelectionRange = gcnew  
       SelectionRange(projectStart, projectEnd);  
    ```  
  
     — lub —  
  
     Ustaw <xref:System.Windows.Forms.MonthCalendar.SelectionStart%2A> i <xref:System.Windows.Forms.MonthCalendar.SelectionEnd%2A> właściwości.  
  
    ```vb  
    MonthCalendar1.SelectionStart = projectStart  
    MonthCalendar1.SelectionEnd = projectEnd  
    ```  
  
    ```csharp  
    monthCalendar1.SelectionStart = projectStart;  
    monthCalendar1.SelectionEnd = projectEnd;  
    ```  
  
    ```cpp  
    monthCalendar1->SelectionStart = projectStart;  
    monthCalendar1->SelectionEnd = projectEnd;  
    ```  
  
## <a name="see-also"></a>Zobacz też  
 [MonthCalendar — formant](../../../../docs/framework/winforms/controls/monthcalendar-control-windows-forms.md)  
 [Porady: Zmienianie wyglądu formantu MonthCalendar formularzy systemu Windows](../../../../docs/framework/winforms/controls/how-to-change-monthcalendar-control-appearance.md)  
 [Porady: wyświetlanie określonych dni pogrubioną czcionką z systemu Windows formantu MonthCalendar formularzy](../../../../docs/framework/winforms/controls/display-specific-days-in-bold-with-wf-monthcalendar-control.md)  
 [Porady: wyświetlanie więcej niż jeden miesiąc w formancie MonthCalendar formularzy systemu Windows](../../../../docs/framework/winforms/controls/display-more-than-one-month-wf-monthcalendar-control.md)
