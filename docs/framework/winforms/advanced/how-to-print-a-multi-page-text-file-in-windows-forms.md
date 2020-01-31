---
title: 'Instrukcje: Drukowanie wielostronicowego pliku tekstowego'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- printing [Windows Forms], printing multiple pages
- text [Windows Forms], printing Windows Forms
- Windows Forms, printing text
- printing [Windows Forms], text
ms.assetid: 362427f8-03d4-4826-b49f-60ab066ad322
ms.openlocfilehash: 51e30706bb7693988d611701d013792c82dccd0b
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76740661"
---
# <a name="how-to-print-a-multi-page-text-file-in-windows-forms"></a><span data-ttu-id="30b70-102">Porady: wyświetlanie podglądu wydruku w aplikacjach formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="30b70-102">How to: Print a Multi-Page Text File in Windows Forms</span></span>
<span data-ttu-id="30b70-103">Drukowanie tekstu jest bardzo popularne dla aplikacji opartych na systemie Windows.</span><span class="sxs-lookup"><span data-stu-id="30b70-103">It is very common for Windows-based applications to print text.</span></span> <span data-ttu-id="30b70-104">Klasa <xref:System.Drawing.Graphics> zapewnia metody rysowania obiektów (grafiki lub tekstu) na urządzeniu, takie jak ekran lub drukarka.</span><span class="sxs-lookup"><span data-stu-id="30b70-104">The <xref:System.Drawing.Graphics> class provides methods for drawing objects (graphics or text) to a device, such as a screen or printer.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="30b70-105"><xref:System.Windows.Forms.TextRenderer.DrawText%2A> metod <xref:System.Windows.Forms.TextRenderer> nie są obsługiwane na potrzeby drukowania.</span><span class="sxs-lookup"><span data-stu-id="30b70-105">The <xref:System.Windows.Forms.TextRenderer.DrawText%2A> methods of <xref:System.Windows.Forms.TextRenderer> are not supported for printing.</span></span> <span data-ttu-id="30b70-106">Należy zawsze używać <xref:System.Drawing.Graphics.DrawString%2A> metod <xref:System.Drawing.Graphics>, jak pokazano w poniższym przykładzie kodu, aby narysować tekst do celów drukowania.</span><span class="sxs-lookup"><span data-stu-id="30b70-106">You should always use the <xref:System.Drawing.Graphics.DrawString%2A> methods of <xref:System.Drawing.Graphics>, as shown in the following code example, to draw text for printing purposes.</span></span>  
  
### <a name="to-print-text"></a><span data-ttu-id="30b70-107">Aby wydrukować tekst</span><span class="sxs-lookup"><span data-stu-id="30b70-107">To print text</span></span>  
  
1. <span data-ttu-id="30b70-108">Dodaj składnik <xref:System.Drawing.Printing.PrintDocument> i ciąg do formularza.</span><span class="sxs-lookup"><span data-stu-id="30b70-108">Add a <xref:System.Drawing.Printing.PrintDocument> component and a string to your form.</span></span>  
  
     [!code-csharp[System.Drawing.Printing.PrintExamples#8](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Printing.PrintExamples/CS/Form1.cs#8)]
     [!code-vb[System.Drawing.Printing.PrintExamples#8](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Printing.PrintExamples/VB/Form1.vb#8)]  
  
2. <span data-ttu-id="30b70-109">W przypadku drukowania dokumentu ustaw właściwość <xref:System.Drawing.Printing.PrintDocument.DocumentName%2A> na dokument, który chcesz wydrukować, a następnie otwórz i Odczytaj zawartość dokumentów do ciągu, który został dodany wcześniej.</span><span class="sxs-lookup"><span data-stu-id="30b70-109">If printing a document, set the <xref:System.Drawing.Printing.PrintDocument.DocumentName%2A> property to the document you wish to print, and open and read the documents contents to the string you added previously.</span></span>  
  
     [!code-csharp[System.Drawing.Printing.PrintExamples#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Printing.PrintExamples/CS/Form1.cs#1)]
     [!code-vb[System.Drawing.Printing.PrintExamples#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Printing.PrintExamples/VB/Form1.vb#1)]  
  
3. <span data-ttu-id="30b70-110">W obsłudze zdarzeń <xref:System.Drawing.Printing.PrintDocument.PrintPage> Użyj właściwości <xref:System.Drawing.Printing.PrintPageEventArgs.Graphics%2A> klasy <xref:System.Drawing.Printing.PrintPageEventArgs> i zawartości dokumentu, aby obliczyć długość i wiersze wierszy na stronie.</span><span class="sxs-lookup"><span data-stu-id="30b70-110">In the <xref:System.Drawing.Printing.PrintDocument.PrintPage> event handler, use the <xref:System.Drawing.Printing.PrintPageEventArgs.Graphics%2A> property of the <xref:System.Drawing.Printing.PrintPageEventArgs> class and the document contents to calculate line length and lines per page.</span></span> <span data-ttu-id="30b70-111">Po narysowaniu każdej strony Sprawdź, czy jest ona ostatnią stroną i odpowiednio ustaw właściwość <xref:System.Drawing.Printing.PrintPageEventArgs.HasMorePages%2A> <xref:System.Drawing.Printing.PrintPageEventArgs>.</span><span class="sxs-lookup"><span data-stu-id="30b70-111">After each page is drawn, check to see if it is the last page, and set the <xref:System.Drawing.Printing.PrintPageEventArgs.HasMorePages%2A> property of the <xref:System.Drawing.Printing.PrintPageEventArgs> accordingly.</span></span> <span data-ttu-id="30b70-112">Zdarzenie <xref:System.Drawing.Printing.PrintDocument.PrintPage> jest zgłaszane do momentu `false`<xref:System.Drawing.Printing.PrintPageEventArgs.HasMorePages%2A>.</span><span class="sxs-lookup"><span data-stu-id="30b70-112">The <xref:System.Drawing.Printing.PrintDocument.PrintPage> event is raised until <xref:System.Drawing.Printing.PrintPageEventArgs.HasMorePages%2A> is `false`.</span></span> <span data-ttu-id="30b70-113">Upewnij się również, że zdarzenie <xref:System.Drawing.Printing.PrintDocument.PrintPage> jest skojarzone z jego metodą obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="30b70-113">Also, make sure the <xref:System.Drawing.Printing.PrintDocument.PrintPage> event is associated with its event-handling method.</span></span>  
  
     <span data-ttu-id="30b70-114">W poniższym przykładzie kodu program obsługi zdarzeń służy do drukowania zawartości pliku "testPage. txt" w tej samej czcionce jak w formularzu.</span><span class="sxs-lookup"><span data-stu-id="30b70-114">In the following code example, the event handler is used to print the contents of the "testPage.txt" file in the same font as is used on the form.</span></span>  
  
     [!code-csharp[System.Drawing.Printing.PrintExamples#2](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Printing.PrintExamples/CS/Form1.cs#2)]
     [!code-vb[System.Drawing.Printing.PrintExamples#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Printing.PrintExamples/VB/Form1.vb#2)]  
  
4. <span data-ttu-id="30b70-115">Wywołaj metodę <xref:System.Drawing.Printing.PrintDocument.Print%2A>, aby zgłosić zdarzenie <xref:System.Drawing.Printing.PrintDocument.PrintPage>.</span><span class="sxs-lookup"><span data-stu-id="30b70-115">Call the <xref:System.Drawing.Printing.PrintDocument.Print%2A> method to raise the <xref:System.Drawing.Printing.PrintDocument.PrintPage> event.</span></span>  
  
     [!code-csharp[System.Drawing.Printing.PrintExamples#5](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Printing.PrintExamples/CS/Form1.cs#5)]
     [!code-vb[System.Drawing.Printing.PrintExamples#5](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Printing.PrintExamples/VB/Form1.vb#5)]  
  
## <a name="example"></a><span data-ttu-id="30b70-116">Przykład</span><span class="sxs-lookup"><span data-stu-id="30b70-116">Example</span></span>  
 [!code-csharp[System.Drawing.Printing.PrintExamples#0](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Printing.PrintExamples/CS/Form1.cs#0)]
 [!code-vb[System.Drawing.Printing.PrintExamples#0](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Printing.PrintExamples/VB/Form1.vb#0)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="30b70-117">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="30b70-117">Compiling the Code</span></span>  
 <span data-ttu-id="30b70-118">Ten przykład wymaga:</span><span class="sxs-lookup"><span data-stu-id="30b70-118">This example requires:</span></span>  
  
- <span data-ttu-id="30b70-119">Plik tekstowy o nazwie testPage. txt zawierający tekst do wydrukowania znajdujący się w katalogu głównym dysku C:\\.</span><span class="sxs-lookup"><span data-stu-id="30b70-119">A text file named testPage.txt containing the text to print, located in the root of drive C:\\.</span></span> <span data-ttu-id="30b70-120">Edytuj kod, aby wydrukować inny plik.</span><span class="sxs-lookup"><span data-stu-id="30b70-120">Edit the code to print a different file.</span></span>  
  
- <span data-ttu-id="30b70-121">Odwołania do zestawów system, system. Windows. Forms, system. Drawing.</span><span class="sxs-lookup"><span data-stu-id="30b70-121">References to the System, System.Windows.Forms, System.Drawing assemblies.</span></span>  
  
- <span data-ttu-id="30b70-122">Aby uzyskać informacje na temat tworzenia tego przykładu z wiersza polecenia dla Visual Basic C#lub wizualizacji, zobacz [Kompilowanie z wiersza polecenia](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) lub [Kompilowanie wiersza polecenia za pomocą pliku CSC. exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="30b70-122">For information about building this example from the command line for Visual Basic or Visual C#, see [Building from the Command Line](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="30b70-123">Możesz również utworzyć ten przykład w programie Visual Studio, wklejając kod do nowego projektu.</span><span class="sxs-lookup"><span data-stu-id="30b70-123">You can also build this example in Visual Studio by pasting the code into a new project.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="30b70-124">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="30b70-124">See also</span></span>

- <xref:System.Drawing.Graphics>
- <xref:System.Drawing.Brush>
- [<span data-ttu-id="30b70-125">Obsługa drukowania w formularzach Windows Forms</span><span class="sxs-lookup"><span data-stu-id="30b70-125">Windows Forms Print Support</span></span>](windows-forms-print-support.md)
