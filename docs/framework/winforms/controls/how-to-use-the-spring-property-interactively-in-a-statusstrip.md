---
title: 'Porady: użycie właściwości Spring interaktywnie w StatusStrip'
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
ms.openlocfilehash: e3818beb96a7c005ea02bc04e9ea740b28a54707
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33533799"
---
# <a name="how-to-use-the-spring-property-interactively-in-a-statusstrip"></a><span data-ttu-id="b2d62-102">Porady: użycie właściwości Spring interaktywnie w StatusStrip</span><span class="sxs-lookup"><span data-stu-id="b2d62-102">How to: Use the Spring Property Interactively in a StatusStrip</span></span>
<span data-ttu-id="b2d62-103">Można użyć <xref:System.Windows.Forms.ToolStripStatusLabel.Spring%2A> ustaw dla właściwości <xref:System.Windows.Forms.ToolStripStatusLabel> kontroli w <xref:System.Windows.Forms.StatusStrip> formantu.</span><span class="sxs-lookup"><span data-stu-id="b2d62-103">You can use the <xref:System.Windows.Forms.ToolStripStatusLabel.Spring%2A> property to position a <xref:System.Windows.Forms.ToolStripStatusLabel> control in a <xref:System.Windows.Forms.StatusStrip> control.</span></span> <span data-ttu-id="b2d62-104"><xref:System.Windows.Forms.ToolStripStatusLabel.Spring%2A> Właściwość określa, czy <xref:System.Windows.Forms.ToolStripStatusLabel> formant automatycznie wypełnienia dostępnego miejsca na <xref:System.Windows.Forms.StatusStrip> formantu.</span><span class="sxs-lookup"><span data-stu-id="b2d62-104">The <xref:System.Windows.Forms.ToolStripStatusLabel.Spring%2A> property determines whether the <xref:System.Windows.Forms.ToolStripStatusLabel> control automatically fills the available space on the <xref:System.Windows.Forms.StatusStrip> control.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b2d62-105">Przykład</span><span class="sxs-lookup"><span data-stu-id="b2d62-105">Example</span></span>  
 <span data-ttu-id="b2d62-106">Poniższy przykład kodu pokazuje sposób użycia <xref:System.Windows.Forms.ToolStripStatusLabel.Spring%2A> ustaw dla właściwości <xref:System.Windows.Forms.ToolStripStatusLabel> kontroli w <xref:System.Windows.Forms.StatusStrip> formantu.</span><span class="sxs-lookup"><span data-stu-id="b2d62-106">The following code example demonstrates how to use the <xref:System.Windows.Forms.ToolStripStatusLabel.Spring%2A> property to position a <xref:System.Windows.Forms.ToolStripStatusLabel> control in a <xref:System.Windows.Forms.StatusStrip> control.</span></span> <span data-ttu-id="b2d62-107"><xref:System.Windows.Forms.ToolStripItem.Click> Wyłącznie wykonuje program obsługi zdarzeń — operacji (XOR), aby przełączyć wartość lub <xref:System.Windows.Forms.ToolStripStatusLabel.Spring%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="b2d62-107">The <xref:System.Windows.Forms.ToolStripItem.Click> event handler performs an exclusive-or (XOR) operation to switch the value of the <xref:System.Windows.Forms.ToolStripStatusLabel.Spring%2A> property.</span></span>  
  
 <span data-ttu-id="b2d62-108">Aby użyć w tym przykładzie kodu, skompiluj i uruchom aplikację, a następnie kliknij **bliski (Spring)** na <xref:System.Windows.Forms.StatusStrip> formantu, aby przełączyć wartość <xref:System.Windows.Forms.ToolStripStatusLabel.Spring%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="b2d62-108">To use this code example, compile and run the application, and then click **Middle (Spring)** on the <xref:System.Windows.Forms.StatusStrip> control to switch the value of the <xref:System.Windows.Forms.ToolStripStatusLabel.Spring%2A> property.</span></span>  
  
 [!code-csharp[System.Windows.Forms.ToolStrip.Misc#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/CS/Program.cs#1)]
 [!code-vb[System.Windows.Forms.ToolStrip.Misc#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/VB/Program.vb#1)]  
[!code-csharp[System.Windows.Forms.ToolStrip.Misc#50](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/CS/Program.cs#50)]
[!code-vb[System.Windows.Forms.ToolStrip.Misc#50](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/VB/Program.vb#50)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="b2d62-109">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="b2d62-109">Compiling the Code</span></span>  
 <span data-ttu-id="b2d62-110">Ten przykład wymaga:</span><span class="sxs-lookup"><span data-stu-id="b2d62-110">This example requires:</span></span>  
  
-   <span data-ttu-id="b2d62-111">Odwołania do zestawów System.Design, System.Drawing i System.Windows.Forms.</span><span class="sxs-lookup"><span data-stu-id="b2d62-111">References to the System.Design, System.Drawing, and System.Windows.Forms assemblies.</span></span>  
  
 <span data-ttu-id="b2d62-112">Uzyskać informacje o kompilowaniu w tym przykładzie z wiersza polecenia dla programu visual Basic lub Visual C#, zobacz [tworzenie z wiersza polecenia](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) lub [kompilowania z wiersza polecenia csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="b2d62-112">For information about building this example from the command line for visual Basic or Visual C#, see [Building from the Command Line](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="b2d62-113">Można także utworzyć w tym przykładzie w programie Visual Studio przez wklejenie kodu do nowego projektu.</span><span class="sxs-lookup"><span data-stu-id="b2d62-113">You can also build this example in Visual Studio by pasting the code into a new project.</span></span>  <span data-ttu-id="b2d62-114">Zobacz też [porady: kompilowanie i uruchamianie pełną Windows formularze kodu przykład za pomocą programu Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span><span class="sxs-lookup"><span data-stu-id="b2d62-114">Also see [How to: Compile and Run a Complete Windows Forms Code Example Using Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b2d62-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b2d62-115">See Also</span></span>  
 <xref:System.Windows.Forms.ToolStripStatusLabel>  
 <xref:System.Windows.Forms.StatusStrip>  
 <xref:System.Windows.Forms.ToolStrip>  
 <xref:System.Windows.Forms.ToolStripItem>  
 <xref:System.Windows.Forms.ToolStripMenuItem>  
 [<span data-ttu-id="b2d62-116">ToolStrip, kontrolka</span><span class="sxs-lookup"><span data-stu-id="b2d62-116">ToolStrip Control</span></span>](../../../../docs/framework/winforms/controls/toolstrip-control-windows-forms.md)
