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
# <a name="how-to-display-more-than-one-month-in-the-windows-forms-monthcalendar-control"></a><span data-ttu-id="1300d-102">Porady: wyświetlanie większej niż jeden liczby miesięcy w formancie MonthCalendar formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="1300d-102">How to: Display More than One Month in the Windows Forms MonthCalendar Control</span></span>
<span data-ttu-id="1300d-103">Kontrolka <xref:System.Windows.Forms.MonthCalendar> Windows Forms może być wyświetlana nawet przez 12 miesięcy.</span><span class="sxs-lookup"><span data-stu-id="1300d-103">The Windows Forms <xref:System.Windows.Forms.MonthCalendar> control can display up to 12 months at a time.</span></span> <span data-ttu-id="1300d-104">Domyślnie kontrolka wyświetla tylko jeden miesiąc, ale można określić, ile miesięcy jest wyświetlanych i jak są ułożone w formancie.</span><span class="sxs-lookup"><span data-stu-id="1300d-104">By default, the control displays only one month, but you can specify how many months are displayed and how they are arranged within the control.</span></span> <span data-ttu-id="1300d-105">Gdy zmienisz wymiary kalendarza, rozmiar formantu jest zmieniany, więc upewnij się, że w formularzu istnieją wystarczające miejsce dla nowych wymiarów.</span><span class="sxs-lookup"><span data-stu-id="1300d-105">When you change the calendar dimensions, the control is resized, so be sure there is enough room on the form for the new dimensions.</span></span>  
  
### <a name="to-display-multiple-months"></a><span data-ttu-id="1300d-106">Aby wyświetlić wiele miesięcy</span><span class="sxs-lookup"><span data-stu-id="1300d-106">To display multiple months</span></span>  
  
- <span data-ttu-id="1300d-107">Ustaw właściwość <xref:System.Windows.Forms.MonthCalendar.CalendarDimensions%2A> na liczbę miesięcy, która ma być wyświetlana w poziomie i w pionie.</span><span class="sxs-lookup"><span data-stu-id="1300d-107">Set the <xref:System.Windows.Forms.MonthCalendar.CalendarDimensions%2A> property to the number of months to display horizontally and vertically.</span></span>  
  
    ```vb  
    MonthCalendar1.CalendarDimensions = New System.Drawing.Size (3,2)  
    ```  
  
    ```csharp  
    monthCalendar1.CalendarDimensions = new System.Drawing.Size (3,2);  
    ```  
  
    ```cpp  
    monthCalendar1->CalendarDimensions = System::Drawing::Size (3,2);  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="1300d-108">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="1300d-108">See also</span></span>

- [<span data-ttu-id="1300d-109">MonthCalendar, kontrolka</span><span class="sxs-lookup"><span data-stu-id="1300d-109">MonthCalendar Control</span></span>](monthcalendar-control-windows-forms.md)
- [<span data-ttu-id="1300d-110">Instrukcje: wybieranie zakresu dat w kontrolce MonthCalendar formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="1300d-110">How to: Select a Range of Dates in the Windows Forms MonthCalendar Control</span></span>](how-to-select-a-range-of-dates-in-the-windows-forms-monthcalendar-control.md)
- [<span data-ttu-id="1300d-111">Instrukcje: zmienianie wyglądu kontrolki MonthCalendar formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="1300d-111">How to: Change the Windows Forms MonthCalendar Control's Appearance</span></span>](how-to-change-monthcalendar-control-appearance.md)
