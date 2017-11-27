---
title: "Porady: wyświetlanie większej niż jeden liczby miesięcy w formancie MonthCalendar formularzy systemu Windows"
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
- calendars [Windows Forms], formatting display
- examples [Windows Forms], calendar controls
- calendars [Windows Forms], multiple months
- MonthCalendar control [Windows Forms], formatting display
ms.assetid: d197caa2-38a5-4cb4-acc3-562130c2ace3
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 63cf236f93fa3352e536c71000f6bb110abf02fa
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-display-more-than-one-month-in-the-windows-forms-monthcalendar-control"></a><span data-ttu-id="fc917-102">Porady: wyświetlanie większej niż jeden liczby miesięcy w formancie MonthCalendar formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="fc917-102">How to: Display More than One Month in the Windows Forms MonthCalendar Control</span></span>
<span data-ttu-id="fc917-103">Formularze systemu Windows <xref:System.Windows.Forms.MonthCalendar> formant może wyświetlać do 12 miesięcy naraz.</span><span class="sxs-lookup"><span data-stu-id="fc917-103">The Windows Forms <xref:System.Windows.Forms.MonthCalendar> control can display up to 12 months at a time.</span></span> <span data-ttu-id="fc917-104">Domyślnie kontrolka ma wyświetlać tylko jeden miesiąc, ale można określić liczbę miesięcy są wyświetlane i sposób rozmieszczenia w formancie.</span><span class="sxs-lookup"><span data-stu-id="fc917-104">By default, the control displays only one month, but you can specify how many months are displayed and how they are arranged within the control.</span></span> <span data-ttu-id="fc917-105">Jeśli zmienisz wymiary kalendarza zostanie zmieniony rozmiar formantu, dlatego upewnij się, że jest za mało miejsca na formularzu dla nowych wymiarów.</span><span class="sxs-lookup"><span data-stu-id="fc917-105">When you change the calendar dimensions, the control is resized, so be sure there is enough room on the form for the new dimensions.</span></span>  
  
### <a name="to-display-multiple-months"></a><span data-ttu-id="fc917-106">Aby wyświetlić wiele miesięcy</span><span class="sxs-lookup"><span data-stu-id="fc917-106">To display multiple months</span></span>  
  
-   <span data-ttu-id="fc917-107">Ustaw <xref:System.Windows.Forms.MonthCalendar.CalendarDimensions%2A> właściwości Liczba miesięcy do wyświetlenia w poziomie i w pionie.</span><span class="sxs-lookup"><span data-stu-id="fc917-107">Set the <xref:System.Windows.Forms.MonthCalendar.CalendarDimensions%2A> property to the number of months to display horizontally and vertically.</span></span>  
  
    ```vb  
    MonthCalendar1.CalendarDimensions = New System.Drawing.Size (3,2)  
    ```  
  
    ```csharp  
    monthCalendar1.CalendarDimensions = new System.Drawing.Size (3,2);  
    ```  
  
    ```cpp  
    monthCalendar1->CalendarDimensions = System::Drawing::Size (3,2);  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="fc917-108">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="fc917-108">See Also</span></span>  
 [<span data-ttu-id="fc917-109">MonthCalendar — formant</span><span class="sxs-lookup"><span data-stu-id="fc917-109">MonthCalendar Control</span></span>](../../../../docs/framework/winforms/controls/monthcalendar-control-windows-forms.md)  
 [<span data-ttu-id="fc917-110">Porady: Wybieranie zakresu dat w formancie MonthCalendar formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="fc917-110">How to: Select a Range of Dates in the Windows Forms MonthCalendar Control</span></span>](../../../../docs/framework/winforms/controls/how-to-select-a-range-of-dates-in-the-windows-forms-monthcalendar-control.md)  
 [<span data-ttu-id="fc917-111">Porady: Zmienianie wyglądu formantu MonthCalendar formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="fc917-111">How to: Change the Windows Forms MonthCalendar Control's Appearance</span></span>](../../../../docs/framework/winforms/controls/how-to-change-monthcalendar-control-appearance.md)
