---
title: "Porady: drukowanie w formularzach systemu Windows przy użyciu podglądu wydruku"
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
helpviewer_keywords:
- printing [Windows Forms], using print preview
- printing [Windows Forms], with print preview
- print preview
ms.assetid: 4a16f7e2-ae10-4485-b0ae-3d558334d0fe
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 9aec07ab0f0897fcabcc2980dea5ef52d81082a6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-print-in-windows-forms-using-print-preview"></a><span data-ttu-id="ef702-102">Porady: drukowanie w formularzach systemu Windows przy użyciu podglądu wydruku</span><span class="sxs-lookup"><span data-stu-id="ef702-102">How to: Print in Windows Forms Using Print Preview</span></span>
<span data-ttu-id="ef702-103">Jest bardzo często programowania oferowanie podglądu wydruku, oprócz usługi drukowania formularzy systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="ef702-103">It is very common in Windows Forms programming to offer print preview in addition to printing services.</span></span> <span data-ttu-id="ef702-104">Prosty sposób dodawania usługi podglądu wydruku do aplikacji jest użycie <xref:System.Windows.Forms.PrintPreviewDialog> kontroli w połączeniu z <xref:System.Drawing.Printing.PrintDocument.PrintPage> logiki obsługi zdarzeń do drukowania pliku.</span><span class="sxs-lookup"><span data-stu-id="ef702-104">An easy way to add print preview services to your application is to use a <xref:System.Windows.Forms.PrintPreviewDialog> control in combination with the <xref:System.Drawing.Printing.PrintDocument.PrintPage> event-handling logic for printing a file.</span></span>  
  
### <a name="to-preview-a-text-document-with-a-printpreviewdialog-control"></a><span data-ttu-id="ef702-105">Aby wyświetlić podgląd dokument tekstowy o printpreviewdialog — formant</span><span class="sxs-lookup"><span data-stu-id="ef702-105">To preview a text document with a PrintPreviewDialog control</span></span>  
  
1.  <span data-ttu-id="ef702-106">Dodaj <xref:System.Windows.Forms.PrintPreviewDialog>, <xref:System.Drawing.Printing.PrintDocument>i dwa ciągi do formularza.</span><span class="sxs-lookup"><span data-stu-id="ef702-106">Add a <xref:System.Windows.Forms.PrintPreviewDialog>, <xref:System.Drawing.Printing.PrintDocument>, and two strings to your form.</span></span>  
  
     [!code-csharp[System.Drawing.Printing.PrintPreviewExample#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Printing.PrintPreviewExample/CS/Form1.cs#1)]
     [!code-vb[System.Drawing.Printing.PrintPreviewExample#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Printing.PrintPreviewExample/VB/Form1.vb#1)]  
  
2.  <span data-ttu-id="ef702-107">Ustaw <xref:System.Drawing.Printing.PrintDocument.DocumentName%2A> właściwości dokumentu chcesz drukowania i otwierać i odczytywać zawartość dokumentu do ciągu dodane wcześniej.</span><span class="sxs-lookup"><span data-stu-id="ef702-107">Set the <xref:System.Drawing.Printing.PrintDocument.DocumentName%2A> property to the document you wish to print, and open and read the document's contents to the string you added previously.</span></span>  
  
     [!code-csharp[System.Drawing.Printing.PrintPreviewExample#2](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Printing.PrintPreviewExample/CS/Form1.cs#2)]
     [!code-vb[System.Drawing.Printing.PrintPreviewExample#2](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Printing.PrintPreviewExample/VB/Form1.vb#2)]  
  
3.  <span data-ttu-id="ef702-108">Jak w przypadku drukowanie dokumentu, w <xref:System.Drawing.Printing.PrintDocument.PrintPage> program obsługi zdarzeń, użyj <xref:System.Drawing.Printing.PrintPageEventArgs.Graphics%2A> właściwość <xref:System.Drawing.Printing.PrintPageEventArgs> klasy i zawartość pliku do obliczania wierszy na stronie i renderowania zawartości dokumentu.</span><span class="sxs-lookup"><span data-stu-id="ef702-108">As you would for printing the document, in the <xref:System.Drawing.Printing.PrintDocument.PrintPage> event handler, use the <xref:System.Drawing.Printing.PrintPageEventArgs.Graphics%2A> property of the <xref:System.Drawing.Printing.PrintPageEventArgs> class and the file contents to calculate lines per page and render the document's contents.</span></span> <span data-ttu-id="ef702-109">Po każdej stronie jest, sprawdź, czy jest to ostatnia strona i ustaw <xref:System.Drawing.Printing.PrintPageEventArgs.HasMorePages%2A> właściwość <xref:System.Drawing.Printing.PrintPageEventArgs> odpowiednio.</span><span class="sxs-lookup"><span data-stu-id="ef702-109">After each page is drawn, check to see if it is the last page, and set the <xref:System.Drawing.Printing.PrintPageEventArgs.HasMorePages%2A> property of the <xref:System.Drawing.Printing.PrintPageEventArgs> accordingly.</span></span> <span data-ttu-id="ef702-110"><xref:System.Drawing.Printing.PrintDocument.PrintPage> Zdarzenie jest wywoływane przed <xref:System.Drawing.Printing.PrintPageEventArgs.HasMorePages%2A> jest `false`.</span><span class="sxs-lookup"><span data-stu-id="ef702-110">The <xref:System.Drawing.Printing.PrintDocument.PrintPage> event is raised until <xref:System.Drawing.Printing.PrintPageEventArgs.HasMorePages%2A> is `false`.</span></span> <span data-ttu-id="ef702-111">Po zakończeniu renderowania dokumentu zresetować parametry do renderowania.</span><span class="sxs-lookup"><span data-stu-id="ef702-111">When the document has finished rendering, reset the string to be rendered.</span></span> <span data-ttu-id="ef702-112">Upewnij się również, <xref:System.Drawing.Printing.PrintDocument.PrintPage> wydarzenie jest skojarzone z metody obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="ef702-112">Also, make sure the <xref:System.Drawing.Printing.PrintDocument.PrintPage> event is associated with its event-handling method.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="ef702-113">Może zostały już wykonane kroki 2 i 3, jeśli zostały zaimplementowane drukowanie w aplikacji.</span><span class="sxs-lookup"><span data-stu-id="ef702-113">You may have already completed steps 2 and 3 if you have implemented printing in your application.</span></span>  
  
     <span data-ttu-id="ef702-114">W poniższym przykładzie kodu programu obsługi zdarzeń służy do drukowania pliku "testPage.txt" w tej samej czcionki w formularzu.</span><span class="sxs-lookup"><span data-stu-id="ef702-114">In the following code example, the event handler is used to print the "testPage.txt" file in the same font used on the form.</span></span>  
  
     [!code-csharp[System.Drawing.Printing.PrintPreviewExample#3](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Printing.PrintPreviewExample/CS/Form1.cs#3)]
     [!code-vb[System.Drawing.Printing.PrintPreviewExample#3](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Printing.PrintPreviewExample/VB/Form1.vb#3)]  
  
4.  <span data-ttu-id="ef702-115">Ustaw <xref:System.Windows.Forms.PrintPreviewDialog.Document%2A> właściwość <xref:System.Windows.Forms.PrintPreviewDialog> formant <xref:System.Drawing.Printing.PrintDocument> składnika w formularzu.</span><span class="sxs-lookup"><span data-stu-id="ef702-115">Set the <xref:System.Windows.Forms.PrintPreviewDialog.Document%2A> property of the <xref:System.Windows.Forms.PrintPreviewDialog> control to the <xref:System.Drawing.Printing.PrintDocument> component on the form.</span></span>  
  
     [!code-csharp[System.Drawing.Printing.PrintPreviewExample#5](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Printing.PrintPreviewExample/CS/Form1.cs#5)]
     [!code-vb[System.Drawing.Printing.PrintPreviewExample#5](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Printing.PrintPreviewExample/VB/Form1.vb#5)]  
  
5.  <span data-ttu-id="ef702-116">Wywołanie <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> metoda <xref:System.Windows.Forms.PrintPreviewDialog> formantu.</span><span class="sxs-lookup"><span data-stu-id="ef702-116">Call the <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> method on the <xref:System.Windows.Forms.PrintPreviewDialog> control.</span></span> <span data-ttu-id="ef702-117">Zwykle możesz wywołać <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> z <xref:System.Windows.Forms.Control.Click> metoda obsługi zdarzeń przycisku.</span><span class="sxs-lookup"><span data-stu-id="ef702-117">You would typically call <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> from the <xref:System.Windows.Forms.Control.Click> event-handling method of a button.</span></span> <span data-ttu-id="ef702-118">Wywoływanie <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> zgłasza <xref:System.Drawing.Printing.PrintDocument.PrintPage> zdarzeń i renderuje dane wyjściowe do <xref:System.Windows.Forms.PrintPreviewDialog> formantu.</span><span class="sxs-lookup"><span data-stu-id="ef702-118">Calling <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> raises the <xref:System.Drawing.Printing.PrintDocument.PrintPage> event and renders the output to the <xref:System.Windows.Forms.PrintPreviewDialog> control.</span></span> <span data-ttu-id="ef702-119">Gdy użytkownik kliknie ikonę drukowania w oknie dialogowym <xref:System.Drawing.Printing.PrintDocument.PrintPage> zdarzenie jest zgłaszane, wysyła dane wyjściowe do drukarki zamiast okna dialogowego podglądu.</span><span class="sxs-lookup"><span data-stu-id="ef702-119">When the user clicks the print icon on the dialog, the <xref:System.Drawing.Printing.PrintDocument.PrintPage> event is raised again, sending the output to the printer instead of the preview dialog.</span></span> <span data-ttu-id="ef702-120">Jest to, dlaczego ten ciąg jest resetowany pod koniec procesu renderowania w kroku 3.</span><span class="sxs-lookup"><span data-stu-id="ef702-120">This is why the string is reset at the end of the rendering process in step 3.</span></span>  
  
     <span data-ttu-id="ef702-121">Poniższy kod przedstawia przykład <xref:System.Windows.Forms.Control.Click> metoda obsługi zdarzeń dla przycisku w formularzu.</span><span class="sxs-lookup"><span data-stu-id="ef702-121">The following code example shows the <xref:System.Windows.Forms.Control.Click> event-handling method for a button on the form.</span></span> <span data-ttu-id="ef702-122">Ta metoda obsługi zdarzeń wywołuje metody służące do odczytu dokumentu i wyświetlenie okna dialogowego podglądu wydruku.</span><span class="sxs-lookup"><span data-stu-id="ef702-122">This event-handling method calls the methods to read the document and show the print preview dialog.</span></span>  
  
     [!code-csharp[System.Drawing.Printing.PrintPreviewExample#4](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Printing.PrintPreviewExample/CS/Form1.cs#4)]
     [!code-vb[System.Drawing.Printing.PrintPreviewExample#4](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Printing.PrintPreviewExample/VB/Form1.vb#4)]  
  
## <a name="example"></a><span data-ttu-id="ef702-123">Przykład</span><span class="sxs-lookup"><span data-stu-id="ef702-123">Example</span></span>  
 [!code-csharp[System.Drawing.Printing.PrintPreviewExample#0](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Printing.PrintPreviewExample/CS/Form1.cs#0)]
 [!code-vb[System.Drawing.Printing.PrintPreviewExample#0](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Printing.PrintPreviewExample/VB/Form1.vb#0)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="ef702-124">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="ef702-124">Compiling the Code</span></span>  
 <span data-ttu-id="ef702-125">Ten przykład wymaga:</span><span class="sxs-lookup"><span data-stu-id="ef702-125">This example requires:</span></span>  
  
-   <span data-ttu-id="ef702-126">Odwołania do systemu, System.Windows.Forms, System.Drawing zestawów.</span><span class="sxs-lookup"><span data-stu-id="ef702-126">References to the System, System.Windows.Forms, System.Drawing assemblies.</span></span>  
  
-   <span data-ttu-id="ef702-127">Informacji dotyczących tworzenia tego przykładu z wiersza polecenia dla [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] lub [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)], zobacz [tworzenie z wiersza polecenia](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) lub [kompilowania z wiersza polecenia csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="ef702-127">For information about building this example from the command line for [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] or [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)], see [Building from the Command Line](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="ef702-128">Można także utworzyć tym przykładzie [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] przez wklejenie kodu do nowego projektu.</span><span class="sxs-lookup"><span data-stu-id="ef702-128">You can also build this example in [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] by pasting the code into a new project.</span></span>  <span data-ttu-id="ef702-129">Zobacz też [porady: kompilowanie i uruchamianie pełną Windows formularze kodu przykład za pomocą programu Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span><span class="sxs-lookup"><span data-stu-id="ef702-129">Also see [How to: Compile and Run a Complete Windows Forms Code Example Using Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ef702-130">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ef702-130">See Also</span></span>  
 [<span data-ttu-id="ef702-131">Instrukcje: wyświetlanie podglądu wydruku w formularzach Windows Forms</span><span class="sxs-lookup"><span data-stu-id="ef702-131">How to: Print a Multi-Page Text File in Windows Forms</span></span>](../../../../docs/framework/winforms/advanced/how-to-print-a-multi-page-text-file-in-windows-forms.md)  
 [<span data-ttu-id="ef702-132">Obsługa drukowania w formularzach Windows Forms</span><span class="sxs-lookup"><span data-stu-id="ef702-132">Windows Forms Print Support</span></span>](../../../../docs/framework/winforms/advanced/windows-forms-print-support.md)  
 [<span data-ttu-id="ef702-133">Bezpieczniejsze drukowanie w formularzach Windows Forms</span><span class="sxs-lookup"><span data-stu-id="ef702-133">More Secure Printing in Windows Forms</span></span>](../../../../docs/framework/winforms/more-secure-printing-in-windows-forms.md)
