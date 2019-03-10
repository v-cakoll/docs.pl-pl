---
title: 'Instrukcje: Tworzenie formularza MDI za pomocą kontrolek ToolStripPanel'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ToolStripPanel control [Windows Forms]
- MDI [Windows Forms], creating forms
- multiple document interface forms
- MDI forms [Windows Forms]
- ToolStrip control [Windows Forms]
- MDI forms [Windows Forms], creating
ms.assetid: d198ef8e-f7c4-4b3f-a7f5-ce858cb90cec
ms.openlocfilehash: 9b3297acabbb05c25ae195acbb6fb9274ad02651
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/09/2019
ms.locfileid: "57725392"
---
# <a name="how-to-create-an-mdi-form-with-toolstrippanel-controls"></a><span data-ttu-id="5bc35-102">Instrukcje: Tworzenie formularza MDI za pomocą kontrolek ToolStripPanel</span><span class="sxs-lookup"><span data-stu-id="5bc35-102">How to: Create an MDI Form with ToolStripPanel Controls</span></span>
<span data-ttu-id="5bc35-103">Można utworzyć wiele formularz interfejsu (MDI) dokumentu, który ma <xref:System.Windows.Forms.ToolStrip> formantów ramek go na wszystkich czterech stron.</span><span class="sxs-lookup"><span data-stu-id="5bc35-103">You can create a multiple document interface (MDI) form that has <xref:System.Windows.Forms.ToolStrip> controls framing it on all four sides.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5bc35-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="5bc35-104">Example</span></span>  
 <span data-ttu-id="5bc35-105">Poniższy przykład kodu demonstruje sposób używania zadokowany <xref:System.Windows.Forms.ToolStripPanel> kontrolki do ramki okna MDI z czterema <xref:System.Windows.Forms.ToolStrip> kontrolki.</span><span class="sxs-lookup"><span data-stu-id="5bc35-105">The following code example demonstrates how to use docked <xref:System.Windows.Forms.ToolStripPanel> controls to frame an MDI window with four <xref:System.Windows.Forms.ToolStrip> controls.</span></span>  
  
 <span data-ttu-id="5bc35-106">W tym przykładzie <xref:System.Windows.Forms.ToolStripPanel.Join%2A> metoda dołącza <xref:System.Windows.Forms.ToolStrip> kontrolki do odpowiednich <xref:System.Windows.Forms.ToolStripPanel> kontrolki.</span><span class="sxs-lookup"><span data-stu-id="5bc35-106">In the example, the <xref:System.Windows.Forms.ToolStripPanel.Join%2A> method attaches the <xref:System.Windows.Forms.ToolStrip> controls to the corresponding <xref:System.Windows.Forms.ToolStripPanel> controls.</span></span>  
  
 [!code-csharp[System.Windows.Forms.ToolStrip.Misc#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/CS/Program.cs#1)]
 [!code-vb[System.Windows.Forms.ToolStrip.Misc#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/VB/Program.vb#1)]  
[!code-csharp[System.Windows.Forms.ToolStrip.Misc#10](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/CS/Program.cs#10)]
[!code-vb[System.Windows.Forms.ToolStrip.Misc#10](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/VB/Program.vb#10)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="5bc35-107">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="5bc35-107">Compiling the Code</span></span>  
 <span data-ttu-id="5bc35-108">Ten przykład wymaga:</span><span class="sxs-lookup"><span data-stu-id="5bc35-108">This example requires:</span></span>  
  
-   <span data-ttu-id="5bc35-109">Odwołania do zestawów System.Drawing i pozycję System.Windows.Forms.</span><span class="sxs-lookup"><span data-stu-id="5bc35-109">References to the System.Drawing and System.Windows.Forms assemblies.</span></span>  
  
 <span data-ttu-id="5bc35-110">Aby dowiedzieć się, jak tworzyć aplikacje w tym przykładzie z wiersza polecenia dla języka Visual Basic lub Visual C#, zobacz [tworzenie z wiersza polecenia](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) lub [wiersza polecenia tworzenia przy użyciu csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="5bc35-110">For information about building this example from the command line for Visual Basic or Visual C#, see [Building from the Command Line](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="5bc35-111">Można także utworzyć tego przykładu w programie Visual Studio, wklejając kod do nowego projektu.</span><span class="sxs-lookup"><span data-stu-id="5bc35-111">You can also build this example in Visual Studio by pasting the code into a new project.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5bc35-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="5bc35-112">See also</span></span>
- <xref:System.Windows.Forms.ToolStrip>
- <xref:System.Windows.Forms.ToolStripPanel>
- <xref:System.Windows.Forms.ToolStripPanel.Join%2A>
- <xref:System.Windows.Forms.ToolStripItem>
- <xref:System.Windows.Forms.ToolStripMenuItem>
- [<span data-ttu-id="5bc35-113">ToolStrip, kontrolka</span><span class="sxs-lookup"><span data-stu-id="5bc35-113">ToolStrip Control</span></span>](toolstrip-control-windows-forms.md)
