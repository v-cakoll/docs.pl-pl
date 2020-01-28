---
title: Wyświetlaj określone dni pogrubione za pomocą kontrolki MonthCalendar
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
ms.openlocfilehash: 377eb76f562fff20aae2136ddb7130516d2d76f7
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76745885"
---
# <a name="how-to-display-specific-days-in-bold-with-the-windows-forms-monthcalendar-control"></a>Porady: wyświetlanie określonych dni pogrubioną czcionką za pomocą formantu MonthCalendar formularzy systemu Windows
W kontrolce <xref:System.Windows.Forms.MonthCalendar> Windows Forms można wyświetlać dni w postaci pogrubienia, jako pojedyncze daty lub powtarzające się. Można to zrobić, aby zwrócić uwagę na daty specjalne, takie jak dni wolne i weekendy.  
  
 Trzy właściwości kontrolują tę funkcję. Właściwość <xref:System.Windows.Forms.MonthCalendar.BoldedDates%2A> zawiera pojedyncze daty. Właściwość <xref:System.Windows.Forms.MonthCalendar.AnnuallyBoldedDates%2A> zawiera daty, które są wyświetlane pogrubione co rok. Właściwość <xref:System.Windows.Forms.MonthCalendar.MonthlyBoldedDates%2A> zawiera daty, które są wyświetlane pogrubione co miesiąc. Każda z tych właściwości zawiera tablicę obiektów <xref:System.DateTime>. Aby dodać lub usunąć datę z jednej z tych list, należy dodać lub usunąć obiekt <xref:System.DateTime>.  
  
### <a name="to-make-a-date-appear-in-bold-type"></a>Aby Data była wyświetlana pogrubioną czcionką  
  
1. Utwórz obiekty <xref:System.DateTime>.  
  
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
  
2. Utwórz pojedynczą datę pogrubioną, wywołując metodę <xref:System.Windows.Forms.MonthCalendar.AddBoldedDate%2A>, <xref:System.Windows.Forms.MonthCalendar.AddAnnuallyBoldedDate%2A>lub <xref:System.Windows.Forms.MonthCalendar.AddMonthlyBoldedDate%2A> formantu <xref:System.Windows.Forms.MonthCalendar>.  
  
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
  
     –lub–  
  
     Utwórz zestaw dat pogrubiony jednocześnie, tworząc tablicę <xref:System.DateTime> obiektów i przypisując ją do jednej z właściwości.  
  
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
  
### <a name="to-make-a-date-appear-in-the-regular-font"></a>Aby Data była wyświetlana w czcionce zwykłej  
  
1. Utwórz pojedynczą pogrubioną datę wyświetlaną w zwykłej czcionce, wywołując metodę <xref:System.Windows.Forms.MonthCalendar.RemoveBoldedDate%2A>, <xref:System.Windows.Forms.MonthCalendar.RemoveAnnuallyBoldedDate%2A>lub <xref:System.Windows.Forms.MonthCalendar.RemoveMonthlyBoldedDate%2A>.  
  
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
  
     –lub–  
  
     Usuń wszystkie Pogrubione daty z jednej z trzech list, wywołując metodę <xref:System.Windows.Forms.MonthCalendar.RemoveAllBoldedDates%2A>, <xref:System.Windows.Forms.MonthCalendar.RemoveAllAnnuallyBoldedDates%2A>lub <xref:System.Windows.Forms.MonthCalendar.RemoveAllMonthlyBoldedDates%2A>.  
  
    ```vb  
    MonthCalendar1.RemoveAllBoldedDates()  
    ```  
  
    ```csharp  
    monthCalendar1.RemoveAllBoldedDates();  
    ```  
  
    ```cpp  
    monthCalendar1->RemoveAllBoldedDates();  
    ```  
  
2. Zaktualizuj wygląd czcionki, wywołując metodę <xref:System.Windows.Forms.MonthCalendar.UpdateBoldedDates%2A>.  
  
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
- [Instrukcje: wybieranie zakresu dat w kontrolce MonthCalendar formularzy Windows Forms](how-to-select-a-range-of-dates-in-the-windows-forms-monthcalendar-control.md)
- [Instrukcje: zmienianie wyglądu kontrolki MonthCalendar formularzy Windows Forms](how-to-change-monthcalendar-control-appearance.md)
- [Instrukcje: wyświetlanie więcej niż jednego miesiąca w kontrolce MonthCalendar formularzy Windows Forms](display-more-than-one-month-wf-monthcalendar-control.md)
