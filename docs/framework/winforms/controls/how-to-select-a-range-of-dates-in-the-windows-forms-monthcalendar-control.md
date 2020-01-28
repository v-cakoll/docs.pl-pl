---
title: Wybierz zakres dat w kontrolce MonthCalendar
ms.date: 03/30/2017
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
ms.openlocfilehash: bda96af21a8f86a54d5c0fe0204546b980076d26
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76732897"
---
# <a name="how-to-select-a-range-of-dates-in-the-windows-forms-monthcalendar-control"></a>Porady: wybieranie zakresu dat w formancie MonthCalendar formularzy systemu Windows
Ważną funkcją formantu Windows Forms <xref:System.Windows.Forms.MonthCalendar> jest to, że użytkownik może wybrać zakres dat. Ta funkcja jest ulepszeniem funkcji wyboru daty w kontrolce <xref:System.Windows.Forms.DateTimePicker>, co umożliwia użytkownikowi wybranie pojedynczej wartości daty/godziny. Można ustawić zakres dat lub uzyskać zakres wyboru ustawiony przez użytkownika przy użyciu właściwości kontrolki <xref:System.Windows.Forms.MonthCalendar>. Poniższy przykład kodu demonstruje, jak ustawić zakres wyboru.  
  
### <a name="to-select-a-range-of-dates"></a>Aby wybrać zakres dat  
  
1. Utwórz obiekty <xref:System.DateTime>, które reprezentują pierwszą i ostatnią datę z zakresu.  
  
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
  
2. Ustaw właściwość <xref:System.Windows.Forms.MonthCalendar.SelectionRange%2A>.  
  
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
  
     –lub–  
  
     Ustaw właściwości <xref:System.Windows.Forms.MonthCalendar.SelectionStart%2A> i <xref:System.Windows.Forms.MonthCalendar.SelectionEnd%2A>.  
  
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
  
## <a name="see-also"></a>Zobacz także

- [MonthCalendar, kontrolka](monthcalendar-control-windows-forms.md)
- [Instrukcje: zmienianie wyglądu kontrolki MonthCalendar formularzy Windows Forms](how-to-change-monthcalendar-control-appearance.md)
- [Instrukcje: wyświetlanie określonych dni pogrubioną czcionką za pomocą kontrolki MonthCalendar formularzy Windows Forms](display-specific-days-in-bold-with-wf-monthcalendar-control.md)
- [Instrukcje: wyświetlanie więcej niż jednego miesiąca w kontrolce MonthCalendar formularzy Windows Forms](display-more-than-one-month-wf-monthcalendar-control.md)
