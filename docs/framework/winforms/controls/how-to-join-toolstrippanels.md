---
title: 'Porady: łączenie ToolStripPanels'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- toolbars [Windows Forms], joining together
- ToolStripPanel control [Windows Forms], joining together
ms.assetid: 4eadda6d-e3b8-4151-aaf2-a8d564fbe6b3
ms.openlocfilehash: 5e1688fb00e6eefa4873284e1ea1ba29536d3227
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/05/2018
ms.locfileid: "43723629"
---
# <a name="how-to-join-toolstrippanels"></a><span data-ttu-id="5d882-102">Porady: łączenie ToolStripPanels</span><span class="sxs-lookup"><span data-stu-id="5d882-102">How to: Join ToolStripPanels</span></span>
<span data-ttu-id="5d882-103">Możesz dołączyć <xref:System.Windows.Forms.ToolStrip> mające na celu <xref:System.Windows.Forms.ToolStripPanel> w czasie wykonywania, który zapewnia elastyczność aplikacji interfejsu wielu dokumentów (MDI).</span><span class="sxs-lookup"><span data-stu-id="5d882-103">You can join <xref:System.Windows.Forms.ToolStrip> controls to a <xref:System.Windows.Forms.ToolStripPanel> at run time, which provides the flexibility of multiple-document interface (MDI) applications.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5d882-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="5d882-104">Example</span></span>  
 <span data-ttu-id="5d882-105">Poniższy przykład kodu pokazuje, jak sprzęgać <xref:System.Windows.Forms.ToolStrip> mające na celu <xref:System.Windows.Forms.ToolStripPanel>.</span><span class="sxs-lookup"><span data-stu-id="5d882-105">The following code example demonstrates how to join <xref:System.Windows.Forms.ToolStrip> controls to a <xref:System.Windows.Forms.ToolStripPanel>.</span></span>  
  
 [!code-csharp[System.Windows.Forms.ToolStrip.Misc#11](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/CS/Program.cs#11)]
 [!code-vb[System.Windows.Forms.ToolStrip.Misc#11](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/VB/Program.vb#11)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="5d882-106">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="5d882-106">Compiling the Code</span></span>  
 <span data-ttu-id="5d882-107">Ten przykład wymaga:</span><span class="sxs-lookup"><span data-stu-id="5d882-107">This example requires:</span></span>  
  
-   <span data-ttu-id="5d882-108">Odwołania do zestawów System.Design System.Drawing i przestrzeń nazw System.Windows.Forms.</span><span class="sxs-lookup"><span data-stu-id="5d882-108">References to the System.Design, System.Drawing, and System.Windows.Forms assemblies.</span></span>  
  
 <span data-ttu-id="5d882-109">Aby uzyskać informacje o tworzeniu tego przykładu z wiersza polecenia dla programu visual Basic lub Visual C#, zobacz [tworzenie z wiersza polecenia](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) lub [wiersza polecenia tworzenia przy użyciu csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="5d882-109">For information about building this example from the command line for visual Basic or Visual C#, see [Building from the Command Line](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="5d882-110">Można także utworzyć tego przykładu w programie Visual Studio, wklejając kod do nowego projektu.</span><span class="sxs-lookup"><span data-stu-id="5d882-110">You can also build this example in Visual Studio by pasting the code into a new project.</span></span>  <span data-ttu-id="5d882-111">Zobacz też [porady: kompilowanie i uruchamianie pełną Windows Forms kodu przykładzie przy użyciu programu Visual Studio](https://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span><span class="sxs-lookup"><span data-stu-id="5d882-111">Also see [How to: Compile and Run a Complete Windows Forms Code Example Using Visual Studio](https://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5d882-112">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="5d882-112">See Also</span></span>  
 <xref:System.Windows.Forms.ToolStrip>  
 <xref:System.Windows.Forms.ToolStripPanel>  
 [<span data-ttu-id="5d882-113">Instrukcje: używanie kontrolek ToolStripPanels dla MDI</span><span class="sxs-lookup"><span data-stu-id="5d882-113">How to: Use ToolStripPanels for MDI</span></span>](../../../../docs/framework/winforms/controls/how-to-use-toolstrippanels-for-mdi.md)
