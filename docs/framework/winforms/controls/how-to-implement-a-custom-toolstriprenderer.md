---
title: 'Instrukcje: implementowanie niestandardowego elementu ToolStripRenderer'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- toolbars [Windows Forms]
- ToolStrip control [Windows Forms]
ms.assetid: c66fd3f7-2377-4553-8f1b-006527f08f32
ms.openlocfilehash: 4a84571bf8b81cd26c864edcd4d313a4009dda16
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/14/2019
ms.locfileid: "65592427"
---
# <a name="how-to-implement-a-custom-toolstriprenderer"></a><span data-ttu-id="9c9b5-102">Instrukcje: implementowanie niestandardowego elementu ToolStripRenderer</span><span class="sxs-lookup"><span data-stu-id="9c9b5-102">How to: Implement a Custom ToolStripRenderer</span></span>
<span data-ttu-id="9c9b5-103">Można dostosować wygląd <xref:System.Windows.Forms.ToolStrip> kontroli poprzez implementację klasy, która pochodzi od klasy <xref:System.Windows.Forms.ToolStripRenderer>.</span><span class="sxs-lookup"><span data-stu-id="9c9b5-103">You can customize the appearance of a <xref:System.Windows.Forms.ToolStrip> control by implementing a class that derives from <xref:System.Windows.Forms.ToolStripRenderer>.</span></span> <span data-ttu-id="9c9b5-104">Daje to możliwość tworzenia wrażenie, że różni się od wyglądem, pod warunkiem <xref:System.Windows.Forms.ToolStripProfessionalRenderer> i <xref:System.Windows.Forms.ToolStripSystemRenderer> klasy.</span><span class="sxs-lookup"><span data-stu-id="9c9b5-104">This gives you the flexibility to create an appearance that differs from the appearance provided the <xref:System.Windows.Forms.ToolStripProfessionalRenderer> and <xref:System.Windows.Forms.ToolStripSystemRenderer> classes.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9c9b5-105">Przykład</span><span class="sxs-lookup"><span data-stu-id="9c9b5-105">Example</span></span>  
 <span data-ttu-id="9c9b5-106">Poniższy przykład kodu demonstruje sposób implementacji niestandardowego <xref:System.Windows.Forms.ToolStripRenderer> klasy.</span><span class="sxs-lookup"><span data-stu-id="9c9b5-106">The following code example demonstrates how to implement a custom <xref:System.Windows.Forms.ToolStripRenderer> class.</span></span> <span data-ttu-id="9c9b5-107">W tym przykładzie `GridStrip` kontrolka implementuje układanki przedłużanie Kafelek, który umożliwia użytkownikowi przenoszenie kafelków w układzie tabeli w celu utworzenia obrazu.</span><span class="sxs-lookup"><span data-stu-id="9c9b5-107">In this example, the `GridStrip` control implements a sliding-tile puzzle, which allows the user to move tiles in a table layout to form an image.</span></span> <span data-ttu-id="9c9b5-108">Niestandardowy <xref:System.Windows.Forms.ToolStrip> rozmieszcza kontroli jego <xref:System.Windows.Forms.ToolStripButton> formantów w układzie siatki.</span><span class="sxs-lookup"><span data-stu-id="9c9b5-108">A custom <xref:System.Windows.Forms.ToolStrip> control arranges its <xref:System.Windows.Forms.ToolStripButton> controls in a grid layout.</span></span> <span data-ttu-id="9c9b5-109">Układ zawiera jedną pustą komórkę, do którego użytkownik może slajd sąsiadujących Kafelek przy użyciu operacji przeciągania i upuszczania.</span><span class="sxs-lookup"><span data-stu-id="9c9b5-109">The layout contains one empty cell, into which the user can slide an adjacent tile by using a drag-and-drop operation.</span></span> <span data-ttu-id="9c9b5-110">Kafelki, które użytkownik może przenieść są wyróżnione.</span><span class="sxs-lookup"><span data-stu-id="9c9b5-110">Tiles that the user can move are highlighted.</span></span>  
  
 <span data-ttu-id="9c9b5-111">`GridStripRenderer` Klasy dostosowuje trzy aspekty `GridStrip` wygląd formantu:</span><span class="sxs-lookup"><span data-stu-id="9c9b5-111">The `GridStripRenderer` class customizes three aspects of the `GridStrip` control's appearance:</span></span>  
  
- <span data-ttu-id="9c9b5-112">`GridStrip` Obramowanie</span><span class="sxs-lookup"><span data-stu-id="9c9b5-112">`GridStrip` border</span></span>  
  
- <span data-ttu-id="9c9b5-113"><xref:System.Windows.Forms.ToolStripButton> Obramowanie</span><span class="sxs-lookup"><span data-stu-id="9c9b5-113"><xref:System.Windows.Forms.ToolStripButton> border</span></span>  
  
- <span data-ttu-id="9c9b5-114"><xref:System.Windows.Forms.ToolStripButton> Obraz</span><span class="sxs-lookup"><span data-stu-id="9c9b5-114"><xref:System.Windows.Forms.ToolStripButton> image</span></span>  
  
 [!code-csharp[System.Windows.Forms.ToolStrip.GridStrip#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.GridStrip/CS/GridStrip.cs#1)]
 [!code-vb[System.Windows.Forms.ToolStrip.GridStrip#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.GridStrip/VB/GridStrip.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="9c9b5-115">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="9c9b5-115">Compiling the Code</span></span>  
 <span data-ttu-id="9c9b5-116">Ten przykład wymaga:</span><span class="sxs-lookup"><span data-stu-id="9c9b5-116">This example requires:</span></span>  
  
- <span data-ttu-id="9c9b5-117">Odwołania do zestawów System.Drawing i pozycję System.Windows.Forms.</span><span class="sxs-lookup"><span data-stu-id="9c9b5-117">References to the System.Drawing and System.Windows.Forms assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9c9b5-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="9c9b5-118">See also</span></span>

- <xref:System.Windows.Forms.MenuStrip>
- <xref:System.Windows.Forms.ToolStrip>
- <xref:System.Windows.Forms.ToolStripRenderer>
- <xref:System.Windows.Forms.ToolStripProfessionalRenderer>
- <xref:System.Windows.Forms.ToolStripSystemRenderer>
- <xref:System.Windows.Forms.StatusStrip>
- [<span data-ttu-id="9c9b5-119">ToolStrip, kontrolka</span><span class="sxs-lookup"><span data-stu-id="9c9b5-119">ToolStrip Control</span></span>](toolstrip-control-windows-forms.md)
