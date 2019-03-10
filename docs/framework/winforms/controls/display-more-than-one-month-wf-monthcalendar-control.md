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
# <a name="how-to-display-more-than-one-month-in-the-windows-forms-monthcalendar-control"></a><span data-ttu-id="c5540-102">Instrukcje: Wyświetl więcej niż jednego miesiąca w kontrolce MonthCalendar formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="c5540-102">How to: Display More than One Month in the Windows Forms MonthCalendar Control</span></span>
<span data-ttu-id="c5540-103">Formularze Windows <xref:System.Windows.Forms.MonthCalendar> formant może wyświetlić maksymalnie 12 miesięcy w danym momencie.</span><span class="sxs-lookup"><span data-stu-id="c5540-103">The Windows Forms <xref:System.Windows.Forms.MonthCalendar> control can display up to 12 months at a time.</span></span> <span data-ttu-id="c5540-104">Domyślnie kontrolka ma wyświetlać tylko jeden miesiąc, ale można określić liczbę miesięcy są wyświetlane i jak są rozmieszczone w kontrolce.</span><span class="sxs-lookup"><span data-stu-id="c5540-104">By default, the control displays only one month, but you can specify how many months are displayed and how they are arranged within the control.</span></span> <span data-ttu-id="c5540-105">Po zmianie wymiary kalendarza zmieni się rozmiar kontrolki, dlatego upewnij się, że jest wystarczająco dużo miejsca w formularzu dla nowych wymiarów.</span><span class="sxs-lookup"><span data-stu-id="c5540-105">When you change the calendar dimensions, the control is resized, so be sure there is enough room on the form for the new dimensions.</span></span>  
  
### <a name="to-display-multiple-months"></a><span data-ttu-id="c5540-106">Aby wyświetlić wiele miesięcy</span><span class="sxs-lookup"><span data-stu-id="c5540-106">To display multiple months</span></span>  
  
-   <span data-ttu-id="c5540-107">Ustaw <xref:System.Windows.Forms.MonthCalendar.CalendarDimensions%2A> liczbę miesięcy do wyświetlenia w poziomie i w pionie.</span><span class="sxs-lookup"><span data-stu-id="c5540-107">Set the <xref:System.Windows.Forms.MonthCalendar.CalendarDimensions%2A> property to the number of months to display horizontally and vertically.</span></span>  
  
    ```vb  
    MonthCalendar1.CalendarDimensions = New System.Drawing.Size (3,2)  
    ```  
  
    ```csharp  
    monthCalendar1.CalendarDimensions = new System.Drawing.Size (3,2);  
    ```  
  
    ```cpp  
    monthCalendar1->CalendarDimensions = System::Drawing::Size (3,2);  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="c5540-108">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c5540-108">See also</span></span>
- [<span data-ttu-id="c5540-109">MonthCalendar, kontrolka</span><span class="sxs-lookup"><span data-stu-id="c5540-109">MonthCalendar Control</span></span>](monthcalendar-control-windows-forms.md)
- [<span data-ttu-id="c5540-110">Instrukcje: Wybieranie zakresu dat w kontrolce MonthCalendar formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="c5540-110">How to: Select a Range of Dates in the Windows Forms MonthCalendar Control</span></span>](how-to-select-a-range-of-dates-in-the-windows-forms-monthcalendar-control.md)
- [<span data-ttu-id="c5540-111">Instrukcje: Zmienianie wyglądu formantu MonthCalendar formularzy Windows</span><span class="sxs-lookup"><span data-stu-id="c5540-111">How to: Change the Windows Forms MonthCalendar Control's Appearance</span></span>](how-to-change-monthcalendar-control-appearance.md)
