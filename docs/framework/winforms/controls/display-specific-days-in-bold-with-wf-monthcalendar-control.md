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
# <a name="how-to-display-specific-days-in-bold-with-the-windows-forms-monthcalendar-control"></a><span data-ttu-id="e6fb1-102">Porady: wyświetlanie określonych dni pogrubioną czcionką za pomocą formantu MonthCalendar formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="e6fb1-102">How to: Display Specific Days in Bold with the Windows Forms MonthCalendar Control</span></span>
<span data-ttu-id="e6fb1-103">W kontrolce <xref:System.Windows.Forms.MonthCalendar> Windows Forms można wyświetlać dni w postaci pogrubienia, jako pojedyncze daty lub powtarzające się.</span><span class="sxs-lookup"><span data-stu-id="e6fb1-103">The Windows Forms <xref:System.Windows.Forms.MonthCalendar> control can display days in bold type, either as singular dates or on a repeating basis.</span></span> <span data-ttu-id="e6fb1-104">Można to zrobić, aby zwrócić uwagę na daty specjalne, takie jak dni wolne i weekendy.</span><span class="sxs-lookup"><span data-stu-id="e6fb1-104">You might do this to draw attention to special dates, such as holidays and weekends.</span></span>  
  
 <span data-ttu-id="e6fb1-105">Trzy właściwości kontrolują tę funkcję.</span><span class="sxs-lookup"><span data-stu-id="e6fb1-105">Three properties control this feature.</span></span> <span data-ttu-id="e6fb1-106">Właściwość <xref:System.Windows.Forms.MonthCalendar.BoldedDates%2A> zawiera pojedyncze daty.</span><span class="sxs-lookup"><span data-stu-id="e6fb1-106">The <xref:System.Windows.Forms.MonthCalendar.BoldedDates%2A> property contains single dates.</span></span> <span data-ttu-id="e6fb1-107">Właściwość <xref:System.Windows.Forms.MonthCalendar.AnnuallyBoldedDates%2A> zawiera daty, które są wyświetlane pogrubione co rok.</span><span class="sxs-lookup"><span data-stu-id="e6fb1-107">The <xref:System.Windows.Forms.MonthCalendar.AnnuallyBoldedDates%2A> property contains dates that appear in bold every year.</span></span> <span data-ttu-id="e6fb1-108">Właściwość <xref:System.Windows.Forms.MonthCalendar.MonthlyBoldedDates%2A> zawiera daty, które są wyświetlane pogrubione co miesiąc.</span><span class="sxs-lookup"><span data-stu-id="e6fb1-108">The <xref:System.Windows.Forms.MonthCalendar.MonthlyBoldedDates%2A> property contains dates that appear in bold every month.</span></span> <span data-ttu-id="e6fb1-109">Każda z tych właściwości zawiera tablicę obiektów <xref:System.DateTime>.</span><span class="sxs-lookup"><span data-stu-id="e6fb1-109">Each of these properties contains an array of <xref:System.DateTime> objects.</span></span> <span data-ttu-id="e6fb1-110">Aby dodać lub usunąć datę z jednej z tych list, należy dodać lub usunąć obiekt <xref:System.DateTime>.</span><span class="sxs-lookup"><span data-stu-id="e6fb1-110">To add or remove a date from one of these lists, you must add or remove a <xref:System.DateTime> object.</span></span>  
  
### <a name="to-make-a-date-appear-in-bold-type"></a><span data-ttu-id="e6fb1-111">Aby Data była wyświetlana pogrubioną czcionką</span><span class="sxs-lookup"><span data-stu-id="e6fb1-111">To make a date appear in bold type</span></span>  
  
1. <span data-ttu-id="e6fb1-112">Utwórz obiekty <xref:System.DateTime>.</span><span class="sxs-lookup"><span data-stu-id="e6fb1-112">Create the <xref:System.DateTime> objects.</span></span>  
  
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
  
2. <span data-ttu-id="e6fb1-113">Utwórz pojedynczą datę pogrubioną, wywołując metodę <xref:System.Windows.Forms.MonthCalendar.AddBoldedDate%2A>, <xref:System.Windows.Forms.MonthCalendar.AddAnnuallyBoldedDate%2A>lub <xref:System.Windows.Forms.MonthCalendar.AddMonthlyBoldedDate%2A> formantu <xref:System.Windows.Forms.MonthCalendar>.</span><span class="sxs-lookup"><span data-stu-id="e6fb1-113">Make a single date bold by calling the <xref:System.Windows.Forms.MonthCalendar.AddBoldedDate%2A>, <xref:System.Windows.Forms.MonthCalendar.AddAnnuallyBoldedDate%2A>, or <xref:System.Windows.Forms.MonthCalendar.AddMonthlyBoldedDate%2A> method of the <xref:System.Windows.Forms.MonthCalendar> control.</span></span>  
  
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
  
     <span data-ttu-id="e6fb1-114">–lub–</span><span class="sxs-lookup"><span data-stu-id="e6fb1-114">–or–</span></span>  
  
     <span data-ttu-id="e6fb1-115">Utwórz zestaw dat pogrubiony jednocześnie, tworząc tablicę <xref:System.DateTime> obiektów i przypisując ją do jednej z właściwości.</span><span class="sxs-lookup"><span data-stu-id="e6fb1-115">Make a set of dates bold all at once by creating an array of <xref:System.DateTime> objects and assigning it to one of the properties.</span></span>  
  
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
  
### <a name="to-make-a-date-appear-in-the-regular-font"></a><span data-ttu-id="e6fb1-116">Aby Data była wyświetlana w czcionce zwykłej</span><span class="sxs-lookup"><span data-stu-id="e6fb1-116">To make a date appear in the regular font</span></span>  
  
1. <span data-ttu-id="e6fb1-117">Utwórz pojedynczą pogrubioną datę wyświetlaną w zwykłej czcionce, wywołując metodę <xref:System.Windows.Forms.MonthCalendar.RemoveBoldedDate%2A>, <xref:System.Windows.Forms.MonthCalendar.RemoveAnnuallyBoldedDate%2A>lub <xref:System.Windows.Forms.MonthCalendar.RemoveMonthlyBoldedDate%2A>.</span><span class="sxs-lookup"><span data-stu-id="e6fb1-117">Make a single bolded date appear in the regular font by calling the <xref:System.Windows.Forms.MonthCalendar.RemoveBoldedDate%2A>, <xref:System.Windows.Forms.MonthCalendar.RemoveAnnuallyBoldedDate%2A>, or <xref:System.Windows.Forms.MonthCalendar.RemoveMonthlyBoldedDate%2A> method.</span></span>  
  
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
  
     <span data-ttu-id="e6fb1-118">–lub–</span><span class="sxs-lookup"><span data-stu-id="e6fb1-118">–or–</span></span>  
  
     <span data-ttu-id="e6fb1-119">Usuń wszystkie Pogrubione daty z jednej z trzech list, wywołując metodę <xref:System.Windows.Forms.MonthCalendar.RemoveAllBoldedDates%2A>, <xref:System.Windows.Forms.MonthCalendar.RemoveAllAnnuallyBoldedDates%2A>lub <xref:System.Windows.Forms.MonthCalendar.RemoveAllMonthlyBoldedDates%2A>.</span><span class="sxs-lookup"><span data-stu-id="e6fb1-119">Remove all the bolded dates from one of the three lists by calling the <xref:System.Windows.Forms.MonthCalendar.RemoveAllBoldedDates%2A>, <xref:System.Windows.Forms.MonthCalendar.RemoveAllAnnuallyBoldedDates%2A>, or <xref:System.Windows.Forms.MonthCalendar.RemoveAllMonthlyBoldedDates%2A> method.</span></span>  
  
    ```vb  
    MonthCalendar1.RemoveAllBoldedDates()  
    ```  
  
    ```csharp  
    monthCalendar1.RemoveAllBoldedDates();  
    ```  
  
    ```cpp  
    monthCalendar1->RemoveAllBoldedDates();  
    ```  
  
2. <span data-ttu-id="e6fb1-120">Zaktualizuj wygląd czcionki, wywołując metodę <xref:System.Windows.Forms.MonthCalendar.UpdateBoldedDates%2A>.</span><span class="sxs-lookup"><span data-stu-id="e6fb1-120">Update the appearance of the font by calling the <xref:System.Windows.Forms.MonthCalendar.UpdateBoldedDates%2A> method.</span></span>  
  
    ```vb  
    MonthCalendar1.UpdateBoldedDates()  
    ```  
  
    ```csharp  
    monthCalendar1.UpdateBoldedDates();  
    ```  
  
    ```cpp  
    monthCalendar1->UpdateBoldedDates();  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="e6fb1-121">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e6fb1-121">See also</span></span>

- [<span data-ttu-id="e6fb1-122">MonthCalendar, kontrolka</span><span class="sxs-lookup"><span data-stu-id="e6fb1-122">MonthCalendar Control</span></span>](monthcalendar-control-windows-forms.md)
- [<span data-ttu-id="e6fb1-123">Instrukcje: wybieranie zakresu dat w kontrolce MonthCalendar formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="e6fb1-123">How to: Select a Range of Dates in the Windows Forms MonthCalendar Control</span></span>](how-to-select-a-range-of-dates-in-the-windows-forms-monthcalendar-control.md)
- [<span data-ttu-id="e6fb1-124">Instrukcje: zmienianie wyglądu kontrolki MonthCalendar formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="e6fb1-124">How to: Change the Windows Forms MonthCalendar Control's Appearance</span></span>](how-to-change-monthcalendar-control-appearance.md)
- [<span data-ttu-id="e6fb1-125">Instrukcje: wyświetlanie więcej niż jednego miesiąca w kontrolce MonthCalendar formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="e6fb1-125">How to: Display More than One Month in the Windows Forms MonthCalendar Control</span></span>](display-more-than-one-month-wf-monthcalendar-control.md)
