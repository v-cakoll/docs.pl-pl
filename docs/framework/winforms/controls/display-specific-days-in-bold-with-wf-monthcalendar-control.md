---
title: 'Instrukcje: wyświetlanie określonych dni pogrubioną czcionką za pomocą kontrolki MonthCalendar formularzy systemu Windows'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- calendars [Windows Forms], displaying dates in bold
- examples [Windows Forms], calendar controls
- GetDayBold event
- MonthCalendar control [Windows Forms], dates displayed in bold
ms.assetid: 8b20db5b-8118-4825-90e8-2c45c186ac7d
ms.openlocfilehash: 27b19e47d108b9af43a6d8882264d62c726ffe56
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2019
ms.locfileid: "59343272"
---
# <a name="how-to-display-specific-days-in-bold-with-the-windows-forms-monthcalendar-control"></a>Instrukcje: wyświetlanie określonych dni pogrubioną czcionką za pomocą kontrolki MonthCalendar formularzy systemu Windows
Formularze Windows <xref:System.Windows.Forms.MonthCalendar> formant może wyświetlić dni pogrubioną czcionką, jako pojedynczej daty lub na zasadzie powtarzające się. Możesz zrobić to, aby zwrócić uwagę czytelnika na wybranych dat, takich jak dni wolnych od pracy i weekendów.  
  
 Trzy właściwości kontroli tej funkcji. <xref:System.Windows.Forms.MonthCalendar.BoldedDates%2A> Właściwość zawiera pojedynczy daty. <xref:System.Windows.Forms.MonthCalendar.AnnuallyBoldedDates%2A> Właściwość zawiera daty wyświetlane wytłuszczonym drukiem co roku. <xref:System.Windows.Forms.MonthCalendar.MonthlyBoldedDates%2A> Właściwość zawiera daty, które są pogrubione co miesiąc. Każdy z tych właściwości zawiera tablicę <xref:System.DateTime> obiektów. Aby dodać lub usunąć wartość typu date z jedną z tych list, należy dodać lub usunąć <xref:System.DateTime> obiektu.  
  
### <a name="to-make-a-date-appear-in-bold-type"></a>Daty są wyświetlane pogrubioną czcionką  
  
1. Utwórz <xref:System.DateTime> obiektów.  
  
    ```vb  
    Dim myVacation1 As Date = New DateTime(2001, 6, 10)  
    Dim myVacation2 As Date = New DateTime(2001, 6, 17)  
    ```  
  
    ```csharp  
    DateTime myVacation1 = new DateTime(2001, 6, 10);  
    DateTime myVacation2 = new DateTime(2001, 6, 17);  
    ```  
  
    ```cpp  
    DateTime myVacation1 = DateTime(2001, 6, 10);  
    DateTime myVacation2 = DateTime(2001, 6, 17);  
    ```  
  
2. Pogrubienie pojedyncza Data, wywołując <xref:System.Windows.Forms.MonthCalendar.AddBoldedDate%2A>, <xref:System.Windows.Forms.MonthCalendar.AddAnnuallyBoldedDate%2A>, lub <xref:System.Windows.Forms.MonthCalendar.AddMonthlyBoldedDate%2A> metody <xref:System.Windows.Forms.MonthCalendar> kontroli.  
  
    ```vb  
    MonthCalendar1.AddBoldedDate(myVacation1)  
    MonthCalendar1.AddBoldedDate(myVacation2)  
    ```  
  
    ```csharp  
    monthCalendar1.AddBoldedDate(myVacation1);  
    monthCalendar1.AddBoldedDate(myVacation2);  
    ```  
  
    ```cpp  
    monthCalendar1->AddBoldedDate(myVacation1);  
    monthCalendar1->AddBoldedDate(myVacation2);  
    ```  
  
     — lub —  
  
     Pogrubienie zestaw dat w całości, tworząc tablicę <xref:System.DateTime> obiektów i przypisywanie jej do jednej z właściwości.  
  
    ```vb  
    Dim VacationDates As DateTime() = {myVacation1, myVacation2}  
    MonthCalendar1.BoldedDates = VacationDates  
    ```  
  
    ```csharp  
    DateTime[] VacationDates = {myVacation1, myVacation2};  
    monthCalendar1.BoldedDates = VacationDates;  
    ```  
  
    ```cpp  
    Array<DateTime>^ VacationDates = {myVacation1, myVacation2};  
    monthCalendar1->BoldedDates = VacationDates;  
    ```  
  
### <a name="to-make-a-date-appear-in-the-regular-font"></a>Daty są wyświetlane w regularnych czcionki  
  
1. Pojawiają się w regularnych czcionki przez wywołanie datę pogrubiony pojedynczego <xref:System.Windows.Forms.MonthCalendar.RemoveBoldedDate%2A>, <xref:System.Windows.Forms.MonthCalendar.RemoveAnnuallyBoldedDate%2A>, lub <xref:System.Windows.Forms.MonthCalendar.RemoveMonthlyBoldedDate%2A> metody.  
  
    ```vb  
    MonthCalendar1.RemoveBoldedDate(myVacation1)  
    MonthCalendar1.RemoveBoldedDate(myVacation2)  
    ```  
  
    ```csharp  
    monthCalendar1.RemoveBoldedDate(myVacation1);  
    monthCalendar1.RemoveBoldedDate(myVacation2);  
    ```  
  
    ```cpp  
    monthCalendar1->RemoveBoldedDate(myVacation1);  
    monthCalendar1->RemoveBoldedDate(myVacation2);  
    ```  
  
     — lub —  
  
     Usuń pogrubione daty z jedną z trzech list, wywołując <xref:System.Windows.Forms.MonthCalendar.RemoveAllBoldedDates%2A>, <xref:System.Windows.Forms.MonthCalendar.RemoveAllAnnuallyBoldedDates%2A>, lub <xref:System.Windows.Forms.MonthCalendar.RemoveAllMonthlyBoldedDates%2A> metody.  
  
    ```vb  
    MonthCalendar1.RemoveAllBoldedDates()  
    ```  
  
    ```csharp  
    monthCalendar1.RemoveAllBoldedDates();  
    ```  
  
    ```cpp  
    monthCalendar1->RemoveAllBoldedDates();  
    ```  
  
2. Zaktualizuj wygląd czcionki, wywołując <xref:System.Windows.Forms.MonthCalendar.UpdateBoldedDates%2A> metody.  
  
    ```vb  
    MonthCalendar1.UpdateBoldedDates()  
    ```  
  
    ```csharp  
    monthCalendar1.UpdateBoldedDates();  
    ```  
  
    ```cpp  
    monthCalendar1->UpdateBoldedDates();  
    ```  
  
## <a name="see-also"></a>Zobacz także

- [MonthCalendar, kontrolka](monthcalendar-control-windows-forms.md)
- [Instrukcje: wybieranie zakresu dat w kontrolce MonthCalendar formularzy systemu Windows](how-to-select-a-range-of-dates-in-the-windows-forms-monthcalendar-control.md)
- [Instrukcje: zmienianie wyglądu kontrolki MonthCalendar formularzy systemu Windows](how-to-change-monthcalendar-control-appearance.md)
- [Instrukcje: wyświetlanie większej niż jeden liczby miesięcy w kontrolce MonthCalendar formularzy systemu Windows](display-more-than-one-month-wf-monthcalendar-control.md)
