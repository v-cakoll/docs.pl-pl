---
title: 'Instrukcje: Wyświetl więcej niż jednego miesiąca w kontrolce MonthCalendar formularzy Windows Forms'
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
ms.openlocfilehash: febed820bae460f51bb19f08caa6027011abd55d
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/09/2019
ms.locfileid: "57715350"
---
# <a name="how-to-display-more-than-one-month-in-the-windows-forms-monthcalendar-control"></a>Instrukcje: Wyświetl więcej niż jednego miesiąca w kontrolce MonthCalendar formularzy Windows Forms
Formularze Windows <xref:System.Windows.Forms.MonthCalendar> formant może wyświetlić maksymalnie 12 miesięcy w danym momencie. Domyślnie kontrolka ma wyświetlać tylko jeden miesiąc, ale można określić liczbę miesięcy są wyświetlane i jak są rozmieszczone w kontrolce. Po zmianie wymiary kalendarza zmieni się rozmiar kontrolki, dlatego upewnij się, że jest wystarczająco dużo miejsca w formularzu dla nowych wymiarów.  
  
### <a name="to-display-multiple-months"></a>Aby wyświetlić wiele miesięcy  
  
-   Ustaw <xref:System.Windows.Forms.MonthCalendar.CalendarDimensions%2A> liczbę miesięcy do wyświetlenia w poziomie i w pionie.  
  
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
