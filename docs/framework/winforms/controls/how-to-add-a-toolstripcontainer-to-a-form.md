---
title: 'Instrukcje: dodawanie elementu ToolStripContainer do formularza'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- toolbars [Windows Forms], built-in rafting
- ToolStrip control [Windows Forms], built-in rafting
- ToolStripContainer control [Windows Forms], adding to Windows Forms
ms.assetid: d0f55095-a833-453e-be5a-644906d75d54
ms.openlocfilehash: 6b35baac09ac47a25cc55877b2c94628f1b57111
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64624073"
---
# <a name="how-to-add-a-toolstripcontainer-to-a-form"></a><span data-ttu-id="f0d74-102">Instrukcje: dodawanie elementu ToolStripContainer do formularza</span><span class="sxs-lookup"><span data-stu-id="f0d74-102">How to: Add a ToolStripContainer to a Form</span></span>
<span data-ttu-id="f0d74-103">Możesz programowo dodać <xref:System.Windows.Forms.ToolStripContainer> do formularza Windows i wypełnić ją za pomocą kontrolek.</span><span class="sxs-lookup"><span data-stu-id="f0d74-103">You can programmatically add a <xref:System.Windows.Forms.ToolStripContainer> to a Windows Form and populate it with controls.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f0d74-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="f0d74-104">Example</span></span>  
 <span data-ttu-id="f0d74-105">Poniższy przykład kodu demonstruje sposób dodawania <xref:System.Windows.Forms.ToolStripContainer> i <xref:System.Windows.Forms.ToolStrip> do formularzy Windows, jak dodać elementy do <xref:System.Windows.Forms.ToolStrip>oraz sposób dodawania <xref:System.Windows.Forms.ToolStrip> do <xref:System.Windows.Forms.ToolStripContainer.TopToolStripPanel%2A> z <xref:System.Windows.Forms.ToolStripContainer>.</span><span class="sxs-lookup"><span data-stu-id="f0d74-105">The following code example demonstrates how to add a <xref:System.Windows.Forms.ToolStripContainer> and a <xref:System.Windows.Forms.ToolStrip> to a Windows Forms, how to add items to the <xref:System.Windows.Forms.ToolStrip>, and how to add the <xref:System.Windows.Forms.ToolStrip> to the <xref:System.Windows.Forms.ToolStripContainer.TopToolStripPanel%2A> of the <xref:System.Windows.Forms.ToolStripContainer>.</span></span>  
  
 [!code-csharp[System.Windows.Forms.ToolStripContainer2#1](~/samples/snippets/csharp/VS_Snippets_Winforms/system.windows.forms.toolstripcontainer2/cs/form1.cs#1)]
 [!code-vb[System.Windows.Forms.ToolStripContainer2#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/system.windows.forms.toolstripcontainer2/vb/form1.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="f0d74-106">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="f0d74-106">Compiling the Code</span></span>  
 <span data-ttu-id="f0d74-107">Poniższy przykład kodu wymaga:</span><span class="sxs-lookup"><span data-stu-id="f0d74-107">This code example requires:</span></span>  
  
- <span data-ttu-id="f0d74-108">Odwołania do zestawów System.Drawing, System.Text i przestrzeń nazw System.Windows.Forms.</span><span class="sxs-lookup"><span data-stu-id="f0d74-108">References to the System.Drawing, System.Text, and System.Windows.Forms assemblies.</span></span>  
  
 <span data-ttu-id="f0d74-109">Aby dowiedzieć się, jak tworzyć aplikacje w tym przykładzie z wiersza polecenia dla języka Visual Basic lub Visual C#, zobacz [tworzenie z wiersza polecenia](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) lub [wiersza polecenia tworzenia przy użyciu csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="f0d74-109">For information about building this example from the command line for Visual Basic or Visual C#, see [Building from the Command Line](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="f0d74-110">Można także utworzyć tego przykładu w programie Visual Studio, wklejając kod do nowego projektu.</span><span class="sxs-lookup"><span data-stu-id="f0d74-110">You can also build this example in Visual Studio by pasting the code into a new project.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="f0d74-111">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f0d74-111">See also</span></span>

- <xref:System.Windows.Forms.ToolStripContainer>
- [<span data-ttu-id="f0d74-112">ToolStripContainer, kontrolka</span><span class="sxs-lookup"><span data-stu-id="f0d74-112">ToolStripContainer Control</span></span>](toolstripcontainer-control.md)
- [<span data-ttu-id="f0d74-113">ToolStrip, kontrolka</span><span class="sxs-lookup"><span data-stu-id="f0d74-113">ToolStrip Control</span></span>](toolstrip-control-windows-forms.md)
