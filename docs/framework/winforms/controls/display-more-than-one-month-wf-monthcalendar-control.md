---
title: 'Instrukcje: wyświetlanie większej niż jeden liczby miesięcy w kontrolce MonthCalendar formularzy systemu Windows'
ms.date: 03/30/2017
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
ms.openlocfilehash: 79100b52d8e0a5b651edb9d6555a4497287ed858
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61972144"
---
# <a name="how-to-display-more-than-one-month-in-the-windows-forms-monthcalendar-control"></a>Instrukcje: wyświetlanie większej niż jeden liczby miesięcy w kontrolce MonthCalendar formularzy systemu Windows
Formularze Windows <xref:System.Windows.Forms.MonthCalendar> formant może wyświetlić maksymalnie 12 miesięcy w danym momencie. Domyślnie kontrolka ma wyświetlać tylko jeden miesiąc, ale można określić liczbę miesięcy są wyświetlane i jak są rozmieszczone w kontrolce. Po zmianie wymiary kalendarza zmieni się rozmiar kontrolki, dlatego upewnij się, że jest wystarczająco dużo miejsca w formularzu dla nowych wymiarów.  
  
### <a name="to-display-multiple-months"></a>Aby wyświetlić wiele miesięcy  
  
- Ustaw <xref:System.Windows.Forms.MonthCalendar.CalendarDimensions%2A> liczbę miesięcy do wyświetlenia w poziomie i w pionie.  
  
    ```vb  
    MonthCalendar1.CalendarDimensions = New System.Drawing.Size (3,2)  
    ```  
  
    ```csharp  
    monthCalendar1.CalendarDimensions = new System.Drawing.Size (3,2);  
    ```  
  
    ```cpp  
    monthCalendar1->CalendarDimensions = System::Drawing::Size (3,2);  
    ```  
  
## <a name="see-also"></a>Zobacz także

- [MonthCalendar, kontrolka](monthcalendar-control-windows-forms.md)
- [Instrukcje: Wybieranie zakresu dat w kontrolce MonthCalendar formularzy Windows Forms](how-to-select-a-range-of-dates-in-the-windows-forms-monthcalendar-control.md)
- [Instrukcje: Zmienianie wyglądu formantu MonthCalendar formularzy Windows](how-to-change-monthcalendar-control-appearance.md)
