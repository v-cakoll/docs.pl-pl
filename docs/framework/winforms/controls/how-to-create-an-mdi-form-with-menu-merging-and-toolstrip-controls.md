---
title: 'Porady: tworzenie formularza MDI za pomocą scalania menu i formantów ToolStrip'
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
- ToolStripPanel control [Windows Forms]
- ToolStrip control [Windows Forms]
- MenuStrip control [Windows Forms]
ms.assetid: 64992ed9-44af-4baf-b45f-863e6ab35711
caps.latest.revision: 6
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 645efb8069d56003038189add5bd430f6daf4a97
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-create-an-mdi-form-with-menu-merging-and-toolstrip-controls"></a><span data-ttu-id="6434a-102">Porady: tworzenie formularza MDI za pomocą scalania menu i formantów ToolStrip</span><span class="sxs-lookup"><span data-stu-id="6434a-102">How to: Create an MDI Form with Menu Merging and ToolStrip Controls</span></span>
<span data-ttu-id="6434a-103"><xref:System.Windows.Forms?displayProperty=nameWithType> Przestrzeń nazw obsługuje wiele aplikacji dokumentu interfejsu (MDI) i <xref:System.Windows.Forms.MenuStrip> sterowanie obsługuje scalania menu.</span><span class="sxs-lookup"><span data-stu-id="6434a-103">The <xref:System.Windows.Forms?displayProperty=nameWithType> namespace supports multiple document interface (MDI) applications, and the <xref:System.Windows.Forms.MenuStrip> control supports menu merging.</span></span> <span data-ttu-id="6434a-104">Formularze MDI może również <xref:System.Windows.Forms.ToolStrip> kontrolki.</span><span class="sxs-lookup"><span data-stu-id="6434a-104">MDI forms can also <xref:System.Windows.Forms.ToolStrip> controls.</span></span>  
  
 <span data-ttu-id="6434a-105">Brak kompleksową obsługę tej funkcji w [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)].</span><span class="sxs-lookup"><span data-stu-id="6434a-105">There is extensive support for this feature in [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)].</span></span>  
  
 <span data-ttu-id="6434a-106">Zobacz też [wskazówki: Tworzenie formularza MDI za pomocą scalania Menu i formantami ToolStrip](http://msdn.microsoft.com/library/ms233676\(v=vs.110\)).</span><span class="sxs-lookup"><span data-stu-id="6434a-106">Also see [Walkthrough: Creating an MDI Form with Menu Merging and ToolStrip Controls](http://msdn.microsoft.com/library/ms233676\(v=vs.110\)).</span></span>  
  
## <a name="example"></a><span data-ttu-id="6434a-107">Przykład</span><span class="sxs-lookup"><span data-stu-id="6434a-107">Example</span></span>  
 <span data-ttu-id="6434a-108">Poniższy przykład kodu pokazuje sposób użycia <xref:System.Windows.Forms.ToolStripPanel> formantów z formularza MDI.</span><span class="sxs-lookup"><span data-stu-id="6434a-108">The following code example demonstrates how to use <xref:System.Windows.Forms.ToolStripPanel> controls with an MDI form.</span></span> <span data-ttu-id="6434a-109">Formularz obsługuje również menu scalanie z menu podrzędnego.</span><span class="sxs-lookup"><span data-stu-id="6434a-109">The form also supports menu merging with child menus.</span></span>  
  
 [!code-csharp[System.Windows.Forms.ToolStrip.MdiForm#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.MdiForm/CS/Form1.cs#1)]
 [!code-vb[System.Windows.Forms.ToolStrip.MdiForm#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.MdiForm/VB/Form1.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="6434a-110">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="6434a-110">Compiling the Code</span></span>  
 <span data-ttu-id="6434a-111">W tym przykładzie kodu wymaga:</span><span class="sxs-lookup"><span data-stu-id="6434a-111">This code example requires:</span></span>  
  
-   <span data-ttu-id="6434a-112">Odwołania do zestawów System.Drawing i System.Windows.Forms.</span><span class="sxs-lookup"><span data-stu-id="6434a-112">References to the System.Drawing and System.Windows.Forms assemblies.</span></span>  
  
 <span data-ttu-id="6434a-113">Uzyskać informacje o kompilowaniu w tym przykładzie z wiersza polecenia dla programu Visual Basic lub Visual C#, zobacz [tworzenie z wiersza polecenia](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) lub [kompilowania z wiersza polecenia csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="6434a-113">For information about building this example from the command line for Visual Basic or Visual C#, see [Building from the Command Line](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="6434a-114">Można także utworzyć tym przykładzie [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] przez wklejenie kodu do nowego projektu.</span><span class="sxs-lookup"><span data-stu-id="6434a-114">You can also build this example in [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] by pasting the code into a new project.</span></span>  <span data-ttu-id="6434a-115">Również sssee [porady: kompilowanie i uruchamianie pełną Windows formularze kodu przykład za pomocą programu Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span><span class="sxs-lookup"><span data-stu-id="6434a-115">Also sssee [How to: Compile and Run a Complete Windows Forms Code Example Using Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6434a-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="6434a-116">See Also</span></span>  
 [<span data-ttu-id="6434a-117">ToolStrip, kontrolka</span><span class="sxs-lookup"><span data-stu-id="6434a-117">ToolStrip Control</span></span>](../../../../docs/framework/winforms/controls/toolstrip-control-windows-forms.md)
