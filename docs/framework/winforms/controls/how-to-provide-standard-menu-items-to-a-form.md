---
title: 'Instrukcje: Zapewnianie elementów Menu standardowego dla formularza'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- toolbars [Windows Forms]
- menu items [Windows Forms], standard
- ToolStrip control [Windows Forms]
ms.assetid: 75db9126-e70c-4e81-921d-b83c0a4a9f50
ms.openlocfilehash: 823cc774e4bfd9ba94ea84efeda493b225a04a35
ms.sourcegitcommit: af0a22a4eb11bbcd33baec49150d551955b50a16
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/14/2019
ms.locfileid: "56260910"
---
# <a name="how-to-provide-standard-menu-items-to-a-form"></a><span data-ttu-id="7cffe-102">Instrukcje: Zapewnianie elementów Menu standardowego dla formularza</span><span class="sxs-lookup"><span data-stu-id="7cffe-102">How to: Provide Standard Menu Items to a Form</span></span>
<span data-ttu-id="7cffe-103">Możesz podać standardowe menu formularzy przy użyciu <xref:System.Windows.Forms.MenuStrip> kontroli.</span><span class="sxs-lookup"><span data-stu-id="7cffe-103">You can provide a standard menu for your forms with the <xref:System.Windows.Forms.MenuStrip> control.</span></span>  
  
 <span data-ttu-id="7cffe-104">Brak zaawansowaną obsługę dla tej funkcji w programie Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="7cffe-104">There is extensive support for this feature in Visual Studio.</span></span>  
  
 <span data-ttu-id="7cffe-105">Zobacz też [instruktażu: Zapewnianie elementów Menu standardowego dla formularza](walkthrough-providing-standard-menu-items-to-a-form.md).</span><span class="sxs-lookup"><span data-stu-id="7cffe-105">Also see [Walkthrough: Providing Standard Menu Items to a Form](walkthrough-providing-standard-menu-items-to-a-form.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="7cffe-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="7cffe-106">Example</span></span>  
 <span data-ttu-id="7cffe-107">Poniższy przykład kodu demonstruje sposób używania <xref:System.Windows.Forms.MenuStrip> formantu, aby utworzyć formularz przy użyciu standardowego menu.</span><span class="sxs-lookup"><span data-stu-id="7cffe-107">The following code example demonstrates how to use a <xref:System.Windows.Forms.MenuStrip> control to create a form with a standard menu.</span></span> <span data-ttu-id="7cffe-108">Opcje elementu menu są wyświetlane w <xref:System.Windows.Forms.StatusStrip> kontroli.</span><span class="sxs-lookup"><span data-stu-id="7cffe-108">Menu item selections are displayed in a <xref:System.Windows.Forms.StatusStrip> control.</span></span>  
  
 [!code-csharp[System.Windows.Forms.ToolStrip.StandardMenu#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StandardMenu/CS/Form1.cs#1)]
 [!code-vb[System.Windows.Forms.ToolStrip.StandardMenu#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StandardMenu/VB/Form1.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="7cffe-109">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="7cffe-109">Compiling the Code</span></span>  
 <span data-ttu-id="7cffe-110">Ten przykład wymaga:</span><span class="sxs-lookup"><span data-stu-id="7cffe-110">This example requires:</span></span>  
  
-   <span data-ttu-id="7cffe-111">Odwołania do zestawów systemu, System.Drawing i przestrzeń nazw System.Windows.Forms.</span><span class="sxs-lookup"><span data-stu-id="7cffe-111">References to the System, System.Drawing and System.Windows.Forms assemblies.</span></span>  
  
 <span data-ttu-id="7cffe-112">Aby dowiedzieć się, jak tworzyć aplikacje w tym przykładzie z wiersza polecenia dla języka Visual Basic lub Visual C#, zobacz [tworzenie z wiersza polecenia](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) lub [wiersza polecenia tworzenia przy użyciu csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="7cffe-112">For information about building this example from the command line for Visual Basic or Visual C#, see [Building from the Command Line](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="7cffe-113">Można także utworzyć tego przykładu w programie Visual Studio, wklejając kod do nowego projektu.</span><span class="sxs-lookup"><span data-stu-id="7cffe-113">You can also build this example in Visual Studio by pasting the code into a new project.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7cffe-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="7cffe-114">See also</span></span>
- <xref:System.Windows.Forms.MenuStrip>
- <xref:System.Windows.Forms.ToolStrip>
- <xref:System.Windows.Forms.StatusStrip>
- [<span data-ttu-id="7cffe-115">MenuStrip, kontrolka</span><span class="sxs-lookup"><span data-stu-id="7cffe-115">MenuStrip Control</span></span>](../../../../docs/framework/winforms/controls/menustrip-control-windows-forms.md)
