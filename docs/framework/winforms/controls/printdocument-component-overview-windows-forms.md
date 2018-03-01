---
title: "PrintDocument — Informacje o składniku (Formularze systemu Windows)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- PrintDocument
helpviewer_keywords:
- PrintDocument component [Windows Forms], about PrintDocument component
- printing [Windows Forms], PrintDocument component
ms.assetid: b59b4b60-dce5-42ca-8421-3a54a2f7bab0
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 414a7972550558b40403b7f4cbfd9a49194666be
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="printdocument-component-overview-windows-forms"></a><span data-ttu-id="67cc4-102">PrintDocument — Informacje o składniku (Formularze systemu Windows)</span><span class="sxs-lookup"><span data-stu-id="67cc4-102">PrintDocument Component Overview (Windows Forms)</span></span>
<span data-ttu-id="67cc4-103">Formularze systemu Windows [PrintDocument —](../../../../docs/framework/winforms/controls/printdocument-component-windows-forms.md) składnika jest używane do definiowania właściwości, które opisują wydruku i możliwość drukowania dokumentów w aplikacjach opartych na systemie Windows.</span><span class="sxs-lookup"><span data-stu-id="67cc4-103">The Windows Forms [PrintDocument](../../../../docs/framework/winforms/controls/printdocument-component-windows-forms.md) component is used to set the properties that describe what to print and the ability to print the document within Windows-based applications.</span></span> <span data-ttu-id="67cc4-104">Mogą być używane w połączeniu z [PrintDialog](../../../../docs/framework/winforms/controls/printdialog-component-windows-forms.md) składnik, aby mieć możliwość kontrolowania wszystkich aspektów drukowanie dokumentów.</span><span class="sxs-lookup"><span data-stu-id="67cc4-104">It can be used in conjunction with the [PrintDialog](../../../../docs/framework/winforms/controls/printdialog-component-windows-forms.md) component to be in control of all aspects of document printing.</span></span>  
  
## <a name="working-with-the-printdocument-component"></a><span data-ttu-id="67cc4-105">Praca z PrintDocument — składnik</span><span class="sxs-lookup"><span data-stu-id="67cc4-105">Working with the PrintDocument Component</span></span>  
 <span data-ttu-id="67cc4-106">Dwa główne scenariusze, które obejmują <xref:System.Drawing.Printing.PrintDocument> składnika są:</span><span class="sxs-lookup"><span data-stu-id="67cc4-106">Two of the main scenarios that involve the <xref:System.Drawing.Printing.PrintDocument> component are:</span></span>  
  
-   <span data-ttu-id="67cc4-107">Proste zadania drukowania, takie jak drukowania pliku tekstowego indywidualnych.</span><span class="sxs-lookup"><span data-stu-id="67cc4-107">Simple print jobs, such as printing an individual text file.</span></span> <span data-ttu-id="67cc4-108">W takim przypadku należy dodać <xref:System.Drawing.Printing.PrintDocument> składnik do formularza systemu Windows, następnie dodanie logiki programowania, która wyświetla plik w <xref:System.Drawing.Printing.PrintDocument.PrintPage> obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="67cc4-108">In such a case you would add the <xref:System.Drawing.Printing.PrintDocument> component to a Windows Form, then add programming logic that prints a file in the <xref:System.Drawing.Printing.PrintDocument.PrintPage> event handler.</span></span> <span data-ttu-id="67cc4-109">Logika programowania powinien kulminacyjny z <xref:System.Drawing.Printing.PrintDocument.Print%2A> metodę, aby wydrukować dokument.</span><span class="sxs-lookup"><span data-stu-id="67cc4-109">The programming logic should culminate with the <xref:System.Drawing.Printing.PrintDocument.Print%2A> method to print the document.</span></span> <span data-ttu-id="67cc4-110">Ta metoda wysyła <xref:System.Drawing.Graphics> obiektów zawartych w <xref:System.Drawing.Printing.PrintPageEventArgs.Graphics%2A> właściwość <xref:System.Drawing.Printing.PrintPageEventArgs> klasy do drukarki.</span><span class="sxs-lookup"><span data-stu-id="67cc4-110">This method sends a <xref:System.Drawing.Graphics> object, contained in the <xref:System.Drawing.Printing.PrintPageEventArgs.Graphics%2A> property of the <xref:System.Drawing.Printing.PrintPageEventArgs> class, to the printer.</span></span> <span data-ttu-id="67cc4-111">Przykład pokazujący sposób drukowanie dokumentu tekstu przy użyciu <xref:System.Drawing.Printing.PrintDocument> składników, zobacz [porady: drukowanie wielu stron pliku tekstowego w formularzach systemu Windows](../../../../docs/framework/winforms/advanced/how-to-print-a-multi-page-text-file-in-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="67cc4-111">For an example that shows how to print a text document using the <xref:System.Drawing.Printing.PrintDocument> component, see [How to: Print a Multi-Page Text File in Windows Forms](../../../../docs/framework/winforms/advanced/how-to-print-a-multi-page-text-file-in-windows-forms.md).</span></span>  
  
-   <span data-ttu-id="67cc4-112">Bardziej złożone zadania drukowania, takie jak sytuacji, w którym można ponowne wykorzystanie logiki drukowania, które zostały zapisane.</span><span class="sxs-lookup"><span data-stu-id="67cc4-112">More complex print jobs, such as a situation where you will want to reuse printing logic you have written.</span></span> <span data-ttu-id="67cc4-113">W takim przypadku może pochodzić z nowego składnika <xref:System.Drawing.Printing.PrintDocument> składnika i zastąpienie (zobacz [zastępuje](~/docs/visual-basic/language-reference/modifiers/overrides.md) w języku Visual Basic lub [zastąpienia](~/docs/csharp/language-reference/keywords/override.md) dla C#) <xref:System.Drawing.Printing.PrintDocument.PrintPage> zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="67cc4-113">In such a case you would derive a new component from the <xref:System.Drawing.Printing.PrintDocument> component and override (see [Overrides](~/docs/visual-basic/language-reference/modifiers/overrides.md) for Visual Basic or [override](~/docs/csharp/language-reference/keywords/override.md) for C#) the <xref:System.Drawing.Printing.PrintDocument.PrintPage> event.</span></span>  
  
 <span data-ttu-id="67cc4-114">Gdy jest ona dodawana do formularza, <xref:System.Drawing.Printing.PrintDocument> składnika jest wyświetlana na pasku w dolnej części Projektant formularzy systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="67cc4-114">When it is added to a form, the <xref:System.Drawing.Printing.PrintDocument> component appears in the tray at the bottom of the Windows Forms Designer.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="67cc4-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="67cc4-115">See Also</span></span>  
 <xref:System.Drawing.Graphics>  
 <xref:System.Drawing.Printing.PrintDocument>  
 [<span data-ttu-id="67cc4-116">Obsługa drukowania w formularzach Windows Forms</span><span class="sxs-lookup"><span data-stu-id="67cc4-116">Windows Forms Print Support</span></span>](../../../../docs/framework/winforms/advanced/windows-forms-print-support.md)  
 [<span data-ttu-id="67cc4-117">PrintDocument, składnik</span><span class="sxs-lookup"><span data-stu-id="67cc4-117">PrintDocument Component</span></span>](../../../../docs/framework/winforms/controls/printdocument-component-windows-forms.md)
