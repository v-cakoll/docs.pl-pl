---
title: "Obsługa drukowania w formularzach systemu Windows"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Windows Forms, printing
- printing [Windows Forms]
- forms [Windows Forms], printing (using designer)
- printing [Windows Forms], Windows Forms, support
- printing [Windows Forms], print support
ms.assetid: a4a2960c-eb70-48e2-b641-cfb222704e46
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 029d5ed424061807cf04446cbb10424ae20afba2
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2017
---
# <a name="windows-forms-print-support"></a><span data-ttu-id="c0885-102">Obsługa drukowania w formularzach systemu Windows</span><span class="sxs-lookup"><span data-stu-id="c0885-102">Windows Forms Print Support</span></span>
<span data-ttu-id="c0885-103">Drukowanie w formularzach systemu Windows obejmuje głównie przy użyciu [PrintDocument — składnik](../../../../docs/framework/winforms/controls/printdocument-component-windows-forms.md) składnik, aby umożliwić użytkownikowi drukowanie i [printpreviewdialog — formant](../../../../docs/framework/winforms/controls/printpreviewdialog-control-windows-forms.md) kontroli, [PrintDialog Składnik](../../../../docs/framework/winforms/controls/printdialog-component-windows-forms.md) i [PageSetupDialog — składnik](../../../../docs/framework/winforms/controls/pagesetupdialog-component-windows-forms.md) składniki zapewnienie znanego interfejsu graficznego użytkownikom zapoznanie się z systemu operacyjnego Windows.</span><span class="sxs-lookup"><span data-stu-id="c0885-103">Printing in Windows Forms consists primarily of using the [PrintDocument Component](../../../../docs/framework/winforms/controls/printdocument-component-windows-forms.md) component to enable the user to print, and the [PrintPreviewDialog Control](../../../../docs/framework/winforms/controls/printpreviewdialog-control-windows-forms.md) control, [PrintDialog Component](../../../../docs/framework/winforms/controls/printdialog-component-windows-forms.md) and [PageSetupDialog Component](../../../../docs/framework/winforms/controls/pagesetupdialog-component-windows-forms.md) components to provide a familiar graphical interface to users accustomed to the Windows operating system.</span></span>  
  
 <span data-ttu-id="c0885-104">Zwykle, Utwórz nowe wystąpienie klasy <xref:System.Drawing.Printing.PrintDocument> składnika, ustawić właściwości, które opisują wydruku przy użyciu <xref:System.Drawing.Printing.PrinterSettings> i <xref:System.Drawing.Printing.PageSettings> klasy i wywołanie <xref:System.Drawing.Printing.PrintDocument.Print%2A> metody faktycznie wydrukować dokument.</span><span class="sxs-lookup"><span data-stu-id="c0885-104">Typically, you create a new instance of the <xref:System.Drawing.Printing.PrintDocument> component, set the properties that describe what to print using the <xref:System.Drawing.Printing.PrinterSettings> and <xref:System.Drawing.Printing.PageSettings> classes, and call the <xref:System.Drawing.Printing.PrintDocument.Print%2A> method to actually print the document.</span></span>  
  
 <span data-ttu-id="c0885-105">Podczas drukowania z aplikacji systemu Windows <xref:System.Drawing.Printing.PrintDocument> składnika wyświetli okno dialogowe drukowania przerwania użytkownikom alertu fakt, że występuje drukowanie i umożliwić zadania drukowania do anulowania.</span><span class="sxs-lookup"><span data-stu-id="c0885-105">During the course of printing from a Windows-based application, the <xref:System.Drawing.Printing.PrintDocument> component will show an abort print dialog box to alert users to the fact that printing is occurring and to allow the print job to be canceled.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="c0885-106">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="c0885-106">In This Section</span></span>  
 [<span data-ttu-id="c0885-107">Porady: tworzenie zadań drukowania formularzy standardowego systemu Windows</span><span class="sxs-lookup"><span data-stu-id="c0885-107">How to: Create Standard Windows Forms Print Jobs</span></span>](../../../../docs/framework/winforms/advanced/how-to-create-standard-windows-forms-print-jobs.md)  
 <span data-ttu-id="c0885-108">Wyjaśniono, jak używać <xref:System.Drawing.Printing.PrintDocument> składnik do drukowania za pomocą formularza systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="c0885-108">Explains how to use the <xref:System.Drawing.Printing.PrintDocument> component to print from a Windows Form.</span></span>  
  
 [<span data-ttu-id="c0885-109">Porady: Przechwytywanie danych wejściowych użytkownika ze składnika PrintDialog w czasie wykonywania</span><span class="sxs-lookup"><span data-stu-id="c0885-109">How to: Capture User Input from a PrintDialog at Run Time</span></span>](../../../../docs/framework/winforms/advanced/how-to-capture-user-input-from-a-printdialog-at-run-time.md)  
 <span data-ttu-id="c0885-110">Wyjaśniono, jak i zmodyfikować wybrane opcje wydruku programowo przy użyciu <xref:System.Windows.Forms.PrintDialog> składnika.</span><span class="sxs-lookup"><span data-stu-id="c0885-110">Explains how to modify selected print options programmatically using the <xref:System.Windows.Forms.PrintDialog> component.</span></span>  
  
 [<span data-ttu-id="c0885-111">Porady: wybieranie drukarek podłączonych do komputera użytkownika w formularzach systemu Windows</span><span class="sxs-lookup"><span data-stu-id="c0885-111">How to: Choose the Printers Attached to a User's Computer in Windows Forms</span></span>](../../../../docs/framework/winforms/advanced/how-to-choose-the-printers-attached-to-user-computer-in-windows-forms.md)  
 <span data-ttu-id="c0885-112">W tym artykule opisano, zmiana drukarki na drukowanie za pomocą <xref:System.Windows.Forms.PrintDialog> składnika w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="c0885-112">Describes changing the printer to print to using the <xref:System.Windows.Forms.PrintDialog> component at run time.</span></span>  
  
 [<span data-ttu-id="c0885-113">Porady: drukowanie grafiki w formularzach systemu Windows</span><span class="sxs-lookup"><span data-stu-id="c0885-113">How to: Print Graphics in Windows Forms</span></span>](../../../../docs/framework/winforms/advanced/how-to-print-graphics-in-windows-forms.md)  
 <span data-ttu-id="c0885-114">Opis wysyłania grafiki do drukarki.</span><span class="sxs-lookup"><span data-stu-id="c0885-114">Describes sending graphics to the printer.</span></span>  
  
 [<span data-ttu-id="c0885-115">Porady: drukowanie pliku tekstowego wiele stron w formularzach systemu Windows</span><span class="sxs-lookup"><span data-stu-id="c0885-115">How to: Print a Multi-Page Text File in Windows Forms</span></span>](../../../../docs/framework/winforms/advanced/how-to-print-a-multi-page-text-file-in-windows-forms.md)  
 <span data-ttu-id="c0885-116">Opis wysyłania tekstu do drukarki.</span><span class="sxs-lookup"><span data-stu-id="c0885-116">Describes sending text to the printer.</span></span>  
  
 [<span data-ttu-id="c0885-117">Porady: zadań drukowania formularzy Windows ukończone</span><span class="sxs-lookup"><span data-stu-id="c0885-117">How to: Complete Windows Forms Print Jobs</span></span>](../../../../docs/framework/winforms/advanced/how-to-complete-windows-forms-print-jobs.md)  
 <span data-ttu-id="c0885-118">Wyjaśniono, jak powiadamiania użytkowników do wykonania zadania drukowania.</span><span class="sxs-lookup"><span data-stu-id="c0885-118">Explains how to alert users to the completion of a print job.</span></span>  
  
 [<span data-ttu-id="c0885-119">Porady: Drukowanie formularza systemu Windows</span><span class="sxs-lookup"><span data-stu-id="c0885-119">How to: Print a Windows Form</span></span>](../../../../docs/framework/winforms/advanced/how-to-print-a-windows-form.md)  
 <span data-ttu-id="c0885-120">Pokazuje, jak wydrukować kopię bieżącego formularza.</span><span class="sxs-lookup"><span data-stu-id="c0885-120">Shows how to print a copy of the current form.</span></span>  
  
 [<span data-ttu-id="c0885-121">Porady: drukowanie w formularzach systemu Windows przy użyciu podglądu wydruku</span><span class="sxs-lookup"><span data-stu-id="c0885-121">How to: Print in Windows Forms Using Print Preview</span></span>](../../../../docs/framework/winforms/advanced/how-to-print-in-windows-forms-using-print-preview.md)  
 <span data-ttu-id="c0885-122">Przedstawia sposób użycia <xref:System.Windows.Forms.PrintPreviewDialog> do drukowania dokumentu.</span><span class="sxs-lookup"><span data-stu-id="c0885-122">Shows how to use a <xref:System.Windows.Forms.PrintPreviewDialog> for printing a document.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="c0885-123">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="c0885-123">Related Sections</span></span>  
 [<span data-ttu-id="c0885-124">PrintDocument — składnik</span><span class="sxs-lookup"><span data-stu-id="c0885-124">PrintDocument Component</span></span>](../../../../docs/framework/winforms/controls/printdocument-component-windows-forms.md)  
 <span data-ttu-id="c0885-125">Wyjaśniono, użycie <xref:System.Drawing.Printing.PrintDocument> składnika.</span><span class="sxs-lookup"><span data-stu-id="c0885-125">Explains usage of the <xref:System.Drawing.Printing.PrintDocument> component.</span></span>  
  
 [<span data-ttu-id="c0885-126">Printdialog — składnik</span><span class="sxs-lookup"><span data-stu-id="c0885-126">PrintDialog Component</span></span>](../../../../docs/framework/winforms/controls/printdialog-component-windows-forms.md)  
 <span data-ttu-id="c0885-127">Wyjaśniono, użycie <xref:System.Windows.Forms.PrintDialog> składnika.</span><span class="sxs-lookup"><span data-stu-id="c0885-127">Explains usage of the <xref:System.Windows.Forms.PrintDialog> component.</span></span>  
  
 [<span data-ttu-id="c0885-128">Printpreviewdialog — formant</span><span class="sxs-lookup"><span data-stu-id="c0885-128">PrintPreviewDialog Control</span></span>](../../../../docs/framework/winforms/controls/printpreviewdialog-control-windows-forms.md)  
 <span data-ttu-id="c0885-129">Wyjaśniono, użycie <xref:System.Windows.Forms.PrintPreviewDialog> formantu.</span><span class="sxs-lookup"><span data-stu-id="c0885-129">Explains usage of the <xref:System.Windows.Forms.PrintPreviewDialog> control.</span></span>  
  
 [<span data-ttu-id="c0885-130">PageSetupDialog — składnik</span><span class="sxs-lookup"><span data-stu-id="c0885-130">PageSetupDialog Component</span></span>](../../../../docs/framework/winforms/controls/pagesetupdialog-component-windows-forms.md)  
 <span data-ttu-id="c0885-131">Wyjaśniono, użycie <xref:System.Windows.Forms.PageSetupDialog> składnika.</span><span class="sxs-lookup"><span data-stu-id="c0885-131">Explains usage of the <xref:System.Windows.Forms.PageSetupDialog> component.</span></span>  
  
 <xref:System.Drawing.Printing>  
 <span data-ttu-id="c0885-132">Zawiera opis klas w <xref:System.Drawing.Printing> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="c0885-132">Describes the classes in the <xref:System.Drawing.Printing> namespace.</span></span>
