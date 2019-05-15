---
title: 'Instrukcje: skojarzenie właściwości ContextMenuStrip z kontrolką'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- context menus [Windows Forms], relating
- ContextMenuStrips [Windows Forms], associating with controls
- context menus [Windows Forms], associating with controls
- ContextMenuStrips [Windows Forms], relating
ms.assetid: 6fc40a42-5d69-427f-aa30-0a146193226b
ms.openlocfilehash: e1b2a49196d6da66d478a3d44eab64298cebe969
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/14/2019
ms.locfileid: "65586602"
---
# <a name="how-to-associate-a-contextmenustrip-with-a-control"></a><span data-ttu-id="9d267-102">Instrukcje: skojarzenie właściwości ContextMenuStrip z kontrolką</span><span class="sxs-lookup"><span data-stu-id="9d267-102">How to: Associate a ContextMenuStrip with a Control</span></span>
<span data-ttu-id="9d267-103">Po utworzeniu menu skrótów i kontrolki, na których należy użyć poniższych procedur do wyświetlenia menu skrótów danego, gdy użytkownik kliknie prawym przyciskiem myszy formant.</span><span class="sxs-lookup"><span data-stu-id="9d267-103">After creating your controls and shortcut menus, use the following procedures to display a given shortcut menu when the user right-clicks the control.</span></span> <span data-ttu-id="9d267-104">Te procedury skojarzyć <xref:System.Windows.Forms.ContextMenuStrip> z formularza Windows i <xref:System.Windows.Forms.ToolStrip> kontroli.</span><span class="sxs-lookup"><span data-stu-id="9d267-104">These procedures associate a <xref:System.Windows.Forms.ContextMenuStrip> with a Windows Form and with a <xref:System.Windows.Forms.ToolStrip> control.</span></span>  
  
### <a name="to-associate-a-contextmenustrip-with-a-windows-form"></a><span data-ttu-id="9d267-105">Aby skojarzenie właściwości ContextMenuStrip z formularzem Windows</span><span class="sxs-lookup"><span data-stu-id="9d267-105">To associate a ContextMenuStrip with a Windows Form</span></span>  
  
1. <span data-ttu-id="9d267-106">Ustaw <xref:System.Windows.Forms.Control.ContextMenuStrip%2A> właściwość na nazwę skojarzonego <xref:System.Windows.Forms.ContextMenuStrip>.</span><span class="sxs-lookup"><span data-stu-id="9d267-106">Set the <xref:System.Windows.Forms.Control.ContextMenuStrip%2A> property to the name of the associated <xref:System.Windows.Forms.ContextMenuStrip>.</span></span>  
  
### <a name="to-associate-a-contextmenustrip-with-a-toolstrip-control"></a><span data-ttu-id="9d267-107">Aby skojarzyć kontrolki ContextMenuStrip z formantu ToolStrip</span><span class="sxs-lookup"><span data-stu-id="9d267-107">To associate a ContextMenuStrip with a ToolStrip control</span></span>  
  
1. <span data-ttu-id="9d267-108">Ustaw dla formantu <xref:System.Windows.Forms.Control.ContextMenuStrip%2A> właściwość na nazwę skojarzonego <xref:System.Windows.Forms.ContextMenuStrip>.</span><span class="sxs-lookup"><span data-stu-id="9d267-108">Set the control's <xref:System.Windows.Forms.Control.ContextMenuStrip%2A> property to the name of the associated <xref:System.Windows.Forms.ContextMenuStrip>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9d267-109">Przykład</span><span class="sxs-lookup"><span data-stu-id="9d267-109">Example</span></span>  
 <span data-ttu-id="9d267-110">Poniższy przykład kodu tworzy formularz Windows i <xref:System.Windows.Forms.ToolStrip>i kojarzy innego <xref:System.Windows.Forms.ContextMenuStrip> kontrolki z każdym z nich.</span><span class="sxs-lookup"><span data-stu-id="9d267-110">The following code example creates a Windows Form and a <xref:System.Windows.Forms.ToolStrip>, and associates a different <xref:System.Windows.Forms.ContextMenuStrip> control with each of them.</span></span>  
  
 [!code-csharp[System.Windows.Forms.ContextMenuStrip#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ContextMenuStrip/CS/form1.cs#1)]
 [!code-vb[System.Windows.Forms.ContextMenuStrip#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ContextMenuStrip/VB/form1.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="9d267-111">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="9d267-111">Compiling the Code</span></span>  
 <span data-ttu-id="9d267-112">Ten przykład wymaga:</span><span class="sxs-lookup"><span data-stu-id="9d267-112">This example requires:</span></span>  
  
- <span data-ttu-id="9d267-113">Odwołania do zestawów systemu, dane systemowe i System.Drawing oraz przestrzeń nazw System.Windows.Forms.</span><span class="sxs-lookup"><span data-stu-id="9d267-113">References to the System, System.Data, System.Drawing and System.Windows.Forms assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9d267-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="9d267-114">See also</span></span>

- <xref:System.Windows.Forms.ContextMenuStrip>
- <xref:System.Windows.Forms.Control.ContextMenuStrip%2A>
- <xref:System.Windows.Forms.ToolStrip>
- [<span data-ttu-id="9d267-115">Instrukcje: Dodawanie elementów Menu do paska ContextMenuStrip</span><span class="sxs-lookup"><span data-stu-id="9d267-115">How to: Add Menu Items to a ContextMenuStrip</span></span>](how-to-add-menu-items-to-a-contextmenustrip.md)
- [<span data-ttu-id="9d267-116">ContextMenuStrip, kontrolka</span><span class="sxs-lookup"><span data-stu-id="9d267-116">ContextMenuStrip Control</span></span>](contextmenustrip-control.md)
