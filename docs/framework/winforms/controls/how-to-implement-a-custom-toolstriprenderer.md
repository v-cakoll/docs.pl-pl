---
title: 'Porady: implementowanie niestandardowego elementu ToolStripRenderer'
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-winforms
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- toolbars [Windows Forms]
- ToolStrip control [Windows Forms]
ms.assetid: c66fd3f7-2377-4553-8f1b-006527f08f32
caps.latest.revision: 9
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: e403cf958840e9b94989dbd782f783675e7c31bc
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-implement-a-custom-toolstriprenderer"></a><span data-ttu-id="804f2-102">Porady: implementowanie niestandardowego elementu ToolStripRenderer</span><span class="sxs-lookup"><span data-stu-id="804f2-102">How to: Implement a Custom ToolStripRenderer</span></span>
<span data-ttu-id="804f2-103">Można dostosować wygląd <xref:System.Windows.Forms.ToolStrip> kontroli dzięki implementacji klasy, która jest pochodną <xref:System.Windows.Forms.ToolStripRenderer>.</span><span class="sxs-lookup"><span data-stu-id="804f2-103">You can customize the appearance of a <xref:System.Windows.Forms.ToolStrip> control by implementing a class that derives from <xref:System.Windows.Forms.ToolStripRenderer>.</span></span> <span data-ttu-id="804f2-104">Daje to możliwość tworzenia wyglądu, która różni się od wygląd podane <xref:System.Windows.Forms.ToolStripProfessionalRenderer> i <xref:System.Windows.Forms.ToolStripSystemRenderer> klasy.</span><span class="sxs-lookup"><span data-stu-id="804f2-104">This gives you the flexibility to create an appearance that differs from the appearance provided the <xref:System.Windows.Forms.ToolStripProfessionalRenderer> and <xref:System.Windows.Forms.ToolStripSystemRenderer> classes.</span></span>  
  
## <a name="example"></a><span data-ttu-id="804f2-105">Przykład</span><span class="sxs-lookup"><span data-stu-id="804f2-105">Example</span></span>  
 <span data-ttu-id="804f2-106">Poniższy przykładowy kod przedstawia sposób zaimplementowania niestandardowego <xref:System.Windows.Forms.ToolStripRenderer> klasy.</span><span class="sxs-lookup"><span data-stu-id="804f2-106">The following code example demonstrates how to implement a custom <xref:System.Windows.Forms.ToolStripRenderer> class.</span></span> <span data-ttu-id="804f2-107">W tym przykładzie `GridStrip` kontroli implementuje układanki przedłużanie kafelka, dzięki czemu użytkownik może przechodzić Kafelki w układzie tabeli do utworzenia obrazu.</span><span class="sxs-lookup"><span data-stu-id="804f2-107">In this example, the `GridStrip` control implements a sliding-tile puzzle, which allows the user to move tiles in a table layout to form an image.</span></span> <span data-ttu-id="804f2-108">Niestandardowy <xref:System.Windows.Forms.ToolStrip> rozmieszcza kontroli jego <xref:System.Windows.Forms.ToolStripButton> formantów w układzie siatki.</span><span class="sxs-lookup"><span data-stu-id="804f2-108">A custom <xref:System.Windows.Forms.ToolStrip> control arranges its <xref:System.Windows.Forms.ToolStripButton> controls in a grid layout.</span></span> <span data-ttu-id="804f2-109">Układ zawiera jedną komórkę pusta, do którego użytkownik może slajd kafelka sąsiadujących ze sobą przy użyciu operacji przeciągania i upuszczania.</span><span class="sxs-lookup"><span data-stu-id="804f2-109">The layout contains one empty cell, into which the user can slide an adjacent tile by using a drag-and-drop operation.</span></span> <span data-ttu-id="804f2-110">Kafelki, które użytkownik może przenieść są wyróżnione.</span><span class="sxs-lookup"><span data-stu-id="804f2-110">Tiles that the user can move are highlighted.</span></span>  
  
 <span data-ttu-id="804f2-111">`GridStripRenderer` Klasy dostosowuje trzy aspekty `GridStrip` wygląd formantu:</span><span class="sxs-lookup"><span data-stu-id="804f2-111">The `GridStripRenderer` class customizes three aspects of the `GridStrip` control's appearance:</span></span>  
  
-   <span data-ttu-id="804f2-112">`GridStrip` Obramowania</span><span class="sxs-lookup"><span data-stu-id="804f2-112">`GridStrip` border</span></span>  
  
-   <span data-ttu-id="804f2-113"><xref:System.Windows.Forms.ToolStripButton> Obramowania</span><span class="sxs-lookup"><span data-stu-id="804f2-113"><xref:System.Windows.Forms.ToolStripButton> border</span></span>  
  
-   <span data-ttu-id="804f2-114"><xref:System.Windows.Forms.ToolStripButton> Obraz</span><span class="sxs-lookup"><span data-stu-id="804f2-114"><xref:System.Windows.Forms.ToolStripButton> image</span></span>  
  
 [!code-csharp[System.Windows.Forms.ToolStrip.GridStrip#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.GridStrip/CS/GridStrip.cs#1)]
 [!code-vb[System.Windows.Forms.ToolStrip.GridStrip#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.GridStrip/VB/GridStrip.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="804f2-115">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="804f2-115">Compiling the Code</span></span>  
 <span data-ttu-id="804f2-116">Ten przykład wymaga:</span><span class="sxs-lookup"><span data-stu-id="804f2-116">This example requires:</span></span>  
  
-   <span data-ttu-id="804f2-117">Odwołania do zestawów System.Drawing i System.Windows.Forms.</span><span class="sxs-lookup"><span data-stu-id="804f2-117">References to the System.Drawing and System.Windows.Forms assemblies.</span></span>  
  
 <span data-ttu-id="804f2-118">Uzyskać informacje o kompilowaniu w tym przykładzie z wiersza polecenia dla programu Visual Basic lub Visual C#, zobacz [tworzenie z wiersza polecenia](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) lub [kompilowania z wiersza polecenia csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="804f2-118">For information about building this example from the command line for Visual Basic or Visual C#, see [Building from the Command Line](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="804f2-119">Można także utworzyć tym przykładzie [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] przez wklejenie kodu do nowego projektu.</span><span class="sxs-lookup"><span data-stu-id="804f2-119">You can also build this example in [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] by pasting the code into a new project.</span></span>  <span data-ttu-id="804f2-120">Zobacz też [porady: kompilowanie i uruchamianie pełną Windows formularze kodu przykład za pomocą programu Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span><span class="sxs-lookup"><span data-stu-id="804f2-120">Also see [How to: Compile and Run a Complete Windows Forms Code Example Using Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="804f2-121">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="804f2-121">See Also</span></span>  
 <xref:System.Windows.Forms.MenuStrip>  
 <xref:System.Windows.Forms.ToolStrip>  
 <xref:System.Windows.Forms.ToolStripRenderer>  
 <xref:System.Windows.Forms.ToolStripProfessionalRenderer>  
 <xref:System.Windows.Forms.ToolStripSystemRenderer>  
 <xref:System.Windows.Forms.StatusStrip>  
 [<span data-ttu-id="804f2-122">ToolStrip, kontrolka</span><span class="sxs-lookup"><span data-stu-id="804f2-122">ToolStrip Control</span></span>](../../../../docs/framework/winforms/controls/toolstrip-control-windows-forms.md)
