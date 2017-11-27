---
title: 'Porady: drukowanie formularza przewijanego (Visual Basic)'
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- entire form [Visual Basic], printing
- scrollable form [Visual Basic], printing
ms.assetid: 1196e1cf-b77f-4928-a3e4-85b51ba3787d
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 380e0f833dc69718142809c99ed7615256dd2e73
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-print-a-scrollable-form-visual-basic"></a><span data-ttu-id="e8373-102">Porady: drukowanie formularza przewijanego (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e8373-102">How to: Print a Scrollable Form (Visual Basic)</span></span>
<span data-ttu-id="e8373-103"><xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> Składnika pozwala na szybkie wydrukowanie obrazu formularza bez użycia <xref:System.Drawing.Printing.PrintDocument> składnika.</span><span class="sxs-lookup"><span data-stu-id="e8373-103">The <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> component enables you to quickly print an image of a form without using a <xref:System.Drawing.Printing.PrintDocument> component.</span></span> <span data-ttu-id="e8373-104">Domyślnie tylko widoczne części formularza jest drukowany; Jeśli użytkownik został zmieniony formularza w czasie wykonywania, obrazu nie mogą drukować, zgodnie z założeniami.</span><span class="sxs-lookup"><span data-stu-id="e8373-104">By default, only the currently visible part of the form is printed; if a user has resized the form at run time, the image may not print as intended.</span></span> <span data-ttu-id="e8373-105">Poniższa procedura przedstawia sposób Drukowanie obszarów klienckich pełne formularza przewijanego, nawet wtedy, gdy formularz został zmieniony.</span><span class="sxs-lookup"><span data-stu-id="e8373-105">The following procedure shows how to print the complete client area of a scrollable form, even if the form has been resized.</span></span>  
  
 <span data-ttu-id="e8373-106">Formantów PowerPack nie są uwzględnione w programie Visual Studio, ale można pobrać je z [Centrum pobierania](http://www.microsoft.com/en-us/download/details.aspx?id=25169).</span><span class="sxs-lookup"><span data-stu-id="e8373-106">The PowerPack controls are no longer included in Visual Studio, but you can download them from the [Download Center](http://www.microsoft.com/en-us/download/details.aspx?id=25169).</span></span>  
  
### <a name="to-print-the-complete-client-area-of-a-scrollable-form"></a><span data-ttu-id="e8373-107">Drukowanie obszarów klienckich pełne formularza przewijanego</span><span class="sxs-lookup"><span data-stu-id="e8373-107">To print the complete client area of a scrollable form</span></span>  
  
1.  <span data-ttu-id="e8373-108">W **przybornika**, kliknij przycisk **Visual Basic PowerPacks** karcie, a następnie przeciągnij <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> składnika na formularzu.</span><span class="sxs-lookup"><span data-stu-id="e8373-108">In the **Toolbox**, click the **Visual Basic PowerPacks** tab and then drag the <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> component onto the form.</span></span>  
  
     <span data-ttu-id="e8373-109"><xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> Składnik zostanie dodany do składnika na pasku zadań.</span><span class="sxs-lookup"><span data-stu-id="e8373-109">The <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> component will be added to the component tray.</span></span>  
  
2.  <span data-ttu-id="e8373-110">W **właściwości** ustaw <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.PrintAction%2A> właściwości <xref:System.Drawing.Printing.PrintAction.PrintToPrinter>.</span><span class="sxs-lookup"><span data-stu-id="e8373-110">In the **Properties** window, set the <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.PrintAction%2A> property to <xref:System.Drawing.Printing.PrintAction.PrintToPrinter>.</span></span>  
  
3.  <span data-ttu-id="e8373-111">Dodaj następujący kod do obsługi zdarzeń odpowiednie (na przykład w `Click` programu obsługi zdarzeń dla **drukowania**`Button`).</span><span class="sxs-lookup"><span data-stu-id="e8373-111">Add the following code in the appropriate event handler (for example, in the `Click` event handler for a **Print**`Button`).</span></span>  
  
    ```  
    PrintForm1.Print(Me, PowerPacks.Printing.PrintForm.PrintOption.Scrollable)  
    ```  
  
    > [!NOTE]
    >  <span data-ttu-id="e8373-112">W niektórych systemach operacyjnych, tekst lub grafiki narysowanymi przez <xref:System.Drawing.Graphics> metody nie mogą drukować poprawnie.</span><span class="sxs-lookup"><span data-stu-id="e8373-112">On some operating systems, text or graphics drawn by <xref:System.Drawing.Graphics> methods may not print correctly.</span></span> <span data-ttu-id="e8373-113">W takim przypadku nie będzie możliwe do drukowania z `Scrollable` parametru.</span><span class="sxs-lookup"><span data-stu-id="e8373-113">In this case, you will not be able to print with the `Scrollable` parameter.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e8373-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e8373-114">See Also</span></span>  
 <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.PrintAction%2A>  
 <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.Print%2A>  
 [<span data-ttu-id="e8373-115">Składnik PrintForm</span><span class="sxs-lookup"><span data-stu-id="e8373-115">PrintForm Component</span></span>](../../../visual-basic/developing-apps/printing/printform-component.md)  
 [<span data-ttu-id="e8373-116">Porady: drukowanie obszarów klienckich formularza</span><span class="sxs-lookup"><span data-stu-id="e8373-116">How to: Print the Client Area of a Form</span></span>](../../../visual-basic/developing-apps/printing/how-to-print-the-client-area-of-a-form.md)  
 [<span data-ttu-id="e8373-117">Porady: drukowanie obszarów klienckich formularza i</span><span class="sxs-lookup"><span data-stu-id="e8373-117">How to: Print Client and Non-Client Areas of a Form</span></span>](../../../visual-basic/developing-apps/printing/how-to-print-client-and-non-client-areas-of-a-form.md)
