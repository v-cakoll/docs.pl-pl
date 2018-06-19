---
title: 'Porady: drukowanie formularza za pomocą składnika PrintForm (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- Form [Visual Basic], printing
ms.assetid: df963bf6-3ee1-49f4-8b2e-1d95d1beb0be
ms.openlocfilehash: 5f8e620fce2b85d3f3cdb66bf80967f8eb281361
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33590016"
---
# <a name="how-to-print-a-form-by-using-the-printform-component-visual-basic"></a><span data-ttu-id="326f5-102">Porady: drukowanie formularza za pomocą składnika PrintForm (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="326f5-102">How to: Print a Form by Using the PrintForm Component (Visual Basic)</span></span>
<span data-ttu-id="326f5-103"><xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> Składnika pozwala na szybkie wydrukowanie obrazu formularza, dokładnie tak, jak wygląda na to, na ekranie bez użycia <xref:System.Drawing.Printing.PrintDocument> składnika.</span><span class="sxs-lookup"><span data-stu-id="326f5-103">The <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> component enables you to quickly print an image of a form exactly as it appears on screen without using a <xref:System.Drawing.Printing.PrintDocument> component.</span></span> <span data-ttu-id="326f5-104">Poniższe procedury pokazują, jak drukowanie formularza na drukarce, okno podglądu wydruku i plik Encapsulated PostScript.</span><span class="sxs-lookup"><span data-stu-id="326f5-104">The following procedures show how to print a form to a printer, to a print preview window, and to an Encapsulated PostScript file.</span></span>  
  
 <span data-ttu-id="326f5-105">Formantów PowerPack nie są uwzględnione w programie Visual Studio, ale można pobrać je z [Centrum pobierania](http://www.microsoft.com/en-us/download/details.aspx?id=25169).</span><span class="sxs-lookup"><span data-stu-id="326f5-105">The PowerPack controls are no longer included in Visual Studio, but you can download them from the [Download Center](http://www.microsoft.com/en-us/download/details.aspx?id=25169).</span></span>  
  
### <a name="to-print-a-form-to-the-default-printer"></a><span data-ttu-id="326f5-106">Drukowanie formularza używają domyślnej drukarki</span><span class="sxs-lookup"><span data-stu-id="326f5-106">To print a form to the default printer</span></span>  
  
1.  <span data-ttu-id="326f5-107">W **przybornika**, kliknij przycisk **Visual Basic PowerPacks** karcie, a następnie przeciągnij <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> składnika na formularzu.</span><span class="sxs-lookup"><span data-stu-id="326f5-107">In the **Toolbox**, click the **Visual Basic PowerPacks** tab and then drag the <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> component onto the form.</span></span>  
  
     <span data-ttu-id="326f5-108"><xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> Składnika jest dodawany do składnika na pasku zadań.</span><span class="sxs-lookup"><span data-stu-id="326f5-108">The <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> component is added to the component tray.</span></span>  
  
2.  <span data-ttu-id="326f5-109">W **właściwości** ustaw <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.PrintAction%2A> właściwości <xref:System.Drawing.Printing.PrintAction.PrintToPrinter>.</span><span class="sxs-lookup"><span data-stu-id="326f5-109">In the **Properties** window, set the <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.PrintAction%2A> property to <xref:System.Drawing.Printing.PrintAction.PrintToPrinter>.</span></span>  
  
3.  <span data-ttu-id="326f5-110">Dodaj następujący kod do obsługi zdarzeń odpowiednie (na przykład w `Click` programu obsługi zdarzeń dla **drukowania**`Button`).</span><span class="sxs-lookup"><span data-stu-id="326f5-110">Add the following code in the appropriate event handler (for example, in the `Click` event handler for a **Print**`Button`).</span></span>  
  
    ```  
    PrintForm1.Print()  
    ```  
  
### <a name="to-display-a-form-in-a-print-preview-window"></a><span data-ttu-id="326f5-111">Do wyświetlania formularza w oknie Podgląd wydruku</span><span class="sxs-lookup"><span data-stu-id="326f5-111">To display a form in a print preview window</span></span>  
  
1.  <span data-ttu-id="326f5-112">W **przybornika**, kliknij przycisk **Visual Basic PowerPacks** karcie, a następnie przeciągnij <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> składnika na formularzu.</span><span class="sxs-lookup"><span data-stu-id="326f5-112">In the **Toolbox**, click the **Visual Basic PowerPacks** tab and then drag the <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> component onto the form.</span></span>  
  
     <span data-ttu-id="326f5-113"><xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> Składnika jest dodawany do składnika na pasku zadań.</span><span class="sxs-lookup"><span data-stu-id="326f5-113">The <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> component is added to the component tray.</span></span>  
  
2.  <span data-ttu-id="326f5-114">W **właściwości** ustaw <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.PrintAction%2A> właściwości <xref:System.Drawing.Printing.PrintAction.PrintToPreview>.</span><span class="sxs-lookup"><span data-stu-id="326f5-114">In the **Properties** window, set the <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.PrintAction%2A> property to <xref:System.Drawing.Printing.PrintAction.PrintToPreview>.</span></span>  
  
3.  <span data-ttu-id="326f5-115">Dodaj następujący kod do obsługi zdarzeń odpowiednie (na przykład w `Click` programu obsługi zdarzeń dla **drukowania**`Button`).</span><span class="sxs-lookup"><span data-stu-id="326f5-115">Add the following code in the appropriate event handler (for example, in the `Click` event handler for a **Print**`Button`).</span></span>  
  
    ```  
    PrintForm1.Print()  
    ```  
  
### <a name="to-print-a-form-to-a-file"></a><span data-ttu-id="326f5-116">Drukowanie formularza do pliku</span><span class="sxs-lookup"><span data-stu-id="326f5-116">To print a form to a file</span></span>  
  
1.  <span data-ttu-id="326f5-117">W **przybornika**, kliknij przycisk **Visual Basic PowerPacks** karcie, a następnie przeciągnij <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> składnika na formularzu.</span><span class="sxs-lookup"><span data-stu-id="326f5-117">In the **Toolbox**, click the **Visual Basic PowerPacks** tab and then drag the <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> component onto the form.</span></span>  
  
     <span data-ttu-id="326f5-118"><xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> Składnika jest dodawany do składnika na pasku zadań.</span><span class="sxs-lookup"><span data-stu-id="326f5-118">The <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> component is added to the component tray.</span></span>  
  
2.  <span data-ttu-id="326f5-119">W **właściwości** ustaw <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.PrintAction%2A> właściwości <xref:System.Drawing.Printing.PrintAction.PrintToFile>.</span><span class="sxs-lookup"><span data-stu-id="326f5-119">In the **Properties** window, set the <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.PrintAction%2A> property to <xref:System.Drawing.Printing.PrintAction.PrintToFile>.</span></span>  
  
3.  <span data-ttu-id="326f5-120">Opcjonalnie wybierz <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.PrintFileName%2A> właściwości i wpisz pełną ścieżkę i nazwę pliku dla pliku docelowego.</span><span class="sxs-lookup"><span data-stu-id="326f5-120">Optionally, select the <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.PrintFileName%2A> property and type the full path and file name for the destination file.</span></span>  
  
     <span data-ttu-id="326f5-121">Jeśli pominiesz ten krok, użytkownik będzie monitowany o nazwę pliku w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="326f5-121">If you skip this step, the user will be prompted for a file name at run time.</span></span>  
  
4.  <span data-ttu-id="326f5-122">Dodaj następujący kod do obsługi zdarzeń odpowiednie (na przykład w `Click` programu obsługi zdarzeń dla **drukowania**`Button`).</span><span class="sxs-lookup"><span data-stu-id="326f5-122">Add the following code in the appropriate event handler (for example, in the `Click` event handler for a **Print**`Button`).</span></span>  
  
    ```  
    PrintForm1.Print()  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="326f5-123">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="326f5-123">See Also</span></span>  
 <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.PrintAction%2A>  
 <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.PrintFileName%2A>  
 [<span data-ttu-id="326f5-124">Instrukcje: drukowanie obszarów klienckich formularza</span><span class="sxs-lookup"><span data-stu-id="326f5-124">How to: Print the Client Area of a Form</span></span>](../../../visual-basic/developing-apps/printing/how-to-print-the-client-area-of-a-form.md)  
 [<span data-ttu-id="326f5-125">Instrukcje: drukowanie obszarów klienckich i nieklienckich formularza</span><span class="sxs-lookup"><span data-stu-id="326f5-125">How to: Print Client and Non-Client Areas of a Form</span></span>](../../../visual-basic/developing-apps/printing/how-to-print-client-and-non-client-areas-of-a-form.md)  
 [<span data-ttu-id="326f5-126">Instrukcje: drukowanie formularza przewijanego</span><span class="sxs-lookup"><span data-stu-id="326f5-126">How to: Print a Scrollable Form</span></span>](../../../visual-basic/developing-apps/printing/how-to-print-a-scrollable-form.md)  
 [<span data-ttu-id="326f5-127">Składnik PrintForm</span><span class="sxs-lookup"><span data-stu-id="326f5-127">PrintForm Component</span></span>](../../../visual-basic/developing-apps/printing/printform-component.md)
