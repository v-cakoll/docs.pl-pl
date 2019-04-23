---
title: 'Instrukcje: włączanie marginesów zaznaczania i marginesów obrazów w kontrolkach ContextMenuStrip'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- toolbars [Windows Forms]
- ShowCheckMargin property [Windows Forms]
- ShowImageMargin property [Windows Forms]
- ToolStrip control [Windows Forms]
- MenuStrip control [Windows Forms]
ms.assetid: eb584e71-59da-4012-aaca-dbe1c7c7a156
ms.openlocfilehash: 80a6b5a7e3ce354abdfbe330a378566d47c011ad
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59170901"
---
# <a name="how-to-enable-check-margins-and-image-margins-in-contextmenustrip-controls"></a><span data-ttu-id="0bc91-102">Instrukcje: włączanie marginesów zaznaczania i marginesów obrazów w kontrolkach ContextMenuStrip</span><span class="sxs-lookup"><span data-stu-id="0bc91-102">How to: Enable Check Margins and Image Margins in ContextMenuStrip Controls</span></span>
<span data-ttu-id="0bc91-103">Można dostosować <xref:System.Windows.Forms.ToolStripMenuItem> obiekty w swojej <xref:System.Windows.Forms.MenuStrip> kontrolę dzięki znaczniki wyboru i obrazów niestandardowych.</span><span class="sxs-lookup"><span data-stu-id="0bc91-103">You can customize the <xref:System.Windows.Forms.ToolStripMenuItem> objects in your <xref:System.Windows.Forms.MenuStrip> control with check marks and custom images.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0bc91-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="0bc91-104">Example</span></span>  
 <span data-ttu-id="0bc91-105">Poniższy przykład kodu pokazuje, jak utworzyć elementy menu, które mają znaczniki wyboru i obrazów niestandardowych.</span><span class="sxs-lookup"><span data-stu-id="0bc91-105">The following code example demonstrates how to create menu items that have check marks and custom images.</span></span>  
  
 [!code-csharp[System.Windows.Forms.ToolStrip.Misc#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/CS/Program.cs#1)]
 [!code-vb[System.Windows.Forms.ToolStrip.Misc#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/VB/Program.vb#1)]  
[!code-csharp[System.Windows.Forms.ToolStrip.Misc#60](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/CS/Program.cs#60)]
[!code-vb[System.Windows.Forms.ToolStrip.Misc#60](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/VB/Program.vb#60)]  
  
 <span data-ttu-id="0bc91-106">Ustaw <xref:System.Windows.Forms.ToolStripDropDownMenu.ShowCheckMargin%2A?displayProperty=nameWithType> i <xref:System.Windows.Forms.ToolStripDropDownMenu.ShowImageMargin%2A?displayProperty=nameWithType> właściwości, aby określić, kiedy znaczniki wyboru i obrazy niestandardowe są wyświetlane w elementów menu.</span><span class="sxs-lookup"><span data-stu-id="0bc91-106">Set the <xref:System.Windows.Forms.ToolStripDropDownMenu.ShowCheckMargin%2A?displayProperty=nameWithType> and <xref:System.Windows.Forms.ToolStripDropDownMenu.ShowImageMargin%2A?displayProperty=nameWithType> properties to specify when check marks and custom images appear in your menu items.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="0bc91-107">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="0bc91-107">Compiling the Code</span></span>  
 <span data-ttu-id="0bc91-108">Ten przykład wymaga:</span><span class="sxs-lookup"><span data-stu-id="0bc91-108">This example requires:</span></span>  
  
-   <span data-ttu-id="0bc91-109">Odwołania do zestawów System.Design System.Drawing i przestrzeń nazw System.Windows.Forms.</span><span class="sxs-lookup"><span data-stu-id="0bc91-109">References to the System.Design, System.Drawing, and System.Windows.Forms assemblies.</span></span>  
  
 <span data-ttu-id="0bc91-110">Aby dowiedzieć się, jak tworzyć aplikacje w tym przykładzie z wiersza polecenia dla języka Visual Basic lub Visual C#, zobacz [tworzenie z wiersza polecenia](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) lub [wiersza polecenia tworzenia przy użyciu csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="0bc91-110">For information about building this example from the command line for Visual Basic or Visual C#, see [Building from the Command Line](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="0bc91-111">Można także utworzyć tego przykładu w programie Visual Studio, wklejając kod do nowego projektu.</span><span class="sxs-lookup"><span data-stu-id="0bc91-111">You can also build this example in Visual Studio by pasting the code into a new project.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0bc91-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="0bc91-112">See also</span></span>

- <xref:System.Windows.Forms.ToolStripMenuItem>
- <xref:System.Windows.Forms.ToolStripDropDownMenu>
- <xref:System.Windows.Forms.MenuStrip>
- <xref:System.Windows.Forms.ToolStrip>
- [<span data-ttu-id="0bc91-113">ToolStrip, kontrolka</span><span class="sxs-lookup"><span data-stu-id="0bc91-113">ToolStrip Control</span></span>](toolstrip-control-windows-forms.md)
