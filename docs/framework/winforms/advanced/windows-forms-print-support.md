---
title: Obsługa drukowania
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms, printing
- printing [Windows Forms]
- forms [Windows Forms], printing (using designer)
- printing [Windows Forms], Windows Forms, support
- printing [Windows Forms], print support
ms.assetid: a4a2960c-eb70-48e2-b641-cfb222704e46
ms.openlocfilehash: d6e8f60db7afe2f1b04eaae6fe71aa93e5c22cae
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76732490"
---
# <a name="windows-forms-print-support"></a><span data-ttu-id="3c708-102">Obsługa drukowania w formularzach systemu Windows</span><span class="sxs-lookup"><span data-stu-id="3c708-102">Windows Forms Print Support</span></span>
<span data-ttu-id="3c708-103">Drukowanie w Windows Forms składa się głównie z używania składnika [składnika PrintDocument](../controls/printdocument-component-windows-forms.md) , aby umożliwić użytkownikowi drukowanie oraz kontrolki [sterowania PrintPreviewDialog](../controls/printpreviewdialog-control-windows-forms.md) , [składnik PrintDialog](../controls/printdialog-component-windows-forms.md) i składnik [składnika PageSetupDialog](../controls/pagesetupdialog-component-windows-forms.md) , aby zapewnić znany interfejs graficzny dla użytkowników przyzwyczajonych do systemu operacyjnego Windows.</span><span class="sxs-lookup"><span data-stu-id="3c708-103">Printing in Windows Forms consists primarily of using the [PrintDocument Component](../controls/printdocument-component-windows-forms.md) component to enable the user to print, and the [PrintPreviewDialog Control](../controls/printpreviewdialog-control-windows-forms.md) control, [PrintDialog Component](../controls/printdialog-component-windows-forms.md) and [PageSetupDialog Component](../controls/pagesetupdialog-component-windows-forms.md) components to provide a familiar graphical interface to users accustomed to the Windows operating system.</span></span>  
  
 <span data-ttu-id="3c708-104">Zazwyczaj tworzysz nowe wystąpienie składnika <xref:System.Drawing.Printing.PrintDocument>, ustaw właściwości opisujące, co należy wydrukować przy użyciu klas <xref:System.Drawing.Printing.PrinterSettings> i <xref:System.Drawing.Printing.PageSettings>, a następnie Wywołaj metodę <xref:System.Drawing.Printing.PrintDocument.Print%2A>, aby rzeczywiście wydrukować dokument.</span><span class="sxs-lookup"><span data-stu-id="3c708-104">Typically, you create a new instance of the <xref:System.Drawing.Printing.PrintDocument> component, set the properties that describe what to print using the <xref:System.Drawing.Printing.PrinterSettings> and <xref:System.Drawing.Printing.PageSettings> classes, and call the <xref:System.Drawing.Printing.PrintDocument.Print%2A> method to actually print the document.</span></span>  
  
 <span data-ttu-id="3c708-105">W trakcie drukowania z aplikacji opartej na systemie Windows, składnik <xref:System.Drawing.Printing.PrintDocument> wyświetli okno dialogowe przerwania drukowania, aby ostrzec użytkowników o tym, że drukowanie odbywa się i aby umożliwić anulowanie zadania drukowania.</span><span class="sxs-lookup"><span data-stu-id="3c708-105">During the course of printing from a Windows-based application, the <xref:System.Drawing.Printing.PrintDocument> component will show an abort print dialog box to alert users to the fact that printing is occurring and to allow the print job to be canceled.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="3c708-106">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="3c708-106">In This Section</span></span>  
 [<span data-ttu-id="3c708-107">Instrukcje: tworzenie standardowych zadań drukowania formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="3c708-107">How to: Create Standard Windows Forms Print Jobs</span></span>](how-to-create-standard-windows-forms-print-jobs.md)  
 <span data-ttu-id="3c708-108">Wyjaśnia, jak używać składnika <xref:System.Drawing.Printing.PrintDocument> do drukowania z formularza systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="3c708-108">Explains how to use the <xref:System.Drawing.Printing.PrintDocument> component to print from a Windows Form.</span></span>  
  
 [<span data-ttu-id="3c708-109">Instrukcje: przechwytywanie danych użytkownika ze składnika PrintDialog w czasie wykonywania</span><span class="sxs-lookup"><span data-stu-id="3c708-109">How to: Capture User Input from a PrintDialog at Run Time</span></span>](how-to-capture-user-input-from-a-printdialog-at-run-time.md)  
 <span data-ttu-id="3c708-110">Wyjaśnia, jak modyfikować wybrane opcje drukowania programowo przy użyciu składnika <xref:System.Windows.Forms.PrintDialog>.</span><span class="sxs-lookup"><span data-stu-id="3c708-110">Explains how to modify selected print options programmatically using the <xref:System.Windows.Forms.PrintDialog> component.</span></span>  
  
 [<span data-ttu-id="3c708-111">Instrukcje: wybieranie w formularzach Windows Forms drukarek podłączonych do komputera użytkownika</span><span class="sxs-lookup"><span data-stu-id="3c708-111">How to: Choose the Printers Attached to a User's Computer in Windows Forms</span></span>](how-to-choose-the-printers-attached-to-user-computer-in-windows-forms.md)  
 <span data-ttu-id="3c708-112">Opisuje zmianę drukarki do drukowania przy użyciu składnika <xref:System.Windows.Forms.PrintDialog> w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="3c708-112">Describes changing the printer to print to using the <xref:System.Windows.Forms.PrintDialog> component at run time.</span></span>  
  
 [<span data-ttu-id="3c708-113">Instrukcje: drukowanie grafiki w formularzach Windows Forms</span><span class="sxs-lookup"><span data-stu-id="3c708-113">How to: Print Graphics in Windows Forms</span></span>](how-to-print-graphics-in-windows-forms.md)  
 <span data-ttu-id="3c708-114">Opisuje wysyłanie grafiki do drukarki.</span><span class="sxs-lookup"><span data-stu-id="3c708-114">Describes sending graphics to the printer.</span></span>  
  
 [<span data-ttu-id="3c708-115">Instrukcje: wyświetlanie podglądu wydruku w formularzach Windows Forms</span><span class="sxs-lookup"><span data-stu-id="3c708-115">How to: Print a Multi-Page Text File in Windows Forms</span></span>](how-to-print-a-multi-page-text-file-in-windows-forms.md)  
 <span data-ttu-id="3c708-116">Opisuje wysyłanie tekstu do drukarki.</span><span class="sxs-lookup"><span data-stu-id="3c708-116">Describes sending text to the printer.</span></span>  
  
 [<span data-ttu-id="3c708-117">Instrukcje: kończenie zadań drukowania formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="3c708-117">How to: Complete Windows Forms Print Jobs</span></span>](how-to-complete-windows-forms-print-jobs.md)  
 <span data-ttu-id="3c708-118">Wyjaśnia, jak wysyłać alerty użytkowników do ukończenia zadania drukowania.</span><span class="sxs-lookup"><span data-stu-id="3c708-118">Explains how to alert users to the completion of a print job.</span></span>  
  
 [<span data-ttu-id="3c708-119">Instrukcje: drukowanie formularza systemu Windows</span><span class="sxs-lookup"><span data-stu-id="3c708-119">How to: Print a Windows Form</span></span>](how-to-print-a-windows-form.md)  
 <span data-ttu-id="3c708-120">Pokazuje, jak drukować kopię bieżącego formularza.</span><span class="sxs-lookup"><span data-stu-id="3c708-120">Shows how to print a copy of the current form.</span></span>  
  
 [<span data-ttu-id="3c708-121">Instrukcje: drukowanie w formularzach Windows Forms przy użyciu podglądu wydruku</span><span class="sxs-lookup"><span data-stu-id="3c708-121">How to: Print in Windows Forms Using Print Preview</span></span>](how-to-print-in-windows-forms-using-print-preview.md)  
 <span data-ttu-id="3c708-122">Pokazuje, w jaki sposób używać <xref:System.Windows.Forms.PrintPreviewDialog> do drukowania dokumentu.</span><span class="sxs-lookup"><span data-stu-id="3c708-122">Shows how to use a <xref:System.Windows.Forms.PrintPreviewDialog> for printing a document.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="3c708-123">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="3c708-123">Related Sections</span></span>  
 [<span data-ttu-id="3c708-124">PrintDocument, składnik</span><span class="sxs-lookup"><span data-stu-id="3c708-124">PrintDocument Component</span></span>](../controls/printdocument-component-windows-forms.md)  
 <span data-ttu-id="3c708-125">Wyjaśnia użycie składnika <xref:System.Drawing.Printing.PrintDocument>.</span><span class="sxs-lookup"><span data-stu-id="3c708-125">Explains usage of the <xref:System.Drawing.Printing.PrintDocument> component.</span></span>  
  
 [<span data-ttu-id="3c708-126">PrintDialog, składnik</span><span class="sxs-lookup"><span data-stu-id="3c708-126">PrintDialog Component</span></span>](../controls/printdialog-component-windows-forms.md)  
 <span data-ttu-id="3c708-127">Wyjaśnia użycie składnika <xref:System.Windows.Forms.PrintDialog>.</span><span class="sxs-lookup"><span data-stu-id="3c708-127">Explains usage of the <xref:System.Windows.Forms.PrintDialog> component.</span></span>  
  
 [<span data-ttu-id="3c708-128">PrintPreviewDialog, kontrolka</span><span class="sxs-lookup"><span data-stu-id="3c708-128">PrintPreviewDialog Control</span></span>](../controls/printpreviewdialog-control-windows-forms.md)  
 <span data-ttu-id="3c708-129">Wyjaśnia użycie kontrolki <xref:System.Windows.Forms.PrintPreviewDialog>.</span><span class="sxs-lookup"><span data-stu-id="3c708-129">Explains usage of the <xref:System.Windows.Forms.PrintPreviewDialog> control.</span></span>  
  
 [<span data-ttu-id="3c708-130">PageSetupDialog, składnik</span><span class="sxs-lookup"><span data-stu-id="3c708-130">PageSetupDialog Component</span></span>](../controls/pagesetupdialog-component-windows-forms.md)  
 <span data-ttu-id="3c708-131">Wyjaśnia użycie składnika <xref:System.Windows.Forms.PageSetupDialog>.</span><span class="sxs-lookup"><span data-stu-id="3c708-131">Explains usage of the <xref:System.Windows.Forms.PageSetupDialog> component.</span></span>  
  
 <xref:System.Drawing.Printing>  
 <span data-ttu-id="3c708-132">Opisuje klasy w przestrzeni nazw <xref:System.Drawing.Printing>.</span><span class="sxs-lookup"><span data-stu-id="3c708-132">Describes the classes in the <xref:System.Drawing.Printing> namespace.</span></span>
