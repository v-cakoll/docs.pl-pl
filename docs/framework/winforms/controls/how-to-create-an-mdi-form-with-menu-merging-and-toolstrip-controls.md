---
title: 'Instrukcje: Tworzenie formularza MDI ze scalaniem Menu i formantów ToolStrip'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- toolbars [Windows Forms]
- ToolStripPanel control [Windows Forms]
- ToolStrip control [Windows Forms]
- MenuStrip control [Windows Forms]
ms.assetid: 64992ed9-44af-4baf-b45f-863e6ab35711
ms.openlocfilehash: 6cbab3c588aa74809a7aef80ae6ffc4c3772069f
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54646019"
---
# <a name="how-to-create-an-mdi-form-with-menu-merging-and-toolstrip-controls"></a><span data-ttu-id="0e703-102">Instrukcje: Tworzenie formularza MDI ze scalaniem Menu i formantów ToolStrip</span><span class="sxs-lookup"><span data-stu-id="0e703-102">How to: Create an MDI Form with Menu Merging and ToolStrip Controls</span></span>
<span data-ttu-id="0e703-103"><xref:System.Windows.Forms?displayProperty=nameWithType> Przestrzeń nazw obsługuje wiele aplikacji interfejsu (MDI) dokumentu i <xref:System.Windows.Forms.MenuStrip> kontrolka obsługuje scalania menu.</span><span class="sxs-lookup"><span data-stu-id="0e703-103">The <xref:System.Windows.Forms?displayProperty=nameWithType> namespace supports multiple document interface (MDI) applications, and the <xref:System.Windows.Forms.MenuStrip> control supports menu merging.</span></span> <span data-ttu-id="0e703-104">Formularze MDI może również <xref:System.Windows.Forms.ToolStrip> kontrolki.</span><span class="sxs-lookup"><span data-stu-id="0e703-104">MDI forms can also <xref:System.Windows.Forms.ToolStrip> controls.</span></span>  
  
 <span data-ttu-id="0e703-105">Brak zaawansowaną obsługę dla tej funkcji w programie Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="0e703-105">There is extensive support for this feature in Visual Studio.</span></span>  
  
 <span data-ttu-id="0e703-106">Zobacz też [instruktażu: Tworzenie formularza MDI za pomocą scalania Menu i formantami ToolStrip](walkthrough-creating-an-mdi-form-with-menu-merging-and-toolstrip-controls.md).</span><span class="sxs-lookup"><span data-stu-id="0e703-106">Also see [Walkthrough: Creating an MDI Form with Menu Merging and ToolStrip Controls](walkthrough-creating-an-mdi-form-with-menu-merging-and-toolstrip-controls.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="0e703-107">Przykład</span><span class="sxs-lookup"><span data-stu-id="0e703-107">Example</span></span>  
 <span data-ttu-id="0e703-108">Poniższy przykład kodu demonstruje sposób używania <xref:System.Windows.Forms.ToolStripPanel> formanty z formularza MDI.</span><span class="sxs-lookup"><span data-stu-id="0e703-108">The following code example demonstrates how to use <xref:System.Windows.Forms.ToolStripPanel> controls with an MDI form.</span></span> <span data-ttu-id="0e703-109">Formularz obsługuje także menu scalanie z menu podrzędne.</span><span class="sxs-lookup"><span data-stu-id="0e703-109">The form also supports menu merging with child menus.</span></span>  
  
 [!code-csharp[System.Windows.Forms.ToolStrip.MdiForm#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.MdiForm/CS/Form1.cs#1)]
 [!code-vb[System.Windows.Forms.ToolStrip.MdiForm#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.MdiForm/VB/Form1.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="0e703-110">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="0e703-110">Compiling the Code</span></span>  
 <span data-ttu-id="0e703-111">Poniższy przykład kodu wymaga:</span><span class="sxs-lookup"><span data-stu-id="0e703-111">This code example requires:</span></span>  
  
-   <span data-ttu-id="0e703-112">Odwołania do zestawów System.Drawing i pozycję System.Windows.Forms.</span><span class="sxs-lookup"><span data-stu-id="0e703-112">References to the System.Drawing and System.Windows.Forms assemblies.</span></span>  
  
 <span data-ttu-id="0e703-113">Aby dowiedzieć się, jak tworzyć aplikacje w tym przykładzie z wiersza polecenia dla języka Visual Basic lub Visual C#, zobacz [tworzenie z wiersza polecenia](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) lub [wiersza polecenia tworzenia przy użyciu csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="0e703-113">For information about building this example from the command line for Visual Basic or Visual C#, see [Building from the Command Line](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="0e703-114">Można także utworzyć tego przykładu w programie Visual Studio, wklejając kod do nowego projektu.</span><span class="sxs-lookup"><span data-stu-id="0e703-114">You can also build this example in Visual Studio by pasting the code into a new project.</span></span>  <span data-ttu-id="0e703-115">Zobacz również [jak: Skompilować i uruchomić przykładowy kod pełną Windows Forms przy użyciu programu Visual Studio](https://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span><span class="sxs-lookup"><span data-stu-id="0e703-115">Also sssee [How to: Compile and Run a Complete Windows Forms Code Example Using Visual Studio](https://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0e703-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="0e703-116">See also</span></span>
- [<span data-ttu-id="0e703-117">ToolStrip, kontrolka</span><span class="sxs-lookup"><span data-stu-id="0e703-117">ToolStrip Control</span></span>](../../../../docs/framework/winforms/controls/toolstrip-control-windows-forms.md)
