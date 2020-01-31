---
title: Drukuj przy użyciu podglądu wydruku
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- printing [Windows Forms], using print preview
- printing [Windows Forms], with print preview
- print preview
ms.assetid: 4a16f7e2-ae10-4485-b0ae-3d558334d0fe
ms.openlocfilehash: 1975c902fdb56326c763f2e2fc11e381ffc7fbd3
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76740606"
---
# <a name="how-to-print-in-windows-forms-using-print-preview"></a><span data-ttu-id="e3a47-102">Porady: drukowanie w formularzach systemu Windows przy użyciu podglądu wydruku</span><span class="sxs-lookup"><span data-stu-id="e3a47-102">How to: Print in Windows Forms Using Print Preview</span></span>
<span data-ttu-id="e3a47-103">Jest to bardzo popularne w Windows Forms programowaniu w celu oferowania podglądu wydruku oprócz usług drukowania.</span><span class="sxs-lookup"><span data-stu-id="e3a47-103">It is very common in Windows Forms programming to offer print preview in addition to printing services.</span></span> <span data-ttu-id="e3a47-104">Łatwym sposobem dodawania usług podglądu wydruku do aplikacji jest użycie kontrolki <xref:System.Windows.Forms.PrintPreviewDialog> w połączeniu z logiką obsługi zdarzeń <xref:System.Drawing.Printing.PrintDocument.PrintPage> do drukowania pliku.</span><span class="sxs-lookup"><span data-stu-id="e3a47-104">An easy way to add print preview services to your application is to use a <xref:System.Windows.Forms.PrintPreviewDialog> control in combination with the <xref:System.Drawing.Printing.PrintDocument.PrintPage> event-handling logic for printing a file.</span></span>  
  
### <a name="to-preview-a-text-document-with-a-printpreviewdialog-control"></a><span data-ttu-id="e3a47-105">Aby wyświetlić podgląd dokumentu tekstowego z kontrolką PrintPreviewDialog</span><span class="sxs-lookup"><span data-stu-id="e3a47-105">To preview a text document with a PrintPreviewDialog control</span></span>  
  
1. <span data-ttu-id="e3a47-106">Dodaj <xref:System.Windows.Forms.PrintPreviewDialog>, <xref:System.Drawing.Printing.PrintDocument>i dwa ciągi do formularza.</span><span class="sxs-lookup"><span data-stu-id="e3a47-106">Add a <xref:System.Windows.Forms.PrintPreviewDialog>, <xref:System.Drawing.Printing.PrintDocument>, and two strings to your form.</span></span>  
  
     [!code-csharp[System.Drawing.Printing.PrintPreviewExample#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Printing.PrintPreviewExample/CS/Form1.cs#1)]
     [!code-vb[System.Drawing.Printing.PrintPreviewExample#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Printing.PrintPreviewExample/VB/Form1.vb#1)]  
  
2. <span data-ttu-id="e3a47-107">Ustaw właściwość <xref:System.Drawing.Printing.PrintDocument.DocumentName%2A> na dokument, który chcesz wydrukować, a następnie otwórz i Odczytaj zawartość dokumentu do ciągu, który został dodany wcześniej.</span><span class="sxs-lookup"><span data-stu-id="e3a47-107">Set the <xref:System.Drawing.Printing.PrintDocument.DocumentName%2A> property to the document you wish to print, and open and read the document's contents to the string you added previously.</span></span>  
  
     [!code-csharp[System.Drawing.Printing.PrintPreviewExample#2](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Printing.PrintPreviewExample/CS/Form1.cs#2)]
     [!code-vb[System.Drawing.Printing.PrintPreviewExample#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Printing.PrintPreviewExample/VB/Form1.vb#2)]  
  
3. <span data-ttu-id="e3a47-108">Tak jak w przypadku drukowania dokumentu, w programie obsługi zdarzeń <xref:System.Drawing.Printing.PrintDocument.PrintPage> Użyj właściwości <xref:System.Drawing.Printing.PrintPageEventArgs.Graphics%2A> klasy <xref:System.Drawing.Printing.PrintPageEventArgs> i zawartości pliku, aby obliczyć linie na stronie i renderować zawartość dokumentu.</span><span class="sxs-lookup"><span data-stu-id="e3a47-108">As you would for printing the document, in the <xref:System.Drawing.Printing.PrintDocument.PrintPage> event handler, use the <xref:System.Drawing.Printing.PrintPageEventArgs.Graphics%2A> property of the <xref:System.Drawing.Printing.PrintPageEventArgs> class and the file contents to calculate lines per page and render the document's contents.</span></span> <span data-ttu-id="e3a47-109">Po narysowaniu każdej strony Sprawdź, czy jest ona ostatnią stroną i odpowiednio ustaw właściwość <xref:System.Drawing.Printing.PrintPageEventArgs.HasMorePages%2A> <xref:System.Drawing.Printing.PrintPageEventArgs>.</span><span class="sxs-lookup"><span data-stu-id="e3a47-109">After each page is drawn, check to see if it is the last page, and set the <xref:System.Drawing.Printing.PrintPageEventArgs.HasMorePages%2A> property of the <xref:System.Drawing.Printing.PrintPageEventArgs> accordingly.</span></span> <span data-ttu-id="e3a47-110">Zdarzenie <xref:System.Drawing.Printing.PrintDocument.PrintPage> jest zgłaszane do momentu `false`<xref:System.Drawing.Printing.PrintPageEventArgs.HasMorePages%2A>.</span><span class="sxs-lookup"><span data-stu-id="e3a47-110">The <xref:System.Drawing.Printing.PrintDocument.PrintPage> event is raised until <xref:System.Drawing.Printing.PrintPageEventArgs.HasMorePages%2A> is `false`.</span></span> <span data-ttu-id="e3a47-111">Po zakończeniu renderowania dokumentu Zresetuj ciąg, który ma być renderowany.</span><span class="sxs-lookup"><span data-stu-id="e3a47-111">When the document has finished rendering, reset the string to be rendered.</span></span> <span data-ttu-id="e3a47-112">Upewnij się również, że zdarzenie <xref:System.Drawing.Printing.PrintDocument.PrintPage> jest skojarzone z jego metodą obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="e3a47-112">Also, make sure the <xref:System.Drawing.Printing.PrintDocument.PrintPage> event is associated with its event-handling method.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="e3a47-113">W przypadku zaimplementowania drukowania w aplikacji mogły już zostać wykonane kroki 2 i 3.</span><span class="sxs-lookup"><span data-stu-id="e3a47-113">You may have already completed steps 2 and 3 if you have implemented printing in your application.</span></span>  
  
     <span data-ttu-id="e3a47-114">W poniższym przykładzie kodu program obsługi zdarzeń służy do drukowania pliku "testPage. txt" w tej samej czcionce, która jest używana w formularzu.</span><span class="sxs-lookup"><span data-stu-id="e3a47-114">In the following code example, the event handler is used to print the "testPage.txt" file in the same font used on the form.</span></span>  
  
     [!code-csharp[System.Drawing.Printing.PrintPreviewExample#3](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Printing.PrintPreviewExample/CS/Form1.cs#3)]
     [!code-vb[System.Drawing.Printing.PrintPreviewExample#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Printing.PrintPreviewExample/VB/Form1.vb#3)]  
  
4. <span data-ttu-id="e3a47-115">Ustaw właściwość <xref:System.Windows.Forms.PrintPreviewDialog.Document%2A> kontrolki <xref:System.Windows.Forms.PrintPreviewDialog> na składnik <xref:System.Drawing.Printing.PrintDocument> w formularzu.</span><span class="sxs-lookup"><span data-stu-id="e3a47-115">Set the <xref:System.Windows.Forms.PrintPreviewDialog.Document%2A> property of the <xref:System.Windows.Forms.PrintPreviewDialog> control to the <xref:System.Drawing.Printing.PrintDocument> component on the form.</span></span>  
  
     [!code-csharp[System.Drawing.Printing.PrintPreviewExample#5](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Printing.PrintPreviewExample/CS/Form1.cs#5)]
     [!code-vb[System.Drawing.Printing.PrintPreviewExample#5](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Printing.PrintPreviewExample/VB/Form1.vb#5)]  
  
5. <span data-ttu-id="e3a47-116">Wywołaj metodę <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> na kontrolce <xref:System.Windows.Forms.PrintPreviewDialog>.</span><span class="sxs-lookup"><span data-stu-id="e3a47-116">Call the <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> method on the <xref:System.Windows.Forms.PrintPreviewDialog> control.</span></span> <span data-ttu-id="e3a47-117">Zazwyczaj należy wywołać <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> z metody obsługi zdarzeń <xref:System.Windows.Forms.Control.Click> przycisku.</span><span class="sxs-lookup"><span data-stu-id="e3a47-117">You would typically call <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> from the <xref:System.Windows.Forms.Control.Click> event-handling method of a button.</span></span> <span data-ttu-id="e3a47-118">Wywołanie <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> wywołuje zdarzenie <xref:System.Drawing.Printing.PrintDocument.PrintPage> i renderuje dane wyjściowe do kontrolki <xref:System.Windows.Forms.PrintPreviewDialog>.</span><span class="sxs-lookup"><span data-stu-id="e3a47-118">Calling <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> raises the <xref:System.Drawing.Printing.PrintDocument.PrintPage> event and renders the output to the <xref:System.Windows.Forms.PrintPreviewDialog> control.</span></span> <span data-ttu-id="e3a47-119">Gdy użytkownik kliknie ikonę drukowania w oknie dialogowym, zostanie ponownie wywołane zdarzenie <xref:System.Drawing.Printing.PrintDocument.PrintPage>, wysyłając dane wyjściowe do drukarki zamiast okna dialogowego podglądu.</span><span class="sxs-lookup"><span data-stu-id="e3a47-119">When the user clicks the print icon on the dialog, the <xref:System.Drawing.Printing.PrintDocument.PrintPage> event is raised again, sending the output to the printer instead of the preview dialog.</span></span> <span data-ttu-id="e3a47-120">To dlatego, że ciąg jest resetowany na końcu procesu renderowania w kroku 3.</span><span class="sxs-lookup"><span data-stu-id="e3a47-120">This is why the string is reset at the end of the rendering process in step 3.</span></span>  
  
     <span data-ttu-id="e3a47-121">Poniższy przykład kodu przedstawia metodę obsługi zdarzeń <xref:System.Windows.Forms.Control.Click> dla przycisku w formularzu.</span><span class="sxs-lookup"><span data-stu-id="e3a47-121">The following code example shows the <xref:System.Windows.Forms.Control.Click> event-handling method for a button on the form.</span></span> <span data-ttu-id="e3a47-122">Ta metoda obsługi zdarzeń wywołuje metody odczytywania dokumentu i wyświetlania okna dialogowego podglądu wydruku.</span><span class="sxs-lookup"><span data-stu-id="e3a47-122">This event-handling method calls the methods to read the document and show the print preview dialog.</span></span>  
  
     [!code-csharp[System.Drawing.Printing.PrintPreviewExample#4](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Printing.PrintPreviewExample/CS/Form1.cs#4)]
     [!code-vb[System.Drawing.Printing.PrintPreviewExample#4](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Printing.PrintPreviewExample/VB/Form1.vb#4)]  
  
## <a name="example"></a><span data-ttu-id="e3a47-123">Przykład</span><span class="sxs-lookup"><span data-stu-id="e3a47-123">Example</span></span>  
 [!code-csharp[System.Drawing.Printing.PrintPreviewExample#0](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Printing.PrintPreviewExample/CS/Form1.cs#0)]
 [!code-vb[System.Drawing.Printing.PrintPreviewExample#0](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Printing.PrintPreviewExample/VB/Form1.vb#0)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="e3a47-124">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="e3a47-124">Compiling the Code</span></span>  
 <span data-ttu-id="e3a47-125">Ten przykład wymaga:</span><span class="sxs-lookup"><span data-stu-id="e3a47-125">This example requires:</span></span>  
  
- <span data-ttu-id="e3a47-126">Odwołania do zestawów system, system. Windows. Forms, system. Drawing.</span><span class="sxs-lookup"><span data-stu-id="e3a47-126">References to the System, System.Windows.Forms, System.Drawing assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e3a47-127">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e3a47-127">See also</span></span>

- [<span data-ttu-id="e3a47-128">Instrukcje: wyświetlanie podglądu wydruku w formularzach Windows Forms</span><span class="sxs-lookup"><span data-stu-id="e3a47-128">How to: Print a Multi-Page Text File in Windows Forms</span></span>](how-to-print-a-multi-page-text-file-in-windows-forms.md)
- [<span data-ttu-id="e3a47-129">Obsługa drukowania w formularzach Windows Forms</span><span class="sxs-lookup"><span data-stu-id="e3a47-129">Windows Forms Print Support</span></span>](windows-forms-print-support.md)
- [<span data-ttu-id="e3a47-130">Bezpieczniejsze drukowanie w formularzach Windows Forms</span><span class="sxs-lookup"><span data-stu-id="e3a47-130">More Secure Printing in Windows Forms</span></span>](../more-secure-printing-in-windows-forms.md)
