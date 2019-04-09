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
ms.openlocfilehash: cf3ec21aa0272f60599f5659d78214120bcfcaf8
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59073705"
---
# <a name="how-to-display-specific-days-in-bold-with-the-windows-forms-monthcalendar-control"></a><span data-ttu-id="e7fbd-102">Instrukcje: wyświetlanie określonych dni pogrubioną czcionką za pomocą kontrolki MonthCalendar formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="e7fbd-102">How to: Display Specific Days in Bold with the Windows Forms MonthCalendar Control</span></span>
<span data-ttu-id="e7fbd-103">Formularze Windows <xref:System.Windows.Forms.MonthCalendar> formant może wyświetlić dni pogrubioną czcionką, jako pojedynczej daty lub na zasadzie powtarzające się.</span><span class="sxs-lookup"><span data-stu-id="e7fbd-103">The Windows Forms <xref:System.Windows.Forms.MonthCalendar> control can display days in bold type, either as singular dates or on a repeating basis.</span></span> <span data-ttu-id="e7fbd-104">Możesz zrobić to, aby zwrócić uwagę czytelnika na wybranych dat, takich jak dni wolnych od pracy i weekendów.</span><span class="sxs-lookup"><span data-stu-id="e7fbd-104">You might do this to draw attention to special dates, such as holidays and weekends.</span></span>  
  
 <span data-ttu-id="e7fbd-105">Trzy właściwości kontroli tej funkcji.</span><span class="sxs-lookup"><span data-stu-id="e7fbd-105">Three properties control this feature.</span></span> <span data-ttu-id="e7fbd-106"><xref:System.Windows.Forms.MonthCalendar.BoldedDates%2A> Właściwość zawiera pojedynczy daty.</span><span class="sxs-lookup"><span data-stu-id="e7fbd-106">The <xref:System.Windows.Forms.MonthCalendar.BoldedDates%2A> property contains single dates.</span></span> <span data-ttu-id="e7fbd-107"><xref:System.Windows.Forms.MonthCalendar.AnnuallyBoldedDates%2A> Właściwość zawiera daty wyświetlane wytłuszczonym drukiem co roku.</span><span class="sxs-lookup"><span data-stu-id="e7fbd-107">The <xref:System.Windows.Forms.MonthCalendar.AnnuallyBoldedDates%2A> property contains dates that appear in bold every year.</span></span> <span data-ttu-id="e7fbd-108"><xref:System.Windows.Forms.MonthCalendar.MonthlyBoldedDates%2A> Właściwość zawiera daty, które są pogrubione co miesiąc.</span><span class="sxs-lookup"><span data-stu-id="e7fbd-108">The <xref:System.Windows.Forms.MonthCalendar.MonthlyBoldedDates%2A> property contains dates that appear in bold every month.</span></span> <span data-ttu-id="e7fbd-109">Każdy z tych właściwości zawiera tablicę <xref:System.DateTime> obiektów.</span><span class="sxs-lookup"><span data-stu-id="e7fbd-109">Each of these properties contains an array of <xref:System.DateTime> objects.</span></span> <span data-ttu-id="e7fbd-110">Aby dodać lub usunąć wartość typu date z jedną z tych list, należy dodać lub usunąć <xref:System.DateTime> obiektu.</span><span class="sxs-lookup"><span data-stu-id="e7fbd-110">To add or remove a date from one of these lists, you must add or remove a <xref:System.DateTime> object.</span></span>  
  
### <a name="to-make-a-date-appear-in-bold-type"></a><span data-ttu-id="e7fbd-111">Daty są wyświetlane pogrubioną czcionką</span><span class="sxs-lookup"><span data-stu-id="e7fbd-111">To make a date appear in bold type</span></span>  
  
1.  <span data-ttu-id="e7fbd-112">Utwórz <xref:System.DateTime> obiektów.</span><span class="sxs-lookup"><span data-stu-id="e7fbd-112">Create the <xref:System.DateTime> objects.</span></span>  
  
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
  
2.  <span data-ttu-id="e7fbd-113">Pogrubienie pojedyncza Data, wywołując <xref:System.Windows.Forms.MonthCalendar.AddBoldedDate%2A>, <xref:System.Windows.Forms.MonthCalendar.AddAnnuallyBoldedDate%2A>, lub <xref:System.Windows.Forms.MonthCalendar.AddMonthlyBoldedDate%2A> metody <xref:System.Windows.Forms.MonthCalendar> kontroli.</span><span class="sxs-lookup"><span data-stu-id="e7fbd-113">Make a single date bold by calling the <xref:System.Windows.Forms.MonthCalendar.AddBoldedDate%2A>, <xref:System.Windows.Forms.MonthCalendar.AddAnnuallyBoldedDate%2A>, or <xref:System.Windows.Forms.MonthCalendar.AddMonthlyBoldedDate%2A> method of the <xref:System.Windows.Forms.MonthCalendar> control.</span></span>  
  
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
  
     <span data-ttu-id="e7fbd-114">— lub —</span><span class="sxs-lookup"><span data-stu-id="e7fbd-114">–or–</span></span>  
  
     <span data-ttu-id="e7fbd-115">Pogrubienie zestaw dat w całości, tworząc tablicę <xref:System.DateTime> obiektów i przypisywanie jej do jednej z właściwości.</span><span class="sxs-lookup"><span data-stu-id="e7fbd-115">Make a set of dates bold all at once by creating an array of <xref:System.DateTime> objects and assigning it to one of the properties.</span></span>  
  
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
  
### <a name="to-make-a-date-appear-in-the-regular-font"></a><span data-ttu-id="e7fbd-116">Daty są wyświetlane w regularnych czcionki</span><span class="sxs-lookup"><span data-stu-id="e7fbd-116">To make a date appear in the regular font</span></span>  
  
1.  <span data-ttu-id="e7fbd-117">Pojawiają się w regularnych czcionki przez wywołanie datę pogrubiony pojedynczego <xref:System.Windows.Forms.MonthCalendar.RemoveBoldedDate%2A>, <xref:System.Windows.Forms.MonthCalendar.RemoveAnnuallyBoldedDate%2A>, lub <xref:System.Windows.Forms.MonthCalendar.RemoveMonthlyBoldedDate%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="e7fbd-117">Make a single bolded date appear in the regular font by calling the <xref:System.Windows.Forms.MonthCalendar.RemoveBoldedDate%2A>, <xref:System.Windows.Forms.MonthCalendar.RemoveAnnuallyBoldedDate%2A>, or <xref:System.Windows.Forms.MonthCalendar.RemoveMonthlyBoldedDate%2A> method.</span></span>  
  
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
  
     <span data-ttu-id="e7fbd-118">— lub —</span><span class="sxs-lookup"><span data-stu-id="e7fbd-118">–or–</span></span>  
  
     <span data-ttu-id="e7fbd-119">Usuń pogrubione daty z jedną z trzech list, wywołując <xref:System.Windows.Forms.MonthCalendar.RemoveAllBoldedDates%2A>, <xref:System.Windows.Forms.MonthCalendar.RemoveAllAnnuallyBoldedDates%2A>, lub <xref:System.Windows.Forms.MonthCalendar.RemoveAllMonthlyBoldedDates%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="e7fbd-119">Remove all the bolded dates from one of the three lists by calling the <xref:System.Windows.Forms.MonthCalendar.RemoveAllBoldedDates%2A>, <xref:System.Windows.Forms.MonthCalendar.RemoveAllAnnuallyBoldedDates%2A>, or <xref:System.Windows.Forms.MonthCalendar.RemoveAllMonthlyBoldedDates%2A> method.</span></span>  
  
    ```vb  
    MonthCalendar1.RemoveAllBoldedDates()  
    ```  
  
    ```csharp  
    monthCalendar1.RemoveAllBoldedDates();  
    ```  
  
    ```cpp  
    monthCalendar1->RemoveAllBoldedDates();  
    ```  
  
2.  <span data-ttu-id="e7fbd-120">Zaktualizuj wygląd czcionki, wywołując <xref:System.Windows.Forms.MonthCalendar.UpdateBoldedDates%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="e7fbd-120">Update the appearance of the font by calling the <xref:System.Windows.Forms.MonthCalendar.UpdateBoldedDates%2A> method.</span></span>  
  
    ```vb  
    MonthCalendar1.UpdateBoldedDates()  
    ```  
  
    ```csharp  
    monthCalendar1.UpdateBoldedDates();  
    ```  
  
    ```cpp  
    monthCalendar1->UpdateBoldedDates();  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="e7fbd-121">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e7fbd-121">See also</span></span>

- [<span data-ttu-id="e7fbd-122">MonthCalendar, kontrolka</span><span class="sxs-lookup"><span data-stu-id="e7fbd-122">MonthCalendar Control</span></span>](monthcalendar-control-windows-forms.md)
- [<span data-ttu-id="e7fbd-123">Instrukcje: wybieranie zakresu dat w kontrolce MonthCalendar formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="e7fbd-123">How to: Select a Range of Dates in the Windows Forms MonthCalendar Control</span></span>](how-to-select-a-range-of-dates-in-the-windows-forms-monthcalendar-control.md)
- [<span data-ttu-id="e7fbd-124">Instrukcje: zmienianie wyglądu kontrolki MonthCalendar formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="e7fbd-124">How to: Change the Windows Forms MonthCalendar Control's Appearance</span></span>](how-to-change-monthcalendar-control-appearance.md)
- [<span data-ttu-id="e7fbd-125">Instrukcje: wyświetlanie większej niż jeden liczby miesięcy w kontrolce MonthCalendar formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="e7fbd-125">How to: Display More than One Month in the Windows Forms MonthCalendar Control</span></span>](display-more-than-one-month-wf-monthcalendar-control.md)
