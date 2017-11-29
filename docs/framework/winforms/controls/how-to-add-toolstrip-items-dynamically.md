---
title: "Porady: dynamiczne dodawanie elementów ToolStrip"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ContextMenuStrip control [Windows Forms]
- toolbars [Windows Forms], adding items dynamically
- ToolStrip control [Windows Forms]
ms.assetid: 0e8dea56-5f46-408b-914d-7e360341a234
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: c7287365013ecd32d5ade6fa61d6c13364ce9b97
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-add-toolstrip-items-dynamically"></a><span data-ttu-id="f1b8d-102">Porady: dynamiczne dodawanie elementów ToolStrip</span><span class="sxs-lookup"><span data-stu-id="f1b8d-102">How to: Add ToolStrip Items Dynamically</span></span>
<span data-ttu-id="f1b8d-103">Dynamiczne można wypełnić kolekcji elementów menu z <xref:System.Windows.Forms.ToolStrip> kontroli, gdy zostanie otwarte menu.</span><span class="sxs-lookup"><span data-stu-id="f1b8d-103">You can dynamically populate the menu item collection of a <xref:System.Windows.Forms.ToolStrip> control when the menu opens.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f1b8d-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="f1b8d-104">Example</span></span>  
 <span data-ttu-id="f1b8d-105">W poniższym przykładzie pokazano, jak dynamiczne dodawanie elementów do <xref:System.Windows.Forms.ContextMenuStrip> formantu.</span><span class="sxs-lookup"><span data-stu-id="f1b8d-105">The following code example demonstrates how to dynamically add items to a <xref:System.Windows.Forms.ContextMenuStrip> control.</span></span> <span data-ttu-id="f1b8d-106">W przykładzie przedstawiono również sposób ponownie użyj tego samego <xref:System.Windows.Forms.ContextMenuStrip> dla trzech różnych kontrolek w formularzu.</span><span class="sxs-lookup"><span data-stu-id="f1b8d-106">The example also shows how to reuse the same <xref:System.Windows.Forms.ContextMenuStrip> for three different controls on the form.</span></span>  
  
 <span data-ttu-id="f1b8d-107">W tym przykładzie <xref:System.Windows.Forms.ToolStripDropDown.Opening> obsługi zdarzenia wypełnia kolekcję elementów menu.</span><span class="sxs-lookup"><span data-stu-id="f1b8d-107">In the example, an <xref:System.Windows.Forms.ToolStripDropDown.Opening> event handler populates the menu item collection.</span></span> <span data-ttu-id="f1b8d-108"><xref:System.Windows.Forms.ToolStripDropDown.Opening> Sprawdza, czy program obsługi zdarzeń <xref:System.Windows.Forms.ContextMenuStrip.SourceControl%2A?displayProperty=nameWithType> i <xref:System.Windows.Forms.ToolStripItem.OwnerItem%2A?displayProperty=nameWithType> właściwości i dodaje <xref:System.Windows.Forms.ToolStripItem> opisujące kontroli źródła.</span><span class="sxs-lookup"><span data-stu-id="f1b8d-108">The <xref:System.Windows.Forms.ToolStripDropDown.Opening> event handler examines the <xref:System.Windows.Forms.ContextMenuStrip.SourceControl%2A?displayProperty=nameWithType> and <xref:System.Windows.Forms.ToolStripItem.OwnerItem%2A?displayProperty=nameWithType> properties and adds a <xref:System.Windows.Forms.ToolStripItem> describing the source control.</span></span>  
  
 [!code-csharp[System.Windows.Forms.ToolStrip.Misc#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/CS/Program.cs#1)]
 [!code-vb[System.Windows.Forms.ToolStrip.Misc#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/VB/Program.vb#1)]  
[!code-csharp[System.Windows.Forms.ToolStrip.Misc#40](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/CS/Program.cs#40)]
[!code-vb[System.Windows.Forms.ToolStrip.Misc#40](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/VB/Program.vb#40)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="f1b8d-109">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="f1b8d-109">Compiling the Code</span></span>  
 <span data-ttu-id="f1b8d-110">Ten przykład wymaga:</span><span class="sxs-lookup"><span data-stu-id="f1b8d-110">This example requires:</span></span>  
  
-   <span data-ttu-id="f1b8d-111">Odwołania do zestawów System.Drawing i System.Windows.Forms.</span><span class="sxs-lookup"><span data-stu-id="f1b8d-111">References to the System.Drawing and System.Windows.Forms assemblies.</span></span>  
  
 <span data-ttu-id="f1b8d-112">Informacji dotyczących tworzenia tego przykładu z wiersza polecenia dla [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] lub [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)], zobacz [tworzenie z wiersza polecenia](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) lub [kompilowania z wiersza polecenia csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="f1b8d-112">For information about building this example from the command line for [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] or [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)], see [Building from the Command Line](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="f1b8d-113">Można także utworzyć tym przykładzie [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] przez wklejenie kodu do nowego projektu.</span><span class="sxs-lookup"><span data-stu-id="f1b8d-113">You can also build this example in [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] by pasting the code into a new project.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f1b8d-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f1b8d-114">See Also</span></span>  
 <xref:System.Windows.Forms.ContextMenuStrip>  
 <xref:System.Windows.Forms.MenuStrip>  
 <xref:System.Windows.Forms.ToolStrip>  
 <xref:System.Windows.Forms.ToolStripItem>  
 <xref:System.Windows.Forms.ToolStripMenuItem>  
 <xref:System.Windows.Forms.ToolStripDropDownButton>  
 [<span data-ttu-id="f1b8d-115">ToolStrip — formant</span><span class="sxs-lookup"><span data-stu-id="f1b8d-115">ToolStrip Control</span></span>](../../../../docs/framework/winforms/controls/toolstrip-control-windows-forms.md)
