---
title: 'Porady: wybieranie zakresu dat w formancie MonthCalendar formularzy systemu Windows'
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
ms.openlocfilehash: 8b6d64fcffb02c4496cff3f2821861117b0062fd
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-select-a-range-of-dates-in-the-windows-forms-monthcalendar-control"></a><span data-ttu-id="cbb4a-102">Porady: wybieranie zakresu dat w formancie MonthCalendar formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="cbb4a-102">How to: Select a Range of Dates in the Windows Forms MonthCalendar Control</span></span>
<span data-ttu-id="cbb4a-103">Ważna cecha formularzy systemu Windows <xref:System.Windows.Forms.MonthCalendar> formant jest, że użytkownik może wybrać zakres dat.</span><span class="sxs-lookup"><span data-stu-id="cbb4a-103">An important feature of the Windows Forms <xref:System.Windows.Forms.MonthCalendar> control is that the user can select a range of dates.</span></span> <span data-ttu-id="cbb4a-104">Ta funkcja jest ulepszoną funkcję wyboru daty <xref:System.Windows.Forms.DateTimePicker> określanie tylko umożliwia użytkownikowi wybranie wartość jednej daty/godziny.</span><span class="sxs-lookup"><span data-stu-id="cbb4a-104">This feature is an improvement over the date-selection feature of the <xref:System.Windows.Forms.DateTimePicker> control, which only enables the user to select a single date/time value.</span></span> <span data-ttu-id="cbb4a-105">Możesz ustawić zakresu dat lub pobrać wybranego zakresu określonego przez tego użytkownika za pomocą właściwości <xref:System.Windows.Forms.MonthCalendar> formantu.</span><span class="sxs-lookup"><span data-stu-id="cbb4a-105">You can set a range of dates or get a selection range set by the user by using properties of the <xref:System.Windows.Forms.MonthCalendar> control.</span></span> <span data-ttu-id="cbb4a-106">W poniższym przykładzie pokazano, jak ustawić wybranego zakresu.</span><span class="sxs-lookup"><span data-stu-id="cbb4a-106">The following code example demonstrates how to set a selection range.</span></span>  
  
### <a name="to-select-a-range-of-dates"></a><span data-ttu-id="cbb4a-107">Aby wybrać zakres dat</span><span class="sxs-lookup"><span data-stu-id="cbb4a-107">To select a range of dates</span></span>  
  
1.  <span data-ttu-id="cbb4a-108">Utwórz <xref:System.DateTime> obiekty reprezentujące imię i nazwisko daty w zakresie.</span><span class="sxs-lookup"><span data-stu-id="cbb4a-108">Create <xref:System.DateTime> objects that represent the first and last dates in a range.</span></span>  
  
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
  
2.  <span data-ttu-id="cbb4a-109">Ustaw <xref:System.Windows.Forms.MonthCalendar.SelectionRange%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="cbb4a-109">Set the <xref:System.Windows.Forms.MonthCalendar.SelectionRange%2A> property.</span></span>  
  
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
  
     <span data-ttu-id="cbb4a-110">— lub —</span><span class="sxs-lookup"><span data-stu-id="cbb4a-110">–or–</span></span>  
  
     <span data-ttu-id="cbb4a-111">Ustaw <xref:System.Windows.Forms.MonthCalendar.SelectionStart%2A> i <xref:System.Windows.Forms.MonthCalendar.SelectionEnd%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="cbb4a-111">Set the <xref:System.Windows.Forms.MonthCalendar.SelectionStart%2A> and <xref:System.Windows.Forms.MonthCalendar.SelectionEnd%2A> properties.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="cbb4a-112">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="cbb4a-112">See Also</span></span>  
 [<span data-ttu-id="cbb4a-113">MonthCalendar, kontrolka</span><span class="sxs-lookup"><span data-stu-id="cbb4a-113">MonthCalendar Control</span></span>](../../../../docs/framework/winforms/controls/monthcalendar-control-windows-forms.md)  
 [<span data-ttu-id="cbb4a-114">Instrukcje: zmienianie wyglądu kontrolki MonthCalendar formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="cbb4a-114">How to: Change the Windows Forms MonthCalendar Control's Appearance</span></span>](../../../../docs/framework/winforms/controls/how-to-change-monthcalendar-control-appearance.md)  
 [<span data-ttu-id="cbb4a-115">Instrukcje: wyświetlanie określonych dni pogrubioną czcionką za pomocą kontrolki MonthCalendar formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="cbb4a-115">How to: Display Specific Days in Bold with the Windows Forms MonthCalendar Control</span></span>](../../../../docs/framework/winforms/controls/display-specific-days-in-bold-with-wf-monthcalendar-control.md)  
 [<span data-ttu-id="cbb4a-116">Instrukcje: wyświetlanie więcej niż jednego miesiąca w kontrolce MonthCalendar formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="cbb4a-116">How to: Display More than One Month in the Windows Forms MonthCalendar Control</span></span>](../../../../docs/framework/winforms/controls/display-more-than-one-month-wf-monthcalendar-control.md)
