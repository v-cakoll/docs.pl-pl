---
title: "Porady: wyświetlanie określonych dni pogrubioną czcionką za pomocą formantu MonthCalendar formularzy systemu Windows"
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
- calendars [Windows Forms], displaying dates in bold
- examples [Windows Forms], calendar controls
- GetDayBold event
- MonthCalendar control [Windows Forms], dates displayed in bold
ms.assetid: 8b20db5b-8118-4825-90e8-2c45c186ac7d
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 18a199592a8bfbef2e4a15b056e37af6d885f5f8
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-display-specific-days-in-bold-with-the-windows-forms-monthcalendar-control"></a><span data-ttu-id="6875d-102">Porady: wyświetlanie określonych dni pogrubioną czcionką za pomocą formantu MonthCalendar formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="6875d-102">How to: Display Specific Days in Bold with the Windows Forms MonthCalendar Control</span></span>
<span data-ttu-id="6875d-103">Formularze systemu Windows <xref:System.Windows.Forms.MonthCalendar> formant może wyświetlać dni pogrubioną czcionką jako pojedynczej daty lub na podstawie powtarzających się.</span><span class="sxs-lookup"><span data-stu-id="6875d-103">The Windows Forms <xref:System.Windows.Forms.MonthCalendar> control can display days in bold type, either as singular dates or on a repeating basis.</span></span> <span data-ttu-id="6875d-104">Możesz zrobić to, aby zwrócić uwagę na wybranych dat, takich jak dni wolnych i w weekendy.</span><span class="sxs-lookup"><span data-stu-id="6875d-104">You might do this to draw attention to special dates, such as holidays and weekends.</span></span>  
  
 <span data-ttu-id="6875d-105">Trzy właściwości formantu tej funkcji.</span><span class="sxs-lookup"><span data-stu-id="6875d-105">Three properties control this feature.</span></span> <span data-ttu-id="6875d-106"><xref:System.Windows.Forms.MonthCalendar.BoldedDates%2A> Właściwość zawiera pojedynczy daty.</span><span class="sxs-lookup"><span data-stu-id="6875d-106">The <xref:System.Windows.Forms.MonthCalendar.BoldedDates%2A> property contains single dates.</span></span> <span data-ttu-id="6875d-107"><xref:System.Windows.Forms.MonthCalendar.AnnuallyBoldedDates%2A> Właściwość zawiera daty, które są pogrubione co roku.</span><span class="sxs-lookup"><span data-stu-id="6875d-107">The <xref:System.Windows.Forms.MonthCalendar.AnnuallyBoldedDates%2A> property contains dates that appear in bold every year.</span></span> <span data-ttu-id="6875d-108"><xref:System.Windows.Forms.MonthCalendar.MonthlyBoldedDates%2A> Właściwość zawiera daty, które są pogrubione co miesiąc.</span><span class="sxs-lookup"><span data-stu-id="6875d-108">The <xref:System.Windows.Forms.MonthCalendar.MonthlyBoldedDates%2A> property contains dates that appear in bold every month.</span></span> <span data-ttu-id="6875d-109">Każdy z tych właściwości zawiera tablicę <xref:System.DateTime> obiektów.</span><span class="sxs-lookup"><span data-stu-id="6875d-109">Each of these properties contains an array of <xref:System.DateTime> objects.</span></span> <span data-ttu-id="6875d-110">Aby dodać lub usunąć datę z jednego z tych list, musisz dodać lub usunąć <xref:System.DateTime> obiektu.</span><span class="sxs-lookup"><span data-stu-id="6875d-110">To add or remove a date from one of these lists, you must add or remove a <xref:System.DateTime> object.</span></span>  
  
### <a name="to-make-a-date-appear-in-bold-type"></a><span data-ttu-id="6875d-111">Aby wyświetlone czcionką pogrubioną datę</span><span class="sxs-lookup"><span data-stu-id="6875d-111">To make a date appear in bold type</span></span>  
  
1.  <span data-ttu-id="6875d-112">Utwórz <xref:System.DateTime> obiektów.</span><span class="sxs-lookup"><span data-stu-id="6875d-112">Create the <xref:System.DateTime> objects.</span></span>  
  
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
  
2.  <span data-ttu-id="6875d-113">Pogrubienie pojedyncza Data wywołując <xref:System.Windows.Forms.MonthCalendar.AddBoldedDate%2A>, <xref:System.Windows.Forms.MonthCalendar.AddAnnuallyBoldedDate%2A>, lub <xref:System.Windows.Forms.MonthCalendar.AddMonthlyBoldedDate%2A> metody <xref:System.Windows.Forms.MonthCalendar> formantu.</span><span class="sxs-lookup"><span data-stu-id="6875d-113">Make a single date bold by calling the <xref:System.Windows.Forms.MonthCalendar.AddBoldedDate%2A>, <xref:System.Windows.Forms.MonthCalendar.AddAnnuallyBoldedDate%2A>, or <xref:System.Windows.Forms.MonthCalendar.AddMonthlyBoldedDate%2A> method of the <xref:System.Windows.Forms.MonthCalendar> control.</span></span>  
  
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
  
     <span data-ttu-id="6875d-114">— lub —</span><span class="sxs-lookup"><span data-stu-id="6875d-114">–or–</span></span>  
  
     <span data-ttu-id="6875d-115">Zastosuj pogrubienie zestaw dat w całości, tworząc tablicę <xref:System.DateTime> obiektów i przypisywania go do jednej z właściwości.</span><span class="sxs-lookup"><span data-stu-id="6875d-115">Make a set of dates bold all at once by creating an array of <xref:System.DateTime> objects and assigning it to one of the properties.</span></span>  
  
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
  
### <a name="to-make-a-date-appear-in-the-regular-font"></a><span data-ttu-id="6875d-116">Daty są wyświetlane w regularnych czcionki</span><span class="sxs-lookup"><span data-stu-id="6875d-116">To make a date appear in the regular font</span></span>  
  
1.  <span data-ttu-id="6875d-117">Pogrubiony jednej daty są wyświetlane w regularnych czcionki, wywołując <xref:System.Windows.Forms.MonthCalendar.RemoveBoldedDate%2A>, <xref:System.Windows.Forms.MonthCalendar.RemoveAnnuallyBoldedDate%2A>, lub <xref:System.Windows.Forms.MonthCalendar.RemoveMonthlyBoldedDate%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="6875d-117">Make a single bolded date appear in the regular font by calling the <xref:System.Windows.Forms.MonthCalendar.RemoveBoldedDate%2A>, <xref:System.Windows.Forms.MonthCalendar.RemoveAnnuallyBoldedDate%2A>, or <xref:System.Windows.Forms.MonthCalendar.RemoveMonthlyBoldedDate%2A> method.</span></span>  
  
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
  
     <span data-ttu-id="6875d-118">— lub —</span><span class="sxs-lookup"><span data-stu-id="6875d-118">–or–</span></span>  
  
     <span data-ttu-id="6875d-119">Usuń pogrubione daty z jednej z trzech list przez wywołanie metody <xref:System.Windows.Forms.MonthCalendar.RemoveAllBoldedDates%2A>, <xref:System.Windows.Forms.MonthCalendar.RemoveAllAnnuallyBoldedDates%2A>, lub <xref:System.Windows.Forms.MonthCalendar.RemoveAllMonthlyBoldedDates%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="6875d-119">Remove all the bolded dates from one of the three lists by calling the <xref:System.Windows.Forms.MonthCalendar.RemoveAllBoldedDates%2A>, <xref:System.Windows.Forms.MonthCalendar.RemoveAllAnnuallyBoldedDates%2A>, or <xref:System.Windows.Forms.MonthCalendar.RemoveAllMonthlyBoldedDates%2A> method.</span></span>  
  
    ```vb  
    MonthCalendar1.RemoveAllBoldedDates()  
    ```  
  
    ```csharp  
    monthCalendar1.RemoveAllBoldedDates();  
    ```  
  
    ```cpp  
    monthCalendar1->RemoveAllBoldedDates();  
    ```  
  
2.  <span data-ttu-id="6875d-120">Zaktualizuj wygląd czcionki przez wywołanie metody <xref:System.Windows.Forms.MonthCalendar.UpdateBoldedDates%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="6875d-120">Update the appearance of the font by calling the <xref:System.Windows.Forms.MonthCalendar.UpdateBoldedDates%2A> method.</span></span>  
  
    ```vb  
    MonthCalendar1.UpdateBoldedDates()  
    ```  
  
    ```csharp  
    monthCalendar1.UpdateBoldedDates();  
    ```  
  
    ```cpp  
    monthCalendar1->UpdateBoldedDates();  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="6875d-121">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="6875d-121">See Also</span></span>  
 [<span data-ttu-id="6875d-122">MonthCalendar — formant</span><span class="sxs-lookup"><span data-stu-id="6875d-122">MonthCalendar Control</span></span>](../../../../docs/framework/winforms/controls/monthcalendar-control-windows-forms.md)  
 [<span data-ttu-id="6875d-123">Porady: Wybieranie zakresu dat w formancie MonthCalendar formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="6875d-123">How to: Select a Range of Dates in the Windows Forms MonthCalendar Control</span></span>](../../../../docs/framework/winforms/controls/how-to-select-a-range-of-dates-in-the-windows-forms-monthcalendar-control.md)  
 [<span data-ttu-id="6875d-124">Porady: Zmienianie wyglądu formantu MonthCalendar formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="6875d-124">How to: Change the Windows Forms MonthCalendar Control's Appearance</span></span>](../../../../docs/framework/winforms/controls/how-to-change-monthcalendar-control-appearance.md)  
 [<span data-ttu-id="6875d-125">Porady: wyświetlanie więcej niż jeden miesiąc w formancie MonthCalendar formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="6875d-125">How to: Display More than One Month in the Windows Forms MonthCalendar Control</span></span>](../../../../docs/framework/winforms/controls/display-more-than-one-month-wf-monthcalendar-control.md)
