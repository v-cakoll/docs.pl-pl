---
title: 'Porady: drukowanie obszarów klienckich i nieklienckich formularza (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- title bar [Visual Basic], printing
- printing
- borders [Visual Basic], printing
- entire form
- non-client area [Visual Basic], printing
ms.assetid: 856bb0e4-dbc3-47e2-81cd-4b376cf07757
ms.openlocfilehash: 566cf295462945a6bc90bc96f8907de34646bd00
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33584745"
---
# <a name="how-to-print-client-and-non-client-areas-of-a-form-visual-basic"></a><span data-ttu-id="e5091-102">Porady: drukowanie obszarów klienckich i nieklienckich formularza (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e5091-102">How to: Print Client and Non-Client Areas of a Form (Visual Basic)</span></span>
<span data-ttu-id="e5091-103"><xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> Składnika pozwala na szybkie wydrukowanie obrazu formularza, dokładnie tak, jak wygląda na to, na ekranie bez użycia <xref:System.Drawing.Printing.PrintDocument> składnika.</span><span class="sxs-lookup"><span data-stu-id="e5091-103">The <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> component enables you to quickly print an image of a form exactly as it appears on screen without using a <xref:System.Drawing.Printing.PrintDocument> component.</span></span> <span data-ttu-id="e5091-104">Poniższa procedura przedstawia sposób Drukowanie formularza, w tym zarówno obszaru klienckiego i obszaru nieklienckiego.</span><span class="sxs-lookup"><span data-stu-id="e5091-104">The following procedure shows how to print a form, including both the client area and the non-client area.</span></span> <span data-ttu-id="e5091-105">Obejmuje obszaru nieklienckiego paska tytułu, obramowania i przewijania pasków.</span><span class="sxs-lookup"><span data-stu-id="e5091-105">The non-client area includes the title bar, borders, and scroll bars.</span></span>  
  
 <span data-ttu-id="e5091-106">Formantów PowerPack nie są uwzględnione w programie Visual Studio, ale można pobrać je z [Centrum pobierania](http://www.microsoft.com/en-us/download/details.aspx?id=25169).</span><span class="sxs-lookup"><span data-stu-id="e5091-106">The PowerPack controls are no longer included in Visual Studio, but you can download them from the [Download Center](http://www.microsoft.com/en-us/download/details.aspx?id=25169).</span></span>  
  
### <a name="to-print-both-the-client-and-the-non-client-areas-of-a-form"></a><span data-ttu-id="e5091-107">Aby wydrukować zarówno klient, jak i obszarów klienckich formularza</span><span class="sxs-lookup"><span data-stu-id="e5091-107">To print both the client and the non-client areas of a form</span></span>  
  
1.  <span data-ttu-id="e5091-108">W **przybornika**, kliknij przycisk **Visual Basic PowerPacks** karcie, a następnie przeciągnij <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> składnika na formularzu.</span><span class="sxs-lookup"><span data-stu-id="e5091-108">In the **Toolbox**, click the **Visual Basic PowerPacks** tab and then drag the <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> component onto the form.</span></span>  
  
     <span data-ttu-id="e5091-109"><xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> Składnika jest dodawany do składnika na pasku zadań.</span><span class="sxs-lookup"><span data-stu-id="e5091-109">The <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> component is added to the component tray.</span></span>  
  
2.  <span data-ttu-id="e5091-110">W **właściwości** ustaw <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.PrintAction%2A> właściwości <xref:System.Drawing.Printing.PrintAction.PrintToPrinter>.</span><span class="sxs-lookup"><span data-stu-id="e5091-110">In the **Properties** window, set the <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.PrintAction%2A> property to <xref:System.Drawing.Printing.PrintAction.PrintToPrinter>.</span></span>  
  
3.  <span data-ttu-id="e5091-111">Dodaj następujący kod do obsługi zdarzeń odpowiednie (na przykład w `Click` programu obsługi zdarzeń dla drukowania `Button`).</span><span class="sxs-lookup"><span data-stu-id="e5091-111">Add the following code in the appropriate event handler (for example, in the `Click` event handler for a Print `Button`).</span></span>  
  
    ```  
    PrintForm1.Print(Me, PowerPacks.Printing.PrintForm.PrintOption.FullWindow)  
    ```  
  
    > [!NOTE]
    >  <span data-ttu-id="e5091-112">W niektórych systemach operacyjnych, tekst lub grafiki narysowanymi przez <xref:System.Drawing.Graphics> metody nie mogą drukować poprawnie.</span><span class="sxs-lookup"><span data-stu-id="e5091-112">On some operating systems, text or graphics drawn by <xref:System.Drawing.Graphics> methods may not print correctly.</span></span> <span data-ttu-id="e5091-113">In this case, użyj metody drukowania zgodne: `PrintForm1.Print(Me, PowerPacks.Printing.PrintForm.PrintOption.CompatibleModeFullWindow`).</span><span class="sxs-lookup"><span data-stu-id="e5091-113">In this case, use the compatible printing method: `PrintForm1.Print(Me, PowerPacks.Printing.PrintForm.PrintOption.CompatibleModeFullWindow`).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e5091-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e5091-114">See Also</span></span>  
 <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.PrintAction%2A>  
 <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.Print%2A>  
 [<span data-ttu-id="e5091-115">Składnik PrintForm</span><span class="sxs-lookup"><span data-stu-id="e5091-115">PrintForm Component</span></span>](../../../visual-basic/developing-apps/printing/printform-component.md)  
 [<span data-ttu-id="e5091-116">Instrukcje: drukowanie formularza przewijanego</span><span class="sxs-lookup"><span data-stu-id="e5091-116">How to: Print a Scrollable Form</span></span>](../../../visual-basic/developing-apps/printing/how-to-print-a-scrollable-form.md)
