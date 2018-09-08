---
title: 'Porady: drukowanie formularza przewijanego (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- entire form [Visual Basic], printing
- scrollable form [Visual Basic], printing
ms.assetid: 1196e1cf-b77f-4928-a3e4-85b51ba3787d
ms.openlocfilehash: 4a509b7c48f2bff705bc95e58fb88252cb8ca4b9
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/08/2018
ms.locfileid: "44182040"
---
# <a name="how-to-print-a-scrollable-form-visual-basic"></a><span data-ttu-id="353dd-102">Porady: drukowanie formularza przewijanego (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="353dd-102">How to: Print a Scrollable Form (Visual Basic)</span></span>
<span data-ttu-id="353dd-103"><xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> Składnika pozwala na szybkie drukowanie obraz formularza bez użycia <xref:System.Drawing.Printing.PrintDocument> składnika.</span><span class="sxs-lookup"><span data-stu-id="353dd-103">The <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> component enables you to quickly print an image of a form without using a <xref:System.Drawing.Printing.PrintDocument> component.</span></span> <span data-ttu-id="353dd-104">Domyślnie wydrukowaniu tylko aktualnie widoczne części formularza; Jeśli użytkownik ma rozmiar formularza, w czasie wykonywania, obraz, który nie może drukować, zgodnie z oczekiwaniami.</span><span class="sxs-lookup"><span data-stu-id="353dd-104">By default, only the currently visible part of the form is printed; if a user has resized the form at run time, the image may not print as intended.</span></span> <span data-ttu-id="353dd-105">Poniższa procedura pokazuje, jak drukowanie obszarów klienckich pełne formularza przewijanego nawet wtedy, gdy formularz został zmieniony.</span><span class="sxs-lookup"><span data-stu-id="353dd-105">The following procedure shows how to print the complete client area of a scrollable form, even if the form has been resized.</span></span>  
  
 <span data-ttu-id="353dd-106">Kontrolki pakietu PowerPack nie są już dostępne w programie Visual Studio, ale można je pobrać w [Centrum pobierania](https://www.microsoft.com/en-us/download/details.aspx?id=25169).</span><span class="sxs-lookup"><span data-stu-id="353dd-106">The PowerPack controls are no longer included in Visual Studio, but you can download them from the [Download Center](https://www.microsoft.com/en-us/download/details.aspx?id=25169).</span></span>  
  
### <a name="to-print-the-complete-client-area-of-a-scrollable-form"></a><span data-ttu-id="353dd-107">Aby wydrukować obszaru klienckiego pełną formularza przewijanego</span><span class="sxs-lookup"><span data-stu-id="353dd-107">To print the complete client area of a scrollable form</span></span>  
  
1.  <span data-ttu-id="353dd-108">W **Przyborniku** kliknij kartę **Visual Basic PowerPacks**, a następnie przeciągnij składnik <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> na formularz. </span><span class="sxs-lookup"><span data-stu-id="353dd-108">In the **Toolbox**, click the **Visual Basic PowerPacks** tab and then drag the <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> component onto the form.</span></span>  
  
     <span data-ttu-id="353dd-109"><xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> Składnik zostanie dodany do zasobnika składnika.</span><span class="sxs-lookup"><span data-stu-id="353dd-109">The <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> component will be added to the component tray.</span></span>  
  
2.  <span data-ttu-id="353dd-110">W oknie **Właściwości** ustaw właściwość <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.PrintAction%2A> na <xref:System.Drawing.Printing.PrintAction.PrintToPrinter>. </span><span class="sxs-lookup"><span data-stu-id="353dd-110">In the **Properties** window, set the <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.PrintAction%2A> property to <xref:System.Drawing.Printing.PrintAction.PrintToPrinter>.</span></span>  
  
3.  <span data-ttu-id="353dd-111">Dodaj następujący kod do odpowiedniej procedury obsługi zdarzeń (na przykład obsługa zdarzenia `Click` dla przycisku (`Button`) **Drukuj**). </span><span class="sxs-lookup"><span data-stu-id="353dd-111">Add the following code in the appropriate event handler (for example, in the `Click` event handler for a **Print**`Button`).</span></span>  
  
    ```  
    PrintForm1.Print(Me, PowerPacks.Printing.PrintForm.PrintOption.Scrollable)  
    ```  
  
    > [!NOTE]
    >  <span data-ttu-id="353dd-112">W niektórych systemach operacyjnych, tekst lub grafiki narysowanymi przez <xref:System.Drawing.Graphics> metody nie może poprawnie wydrukować.</span><span class="sxs-lookup"><span data-stu-id="353dd-112">On some operating systems, text or graphics drawn by <xref:System.Drawing.Graphics> methods may not print correctly.</span></span> <span data-ttu-id="353dd-113">W tym przypadku nie można wydrukować z `Scrollable` parametru.</span><span class="sxs-lookup"><span data-stu-id="353dd-113">In this case, you will not be able to print with the `Scrollable` parameter.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="353dd-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="353dd-114">See Also</span></span>  
 <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.PrintAction%2A>  
 <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.Print%2A>  
 [<span data-ttu-id="353dd-115">Składnik PrintForm</span><span class="sxs-lookup"><span data-stu-id="353dd-115">PrintForm Component</span></span>](../../../visual-basic/developing-apps/printing/printform-component.md)  
 [<span data-ttu-id="353dd-116">Instrukcje: drukowanie obszarów klienckich formularza</span><span class="sxs-lookup"><span data-stu-id="353dd-116">How to: Print the Client Area of a Form</span></span>](../../../visual-basic/developing-apps/printing/how-to-print-the-client-area-of-a-form.md)  
 [<span data-ttu-id="353dd-117">Instrukcje: drukowanie obszarów klienckich i nieklienckich formularza</span><span class="sxs-lookup"><span data-stu-id="353dd-117">How to: Print Client and Non-Client Areas of a Form</span></span>](../../../visual-basic/developing-apps/printing/how-to-print-client-and-non-client-areas-of-a-form.md)
