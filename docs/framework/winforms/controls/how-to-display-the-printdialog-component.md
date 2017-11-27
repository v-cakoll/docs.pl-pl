---
title: "Porady: wyświetlanie składnika PrintDialog"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Print dialog box [Windows Forms], displaying
- PrintDialog component [Windows Forms], displaying
- printing [Windows Forms], displaying print dialog box
ms.assetid: 745a8db7-0526-4b21-b09d-18e13ed32014
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 7e1162a4e926d5be35f8f7bb7cdeb92264f293aa
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-display-the-printdialog-component"></a><span data-ttu-id="c805b-102">Porady: wyświetlanie składnika PrintDialog</span><span class="sxs-lookup"><span data-stu-id="c805b-102">How to: Display the PrintDialog Component</span></span>
<span data-ttu-id="c805b-103"><xref:System.Windows.Forms.PrintDialog> Składnik jest standardowe okno dialogowe wydruku systemu Windows, który wielu użytkowników należy zapoznać się z.</span><span class="sxs-lookup"><span data-stu-id="c805b-103">The <xref:System.Windows.Forms.PrintDialog> component is the standard Windows print dialog box that many of your users will be familiar with.</span></span> <span data-ttu-id="c805b-104">Ponieważ użytkownicy będą natychmiast doświadczenia z nim, jest przydatne w przypadku użycia <xref:System.Windows.Forms.PrintDialog> składnika.</span><span class="sxs-lookup"><span data-stu-id="c805b-104">Because your users will be immediately comfortable with it, it would be beneficial for you to use the <xref:System.Windows.Forms.PrintDialog> component.</span></span>  
  
### <a name="to-display-the-printdialog-component"></a><span data-ttu-id="c805b-105">Aby wyświetlić składnika PrintDialog</span><span class="sxs-lookup"><span data-stu-id="c805b-105">To display the PrintDialog component</span></span>  
  
-   <span data-ttu-id="c805b-106">Wywołanie <xref:System.Windows.Forms.Form.ShowDialog%2A> metodę z kodu aplikacji.</span><span class="sxs-lookup"><span data-stu-id="c805b-106">Call the <xref:System.Windows.Forms.Form.ShowDialog%2A> method from within the code of your application.</span></span>  
  
     <span data-ttu-id="c805b-107">Gdy składnik jest wyświetlany, użytkowników będzie korzystać z niego, ustawianie właściwości zadania drukowania.</span><span class="sxs-lookup"><span data-stu-id="c805b-107">Once the component is shown, users will interact with it, setting the properties of the print job.</span></span> <span data-ttu-id="c805b-108">Są one zapisane w <!--zz <xref:System.Drawing.Printing.PrinterSetting>--> `PrinterSetting` klasy (i <xref:System.Drawing.Printing.PageSettings> klasy, jeśli użytkownik uzyskuje dostęp do [PageSetupDialog — składnik](../../../../docs/framework/winforms/controls/pagesetupdialog-component-windows-forms.md) za pośrednictwem <xref:System.Windows.Forms.PrintDialog> składnika) skojarzony z tym zadania drukowania.</span><span class="sxs-lookup"><span data-stu-id="c805b-108">These are saved in the <!--zz <xref:System.Drawing.Printing.PrinterSetting>--> `PrinterSetting` class (and the <xref:System.Drawing.Printing.PageSettings> class, if the user accesses the [PageSetupDialog Component](../../../../docs/framework/winforms/controls/pagesetupdialog-component-windows-forms.md) through the <xref:System.Windows.Forms.PrintDialog> component) associated with that print job.</span></span> <span data-ttu-id="c805b-109">Następnie można wprowadzić wywołań właściwości zestawu ustalić szczegółowe informacje na temat zadania drukowania.</span><span class="sxs-lookup"><span data-stu-id="c805b-109">You can then make calls to the properties they set to determine the specifics of the print job.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c805b-110">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c805b-110">See Also</span></span>  
 [<span data-ttu-id="c805b-111">Porady: tworzenie zadań drukowania formularzy standardowego systemu Windows</span><span class="sxs-lookup"><span data-stu-id="c805b-111">How to: Create Standard Windows Forms Print Jobs</span></span>](../../../../docs/framework/winforms/advanced/how-to-create-standard-windows-forms-print-jobs.md)  
 [<span data-ttu-id="c805b-112">Porady: Przechwytywanie danych wejściowych użytkownika ze składnika PrintDialog w czasie wykonywania</span><span class="sxs-lookup"><span data-stu-id="c805b-112">How to: Capture User Input from a PrintDialog at Run Time</span></span>](../../../../docs/framework/winforms/advanced/how-to-capture-user-input-from-a-printdialog-at-run-time.md)  
 [<span data-ttu-id="c805b-113">Printpreviewdialog — formant</span><span class="sxs-lookup"><span data-stu-id="c805b-113">PrintPreviewDialog Control</span></span>](../../../../docs/framework/winforms/controls/printpreviewdialog-control-windows-forms.md)  
 [<span data-ttu-id="c805b-114">Printdialog — składnik</span><span class="sxs-lookup"><span data-stu-id="c805b-114">PrintDialog Component</span></span>](../../../../docs/framework/winforms/controls/printdialog-component-windows-forms.md)  
 [<span data-ttu-id="c805b-115">Obsługa drukowania w formularzach systemu Windows</span><span class="sxs-lookup"><span data-stu-id="c805b-115">Windows Forms Print Support</span></span>](../../../../docs/framework/winforms/advanced/windows-forms-print-support.md)  
 [<span data-ttu-id="c805b-116">Formanty formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="c805b-116">Windows Forms Controls</span></span>](../../../../docs/framework/winforms/controls/index.md)
