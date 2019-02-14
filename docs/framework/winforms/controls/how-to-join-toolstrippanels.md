---
title: 'Instrukcje: Łączenie kontrolek ToolStripPanel'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- toolbars [Windows Forms], joining together
- ToolStripPanel control [Windows Forms], joining together
ms.assetid: 4eadda6d-e3b8-4151-aaf2-a8d564fbe6b3
ms.openlocfilehash: cebfcb417dc011ed8990e9d536cd165c2a92cb68
ms.sourcegitcommit: af0a22a4eb11bbcd33baec49150d551955b50a16
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/14/2019
ms.locfileid: "56260741"
---
# <a name="how-to-join-toolstrippanels"></a><span data-ttu-id="85a82-102">Instrukcje: Łączenie kontrolek ToolStripPanel</span><span class="sxs-lookup"><span data-stu-id="85a82-102">How to: Join ToolStripPanels</span></span>
<span data-ttu-id="85a82-103">Możesz dołączyć <xref:System.Windows.Forms.ToolStrip> mające na celu <xref:System.Windows.Forms.ToolStripPanel> w czasie wykonywania, który zapewnia elastyczność aplikacji interfejsu wielu dokumentów (MDI).</span><span class="sxs-lookup"><span data-stu-id="85a82-103">You can join <xref:System.Windows.Forms.ToolStrip> controls to a <xref:System.Windows.Forms.ToolStripPanel> at run time, which provides the flexibility of multiple-document interface (MDI) applications.</span></span>  
  
## <a name="example"></a><span data-ttu-id="85a82-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="85a82-104">Example</span></span>  
 <span data-ttu-id="85a82-105">Poniższy przykład kodu pokazuje, jak sprzęgać <xref:System.Windows.Forms.ToolStrip> mające na celu <xref:System.Windows.Forms.ToolStripPanel>.</span><span class="sxs-lookup"><span data-stu-id="85a82-105">The following code example demonstrates how to join <xref:System.Windows.Forms.ToolStrip> controls to a <xref:System.Windows.Forms.ToolStripPanel>.</span></span>  
  
 [!code-csharp[System.Windows.Forms.ToolStrip.Misc#11](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/CS/Program.cs#11)]
 [!code-vb[System.Windows.Forms.ToolStrip.Misc#11](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/VB/Program.vb#11)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="85a82-106">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="85a82-106">Compiling the Code</span></span>  
 <span data-ttu-id="85a82-107">Ten przykład wymaga:</span><span class="sxs-lookup"><span data-stu-id="85a82-107">This example requires:</span></span>  
  
-   <span data-ttu-id="85a82-108">Odwołania do zestawów System.Design System.Drawing i przestrzeń nazw System.Windows.Forms.</span><span class="sxs-lookup"><span data-stu-id="85a82-108">References to the System.Design, System.Drawing, and System.Windows.Forms assemblies.</span></span>  
  
 <span data-ttu-id="85a82-109">Aby dowiedzieć się, jak tworzyć aplikacje w tym przykładzie z wiersza polecenia dla języka Visual Basic lub Visual C#, zobacz [tworzenie z wiersza polecenia](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) lub [wiersza polecenia tworzenia przy użyciu csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="85a82-109">For information about building this example from the command line for Visual Basic or Visual C#, see [Building from the Command Line](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="85a82-110">Można także utworzyć tego przykładu w programie Visual Studio, wklejając kod do nowego projektu.</span><span class="sxs-lookup"><span data-stu-id="85a82-110">You can also build this example in Visual Studio by pasting the code into a new project.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="85a82-111">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="85a82-111">See also</span></span>
- <xref:System.Windows.Forms.ToolStrip>
- <xref:System.Windows.Forms.ToolStripPanel>
- [<span data-ttu-id="85a82-112">Instrukcje: Używanie elementu ToolStripPanels dla MDI</span><span class="sxs-lookup"><span data-stu-id="85a82-112">How to: Use ToolStripPanels for MDI</span></span>](../../../../docs/framework/winforms/controls/how-to-use-toolstrippanels-for-mdi.md)
