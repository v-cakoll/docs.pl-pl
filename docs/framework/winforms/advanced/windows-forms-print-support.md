---
title: Obsługa drukowania w formularzach systemu Windows
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms, printing
- printing [Windows Forms]
- forms [Windows Forms], printing (using designer)
- printing [Windows Forms], Windows Forms, support
- printing [Windows Forms], print support
ms.assetid: a4a2960c-eb70-48e2-b641-cfb222704e46
ms.openlocfilehash: 8e008f2cb4b2f32cdba676e68d9fd790530e2b06
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62011856"
---
# <a name="windows-forms-print-support"></a><span data-ttu-id="42ce5-102">Obsługa drukowania w formularzach systemu Windows</span><span class="sxs-lookup"><span data-stu-id="42ce5-102">Windows Forms Print Support</span></span>
<span data-ttu-id="42ce5-103">Drukowanie w formularzach Windows Forms składa się przede wszystkim za pomocą [PrintDocument, składnik](../controls/printdocument-component-windows-forms.md) składnik, aby umożliwić użytkownikowi drukowanie i [PrintPreviewDialog, kontrolka](../controls/printpreviewdialog-control-windows-forms.md) kontroli [PrintDialog Składnik](../controls/printdialog-component-windows-forms.md) i [PageSetupDialog, składnik](../controls/pagesetupdialog-component-windows-forms.md) składniki zapewnienie znanego interfejsu graficznego użytkownikom zapoznanie się z systemu operacyjnego Windows.</span><span class="sxs-lookup"><span data-stu-id="42ce5-103">Printing in Windows Forms consists primarily of using the [PrintDocument Component](../controls/printdocument-component-windows-forms.md) component to enable the user to print, and the [PrintPreviewDialog Control](../controls/printpreviewdialog-control-windows-forms.md) control, [PrintDialog Component](../controls/printdialog-component-windows-forms.md) and [PageSetupDialog Component](../controls/pagesetupdialog-component-windows-forms.md) components to provide a familiar graphical interface to users accustomed to the Windows operating system.</span></span>  
  
 <span data-ttu-id="42ce5-104">Zwykle, Utwórz nowe wystąpienie klasy <xref:System.Drawing.Printing.PrintDocument> składnika, ustawić właściwości, które opisują, jakie drukowanie przy użyciu <xref:System.Drawing.Printing.PrinterSettings> i <xref:System.Drawing.Printing.PageSettings> klasy i wywołania <xref:System.Drawing.Printing.PrintDocument.Print%2A> metodę, aby faktycznie wydrukować dokument.</span><span class="sxs-lookup"><span data-stu-id="42ce5-104">Typically, you create a new instance of the <xref:System.Drawing.Printing.PrintDocument> component, set the properties that describe what to print using the <xref:System.Drawing.Printing.PrinterSettings> and <xref:System.Drawing.Printing.PageSettings> classes, and call the <xref:System.Drawing.Printing.PrintDocument.Print%2A> method to actually print the document.</span></span>  
  
 <span data-ttu-id="42ce5-105">W trakcie drukowaniem z aplikacji z systemem Windows <xref:System.Drawing.Printing.PrintDocument> składnika pokaże dialogowe przerwania ostrzegać użytkowników fakt, że jest wykonywane drukowanie i umożliwić zadania drukowania, zostaną anulowane.</span><span class="sxs-lookup"><span data-stu-id="42ce5-105">During the course of printing from a Windows-based application, the <xref:System.Drawing.Printing.PrintDocument> component will show an abort print dialog box to alert users to the fact that printing is occurring and to allow the print job to be canceled.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="42ce5-106">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="42ce5-106">In This Section</span></span>  
 [<span data-ttu-id="42ce5-107">Instrukcje: Tworzenie zadań drukowania formularzy Windows Standard</span><span class="sxs-lookup"><span data-stu-id="42ce5-107">How to: Create Standard Windows Forms Print Jobs</span></span>](how-to-create-standard-windows-forms-print-jobs.md)  
 <span data-ttu-id="42ce5-108">Opis sposobu użycia <xref:System.Drawing.Printing.PrintDocument> składnik do drukowania z formularza Windows.</span><span class="sxs-lookup"><span data-stu-id="42ce5-108">Explains how to use the <xref:System.Drawing.Printing.PrintDocument> component to print from a Windows Form.</span></span>  
  
 [<span data-ttu-id="42ce5-109">Instrukcje: Przechwytywanie danych wejściowych użytkownika ze składnika PrintDialog w czasie wykonywania</span><span class="sxs-lookup"><span data-stu-id="42ce5-109">How to: Capture User Input from a PrintDialog at Run Time</span></span>](how-to-capture-user-input-from-a-printdialog-at-run-time.md)  
 <span data-ttu-id="42ce5-110">Wyjaśnia sposób modyfikowania wybranych opcji drukowania, programowo przy użyciu <xref:System.Windows.Forms.PrintDialog> składnika.</span><span class="sxs-lookup"><span data-stu-id="42ce5-110">Explains how to modify selected print options programmatically using the <xref:System.Windows.Forms.PrintDialog> component.</span></span>  
  
 [<span data-ttu-id="42ce5-111">Instrukcje: Wybieranie drukarek podłączonych do komputera użytkownika w formularzach Windows Forms</span><span class="sxs-lookup"><span data-stu-id="42ce5-111">How to: Choose the Printers Attached to a User's Computer in Windows Forms</span></span>](how-to-choose-the-printers-attached-to-user-computer-in-windows-forms.md)  
 <span data-ttu-id="42ce5-112">W tym artykule opisano, zmienianie drukarki do wydrukowania za pomocą <xref:System.Windows.Forms.PrintDialog> składnika w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="42ce5-112">Describes changing the printer to print to using the <xref:System.Windows.Forms.PrintDialog> component at run time.</span></span>  
  
 [<span data-ttu-id="42ce5-113">Instrukcje: Drukowanie grafiki w formularzach Windows Forms</span><span class="sxs-lookup"><span data-stu-id="42ce5-113">How to: Print Graphics in Windows Forms</span></span>](how-to-print-graphics-in-windows-forms.md)  
 <span data-ttu-id="42ce5-114">W tym artykule opisano wysyłanie grafiki do drukarki.</span><span class="sxs-lookup"><span data-stu-id="42ce5-114">Describes sending graphics to the printer.</span></span>  
  
 [<span data-ttu-id="42ce5-115">Instrukcje: Podglądu wydruku w formularzach Windows Forms</span><span class="sxs-lookup"><span data-stu-id="42ce5-115">How to: Print a Multi-Page Text File in Windows Forms</span></span>](how-to-print-a-multi-page-text-file-in-windows-forms.md)  
 <span data-ttu-id="42ce5-116">W tym artykule opisano wysyłanie tekstu do drukarki.</span><span class="sxs-lookup"><span data-stu-id="42ce5-116">Describes sending text to the printer.</span></span>  
  
 [<span data-ttu-id="42ce5-117">Instrukcje: Zadań drukowania formularzy Windows ukończone</span><span class="sxs-lookup"><span data-stu-id="42ce5-117">How to: Complete Windows Forms Print Jobs</span></span>](how-to-complete-windows-forms-print-jobs.md)  
 <span data-ttu-id="42ce5-118">Wyjaśnia, jak powiadamia użytkowników do wykonania zadania drukowania.</span><span class="sxs-lookup"><span data-stu-id="42ce5-118">Explains how to alert users to the completion of a print job.</span></span>  
  
 [<span data-ttu-id="42ce5-119">Instrukcje: Drukowanie formularza Windows</span><span class="sxs-lookup"><span data-stu-id="42ce5-119">How to: Print a Windows Form</span></span>](how-to-print-a-windows-form.md)  
 <span data-ttu-id="42ce5-120">Pokazuje jak drukować kopię bieżącego formularza.</span><span class="sxs-lookup"><span data-stu-id="42ce5-120">Shows how to print a copy of the current form.</span></span>  
  
 [<span data-ttu-id="42ce5-121">Instrukcje: Drukowanie w formularzach Windows Forms przy użyciu podglądu wydruku</span><span class="sxs-lookup"><span data-stu-id="42ce5-121">How to: Print in Windows Forms Using Print Preview</span></span>](how-to-print-in-windows-forms-using-print-preview.md)  
 <span data-ttu-id="42ce5-122">Ilustruje sposób używania <xref:System.Windows.Forms.PrintPreviewDialog> do drukowania dokumentu.</span><span class="sxs-lookup"><span data-stu-id="42ce5-122">Shows how to use a <xref:System.Windows.Forms.PrintPreviewDialog> for printing a document.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="42ce5-123">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="42ce5-123">Related Sections</span></span>  
 [<span data-ttu-id="42ce5-124">PrintDocument, składnik</span><span class="sxs-lookup"><span data-stu-id="42ce5-124">PrintDocument Component</span></span>](../controls/printdocument-component-windows-forms.md)  
 <span data-ttu-id="42ce5-125">Wyjaśnia, użycie <xref:System.Drawing.Printing.PrintDocument> składnika.</span><span class="sxs-lookup"><span data-stu-id="42ce5-125">Explains usage of the <xref:System.Drawing.Printing.PrintDocument> component.</span></span>  
  
 [<span data-ttu-id="42ce5-126">PrintDialog, składnik</span><span class="sxs-lookup"><span data-stu-id="42ce5-126">PrintDialog Component</span></span>](../controls/printdialog-component-windows-forms.md)  
 <span data-ttu-id="42ce5-127">Wyjaśnia, użycie <xref:System.Windows.Forms.PrintDialog> składnika.</span><span class="sxs-lookup"><span data-stu-id="42ce5-127">Explains usage of the <xref:System.Windows.Forms.PrintDialog> component.</span></span>  
  
 [<span data-ttu-id="42ce5-128">PrintPreviewDialog, kontrolka</span><span class="sxs-lookup"><span data-stu-id="42ce5-128">PrintPreviewDialog Control</span></span>](../controls/printpreviewdialog-control-windows-forms.md)  
 <span data-ttu-id="42ce5-129">Wyjaśnia, użycie <xref:System.Windows.Forms.PrintPreviewDialog> kontroli.</span><span class="sxs-lookup"><span data-stu-id="42ce5-129">Explains usage of the <xref:System.Windows.Forms.PrintPreviewDialog> control.</span></span>  
  
 [<span data-ttu-id="42ce5-130">PageSetupDialog, składnik</span><span class="sxs-lookup"><span data-stu-id="42ce5-130">PageSetupDialog Component</span></span>](../controls/pagesetupdialog-component-windows-forms.md)  
 <span data-ttu-id="42ce5-131">Wyjaśnia, użycie <xref:System.Windows.Forms.PageSetupDialog> składnika.</span><span class="sxs-lookup"><span data-stu-id="42ce5-131">Explains usage of the <xref:System.Windows.Forms.PageSetupDialog> component.</span></span>  
  
 <xref:System.Drawing.Printing>  
 <span data-ttu-id="42ce5-132">Opisuje klasy w <xref:System.Drawing.Printing> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="42ce5-132">Describes the classes in the <xref:System.Drawing.Printing> namespace.</span></span>
