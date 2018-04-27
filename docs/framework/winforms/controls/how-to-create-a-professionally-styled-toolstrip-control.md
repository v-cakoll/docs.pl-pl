---
title: 'Porady: tworzenie profesjonalnego formantu ToolStrip'
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-winforms
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- toolbars [Windows Forms]
- ToolStripProfessionalRenderer class [Windows Forms]
- ToolStripRenderer class [Windows Forms]
- ToolStrip control [Windows Forms]
ms.assetid: c208b2f6-8105-474b-9075-d582e1792870
caps.latest.revision: 9
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 7ab44faf9e95a2ff5f1957bd6f46fc62944a4f44
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-create-a-professionally-styled-toolstrip-control"></a><span data-ttu-id="09f5c-102">Porady: tworzenie profesjonalnego formantu ToolStrip</span><span class="sxs-lookup"><span data-stu-id="09f5c-102">How to: Create a Professionally Styled ToolStrip Control</span></span>
<span data-ttu-id="09f5c-103">Umożliwia aplikacji <xref:System.Windows.Forms.ToolStrip> steruje profesjonalny wygląd i zachowanie (wygląd i działanie) przez pisanie własnych klas pochodnych <xref:System.Windows.Forms.ToolStripProfessionalRenderer> typu.</span><span class="sxs-lookup"><span data-stu-id="09f5c-103">You can give your application’s <xref:System.Windows.Forms.ToolStrip> controls a professional appearance and behavior (look and feel) by writing your own class derived from the <xref:System.Windows.Forms.ToolStripProfessionalRenderer> type.</span></span>  
  
 <span data-ttu-id="09f5c-104">Brak kompleksową obsługę tej funkcji w [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)].</span><span class="sxs-lookup"><span data-stu-id="09f5c-104">There is extensive support for this feature in [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)].</span></span>  
  
 <span data-ttu-id="09f5c-105">Zobacz [wskazówki: tworzenie profesjonalnego formantu ToolStrip](../../../../docs/framework/winforms/controls/walkthrough-creating-a-professionally-styled-toolstrip-control.md).</span><span class="sxs-lookup"><span data-stu-id="09f5c-105">See [Walkthrough: Creating a Professionally Styled ToolStrip Control](../../../../docs/framework/winforms/controls/walkthrough-creating-a-professionally-styled-toolstrip-control.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="09f5c-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="09f5c-106">Example</span></span>  
 <span data-ttu-id="09f5c-107">Poniższy przykład kodu pokazuje sposób użycia <xref:System.Windows.Forms.ToolStrip> służy do tworzenia złożonych kontrolek, które symuluje **okienka nawigacji** udostępniane przez Microsoft Outlook®.</span><span class="sxs-lookup"><span data-stu-id="09f5c-107">The following code example demonstrates how to use <xref:System.Windows.Forms.ToolStrip> controls to create a composite control that mimics the **Navigation Pane** provided by Microsoft® Outlook®.</span></span>  
  
 [!code-csharp[System.Windows.Forms.ToolStrip.StackView#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StackView/CS/StackView.cs#1)]
 [!code-vb[System.Windows.Forms.ToolStrip.StackView#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StackView/VB/StackView.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="09f5c-108">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="09f5c-108">Compiling the Code</span></span>  
 <span data-ttu-id="09f5c-109">Ten przykład wymaga:</span><span class="sxs-lookup"><span data-stu-id="09f5c-109">This example requires:</span></span>  
  
-   <span data-ttu-id="09f5c-110">Odwołania do zestawów System.Drawing i System.Windows.Forms.</span><span class="sxs-lookup"><span data-stu-id="09f5c-110">References to the System.Drawing and System.Windows.Forms assemblies.</span></span>  
  
 <span data-ttu-id="09f5c-111">Uzyskać informacje o kompilowaniu w tym przykładzie z wiersza polecenia dla programu Visual Basic lub Visual C#, zobacz [tworzenie z wiersza polecenia](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) lub [kompilowania z wiersza polecenia csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="09f5c-111">For information about building this example from the command line for Visual Basic or Visual C#, see [Building from the Command Line](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="09f5c-112">Można także utworzyć tym przykładzie [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] przez wklejenie kodu do nowego projektu.</span><span class="sxs-lookup"><span data-stu-id="09f5c-112">You can also build this example in [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] by pasting the code into a new project.</span></span>  <span data-ttu-id="09f5c-113">Zobacz też [wskazówki: tworzenie profesjonalnego styl formantu ToolStrip](http://msdn.microsoft.com/library/ms233664\(v=vs.110\)).</span><span class="sxs-lookup"><span data-stu-id="09f5c-113">Also see [Walkthrough: Creating a Professionally Styled ToolStrip Control](http://msdn.microsoft.com/library/ms233664\(v=vs.110\)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="09f5c-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="09f5c-114">See Also</span></span>  
 <xref:System.Windows.Forms.MenuStrip>  
 <xref:System.Windows.Forms.ToolStrip>  
 <xref:System.Windows.Forms.StatusStrip>  
 [<span data-ttu-id="09f5c-115">ToolStrip, kontrolka</span><span class="sxs-lookup"><span data-stu-id="09f5c-115">ToolStrip Control</span></span>](../../../../docs/framework/winforms/controls/toolstrip-control-windows-forms.md)  
 [<span data-ttu-id="09f5c-116">Instrukcje: zapewnianie elementów menu standardowego dla formularza</span><span class="sxs-lookup"><span data-stu-id="09f5c-116">How to: Provide Standard Menu Items to a Form</span></span>](../../../../docs/framework/winforms/controls/how-to-provide-standard-menu-items-to-a-form.md)
