---
title: 'Instrukcje: Użycie właściwości Spring interaktywnie w StatusStrip'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- StatusStrip control [Windows Forms]
- ToolStrip control [Windows Forms]
- status bars [Windows Forms], examples
- Spring property [Windows Forms]
ms.assetid: 18bde842-a93c-48dd-9db3-15738a1775ce
ms.openlocfilehash: 0e1d085b0695150e40c88683721134e9ea5116d9
ms.sourcegitcommit: af0a22a4eb11bbcd33baec49150d551955b50a16
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/14/2019
ms.locfileid: "56260980"
---
# <a name="how-to-use-the-spring-property-interactively-in-a-statusstrip"></a><span data-ttu-id="826e2-102">Instrukcje: Użycie właściwości Spring interaktywnie w StatusStrip</span><span class="sxs-lookup"><span data-stu-id="826e2-102">How to: Use the Spring Property Interactively in a StatusStrip</span></span>
<span data-ttu-id="826e2-103">Możesz użyć <xref:System.Windows.Forms.ToolStripStatusLabel.Spring%2A> właściwości pozycji <xref:System.Windows.Forms.ToolStripStatusLabel> w kontrolce <xref:System.Windows.Forms.StatusStrip> kontroli.</span><span class="sxs-lookup"><span data-stu-id="826e2-103">You can use the <xref:System.Windows.Forms.ToolStripStatusLabel.Spring%2A> property to position a <xref:System.Windows.Forms.ToolStripStatusLabel> control in a <xref:System.Windows.Forms.StatusStrip> control.</span></span> <span data-ttu-id="826e2-104"><xref:System.Windows.Forms.ToolStripStatusLabel.Spring%2A> Właściwość określa, czy <xref:System.Windows.Forms.ToolStripStatusLabel> kontroli automatycznie wypełni dostępne miejsce na <xref:System.Windows.Forms.StatusStrip> kontroli.</span><span class="sxs-lookup"><span data-stu-id="826e2-104">The <xref:System.Windows.Forms.ToolStripStatusLabel.Spring%2A> property determines whether the <xref:System.Windows.Forms.ToolStripStatusLabel> control automatically fills the available space on the <xref:System.Windows.Forms.StatusStrip> control.</span></span>  
  
## <a name="example"></a><span data-ttu-id="826e2-105">Przykład</span><span class="sxs-lookup"><span data-stu-id="826e2-105">Example</span></span>  
 <span data-ttu-id="826e2-106">Poniższy przykład kodu demonstruje sposób używania <xref:System.Windows.Forms.ToolStripStatusLabel.Spring%2A> właściwości pozycji <xref:System.Windows.Forms.ToolStripStatusLabel> w kontrolce <xref:System.Windows.Forms.StatusStrip> kontroli.</span><span class="sxs-lookup"><span data-stu-id="826e2-106">The following code example demonstrates how to use the <xref:System.Windows.Forms.ToolStripStatusLabel.Spring%2A> property to position a <xref:System.Windows.Forms.ToolStripStatusLabel> control in a <xref:System.Windows.Forms.StatusStrip> control.</span></span> <span data-ttu-id="826e2-107"><xref:System.Windows.Forms.ToolStripItem.Click> Programu obsługi zdarzeń wykonuje wyłącznie — lub operacji (XOR), aby przełączyć się wartość <xref:System.Windows.Forms.ToolStripStatusLabel.Spring%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="826e2-107">The <xref:System.Windows.Forms.ToolStripItem.Click> event handler performs an exclusive-or (XOR) operation to switch the value of the <xref:System.Windows.Forms.ToolStripStatusLabel.Spring%2A> property.</span></span>  
  
 <span data-ttu-id="826e2-108">Aby wykorzystać ten przykład kodu, skompiluj i uruchom aplikację, a następnie kliknij **bliski (Spring)** na <xref:System.Windows.Forms.StatusStrip> sterowania, aby przełączyć się wartość <xref:System.Windows.Forms.ToolStripStatusLabel.Spring%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="826e2-108">To use this code example, compile and run the application, and then click **Middle (Spring)** on the <xref:System.Windows.Forms.StatusStrip> control to switch the value of the <xref:System.Windows.Forms.ToolStripStatusLabel.Spring%2A> property.</span></span>  
  
 [!code-csharp[System.Windows.Forms.ToolStrip.Misc#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/CS/Program.cs#1)]
 [!code-vb[System.Windows.Forms.ToolStrip.Misc#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/VB/Program.vb#1)]  
[!code-csharp[System.Windows.Forms.ToolStrip.Misc#50](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/CS/Program.cs#50)]
[!code-vb[System.Windows.Forms.ToolStrip.Misc#50](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/VB/Program.vb#50)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="826e2-109">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="826e2-109">Compiling the Code</span></span>  
 <span data-ttu-id="826e2-110">Ten przykład wymaga:</span><span class="sxs-lookup"><span data-stu-id="826e2-110">This example requires:</span></span>  
  
-   <span data-ttu-id="826e2-111">Odwołania do zestawów System.Design System.Drawing i przestrzeń nazw System.Windows.Forms.</span><span class="sxs-lookup"><span data-stu-id="826e2-111">References to the System.Design, System.Drawing, and System.Windows.Forms assemblies.</span></span>  
  
 <span data-ttu-id="826e2-112">Aby dowiedzieć się, jak tworzyć aplikacje w tym przykładzie z wiersza polecenia dla języka Visual Basic lub Visual C#, zobacz [tworzenie z wiersza polecenia](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) lub [wiersza polecenia tworzenia przy użyciu csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="826e2-112">For information about building this example from the command line for Visual Basic or Visual C#, see [Building from the Command Line](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="826e2-113">Można także utworzyć tego przykładu w programie Visual Studio, wklejając kod do nowego projektu.</span><span class="sxs-lookup"><span data-stu-id="826e2-113">You can also build this example in Visual Studio by pasting the code into a new project.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="826e2-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="826e2-114">See also</span></span>
- <xref:System.Windows.Forms.ToolStripStatusLabel>
- <xref:System.Windows.Forms.StatusStrip>
- <xref:System.Windows.Forms.ToolStrip>
- <xref:System.Windows.Forms.ToolStripItem>
- <xref:System.Windows.Forms.ToolStripMenuItem>
- [<span data-ttu-id="826e2-115">ToolStrip, kontrolka</span><span class="sxs-lookup"><span data-stu-id="826e2-115">ToolStrip Control</span></span>](../../../../docs/framework/winforms/controls/toolstrip-control-windows-forms.md)
