---
title: 'Instrukcje: dynamiczne dodawanie elementów ToolStrip'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ContextMenuStrip control [Windows Forms]
- toolbars [Windows Forms], adding items dynamically
- ToolStrip control [Windows Forms]
ms.assetid: 0e8dea56-5f46-408b-914d-7e360341a234
ms.openlocfilehash: 08d08a292995cc5e12fbab3e91a0962c3b895a02
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/14/2019
ms.locfileid: "65588879"
---
# <a name="how-to-add-toolstrip-items-dynamically"></a><span data-ttu-id="0f8b7-102">Instrukcje: dynamiczne dodawanie elementów ToolStrip</span><span class="sxs-lookup"><span data-stu-id="0f8b7-102">How to: Add ToolStrip Items Dynamically</span></span>
<span data-ttu-id="0f8b7-103">Możesz dynamicznie wypełnić kolekcję elementów menu <xref:System.Windows.Forms.ToolStrip> kontrolować, po otwarciu menu.</span><span class="sxs-lookup"><span data-stu-id="0f8b7-103">You can dynamically populate the menu item collection of a <xref:System.Windows.Forms.ToolStrip> control when the menu opens.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0f8b7-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="0f8b7-104">Example</span></span>  
 <span data-ttu-id="0f8b7-105">Poniższy przykład kodu pokazuje, jak dynamicznie dodać elementy do <xref:System.Windows.Forms.ContextMenuStrip> kontroli.</span><span class="sxs-lookup"><span data-stu-id="0f8b7-105">The following code example demonstrates how to dynamically add items to a <xref:System.Windows.Forms.ContextMenuStrip> control.</span></span> <span data-ttu-id="0f8b7-106">W przykładzie pokazano również sposób ponownie użyj tego samego <xref:System.Windows.Forms.ContextMenuStrip> dla trzech różnych kontrolek w formularzu.</span><span class="sxs-lookup"><span data-stu-id="0f8b7-106">The example also shows how to reuse the same <xref:System.Windows.Forms.ContextMenuStrip> for three different controls on the form.</span></span>  
  
 <span data-ttu-id="0f8b7-107">W tym przykładzie <xref:System.Windows.Forms.ToolStripDropDown.Opening> program obsługi zdarzeń wypełnia kolekcję elementów menu.</span><span class="sxs-lookup"><span data-stu-id="0f8b7-107">In the example, an <xref:System.Windows.Forms.ToolStripDropDown.Opening> event handler populates the menu item collection.</span></span> <span data-ttu-id="0f8b7-108"><xref:System.Windows.Forms.ToolStripDropDown.Opening> Sprawdza, czy program obsługi zdarzeń <xref:System.Windows.Forms.ContextMenuStrip.SourceControl%2A?displayProperty=nameWithType> i <xref:System.Windows.Forms.ToolStripItem.OwnerItem%2A?displayProperty=nameWithType> właściwości i dodaje <xref:System.Windows.Forms.ToolStripItem> opisujące kontroli źródła.</span><span class="sxs-lookup"><span data-stu-id="0f8b7-108">The <xref:System.Windows.Forms.ToolStripDropDown.Opening> event handler examines the <xref:System.Windows.Forms.ContextMenuStrip.SourceControl%2A?displayProperty=nameWithType> and <xref:System.Windows.Forms.ToolStripItem.OwnerItem%2A?displayProperty=nameWithType> properties and adds a <xref:System.Windows.Forms.ToolStripItem> describing the source control.</span></span>  
  
 [!code-csharp[System.Windows.Forms.ToolStrip.Misc#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/CS/Program.cs#1)]
 [!code-vb[System.Windows.Forms.ToolStrip.Misc#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/VB/Program.vb#1)]  
[!code-csharp[System.Windows.Forms.ToolStrip.Misc#40](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/CS/Program.cs#40)]
[!code-vb[System.Windows.Forms.ToolStrip.Misc#40](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/VB/Program.vb#40)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="0f8b7-109">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="0f8b7-109">Compiling the Code</span></span>  
 <span data-ttu-id="0f8b7-110">Ten przykład wymaga:</span><span class="sxs-lookup"><span data-stu-id="0f8b7-110">This example requires:</span></span>  
  
- <span data-ttu-id="0f8b7-111">Odwołania do zestawów System.Drawing i pozycję System.Windows.Forms.</span><span class="sxs-lookup"><span data-stu-id="0f8b7-111">References to the System.Drawing and System.Windows.Forms assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0f8b7-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="0f8b7-112">See also</span></span>

- <xref:System.Windows.Forms.ContextMenuStrip>
- <xref:System.Windows.Forms.MenuStrip>
- <xref:System.Windows.Forms.ToolStrip>
- <xref:System.Windows.Forms.ToolStripItem>
- <xref:System.Windows.Forms.ToolStripMenuItem>
- <xref:System.Windows.Forms.ToolStripDropDownButton>
- [<span data-ttu-id="0f8b7-113">ToolStrip, kontrolka</span><span class="sxs-lookup"><span data-stu-id="0f8b7-113">ToolStrip Control</span></span>](toolstrip-control-windows-forms.md)
