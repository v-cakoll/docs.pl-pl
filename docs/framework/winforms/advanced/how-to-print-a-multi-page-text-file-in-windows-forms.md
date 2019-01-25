---
title: 'Instrukcje: Podglądu wydruku w formularzach Windows Forms'
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
ms.openlocfilehash: 149f0ca6df60931f8bb567ef5e4876c779825f1e
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54604378"
---
# <a name="how-to-print-a-multi-page-text-file-in-windows-forms"></a><span data-ttu-id="c232e-102">Instrukcje: Podglądu wydruku w formularzach Windows Forms</span><span class="sxs-lookup"><span data-stu-id="c232e-102">How to: Print a Multi-Page Text File in Windows Forms</span></span>
<span data-ttu-id="c232e-103">Jest to często stosowane w aplikacjach Windows do drukowania tekstu.</span><span class="sxs-lookup"><span data-stu-id="c232e-103">It is very common for Windows-based applications to print text.</span></span> <span data-ttu-id="c232e-104"><xref:System.Drawing.Graphics> Klasa dostarcza metody do rysowania obiektów (grafiki lub tekst) do urządzenia, takich jak ekranu lub drukarki.</span><span class="sxs-lookup"><span data-stu-id="c232e-104">The <xref:System.Drawing.Graphics> class provides methods for drawing objects (graphics or text) to a device, such as a screen or printer.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c232e-105"><xref:System.Windows.Forms.TextRenderer.DrawText%2A> Metody <xref:System.Windows.Forms.TextRenderer> nie są obsługiwane na potrzeby drukowania.</span><span class="sxs-lookup"><span data-stu-id="c232e-105">The <xref:System.Windows.Forms.TextRenderer.DrawText%2A> methods of <xref:System.Windows.Forms.TextRenderer> are not supported for printing.</span></span> <span data-ttu-id="c232e-106">Należy zawsze używać <xref:System.Drawing.Graphics.DrawString%2A> metody <xref:System.Drawing.Graphics>, jak pokazano w poniższym przykładzie kodu, aby rysować tekst na potrzeby drukowania.</span><span class="sxs-lookup"><span data-stu-id="c232e-106">You should always use the <xref:System.Drawing.Graphics.DrawString%2A> methods of <xref:System.Drawing.Graphics>, as shown in the following code example, to draw text for printing purposes.</span></span>  
  
### <a name="to-print-text"></a><span data-ttu-id="c232e-107">Aby wydrukować tekst</span><span class="sxs-lookup"><span data-stu-id="c232e-107">To print text</span></span>  
  
1.  <span data-ttu-id="c232e-108">Dodaj <xref:System.Drawing.Printing.PrintDocument> składnika i ciąg do formularza.</span><span class="sxs-lookup"><span data-stu-id="c232e-108">Add a <xref:System.Drawing.Printing.PrintDocument> component and a string to your form.</span></span>  
  
     [!code-csharp[System.Drawing.Printing.PrintExamples#8](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Printing.PrintExamples/CS/Form1.cs#8)]
     [!code-vb[System.Drawing.Printing.PrintExamples#8](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Printing.PrintExamples/VB/Form1.vb#8)]  
  
2.  <span data-ttu-id="c232e-109">Jeśli drukowanie dokumentu, ustaw <xref:System.Drawing.Printing.PrintDocument.DocumentName%2A> właściwości dokumentu chcesz wydrukować i otwierać i odczytywać zawartość dokumentów, aby ten ciąg zostanie dodane wcześniej.</span><span class="sxs-lookup"><span data-stu-id="c232e-109">If printing a document, set the <xref:System.Drawing.Printing.PrintDocument.DocumentName%2A> property to the document you wish to print, and open and read the documents contents to the string you added previously.</span></span>  
  
     [!code-csharp[System.Drawing.Printing.PrintExamples#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Printing.PrintExamples/CS/Form1.cs#1)]
     [!code-vb[System.Drawing.Printing.PrintExamples#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Printing.PrintExamples/VB/Form1.vb#1)]  
  
3.  <span data-ttu-id="c232e-110">W <xref:System.Drawing.Printing.PrintDocument.PrintPage> programu obsługi zdarzeń, użyj <xref:System.Drawing.Printing.PrintPageEventArgs.Graphics%2A> właściwość <xref:System.Drawing.Printing.PrintPageEventArgs> klasy i zawartość dokumentu, aby obliczyć długość i wierszy na stronie linii.</span><span class="sxs-lookup"><span data-stu-id="c232e-110">In the <xref:System.Drawing.Printing.PrintDocument.PrintPage> event handler, use the <xref:System.Drawing.Printing.PrintPageEventArgs.Graphics%2A> property of the <xref:System.Drawing.Printing.PrintPageEventArgs> class and the document contents to calculate line length and lines per page.</span></span> <span data-ttu-id="c232e-111">Po każdej stronie jest rysowana, sprawdź, czy jest ostatniej strony i ustaw <xref:System.Drawing.Printing.PrintPageEventArgs.HasMorePages%2A> właściwość <xref:System.Drawing.Printing.PrintPageEventArgs> odpowiednio.</span><span class="sxs-lookup"><span data-stu-id="c232e-111">After each page is drawn, check to see if it is the last page, and set the <xref:System.Drawing.Printing.PrintPageEventArgs.HasMorePages%2A> property of the <xref:System.Drawing.Printing.PrintPageEventArgs> accordingly.</span></span> <span data-ttu-id="c232e-112"><xref:System.Drawing.Printing.PrintDocument.PrintPage> Zdarzenie jest zgłaszane do momentu <xref:System.Drawing.Printing.PrintPageEventArgs.HasMorePages%2A> jest `false`.</span><span class="sxs-lookup"><span data-stu-id="c232e-112">The <xref:System.Drawing.Printing.PrintDocument.PrintPage> event is raised until <xref:System.Drawing.Printing.PrintPageEventArgs.HasMorePages%2A> is `false`.</span></span> <span data-ttu-id="c232e-113">Upewnij się również, <xref:System.Drawing.Printing.PrintDocument.PrintPage> wydarzenie jest skojarzone z jego metody obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="c232e-113">Also, make sure the <xref:System.Drawing.Printing.PrintDocument.PrintPage> event is associated with its event-handling method.</span></span>  
  
     <span data-ttu-id="c232e-114">W poniższym przykładzie kodu programu obsługi zdarzeń służy do drukowania zawartości pliku "testPage.txt" w tej samej czcionki, ponieważ jest używany w formularzu.</span><span class="sxs-lookup"><span data-stu-id="c232e-114">In the following code example, the event handler is used to print the contents of the "testPage.txt" file in the same font as is used on the form.</span></span>  
  
     [!code-csharp[System.Drawing.Printing.PrintExamples#2](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Printing.PrintExamples/CS/Form1.cs#2)]
     [!code-vb[System.Drawing.Printing.PrintExamples#2](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Printing.PrintExamples/VB/Form1.vb#2)]  
  
4.  <span data-ttu-id="c232e-115">Wywołaj <xref:System.Drawing.Printing.PrintDocument.Print%2A> metodę, aby podnieść <xref:System.Drawing.Printing.PrintDocument.PrintPage> zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="c232e-115">Call the <xref:System.Drawing.Printing.PrintDocument.Print%2A> method to raise the <xref:System.Drawing.Printing.PrintDocument.PrintPage> event.</span></span>  
  
     [!code-csharp[System.Drawing.Printing.PrintExamples#5](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Printing.PrintExamples/CS/Form1.cs#5)]
     [!code-vb[System.Drawing.Printing.PrintExamples#5](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Printing.PrintExamples/VB/Form1.vb#5)]  
  
## <a name="example"></a><span data-ttu-id="c232e-116">Przykład</span><span class="sxs-lookup"><span data-stu-id="c232e-116">Example</span></span>  
 [!code-csharp[System.Drawing.Printing.PrintExamples#0](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Printing.PrintExamples/CS/Form1.cs#0)]
 [!code-vb[System.Drawing.Printing.PrintExamples#0](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Printing.PrintExamples/VB/Form1.vb#0)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="c232e-117">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="c232e-117">Compiling the Code</span></span>  
 <span data-ttu-id="c232e-118">Ten przykład wymaga:</span><span class="sxs-lookup"><span data-stu-id="c232e-118">This example requires:</span></span>  
  
-   <span data-ttu-id="c232e-119">Plik tekstowy o nazwie testPage.txt zawierający tekst, aby wydrukować, znajduje się w folderze głównym dysku C:\\.</span><span class="sxs-lookup"><span data-stu-id="c232e-119">A text file named testPage.txt containing the text to print, located in the root of drive C:\\.</span></span> <span data-ttu-id="c232e-120">Edytuj kod, aby wydrukować inny plik.</span><span class="sxs-lookup"><span data-stu-id="c232e-120">Edit the code to print a different file.</span></span>  
  
-   <span data-ttu-id="c232e-121">Odwołania do systemu, przestrzeń nazw System.Windows.Forms, System.Drawing zestawów.</span><span class="sxs-lookup"><span data-stu-id="c232e-121">References to the System, System.Windows.Forms, System.Drawing assemblies.</span></span>  
  
-   <span data-ttu-id="c232e-122">Aby dowiedzieć się, jak tworzyć aplikacje w tym przykładzie z wiersza polecenia dla języka Visual Basic lub Visual C#, zobacz [tworzenie z wiersza polecenia](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) lub [wiersza polecenia tworzenia przy użyciu csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="c232e-122">For information about building this example from the command line for Visual Basic or Visual C#, see [Building from the Command Line](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="c232e-123">Można także utworzyć tego przykładu w programie Visual Studio, wklejając kod do nowego projektu.</span><span class="sxs-lookup"><span data-stu-id="c232e-123">You can also build this example in Visual Studio by pasting the code into a new project.</span></span>  <span data-ttu-id="c232e-124">Zobacz też [jak: Skompilować i uruchomić przykładowy kod pełną Windows Forms przy użyciu programu Visual Studio](https://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span><span class="sxs-lookup"><span data-stu-id="c232e-124">Also see [How to: Compile and Run a Complete Windows Forms Code Example Using Visual Studio](https://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c232e-125">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c232e-125">See also</span></span>
- <xref:System.Drawing.Graphics>
- <xref:System.Drawing.Brush>
- [<span data-ttu-id="c232e-126">Obsługa drukowania w formularzach Windows Forms</span><span class="sxs-lookup"><span data-stu-id="c232e-126">Windows Forms Print Support</span></span>](../../../../docs/framework/winforms/advanced/windows-forms-print-support.md)
