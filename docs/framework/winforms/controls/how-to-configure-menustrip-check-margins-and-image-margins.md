---
title: 'Instrukcje: konfiguracja marginesów zaznaczania MenuStrip i marginesów obrazu'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- margins [Windows Forms], setting in MenuStrip controls
- menus [Windows Forms], setting margins
- MenuStrip control [Windows Forms], configuring check and image margins
ms.assetid: 45a9075d-4bea-4ce2-9b2c-7619aa39f8ce
ms.openlocfilehash: fa099012fa77daacd1f428e64abd662ee1738f84
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/14/2019
ms.locfileid: "65586585"
---
# <a name="how-to-configure-menustrip-check-margins-and-image-margins"></a><span data-ttu-id="0ac80-102">Instrukcje: konfiguracja marginesów zaznaczania MenuStrip i marginesów obrazu</span><span class="sxs-lookup"><span data-stu-id="0ac80-102">How to: Configure MenuStrip Check Margins and Image Margins</span></span>
<span data-ttu-id="0ac80-103">Można dostosować <xref:System.Windows.Forms.MenuStrip> , ustawiając <xref:System.Windows.Forms.ToolStripDropDownMenu.ShowImageMargin%2A> i <xref:System.Windows.Forms.ToolStripDropDownMenu.ShowCheckMargin%2A> właściwości w różnych kombinacjach.</span><span class="sxs-lookup"><span data-stu-id="0ac80-103">You can customize a <xref:System.Windows.Forms.MenuStrip> by setting the <xref:System.Windows.Forms.ToolStripDropDownMenu.ShowImageMargin%2A> and <xref:System.Windows.Forms.ToolStripDropDownMenu.ShowCheckMargin%2A> properties in various combinations.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0ac80-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="0ac80-104">Example</span></span>  
 <span data-ttu-id="0ac80-105">Poniższy przykład kodu demonstruje sposób ustawiania i dostosować <xref:System.Windows.Forms.ContextMenuStrip> Sprawdź marginesów zaznaczania i marginesów obrazu.</span><span class="sxs-lookup"><span data-stu-id="0ac80-105">The following code example demonstrates how to set and customize the <xref:System.Windows.Forms.ContextMenuStrip> check margins and image margins.</span></span> <span data-ttu-id="0ac80-106">Procedura jest taka sama dla <xref:System.Windows.Forms.ContextMenuStrip> lub <xref:System.Windows.Forms.MenuStrip>.</span><span class="sxs-lookup"><span data-stu-id="0ac80-106">The procedure is the same for a <xref:System.Windows.Forms.ContextMenuStrip> or a <xref:System.Windows.Forms.MenuStrip>.</span></span>  
  
 [!code-csharp[System.Windows.Forms.ToolStrip.Misc#60](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/CS/Program.cs#60)]
 [!code-vb[System.Windows.Forms.ToolStrip.Misc#60](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/VB/Program.vb#60)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="0ac80-107">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="0ac80-107">Compiling the Code</span></span>  
 <span data-ttu-id="0ac80-108">Ten przykład wymaga:</span><span class="sxs-lookup"><span data-stu-id="0ac80-108">This example requires:</span></span>  
  
- <span data-ttu-id="0ac80-109">Odwołania do zestawów systemu, System.Drawing i przestrzeń nazw System.Windows.Forms.</span><span class="sxs-lookup"><span data-stu-id="0ac80-109">References to the System, System.Drawing and System.Windows.Forms assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0ac80-110">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="0ac80-110">See also</span></span>

- <xref:System.Windows.Forms.MenuStrip>
- <xref:System.Windows.Forms.ContextMenuStrip>
- <xref:System.Windows.Forms.ToolStripDropDown>
- [<span data-ttu-id="0ac80-111">ToolStrip, kontrolka</span><span class="sxs-lookup"><span data-stu-id="0ac80-111">ToolStrip Control</span></span>](toolstrip-control-windows-forms.md)
- [<span data-ttu-id="0ac80-112">Instrukcje: Włączanie marginesów zaznaczania i marginesów obrazów w formantach ContextMenuStrip</span><span class="sxs-lookup"><span data-stu-id="0ac80-112">How to: Enable Check Margins and Image Margins in ContextMenuStrip Controls</span></span>](how-to-enable-check-margins-and-image-margins-in-contextmenustrip-controls.md)
