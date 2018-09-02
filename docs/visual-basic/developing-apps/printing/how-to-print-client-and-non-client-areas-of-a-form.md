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
ms.openlocfilehash: 5109993146a8d53d5cbeebcc52c018a6f0f57ed5
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/01/2018
ms.locfileid: "43408442"
---
# <a name="how-to-print-client-and-non-client-areas-of-a-form-visual-basic"></a><span data-ttu-id="e61a6-102">Porady: drukowanie obszarów klienckich i nieklienckich formularza (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e61a6-102">How to: Print Client and Non-Client Areas of a Form (Visual Basic)</span></span>
<span data-ttu-id="e61a6-103"><xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> Składnika pozwala na szybkie drukowanie obraz formularza, dokładnie tak, jak wygląda na to, na ekranie bez użycia <xref:System.Drawing.Printing.PrintDocument> składnika.</span><span class="sxs-lookup"><span data-stu-id="e61a6-103">The <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> component enables you to quickly print an image of a form exactly as it appears on screen without using a <xref:System.Drawing.Printing.PrintDocument> component.</span></span> <span data-ttu-id="e61a6-104">Poniższa procedura pokazuje, jak drukowanie formularza, w tym obszar klienta i obszaru nieklienckiego.</span><span class="sxs-lookup"><span data-stu-id="e61a6-104">The following procedure shows how to print a form, including both the client area and the non-client area.</span></span> <span data-ttu-id="e61a6-105">Obszaru nieklienckiego zawiera pasek tytułu, obramowania i przewijania pasków.</span><span class="sxs-lookup"><span data-stu-id="e61a6-105">The non-client area includes the title bar, borders, and scroll bars.</span></span>  
  
 <span data-ttu-id="e61a6-106">Formantów PowerPack znajdują się już w programie Visual Studio, ale można je pobrać [Centrum pobierania](https://www.microsoft.com/en-us/download/details.aspx?id=25169).</span><span class="sxs-lookup"><span data-stu-id="e61a6-106">The PowerPack controls are no longer included in Visual Studio, but you can download them from the [Download Center](https://www.microsoft.com/en-us/download/details.aspx?id=25169).</span></span>  
  
### <a name="to-print-both-the-client-and-the-non-client-areas-of-a-form"></a><span data-ttu-id="e61a6-107">Aby wydrukować zarówno klient, jak i obszarów klienckich formularza</span><span class="sxs-lookup"><span data-stu-id="e61a6-107">To print both the client and the non-client areas of a form</span></span>  
  
1.  <span data-ttu-id="e61a6-108">W **przybornika**, kliknij przycisk **Visual Basic PowerPacks** kartę, a następnie przeciągnij <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> składnika do formularza.</span><span class="sxs-lookup"><span data-stu-id="e61a6-108">In the **Toolbox**, click the **Visual Basic PowerPacks** tab and then drag the <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> component onto the form.</span></span>  
  
     <span data-ttu-id="e61a6-109"><xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> Składnik zostanie dodany do zasobnika składnika.</span><span class="sxs-lookup"><span data-stu-id="e61a6-109">The <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> component is added to the component tray.</span></span>  
  
2.  <span data-ttu-id="e61a6-110">W **właściwości** oknie <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.PrintAction%2A> właściwość <xref:System.Drawing.Printing.PrintAction.PrintToPrinter>.</span><span class="sxs-lookup"><span data-stu-id="e61a6-110">In the **Properties** window, set the <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.PrintAction%2A> property to <xref:System.Drawing.Printing.PrintAction.PrintToPrinter>.</span></span>  
  
3.  <span data-ttu-id="e61a6-111">Dodaj następujący kod w obsłudze odpowiedniego zdarzenia (na przykład w `Click` program obsługi zdarzeń dla drukowania `Button`).</span><span class="sxs-lookup"><span data-stu-id="e61a6-111">Add the following code in the appropriate event handler (for example, in the `Click` event handler for a Print `Button`).</span></span>  
  
    ```  
    PrintForm1.Print(Me, PowerPacks.Printing.PrintForm.PrintOption.FullWindow)  
    ```  
  
    > [!NOTE]
    >  <span data-ttu-id="e61a6-112">W niektórych systemach operacyjnych, tekst lub grafiki narysowanymi przez <xref:System.Drawing.Graphics> metody nie może poprawnie wydrukować.</span><span class="sxs-lookup"><span data-stu-id="e61a6-112">On some operating systems, text or graphics drawn by <xref:System.Drawing.Graphics> methods may not print correctly.</span></span> <span data-ttu-id="e61a6-113">In this case, użyj kompatybilna metoda drukowania: `PrintForm1.Print(Me, PowerPacks.Printing.PrintForm.PrintOption.CompatibleModeFullWindow`).</span><span class="sxs-lookup"><span data-stu-id="e61a6-113">In this case, use the compatible printing method: `PrintForm1.Print(Me, PowerPacks.Printing.PrintForm.PrintOption.CompatibleModeFullWindow`).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e61a6-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e61a6-114">See Also</span></span>  
 <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.PrintAction%2A>  
 <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.Print%2A>  
 [<span data-ttu-id="e61a6-115">Składnik PrintForm</span><span class="sxs-lookup"><span data-stu-id="e61a6-115">PrintForm Component</span></span>](../../../visual-basic/developing-apps/printing/printform-component.md)  
 [<span data-ttu-id="e61a6-116">Instrukcje: drukowanie formularza przewijanego</span><span class="sxs-lookup"><span data-stu-id="e61a6-116">How to: Print a Scrollable Form</span></span>](../../../visual-basic/developing-apps/printing/how-to-print-a-scrollable-form.md)
