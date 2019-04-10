---
title: 'Instrukcje: wybieranie zakresu dat w kontrolce MonthCalendar formularzy systemu Windows'
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
ms.openlocfilehash: 82d0499cb40f79a3110b8432fbee66774bcc14a7
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2019
ms.locfileid: "59332238"
---
# <a name="how-to-select-a-range-of-dates-in-the-windows-forms-monthcalendar-control"></a>Instrukcje: wybieranie zakresu dat w kontrolce MonthCalendar formularzy systemu Windows
Ważną funkcją formularzy Windows Forms <xref:System.Windows.Forms.MonthCalendar> formant jest, że użytkownik może wybrać zakres dat. Ta funkcja jest ulepszoną funkcję wybór daty <xref:System.Windows.Forms.DateTimePicker> formant, który tylko umożliwia użytkownikowi wybranie wartości daty/godziny w pojedynczej. Możesz ustawić zakresu dat lub pobrać zaznaczony zakres ustawiony przez użytkownika za pomocą właściwości <xref:System.Windows.Forms.MonthCalendar> kontroli. Poniższy przykład kodu demonstruje sposób ustawiania zaznaczony zakres.  
  
### <a name="to-select-a-range-of-dates"></a>Aby wybrać zakres dat  
  
1. Utwórz <xref:System.DateTime> obiekty reprezentujące daty imię i nazwisko w zakresie.  
  
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
  
2. Ustaw <xref:System.Windows.Forms.MonthCalendar.SelectionRange%2A> właściwości.  
  
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
  
## <a name="see-also"></a>Zobacz także

- [MonthCalendar, kontrolka](monthcalendar-control-windows-forms.md)
- [Instrukcje: zmienianie wyglądu kontrolki MonthCalendar formularzy systemu Windows](how-to-change-monthcalendar-control-appearance.md)
- [Instrukcje: wyświetlanie określonych dni pogrubioną czcionką za pomocą kontrolki MonthCalendar formularzy systemu Windows](display-specific-days-in-bold-with-wf-monthcalendar-control.md)
- [Instrukcje: wyświetlanie większej niż jeden liczby miesięcy w kontrolce MonthCalendar formularzy systemu Windows](display-more-than-one-month-wf-monthcalendar-control.md)
