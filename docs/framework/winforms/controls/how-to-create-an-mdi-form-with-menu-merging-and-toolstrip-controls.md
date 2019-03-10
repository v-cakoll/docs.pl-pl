---
title: 'Instrukcje: Tworzenie formularza MDI ze scalaniem Menu i formantów ToolStrip'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- toolbars [Windows Forms]
- ToolStripPanel control [Windows Forms]
- ToolStrip control [Windows Forms]
- MenuStrip control [Windows Forms]
ms.assetid: 64992ed9-44af-4baf-b45f-863e6ab35711
ms.openlocfilehash: 2942d0e92a0f58bef5533d69b27a646d284fef62
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/09/2019
ms.locfileid: "57721115"
---
# <a name="how-to-create-an-mdi-form-with-menu-merging-and-toolstrip-controls"></a><span data-ttu-id="15b0b-102">Instrukcje: Tworzenie formularza MDI ze scalaniem Menu i formantów ToolStrip</span><span class="sxs-lookup"><span data-stu-id="15b0b-102">How to: Create an MDI Form with Menu Merging and ToolStrip Controls</span></span>
<span data-ttu-id="15b0b-103"><xref:System.Windows.Forms?displayProperty=nameWithType> Przestrzeń nazw obsługuje wiele aplikacji interfejsu (MDI) dokumentu i <xref:System.Windows.Forms.MenuStrip> kontrolka obsługuje scalania menu.</span><span class="sxs-lookup"><span data-stu-id="15b0b-103">The <xref:System.Windows.Forms?displayProperty=nameWithType> namespace supports multiple document interface (MDI) applications, and the <xref:System.Windows.Forms.MenuStrip> control supports menu merging.</span></span> <span data-ttu-id="15b0b-104">Formularze MDI może również <xref:System.Windows.Forms.ToolStrip> kontrolki.</span><span class="sxs-lookup"><span data-stu-id="15b0b-104">MDI forms can also <xref:System.Windows.Forms.ToolStrip> controls.</span></span>  
  
 <span data-ttu-id="15b0b-105">Brak zaawansowaną obsługę dla tej funkcji w programie Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="15b0b-105">There is extensive support for this feature in Visual Studio.</span></span>  
  
 <span data-ttu-id="15b0b-106">Zobacz też [instruktażu: Tworzenie formularza MDI za pomocą scalania Menu i formantami ToolStrip](walkthrough-creating-an-mdi-form-with-menu-merging-and-toolstrip-controls.md).</span><span class="sxs-lookup"><span data-stu-id="15b0b-106">Also see [Walkthrough: Creating an MDI Form with Menu Merging and ToolStrip Controls](walkthrough-creating-an-mdi-form-with-menu-merging-and-toolstrip-controls.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="15b0b-107">Przykład</span><span class="sxs-lookup"><span data-stu-id="15b0b-107">Example</span></span>  
 <span data-ttu-id="15b0b-108">Poniższy przykład kodu demonstruje sposób używania <xref:System.Windows.Forms.ToolStripPanel> formanty z formularza MDI.</span><span class="sxs-lookup"><span data-stu-id="15b0b-108">The following code example demonstrates how to use <xref:System.Windows.Forms.ToolStripPanel> controls with an MDI form.</span></span> <span data-ttu-id="15b0b-109">Formularz obsługuje także menu scalanie z menu podrzędne.</span><span class="sxs-lookup"><span data-stu-id="15b0b-109">The form also supports menu merging with child menus.</span></span>  
  
 [!code-csharp[System.Windows.Forms.ToolStrip.MdiForm#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.MdiForm/CS/Form1.cs#1)]
 [!code-vb[System.Windows.Forms.ToolStrip.MdiForm#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.MdiForm/VB/Form1.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="15b0b-110">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="15b0b-110">Compiling the Code</span></span>  
 <span data-ttu-id="15b0b-111">Poniższy przykład kodu wymaga:</span><span class="sxs-lookup"><span data-stu-id="15b0b-111">This code example requires:</span></span>  
  
-   <span data-ttu-id="15b0b-112">Odwołania do zestawów System.Drawing i pozycję System.Windows.Forms.</span><span class="sxs-lookup"><span data-stu-id="15b0b-112">References to the System.Drawing and System.Windows.Forms assemblies.</span></span>  
  
 <span data-ttu-id="15b0b-113">Aby dowiedzieć się, jak tworzyć aplikacje w tym przykładzie z wiersza polecenia dla języka Visual Basic lub Visual C#, zobacz [tworzenie z wiersza polecenia](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) lub [wiersza polecenia tworzenia przy użyciu csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="15b0b-113">For information about building this example from the command line for Visual Basic or Visual C#, see [Building from the Command Line](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="15b0b-114">Można także utworzyć tego przykładu w programie Visual Studio, wklejając kod do nowego projektu.</span><span class="sxs-lookup"><span data-stu-id="15b0b-114">You can also build this example in Visual Studio by pasting the code into a new project.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="15b0b-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="15b0b-115">See also</span></span>
- [<span data-ttu-id="15b0b-116">ToolStrip, kontrolka</span><span class="sxs-lookup"><span data-stu-id="15b0b-116">ToolStrip Control</span></span>](toolstrip-control-windows-forms.md)
