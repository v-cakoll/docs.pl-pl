---
title: 'Instrukcje: definiowanie porządku osi Z zadokowanych kontrolek ToolStrip'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ToolStrip control [Windows Forms]
- MenuStrip control [Windows Forms]
- toolbars [Windows Forms], specifying z-order
- z-order
ms.assetid: 8b595429-ba9f-46af-9c55-3d5cc53f7fff
ms.openlocfilehash: 514c9dd1c91adcadf6f5d383ba734886dec3151d
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/14/2019
ms.locfileid: "65591907"
---
# <a name="how-to-define-z-ordering-of-docked-toolstrip-controls"></a><span data-ttu-id="e5694-102">Instrukcje: definiowanie porządku osi Z zadokowanych kontrolek ToolStrip</span><span class="sxs-lookup"><span data-stu-id="e5694-102">How to: Define Z-Ordering of Docked ToolStrip Controls</span></span>
<span data-ttu-id="e5694-103">Położenie <xref:System.Windows.Forms.ToolStrip> kontroli poprawnie za pomocą dokowania, należy umieścić formant poprawnie w kolejności z formularza.</span><span class="sxs-lookup"><span data-stu-id="e5694-103">To position a <xref:System.Windows.Forms.ToolStrip> control correctly with docking, you must position the control correctly in the form's z-order.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e5694-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="e5694-104">Example</span></span>  
 <span data-ttu-id="e5694-105">Poniższy przykład kodu demonstruje sposób rozmieszczenia <xref:System.Windows.Forms.ToolStrip> kontroli i zadokowany <xref:System.Windows.Forms.MenuStrip> kontroli przez określenie porządku osi z.</span><span class="sxs-lookup"><span data-stu-id="e5694-105">The following code example demonstrates how to arrange a <xref:System.Windows.Forms.ToolStrip> control and a docked <xref:System.Windows.Forms.MenuStrip> control by specifying the z-order.</span></span>  
  
 [!code-csharp[System.Windows.Forms.ToolStrip.Misc#21](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/CS/Program.cs#21)]
 [!code-vb[System.Windows.Forms.ToolStrip.Misc#21](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/VB/Program.vb#21)]  
  
 <span data-ttu-id="e5694-106">Kolejność jest określana przez kolejność, w której <xref:System.Windows.Forms.ToolStrip> i <xref:System.Windows.Forms.MenuStrip></span><span class="sxs-lookup"><span data-stu-id="e5694-106">The z-order is determined by the order in which the <xref:System.Windows.Forms.ToolStrip> and <xref:System.Windows.Forms.MenuStrip></span></span>  
  
 <span data-ttu-id="e5694-107">Formanty są dodawane do formularza <xref:System.Windows.Forms.Control.Controls%2A> kolekcji.</span><span class="sxs-lookup"><span data-stu-id="e5694-107">controls are added to the form's <xref:System.Windows.Forms.Control.Controls%2A> collection.</span></span>  
  
 [!code-csharp[System.Windows.Forms.ToolStrip.Misc#23](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/CS/Program.cs#23)]
 [!code-vb[System.Windows.Forms.ToolStrip.Misc#23](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/VB/Program.vb#23)]  
  
 <span data-ttu-id="e5694-108">Odwracanie kolejności tych wywołań <xref:System.Windows.Forms.Control.ControlCollection.Add%2A> metody i widoku. wpływa na układ.</span><span class="sxs-lookup"><span data-stu-id="e5694-108">Reverse the order of these calls to the <xref:System.Windows.Forms.Control.ControlCollection.Add%2A> method and view the effect on the layout.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="e5694-109">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="e5694-109">Compiling the Code</span></span>  
 <span data-ttu-id="e5694-110">Ten przykład wymaga:</span><span class="sxs-lookup"><span data-stu-id="e5694-110">This example requires:</span></span>  
  
- <span data-ttu-id="e5694-111">Odwołania do zestawów System.Design System.Drawing i przestrzeń nazw System.Windows.Forms.</span><span class="sxs-lookup"><span data-stu-id="e5694-111">References to the System.Design, System.Drawing, and System.Windows.Forms assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e5694-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e5694-112">See also</span></span>

- <xref:System.Windows.Forms.MenuStrip>
- <xref:System.Windows.Forms.ToolStrip>
- <xref:System.Windows.Forms.Control.ControlCollection.Add%2A>
- <xref:System.Windows.Forms.Control.Controls%2A>
- <xref:System.Windows.Forms.Control.Dock%2A>
- [<span data-ttu-id="e5694-113">ToolStrip, kontrolka</span><span class="sxs-lookup"><span data-stu-id="e5694-113">ToolStrip Control</span></span>](toolstrip-control-windows-forms.md)
