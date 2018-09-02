---
title: 'Porady: konfiguracja marginesów zaznaczania MenuStrip i marginesów obrazu'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- margins [Windows Forms], setting in MenuStrip controls
- menus [Windows Forms], setting margins
- MenuStrip control [Windows Forms], configuring check and image margins
ms.assetid: 45a9075d-4bea-4ce2-9b2c-7619aa39f8ce
ms.openlocfilehash: 872139fd234bafb303168d906c6ec96ce7b1611c
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/01/2018
ms.locfileid: "43388500"
---
# <a name="how-to-configure-menustrip-check-margins-and-image-margins"></a><span data-ttu-id="b6882-102">Porady: konfiguracja marginesów zaznaczania MenuStrip i marginesów obrazu</span><span class="sxs-lookup"><span data-stu-id="b6882-102">How to: Configure MenuStrip Check Margins and Image Margins</span></span>
<span data-ttu-id="b6882-103">Można dostosować <xref:System.Windows.Forms.MenuStrip> , ustawiając <xref:System.Windows.Forms.ToolStripDropDownMenu.ShowImageMargin%2A> i <xref:System.Windows.Forms.ToolStripDropDownMenu.ShowCheckMargin%2A> właściwości w różnych kombinacjach.</span><span class="sxs-lookup"><span data-stu-id="b6882-103">You can customize a <xref:System.Windows.Forms.MenuStrip> by setting the <xref:System.Windows.Forms.ToolStripDropDownMenu.ShowImageMargin%2A> and <xref:System.Windows.Forms.ToolStripDropDownMenu.ShowCheckMargin%2A> properties in various combinations.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b6882-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="b6882-104">Example</span></span>  
 <span data-ttu-id="b6882-105">Poniższy przykład kodu demonstruje sposób ustawiania i dostosować <xref:System.Windows.Forms.ContextMenuStrip> Sprawdź marginesów zaznaczania i marginesów obrazu.</span><span class="sxs-lookup"><span data-stu-id="b6882-105">The following code example demonstrates how to set and customize the <xref:System.Windows.Forms.ContextMenuStrip> check margins and image margins.</span></span> <span data-ttu-id="b6882-106">Procedura jest taka sama dla <xref:System.Windows.Forms.ContextMenuStrip> lub <xref:System.Windows.Forms.MenuStrip>.</span><span class="sxs-lookup"><span data-stu-id="b6882-106">The procedure is the same for a <xref:System.Windows.Forms.ContextMenuStrip> or a <xref:System.Windows.Forms.MenuStrip>.</span></span>  
  
 [!code-csharp[System.Windows.Forms.ToolStrip.Misc#60](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/CS/Program.cs#60)]
 [!code-vb[System.Windows.Forms.ToolStrip.Misc#60](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/VB/Program.vb#60)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="b6882-107">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="b6882-107">Compiling the Code</span></span>  
 <span data-ttu-id="b6882-108">Ten przykład wymaga:</span><span class="sxs-lookup"><span data-stu-id="b6882-108">This example requires:</span></span>  
  
-   <span data-ttu-id="b6882-109">Odwołania do zestawów systemu, System.Drawing i przestrzeń nazw System.Windows.Forms.</span><span class="sxs-lookup"><span data-stu-id="b6882-109">References to the System, System.Drawing and System.Windows.Forms assemblies.</span></span>  
  
 <span data-ttu-id="b6882-110">Aby dowiedzieć się, jak tworzyć aplikacje w tym przykładzie z wiersza polecenia dla języka Visual Basic lub Visual C#, zobacz [tworzenie z wiersza polecenia](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) lub [wiersza polecenia tworzenia przy użyciu csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="b6882-110">For information about building this example from the command line for Visual Basic or Visual C#, see [Building from the Command Line](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="b6882-111">Można także utworzyć tego przykładu w programie Visual Studio, wklejając kod do nowego projektu.</span><span class="sxs-lookup"><span data-stu-id="b6882-111">You can also build this example in Visual Studio by pasting the code into a new project.</span></span>  <span data-ttu-id="b6882-112">Zobacz też [porady: kompilowanie i uruchamianie pełną Windows Forms kodu przykładzie przy użyciu programu Visual Studio](https://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span><span class="sxs-lookup"><span data-stu-id="b6882-112">Also see [How to: Compile and Run a Complete Windows Forms Code Example Using Visual Studio](https://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b6882-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b6882-113">See Also</span></span>  
 <xref:System.Windows.Forms.MenuStrip>  
 <xref:System.Windows.Forms.ContextMenuStrip>  
 <xref:System.Windows.Forms.ToolStripDropDown>  
 [<span data-ttu-id="b6882-114">ToolStrip, kontrolka</span><span class="sxs-lookup"><span data-stu-id="b6882-114">ToolStrip Control</span></span>](../../../../docs/framework/winforms/controls/toolstrip-control-windows-forms.md)  
 [<span data-ttu-id="b6882-115">Instrukcje: włączanie marginesów zaznaczania i marginesów obrazów w kontrolkach ContextMenuStrip</span><span class="sxs-lookup"><span data-stu-id="b6882-115">How to: Enable Check Margins and Image Margins in ContextMenuStrip Controls</span></span>](../../../../docs/framework/winforms/controls/how-to-enable-check-margins-and-image-margins-in-contextmenustrip-controls.md)
