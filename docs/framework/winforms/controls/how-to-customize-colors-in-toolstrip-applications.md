---
title: 'Porady: dostosowywanie kolorów w aplikacjach ToolStrip'
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
- toolbars [Windows Forms], customizing colors
- colors [Windows Forms], customizing in ToolStrip controls [Windows Forms]
- ToolStrip control [Windows Forms], custom colors
ms.assetid: e2752fe2-1afb-489e-ab96-b7805acd96bc
caps.latest.revision: 9
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 3b8806878c2bac338b4bce9cbee311edd7bf7978
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-customize-colors-in-toolstrip-applications"></a><span data-ttu-id="9a2fe-102">Porady: dostosowywanie kolorów w aplikacjach ToolStrip</span><span class="sxs-lookup"><span data-stu-id="9a2fe-102">How to: Customize Colors in ToolStrip Applications</span></span>
<span data-ttu-id="9a2fe-103">Można dostosować wygląd Twojej <xref:System.Windows.Forms.ToolStrip> przy użyciu <xref:System.Windows.Forms.ToolStripProfessionalRenderer> klasę, aby użyć kolory niestandardowe.</span><span class="sxs-lookup"><span data-stu-id="9a2fe-103">You can customize the appearance of your <xref:System.Windows.Forms.ToolStrip> by using the <xref:System.Windows.Forms.ToolStripProfessionalRenderer> class to use customized colors.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9a2fe-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="9a2fe-104">Example</span></span>  
 <span data-ttu-id="9a2fe-105">Poniższy przykład kodu pokazuje sposób użycia <xref:System.Windows.Forms.ToolStripProfessionalRenderer> na zdefiniowanie kolorów niestandardowych w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="9a2fe-105">The following code example demonstrates how to use a <xref:System.Windows.Forms.ToolStripProfessionalRenderer> to define custom colors at run time.</span></span>  
  
 [!code-csharp[System.Windows.Forms.ToolStrip.Misc#20](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/CS/Program.cs#20)]
 [!code-vb[System.Windows.Forms.ToolStrip.Misc#20](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/VB/Program.vb#20)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="9a2fe-106">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="9a2fe-106">Compiling the Code</span></span>  
 <span data-ttu-id="9a2fe-107">Ten przykład wymaga:</span><span class="sxs-lookup"><span data-stu-id="9a2fe-107">This example requires:</span></span>  
  
-   <span data-ttu-id="9a2fe-108">Odwołania do zestawów System.Design, System.Drawing i System.Windows.Forms.</span><span class="sxs-lookup"><span data-stu-id="9a2fe-108">References to the System.Design, System.Drawing, and System.Windows.Forms assemblies.</span></span>  
  
 <span data-ttu-id="9a2fe-109">Uzyskać informacje o kompilowaniu w tym przykładzie z wiersza polecenia dla programu Visual Basic lub Visual C#, zobacz [tworzenie z wiersza polecenia](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) lub [kompilowania z wiersza polecenia csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="9a2fe-109">For information about building this example from the command line for Visual Basic or Visual C#, see [Building from the Command Line](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="9a2fe-110">Można także utworzyć tym przykładzie [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] przez wklejenie kodu do nowego projektu.</span><span class="sxs-lookup"><span data-stu-id="9a2fe-110">You can also build this example in [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] by pasting the code into a new project.</span></span>  <span data-ttu-id="9a2fe-111">Zobacz też [porady: kompilowanie i uruchamianie pełną Windows formularze kodu przykład za pomocą programu Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span><span class="sxs-lookup"><span data-stu-id="9a2fe-111">Also see [How to: Compile and Run a Complete Windows Forms Code Example Using Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9a2fe-112">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="9a2fe-112">See Also</span></span>  
 <xref:System.Windows.Forms.ToolStripManager>  
 <xref:System.Windows.Forms.ProfessionalColorTable>  
 <xref:System.Windows.Forms.MenuStrip>  
 <xref:System.Windows.Forms.ToolStrip>  
 <xref:System.Windows.Forms.ToolStripProfessionalRenderer>
