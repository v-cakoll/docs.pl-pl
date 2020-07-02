---
title: Drukuj przy użyciu podglądu wydruku
description: Dowiedz się, jak dodać usługi podglądu wydruku do aplikacji przy użyciu kontrolki PrintPreviewDialog Windows Forms.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- printing [Windows Forms], using print preview
- printing [Windows Forms], with print preview
- print preview
ms.assetid: 4a16f7e2-ae10-4485-b0ae-3d558334d0fe
ms.openlocfilehash: abcf77db40f648df1a0cd49922bb49e5c9407811
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621616"
---
# <a name="how-to-print-in-windows-forms-using-print-preview"></a><span data-ttu-id="6e4bc-103">Porady: drukowanie w formularzach systemu Windows przy użyciu podglądu wydruku</span><span class="sxs-lookup"><span data-stu-id="6e4bc-103">How to: Print in Windows Forms Using Print Preview</span></span>
<span data-ttu-id="6e4bc-104">Jest to bardzo popularne w Windows Forms programowaniu w celu oferowania podglądu wydruku oprócz usług drukowania.</span><span class="sxs-lookup"><span data-stu-id="6e4bc-104">It is very common in Windows Forms programming to offer print preview in addition to printing services.</span></span> <span data-ttu-id="6e4bc-105">Łatwym sposobem dodawania usług podglądu wydruku do aplikacji jest użycie <xref:System.Windows.Forms.PrintPreviewDialog> kontrolki w połączeniu z <xref:System.Drawing.Printing.PrintDocument.PrintPage> logiką obsługi zdarzeń do drukowania pliku.</span><span class="sxs-lookup"><span data-stu-id="6e4bc-105">An easy way to add print preview services to your application is to use a <xref:System.Windows.Forms.PrintPreviewDialog> control in combination with the <xref:System.Drawing.Printing.PrintDocument.PrintPage> event-handling logic for printing a file.</span></span>  
  
### <a name="to-preview-a-text-document-with-a-printpreviewdialog-control"></a><span data-ttu-id="6e4bc-106">Aby wyświetlić podgląd dokumentu tekstowego z kontrolką PrintPreviewDialog</span><span class="sxs-lookup"><span data-stu-id="6e4bc-106">To preview a text document with a PrintPreviewDialog control</span></span>  
  
1. <span data-ttu-id="6e4bc-107">Dodaj <xref:System.Windows.Forms.PrintPreviewDialog> , <xref:System.Drawing.Printing.PrintDocument> i dwa ciągi do formularza.</span><span class="sxs-lookup"><span data-stu-id="6e4bc-107">Add a <xref:System.Windows.Forms.PrintPreviewDialog>, <xref:System.Drawing.Printing.PrintDocument>, and two strings to your form.</span></span>  
  
     [!code-csharp[System.Drawing.Printing.PrintPreviewExample#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Printing.PrintPreviewExample/CS/Form1.cs#1)]
     [!code-vb[System.Drawing.Printing.PrintPreviewExample#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Printing.PrintPreviewExample/VB/Form1.vb#1)]  
  
2. <span data-ttu-id="6e4bc-108">Ustaw <xref:System.Drawing.Printing.PrintDocument.DocumentName%2A> Właściwość na dokument, który chcesz wydrukować, i Otwórz i Odczytaj zawartość dokumentu do ciągu, który został dodany wcześniej.</span><span class="sxs-lookup"><span data-stu-id="6e4bc-108">Set the <xref:System.Drawing.Printing.PrintDocument.DocumentName%2A> property to the document you wish to print, and open and read the document's contents to the string you added previously.</span></span>  
  
     [!code-csharp[System.Drawing.Printing.PrintPreviewExample#2](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Printing.PrintPreviewExample/CS/Form1.cs#2)]
     [!code-vb[System.Drawing.Printing.PrintPreviewExample#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Printing.PrintPreviewExample/VB/Form1.vb#2)]  
  
3. <span data-ttu-id="6e4bc-109">Podobnie jak w przypadku drukowania dokumentu, w programie <xref:System.Drawing.Printing.PrintDocument.PrintPage> obsługi zdarzeń należy użyć <xref:System.Drawing.Printing.PrintPageEventArgs.Graphics%2A> właściwości <xref:System.Drawing.Printing.PrintPageEventArgs> klasy i zawartości pliku, aby obliczyć linie na stronie i renderować zawartość dokumentu.</span><span class="sxs-lookup"><span data-stu-id="6e4bc-109">As you would for printing the document, in the <xref:System.Drawing.Printing.PrintDocument.PrintPage> event handler, use the <xref:System.Drawing.Printing.PrintPageEventArgs.Graphics%2A> property of the <xref:System.Drawing.Printing.PrintPageEventArgs> class and the file contents to calculate lines per page and render the document's contents.</span></span> <span data-ttu-id="6e4bc-110">Po narysowaniu każdej strony Sprawdź, czy jest ona ostatnią stroną, i ustaw <xref:System.Drawing.Printing.PrintPageEventArgs.HasMorePages%2A> Właściwość <xref:System.Drawing.Printing.PrintPageEventArgs> odpowiednio.</span><span class="sxs-lookup"><span data-stu-id="6e4bc-110">After each page is drawn, check to see if it is the last page, and set the <xref:System.Drawing.Printing.PrintPageEventArgs.HasMorePages%2A> property of the <xref:System.Drawing.Printing.PrintPageEventArgs> accordingly.</span></span> <span data-ttu-id="6e4bc-111"><xref:System.Drawing.Printing.PrintDocument.PrintPage>Zdarzenie jest zgłaszane do momentu <xref:System.Drawing.Printing.PrintPageEventArgs.HasMorePages%2A> `false` .</span><span class="sxs-lookup"><span data-stu-id="6e4bc-111">The <xref:System.Drawing.Printing.PrintDocument.PrintPage> event is raised until <xref:System.Drawing.Printing.PrintPageEventArgs.HasMorePages%2A> is `false`.</span></span> <span data-ttu-id="6e4bc-112">Po zakończeniu renderowania dokumentu Zresetuj ciąg, który ma być renderowany.</span><span class="sxs-lookup"><span data-stu-id="6e4bc-112">When the document has finished rendering, reset the string to be rendered.</span></span> <span data-ttu-id="6e4bc-113">Upewnij się również, że <xref:System.Drawing.Printing.PrintDocument.PrintPage> zdarzenie jest skojarzone z jego metodą obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="6e4bc-113">Also, make sure the <xref:System.Drawing.Printing.PrintDocument.PrintPage> event is associated with its event-handling method.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="6e4bc-114">W przypadku zaimplementowania drukowania w aplikacji mogły już zostać wykonane kroki 2 i 3.</span><span class="sxs-lookup"><span data-stu-id="6e4bc-114">You may have already completed steps 2 and 3 if you have implemented printing in your application.</span></span>  
  
     <span data-ttu-id="6e4bc-115">W poniższym przykładzie kodu program obsługi zdarzeń służy do drukowania pliku "testPage.txt" w tej samej czcionce, która jest używana w formularzu.</span><span class="sxs-lookup"><span data-stu-id="6e4bc-115">In the following code example, the event handler is used to print the "testPage.txt" file in the same font used on the form.</span></span>  
  
     [!code-csharp[System.Drawing.Printing.PrintPreviewExample#3](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Printing.PrintPreviewExample/CS/Form1.cs#3)]
     [!code-vb[System.Drawing.Printing.PrintPreviewExample#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Printing.PrintPreviewExample/VB/Form1.vb#3)]  
  
4. <span data-ttu-id="6e4bc-116">Ustaw <xref:System.Windows.Forms.PrintPreviewDialog.Document%2A> Właściwość <xref:System.Windows.Forms.PrintPreviewDialog> formantu na <xref:System.Drawing.Printing.PrintDocument> składnik w formularzu.</span><span class="sxs-lookup"><span data-stu-id="6e4bc-116">Set the <xref:System.Windows.Forms.PrintPreviewDialog.Document%2A> property of the <xref:System.Windows.Forms.PrintPreviewDialog> control to the <xref:System.Drawing.Printing.PrintDocument> component on the form.</span></span>  
  
     [!code-csharp[System.Drawing.Printing.PrintPreviewExample#5](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Printing.PrintPreviewExample/CS/Form1.cs#5)]
     [!code-vb[System.Drawing.Printing.PrintPreviewExample#5](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Printing.PrintPreviewExample/VB/Form1.vb#5)]  
  
5. <span data-ttu-id="6e4bc-117">Wywołaj <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> metodę w <xref:System.Windows.Forms.PrintPreviewDialog> kontrolce.</span><span class="sxs-lookup"><span data-stu-id="6e4bc-117">Call the <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> method on the <xref:System.Windows.Forms.PrintPreviewDialog> control.</span></span> <span data-ttu-id="6e4bc-118">Zwykle jest wywoływana <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> z <xref:System.Windows.Forms.Control.Click> metody obsługi zdarzeń przycisku.</span><span class="sxs-lookup"><span data-stu-id="6e4bc-118">You would typically call <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> from the <xref:System.Windows.Forms.Control.Click> event-handling method of a button.</span></span> <span data-ttu-id="6e4bc-119">Wywołanie <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> wywołuje <xref:System.Drawing.Printing.PrintDocument.PrintPage> zdarzenie i renderuje dane wyjściowe do <xref:System.Windows.Forms.PrintPreviewDialog> kontrolki.</span><span class="sxs-lookup"><span data-stu-id="6e4bc-119">Calling <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> raises the <xref:System.Drawing.Printing.PrintDocument.PrintPage> event and renders the output to the <xref:System.Windows.Forms.PrintPreviewDialog> control.</span></span> <span data-ttu-id="6e4bc-120">Gdy użytkownik kliknie ikonę drukowania w oknie dialogowym, <xref:System.Drawing.Printing.PrintDocument.PrintPage> zostanie ponownie wywołane zdarzenie, wysyłając dane wyjściowe do drukarki zamiast okna dialogowego podglądu.</span><span class="sxs-lookup"><span data-stu-id="6e4bc-120">When the user clicks the print icon on the dialog, the <xref:System.Drawing.Printing.PrintDocument.PrintPage> event is raised again, sending the output to the printer instead of the preview dialog.</span></span> <span data-ttu-id="6e4bc-121">To dlatego, że ciąg jest resetowany na końcu procesu renderowania w kroku 3.</span><span class="sxs-lookup"><span data-stu-id="6e4bc-121">This is why the string is reset at the end of the rendering process in step 3.</span></span>  
  
     <span data-ttu-id="6e4bc-122">Poniższy przykład kodu pokazuje <xref:System.Windows.Forms.Control.Click> metodę obsługi zdarzeń dla przycisku w formularzu.</span><span class="sxs-lookup"><span data-stu-id="6e4bc-122">The following code example shows the <xref:System.Windows.Forms.Control.Click> event-handling method for a button on the form.</span></span> <span data-ttu-id="6e4bc-123">Ta metoda obsługi zdarzeń wywołuje metody odczytywania dokumentu i wyświetlania okna dialogowego podglądu wydruku.</span><span class="sxs-lookup"><span data-stu-id="6e4bc-123">This event-handling method calls the methods to read the document and show the print preview dialog.</span></span>  
  
     [!code-csharp[System.Drawing.Printing.PrintPreviewExample#4](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Printing.PrintPreviewExample/CS/Form1.cs#4)]
     [!code-vb[System.Drawing.Printing.PrintPreviewExample#4](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Printing.PrintPreviewExample/VB/Form1.vb#4)]  
  
## <a name="example"></a><span data-ttu-id="6e4bc-124">Przykład</span><span class="sxs-lookup"><span data-stu-id="6e4bc-124">Example</span></span>  
 [!code-csharp[System.Drawing.Printing.PrintPreviewExample#0](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Printing.PrintPreviewExample/CS/Form1.cs#0)]
 [!code-vb[System.Drawing.Printing.PrintPreviewExample#0](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Printing.PrintPreviewExample/VB/Form1.vb#0)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="6e4bc-125">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="6e4bc-125">Compiling the Code</span></span>  
 <span data-ttu-id="6e4bc-126">Ten przykład wymaga:</span><span class="sxs-lookup"><span data-stu-id="6e4bc-126">This example requires:</span></span>  
  
- <span data-ttu-id="6e4bc-127">Odwołania do zestawów system, system. Windows. Forms, system. Drawing.</span><span class="sxs-lookup"><span data-stu-id="6e4bc-127">References to the System, System.Windows.Forms, System.Drawing assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6e4bc-128">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="6e4bc-128">See also</span></span>

- [<span data-ttu-id="6e4bc-129">Instrukcje: wyświetlanie podglądu wydruku w formularzach Windows Forms</span><span class="sxs-lookup"><span data-stu-id="6e4bc-129">How to: Print a Multi-Page Text File in Windows Forms</span></span>](how-to-print-a-multi-page-text-file-in-windows-forms.md)
- [<span data-ttu-id="6e4bc-130">Obsługa drukowania w formularzach systemu Windows</span><span class="sxs-lookup"><span data-stu-id="6e4bc-130">Windows Forms Print Support</span></span>](windows-forms-print-support.md)
- [<span data-ttu-id="6e4bc-131">Bezpieczniejsze drukowanie w formularzach systemu Windows</span><span class="sxs-lookup"><span data-stu-id="6e4bc-131">More Secure Printing in Windows Forms</span></span>](../more-secure-printing-in-windows-forms.md)
