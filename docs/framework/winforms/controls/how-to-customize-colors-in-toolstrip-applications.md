---
title: 'Porady: dostosowywanie kolorów w aplikacjach ToolStrip'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- toolbars [Windows Forms], customizing colors
- colors [Windows Forms], customizing in ToolStrip controls [Windows Forms]
- ToolStrip control [Windows Forms], custom colors
ms.assetid: e2752fe2-1afb-489e-ab96-b7805acd96bc
ms.openlocfilehash: 9a3f712a4d729452ac0d2d4755a5fba59ca102ed
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/05/2018
ms.locfileid: "43732718"
---
# <a name="how-to-customize-colors-in-toolstrip-applications"></a><span data-ttu-id="6bf1b-102">Porady: dostosowywanie kolorów w aplikacjach ToolStrip</span><span class="sxs-lookup"><span data-stu-id="6bf1b-102">How to: Customize Colors in ToolStrip Applications</span></span>
<span data-ttu-id="6bf1b-103">Można dostosować wygląd Twojego <xref:System.Windows.Forms.ToolStrip> przy użyciu <xref:System.Windows.Forms.ToolStripProfessionalRenderer> klasy, aby używać kolorów niestandardowych.</span><span class="sxs-lookup"><span data-stu-id="6bf1b-103">You can customize the appearance of your <xref:System.Windows.Forms.ToolStrip> by using the <xref:System.Windows.Forms.ToolStripProfessionalRenderer> class to use customized colors.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6bf1b-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="6bf1b-104">Example</span></span>  
 <span data-ttu-id="6bf1b-105">Poniższy przykład kodu demonstruje sposób używania <xref:System.Windows.Forms.ToolStripProfessionalRenderer> definiowanie kolorów niestandardowych w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="6bf1b-105">The following code example demonstrates how to use a <xref:System.Windows.Forms.ToolStripProfessionalRenderer> to define custom colors at run time.</span></span>  
  
 [!code-csharp[System.Windows.Forms.ToolStrip.Misc#20](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/CS/Program.cs#20)]
 [!code-vb[System.Windows.Forms.ToolStrip.Misc#20](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/VB/Program.vb#20)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="6bf1b-106">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="6bf1b-106">Compiling the Code</span></span>  
 <span data-ttu-id="6bf1b-107">Ten przykład wymaga:</span><span class="sxs-lookup"><span data-stu-id="6bf1b-107">This example requires:</span></span>  
  
-   <span data-ttu-id="6bf1b-108">Odwołania do zestawów System.Design System.Drawing i przestrzeń nazw System.Windows.Forms.</span><span class="sxs-lookup"><span data-stu-id="6bf1b-108">References to the System.Design, System.Drawing, and System.Windows.Forms assemblies.</span></span>  
  
 <span data-ttu-id="6bf1b-109">Aby dowiedzieć się, jak tworzyć aplikacje w tym przykładzie z wiersza polecenia dla języka Visual Basic lub Visual C#, zobacz [tworzenie z wiersza polecenia](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) lub [wiersza polecenia tworzenia przy użyciu csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="6bf1b-109">For information about building this example from the command line for Visual Basic or Visual C#, see [Building from the Command Line](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="6bf1b-110">Można także utworzyć tego przykładu w programie Visual Studio, wklejając kod do nowego projektu.</span><span class="sxs-lookup"><span data-stu-id="6bf1b-110">You can also build this example in Visual Studio by pasting the code into a new project.</span></span>  <span data-ttu-id="6bf1b-111">Zobacz też [porady: kompilowanie i uruchamianie pełną Windows Forms kodu przykładzie przy użyciu programu Visual Studio](https://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span><span class="sxs-lookup"><span data-stu-id="6bf1b-111">Also see [How to: Compile and Run a Complete Windows Forms Code Example Using Visual Studio](https://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6bf1b-112">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="6bf1b-112">See Also</span></span>  
 <xref:System.Windows.Forms.ToolStripManager>  
 <xref:System.Windows.Forms.ProfessionalColorTable>  
 <xref:System.Windows.Forms.MenuStrip>  
 <xref:System.Windows.Forms.ToolStrip>  
 <xref:System.Windows.Forms.ToolStripProfessionalRenderer>
