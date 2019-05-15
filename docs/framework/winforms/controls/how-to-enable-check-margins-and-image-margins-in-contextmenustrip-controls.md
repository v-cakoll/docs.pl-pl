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
ms.openlocfilehash: bf8440704a7e457d0c987c933cc26e0e12e9565f
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/14/2019
ms.locfileid: "65591693"
---
# <a name="how-to-enable-check-margins-and-image-margins-in-contextmenustrip-controls"></a><span data-ttu-id="128b7-102">Instrukcje: włączanie marginesów zaznaczania i marginesów obrazów w kontrolkach ContextMenuStrip</span><span class="sxs-lookup"><span data-stu-id="128b7-102">How to: Enable Check Margins and Image Margins in ContextMenuStrip Controls</span></span>
<span data-ttu-id="128b7-103">Można dostosować <xref:System.Windows.Forms.ToolStripMenuItem> obiekty w swojej <xref:System.Windows.Forms.MenuStrip> kontrolę dzięki znaczniki wyboru i obrazów niestandardowych.</span><span class="sxs-lookup"><span data-stu-id="128b7-103">You can customize the <xref:System.Windows.Forms.ToolStripMenuItem> objects in your <xref:System.Windows.Forms.MenuStrip> control with check marks and custom images.</span></span>  
  
## <a name="example"></a><span data-ttu-id="128b7-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="128b7-104">Example</span></span>  
 <span data-ttu-id="128b7-105">Poniższy przykład kodu pokazuje, jak utworzyć elementy menu, które mają znaczniki wyboru i obrazów niestandardowych.</span><span class="sxs-lookup"><span data-stu-id="128b7-105">The following code example demonstrates how to create menu items that have check marks and custom images.</span></span>  
  
 [!code-csharp[System.Windows.Forms.ToolStrip.Misc#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/CS/Program.cs#1)]
 [!code-vb[System.Windows.Forms.ToolStrip.Misc#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/VB/Program.vb#1)]  
[!code-csharp[System.Windows.Forms.ToolStrip.Misc#60](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/CS/Program.cs#60)]
[!code-vb[System.Windows.Forms.ToolStrip.Misc#60](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/VB/Program.vb#60)]  
  
 <span data-ttu-id="128b7-106">Ustaw <xref:System.Windows.Forms.ToolStripDropDownMenu.ShowCheckMargin%2A?displayProperty=nameWithType> i <xref:System.Windows.Forms.ToolStripDropDownMenu.ShowImageMargin%2A?displayProperty=nameWithType> właściwości, aby określić, kiedy znaczniki wyboru i obrazy niestandardowe są wyświetlane w elementów menu.</span><span class="sxs-lookup"><span data-stu-id="128b7-106">Set the <xref:System.Windows.Forms.ToolStripDropDownMenu.ShowCheckMargin%2A?displayProperty=nameWithType> and <xref:System.Windows.Forms.ToolStripDropDownMenu.ShowImageMargin%2A?displayProperty=nameWithType> properties to specify when check marks and custom images appear in your menu items.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="128b7-107">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="128b7-107">Compiling the Code</span></span>  
 <span data-ttu-id="128b7-108">Ten przykład wymaga:</span><span class="sxs-lookup"><span data-stu-id="128b7-108">This example requires:</span></span>  
  
- <span data-ttu-id="128b7-109">Odwołania do zestawów System.Design System.Drawing i przestrzeń nazw System.Windows.Forms.</span><span class="sxs-lookup"><span data-stu-id="128b7-109">References to the System.Design, System.Drawing, and System.Windows.Forms assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="128b7-110">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="128b7-110">See also</span></span>

- <xref:System.Windows.Forms.ToolStripMenuItem>
- <xref:System.Windows.Forms.ToolStripDropDownMenu>
- <xref:System.Windows.Forms.MenuStrip>
- <xref:System.Windows.Forms.ToolStrip>
- [<span data-ttu-id="128b7-111">ToolStrip, kontrolka</span><span class="sxs-lookup"><span data-stu-id="128b7-111">ToolStrip Control</span></span>](toolstrip-control-windows-forms.md)
