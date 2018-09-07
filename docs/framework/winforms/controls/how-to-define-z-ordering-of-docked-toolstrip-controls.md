---
title: 'Porady: definiowanie porządku osi Z zadokowanych formantów ToolStrip'
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
ms.openlocfilehash: 34d600454a7fa63c7ba59bebded6365cd5401cb4
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2018
ms.locfileid: "44064741"
---
# <a name="how-to-define-z-ordering-of-docked-toolstrip-controls"></a><span data-ttu-id="75170-102">Porady: definiowanie porządku osi Z zadokowanych formantów ToolStrip</span><span class="sxs-lookup"><span data-stu-id="75170-102">How to: Define Z-Ordering of Docked ToolStrip Controls</span></span>
<span data-ttu-id="75170-103">Położenie <xref:System.Windows.Forms.ToolStrip> kontroli poprawnie za pomocą dokowania, należy umieścić formant poprawnie w kolejności z formularza.</span><span class="sxs-lookup"><span data-stu-id="75170-103">To position a <xref:System.Windows.Forms.ToolStrip> control correctly with docking, you must position the control correctly in the form's z-order.</span></span>  
  
## <a name="example"></a><span data-ttu-id="75170-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="75170-104">Example</span></span>  
 <span data-ttu-id="75170-105">Poniższy przykład kodu demonstruje sposób rozmieszczenia <xref:System.Windows.Forms.ToolStrip> kontroli i zadokowany <xref:System.Windows.Forms.MenuStrip> kontroli przez określenie porządku osi z.</span><span class="sxs-lookup"><span data-stu-id="75170-105">The following code example demonstrates how to arrange a <xref:System.Windows.Forms.ToolStrip> control and a docked <xref:System.Windows.Forms.MenuStrip> control by specifying the z-order.</span></span>  
  
 [!code-csharp[System.Windows.Forms.ToolStrip.Misc#21](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/CS/Program.cs#21)]
 [!code-vb[System.Windows.Forms.ToolStrip.Misc#21](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/VB/Program.vb#21)]  
  
 <span data-ttu-id="75170-106">Kolejność jest określana przez kolejność, w której <xref:System.Windows.Forms.ToolStrip> i <xref:System.Windows.Forms.MenuStrip></span><span class="sxs-lookup"><span data-stu-id="75170-106">The z-order is determined by the order in which the <xref:System.Windows.Forms.ToolStrip> and <xref:System.Windows.Forms.MenuStrip></span></span>  
  
 <span data-ttu-id="75170-107">Formanty są dodawane do formularza <xref:System.Windows.Forms.Control.Controls%2A> kolekcji.</span><span class="sxs-lookup"><span data-stu-id="75170-107">controls are added to the form's <xref:System.Windows.Forms.Control.Controls%2A> collection.</span></span>  
  
 [!code-csharp[System.Windows.Forms.ToolStrip.Misc#23](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/CS/Program.cs#23)]
 [!code-vb[System.Windows.Forms.ToolStrip.Misc#23](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/VB/Program.vb#23)]  
  
 <span data-ttu-id="75170-108">Odwracanie kolejności tych wywołań <xref:System.Windows.Forms.Control.ControlCollection.Add%2A> metody i widoku. wpływa na układ.</span><span class="sxs-lookup"><span data-stu-id="75170-108">Reverse the order of these calls to the <xref:System.Windows.Forms.Control.ControlCollection.Add%2A> method and view the effect on the layout.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="75170-109">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="75170-109">Compiling the Code</span></span>  
 <span data-ttu-id="75170-110">Ten przykład wymaga:</span><span class="sxs-lookup"><span data-stu-id="75170-110">This example requires:</span></span>  
  
-   <span data-ttu-id="75170-111">Odwołania do zestawów System.Design System.Drawing i przestrzeń nazw System.Windows.Forms.</span><span class="sxs-lookup"><span data-stu-id="75170-111">References to the System.Design, System.Drawing, and System.Windows.Forms assemblies.</span></span>  
  
 <span data-ttu-id="75170-112">Aby dowiedzieć się, jak tworzyć aplikacje w tym przykładzie z wiersza polecenia dla języka Visual Basic lub Visual C#, zobacz [tworzenie z wiersza polecenia](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) lub [wiersza polecenia tworzenia przy użyciu csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="75170-112">For information about building this example from the command line for Visual Basic or Visual C#, see [Building from the Command Line](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="75170-113">Można także utworzyć tego przykładu w programie Visual Studio, wklejając kod do nowego projektu.</span><span class="sxs-lookup"><span data-stu-id="75170-113">You can also build this example in Visual Studio by pasting the code into a new project.</span></span>  <span data-ttu-id="75170-114">Również se [porady: kompilowanie i uruchamianie pełną Windows Forms kodu przykładzie przy użyciu programu Visual Studio](https://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span><span class="sxs-lookup"><span data-stu-id="75170-114">Also se [How to: Compile and Run a Complete Windows Forms Code Example Using Visual Studio](https://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="75170-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="75170-115">See Also</span></span>  
 <xref:System.Windows.Forms.MenuStrip>  
 <xref:System.Windows.Forms.ToolStrip>  
 <xref:System.Windows.Forms.Control.ControlCollection.Add%2A>  
 <xref:System.Windows.Forms.Control.Controls%2A>  
 <xref:System.Windows.Forms.Control.Dock%2A>  
 [<span data-ttu-id="75170-116">ToolStrip, kontrolka</span><span class="sxs-lookup"><span data-stu-id="75170-116">ToolStrip Control</span></span>](../../../../docs/framework/winforms/controls/toolstrip-control-windows-forms.md)
