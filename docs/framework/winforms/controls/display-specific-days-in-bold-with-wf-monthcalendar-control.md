---
title: 'Porady: wyświetlanie określonych dni pogrubioną czcionką za pomocą formantu MonthCalendar formularzy systemu Windows'
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
ms.openlocfilehash: 0ee89fb4cfb6ddbf975eb0e85e7dd1bab30f08d1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-display-specific-days-in-bold-with-the-windows-forms-monthcalendar-control"></a>Porady: wyświetlanie określonych dni pogrubioną czcionką za pomocą formantu MonthCalendar formularzy systemu Windows
Formularze systemu Windows <xref:System.Windows.Forms.MonthCalendar> formant może wyświetlać dni pogrubioną czcionką jako pojedynczej daty lub na podstawie powtarzających się. Możesz zrobić to, aby zwrócić uwagę na wybranych dat, takich jak dni wolnych i w weekendy.  
  
 Trzy właściwości formantu tej funkcji. <xref:System.Windows.Forms.MonthCalendar.BoldedDates%2A> Właściwość zawiera pojedynczy daty. <xref:System.Windows.Forms.MonthCalendar.AnnuallyBoldedDates%2A> Właściwość zawiera daty, które są pogrubione co roku. <xref:System.Windows.Forms.MonthCalendar.MonthlyBoldedDates%2A> Właściwość zawiera daty, które są pogrubione co miesiąc. Każdy z tych właściwości zawiera tablicę <xref:System.DateTime> obiektów. Aby dodać lub usunąć datę z jednego z tych list, musisz dodać lub usunąć <xref:System.DateTime> obiektu.  
  
### <a name="to-make-a-date-appear-in-bold-type"></a>Aby wyświetlone czcionką pogrubioną datę  
  
1.  Utwórz <xref:System.DateTime> obiektów.  
  
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
  
2.  Pogrubienie pojedyncza Data wywołując <xref:System.Windows.Forms.MonthCalendar.AddBoldedDate%2A>, <xref:System.Windows.Forms.MonthCalendar.AddAnnuallyBoldedDate%2A>, lub <xref:System.Windows.Forms.MonthCalendar.AddMonthlyBoldedDate%2A> metody <xref:System.Windows.Forms.MonthCalendar> formantu.  
  
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
  
     Zastosuj pogrubienie zestaw dat w całości, tworząc tablicę <xref:System.DateTime> obiektów i przypisywania go do jednej z właściwości.  
  
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
  
1.  Pogrubiony jednej daty są wyświetlane w regularnych czcionki, wywołując <xref:System.Windows.Forms.MonthCalendar.RemoveBoldedDate%2A>, <xref:System.Windows.Forms.MonthCalendar.RemoveAnnuallyBoldedDate%2A>, lub <xref:System.Windows.Forms.MonthCalendar.RemoveMonthlyBoldedDate%2A> metody.  
  
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
  
     Usuń pogrubione daty z jednej z trzech list przez wywołanie metody <xref:System.Windows.Forms.MonthCalendar.RemoveAllBoldedDates%2A>, <xref:System.Windows.Forms.MonthCalendar.RemoveAllAnnuallyBoldedDates%2A>, lub <xref:System.Windows.Forms.MonthCalendar.RemoveAllMonthlyBoldedDates%2A> metody.  
  
    ```vb  
    MonthCalendar1.RemoveAllBoldedDates()  
    ```  
  
    ```csharp  
    monthCalendar1.RemoveAllBoldedDates();  
    ```  
  
    ```cpp  
    monthCalendar1->RemoveAllBoldedDates();  
    ```  
  
2.  Zaktualizuj wygląd czcionki przez wywołanie metody <xref:System.Windows.Forms.MonthCalendar.UpdateBoldedDates%2A> metody.  
  
    ```vb  
    MonthCalendar1.UpdateBoldedDates()  
    ```  
  
    ```csharp  
    monthCalendar1.UpdateBoldedDates();  
    ```  
  
    ```cpp  
    monthCalendar1->UpdateBoldedDates();  
    ```  
  
## <a name="see-also"></a>Zobacz też  
 [MonthCalendar, kontrolka](../../../../docs/framework/winforms/controls/monthcalendar-control-windows-forms.md)  
 [Instrukcje: wybieranie zakresu dat w kontrolce MonthCalendar formularzy Windows Forms](../../../../docs/framework/winforms/controls/how-to-select-a-range-of-dates-in-the-windows-forms-monthcalendar-control.md)  
 [Instrukcje: zmienianie wyglądu kontrolki MonthCalendar formularzy Windows Forms](../../../../docs/framework/winforms/controls/how-to-change-monthcalendar-control-appearance.md)  
 [Instrukcje: wyświetlanie więcej niż jednego miesiąca w kontrolce MonthCalendar formularzy Windows Forms](../../../../docs/framework/winforms/controls/display-more-than-one-month-wf-monthcalendar-control.md)
