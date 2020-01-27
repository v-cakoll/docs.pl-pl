---
title: Wyświetl więcej niż jeden miesiąc w kontrolce MonthCalendar
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
ms.openlocfilehash: 5d3925bc19ddcd67742f0ab8b5b2e45530820f38
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76745900"
---
# <a name="how-to-display-more-than-one-month-in-the-windows-forms-monthcalendar-control"></a>Porady: wyświetlanie większej niż jeden liczby miesięcy w formancie MonthCalendar formularzy systemu Windows
Kontrolka <xref:System.Windows.Forms.MonthCalendar> Windows Forms może być wyświetlana nawet przez 12 miesięcy. Domyślnie kontrolka wyświetla tylko jeden miesiąc, ale można określić, ile miesięcy jest wyświetlanych i jak są ułożone w formancie. Gdy zmienisz wymiary kalendarza, rozmiar formantu jest zmieniany, więc upewnij się, że w formularzu istnieją wystarczające miejsce dla nowych wymiarów.  
  
### <a name="to-display-multiple-months"></a>Aby wyświetlić wiele miesięcy  
  
- Ustaw właściwość <xref:System.Windows.Forms.MonthCalendar.CalendarDimensions%2A> na liczbę miesięcy, która ma być wyświetlana w poziomie i w pionie.  
  
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
- [Instrukcje: wybieranie zakresu dat w kontrolce MonthCalendar formularzy Windows Forms](how-to-select-a-range-of-dates-in-the-windows-forms-monthcalendar-control.md)
- [Instrukcje: zmienianie wyglądu kontrolki MonthCalendar formularzy Windows Forms](how-to-change-monthcalendar-control-appearance.md)
