---
title: 'Porady: drukowanie obszarów klienckich formularza (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- client area [Visual Basic], printing
ms.assetid: c06c9c0e-bc07-48cd-9596-e29a2ff96236
ms.openlocfilehash: b2f13d1ec151a5fd1967b522a601e0e19de04cbb
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/16/2018
ms.locfileid: "45689226"
---
# <a name="how-to-print-the-client-area-of-a-form-visual-basic"></a><span data-ttu-id="0d5bf-102">Porady: drukowanie obszarów klienckich formularza (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0d5bf-102">How to: Print the Client Area of a Form (Visual Basic)</span></span>
<span data-ttu-id="0d5bf-103"><xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> Składnika pozwala na szybkie drukowanie obraz formularza bez użycia <xref:System.Drawing.Printing.PrintDocument> składnika.</span><span class="sxs-lookup"><span data-stu-id="0d5bf-103">The <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> component enables you to quickly print an image of a form without using a <xref:System.Drawing.Printing.PrintDocument> component.</span></span> <span data-ttu-id="0d5bf-104">Poniższa procedura pokazuje jak drukować po prostu obszaru klienta formularza, bez paska tytułu, obramowania i paski przewijania.</span><span class="sxs-lookup"><span data-stu-id="0d5bf-104">The following procedure shows how to print just the client area of a form, without the title bar, borders, and scroll bars.</span></span>  
  
 <span data-ttu-id="0d5bf-105">Kontrolki pakietu PowerPack nie są już dostępne w programie Visual Studio, ale można je pobrać w [Centrum pobierania](https://www.microsoft.com/en-us/download/details.aspx?id=25169).</span><span class="sxs-lookup"><span data-stu-id="0d5bf-105">The PowerPack controls are no longer included in Visual Studio, but you can download them from the [Download Center](https://www.microsoft.com/en-us/download/details.aspx?id=25169).</span></span>  
  
### <a name="to-print-the-client-area-of-a-form"></a><span data-ttu-id="0d5bf-106">Aby drukowanie obszarów klienckich formularza</span><span class="sxs-lookup"><span data-stu-id="0d5bf-106">To print the client area of a form</span></span>  
  
1.  <span data-ttu-id="0d5bf-107">W **Przyborniku** kliknij kartę **Visual Basic PowerPacks**, a następnie przeciągnij składnik <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> na formularz. </span><span class="sxs-lookup"><span data-stu-id="0d5bf-107">In the **Toolbox**, click the **Visual Basic PowerPacks** tab and then drag the <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> component onto the form.</span></span>  
  
     <span data-ttu-id="0d5bf-108">Składnik <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> jest dodawany do zasobnika składników. </span><span class="sxs-lookup"><span data-stu-id="0d5bf-108">The <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> component is added to the component tray.</span></span>  
  
2.  <span data-ttu-id="0d5bf-109">W oknie **Właściwości** ustaw właściwość <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.PrintAction%2A> na <xref:System.Drawing.Printing.PrintAction.PrintToPrinter>. </span><span class="sxs-lookup"><span data-stu-id="0d5bf-109">In the **Properties** window, set the <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.PrintAction%2A> property to <xref:System.Drawing.Printing.PrintAction.PrintToPrinter>.</span></span>  
  
3.  <span data-ttu-id="0d5bf-110">Dodaj następujący kod do odpowiedniej procedury obsługi zdarzeń (na przykład obsługa zdarzenia `Click` dla przycisku (`Button`) **Drukuj**). </span><span class="sxs-lookup"><span data-stu-id="0d5bf-110">Add the following code in the appropriate event handler (for example, in the `Click` event handler for a **Print**`Button`).</span></span>  
  
    ```  
    PrintForm1.Print(Me, PowerPacks.Printing.PrintForm.PrintOption.ClientAreaOnly)  
    ```  
  
    > [!NOTE]
    >  <span data-ttu-id="0d5bf-111">W niektórych systemach operacyjnych, tekst lub grafiki narysowanymi przez <xref:System.Drawing.Graphics> metody nie może poprawnie wydrukować.</span><span class="sxs-lookup"><span data-stu-id="0d5bf-111">On some operating systems, text or graphics drawn by <xref:System.Drawing.Graphics> methods may not print correctly.</span></span> <span data-ttu-id="0d5bf-112">W takim przypadku należy użyć kompatybilna metoda drukowania: `PrintForm1.Print(Me, PowerPacks.Printing.PrintForm.PrintOption CompatibleModeClientAreaOnly).`</span><span class="sxs-lookup"><span data-stu-id="0d5bf-112">In this case, use the compatible printing method: `PrintForm1.Print(Me, PowerPacks.Printing.PrintForm.PrintOption CompatibleModeClientAreaOnly).`</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0d5bf-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="0d5bf-113">See Also</span></span>  
 <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.PrintAction%2A>  
 <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.Print%2A>  
 [<span data-ttu-id="0d5bf-114">Składnik PrintForm</span><span class="sxs-lookup"><span data-stu-id="0d5bf-114">PrintForm Component</span></span>](../../../visual-basic/developing-apps/printing/printform-component.md)  
 [<span data-ttu-id="0d5bf-115">Instrukcje: drukowanie obszarów klienckich i nieklienckich formularza</span><span class="sxs-lookup"><span data-stu-id="0d5bf-115">How to: Print Client and Non-Client Areas of a Form</span></span>](../../../visual-basic/developing-apps/printing/how-to-print-client-and-non-client-areas-of-a-form.md)  
 [<span data-ttu-id="0d5bf-116">Instrukcje: drukowanie formularza przewijanego</span><span class="sxs-lookup"><span data-stu-id="0d5bf-116">How to: Print a Scrollable Form</span></span>](../../../visual-basic/developing-apps/printing/how-to-print-a-scrollable-form.md)
