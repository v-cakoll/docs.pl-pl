---
title: 'Instrukcje: Kojarzenie kontrolki ContextMenuStrip z kontrolką'
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
ms.openlocfilehash: 4b61da8dc9f36e0a80807547e2049ef512c94747
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/09/2019
ms.locfileid: "57718341"
---
# <a name="how-to-associate-a-contextmenustrip-with-a-control"></a><span data-ttu-id="50eb3-102">Instrukcje: Kojarzenie kontrolki ContextMenuStrip z kontrolką</span><span class="sxs-lookup"><span data-stu-id="50eb3-102">How to: Associate a ContextMenuStrip with a Control</span></span>
<span data-ttu-id="50eb3-103">Po utworzeniu menu skrótów i kontrolki, na których należy użyć poniższych procedur do wyświetlenia menu skrótów danego, gdy użytkownik kliknie prawym przyciskiem myszy formant.</span><span class="sxs-lookup"><span data-stu-id="50eb3-103">After creating your controls and shortcut menus, use the following procedures to display a given shortcut menu when the user right-clicks the control.</span></span> <span data-ttu-id="50eb3-104">Te procedury skojarzyć <xref:System.Windows.Forms.ContextMenuStrip> z formularza Windows i <xref:System.Windows.Forms.ToolStrip> kontroli.</span><span class="sxs-lookup"><span data-stu-id="50eb3-104">These procedures associate a <xref:System.Windows.Forms.ContextMenuStrip> with a Windows Form and with a <xref:System.Windows.Forms.ToolStrip> control.</span></span>  
  
### <a name="to-associate-a-contextmenustrip-with-a-windows-form"></a><span data-ttu-id="50eb3-105">Aby skojarzenie właściwości ContextMenuStrip z formularzem Windows</span><span class="sxs-lookup"><span data-stu-id="50eb3-105">To associate a ContextMenuStrip with a Windows Form</span></span>  
  
1.  <span data-ttu-id="50eb3-106">Ustaw <xref:System.Windows.Forms.Control.ContextMenuStrip%2A> właściwość na nazwę skojarzonego <xref:System.Windows.Forms.ContextMenuStrip>.</span><span class="sxs-lookup"><span data-stu-id="50eb3-106">Set the <xref:System.Windows.Forms.Control.ContextMenuStrip%2A> property to the name of the associated <xref:System.Windows.Forms.ContextMenuStrip>.</span></span>  
  
### <a name="to-associate-a-contextmenustrip-with-a-toolstrip-control"></a><span data-ttu-id="50eb3-107">Aby skojarzyć kontrolki ContextMenuStrip z formantu ToolStrip</span><span class="sxs-lookup"><span data-stu-id="50eb3-107">To associate a ContextMenuStrip with a ToolStrip control</span></span>  
  
1.  <span data-ttu-id="50eb3-108">Ustaw dla formantu <xref:System.Windows.Forms.Control.ContextMenuStrip%2A> właściwość na nazwę skojarzonego <xref:System.Windows.Forms.ContextMenuStrip>.</span><span class="sxs-lookup"><span data-stu-id="50eb3-108">Set the control's <xref:System.Windows.Forms.Control.ContextMenuStrip%2A> property to the name of the associated <xref:System.Windows.Forms.ContextMenuStrip>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="50eb3-109">Przykład</span><span class="sxs-lookup"><span data-stu-id="50eb3-109">Example</span></span>  
 <span data-ttu-id="50eb3-110">Poniższy przykład kodu tworzy formularz Windows i <xref:System.Windows.Forms.ToolStrip>i kojarzy innego <xref:System.Windows.Forms.ContextMenuStrip> kontrolki z każdym z nich.</span><span class="sxs-lookup"><span data-stu-id="50eb3-110">The following code example creates a Windows Form and a <xref:System.Windows.Forms.ToolStrip>, and associates a different <xref:System.Windows.Forms.ContextMenuStrip> control with each of them.</span></span>  
  
 [!code-csharp[System.Windows.Forms.ContextMenuStrip#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ContextMenuStrip/CS/form1.cs#1)]
 [!code-vb[System.Windows.Forms.ContextMenuStrip#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ContextMenuStrip/VB/form1.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="50eb3-111">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="50eb3-111">Compiling the Code</span></span>  
 <span data-ttu-id="50eb3-112">Ten przykład wymaga:</span><span class="sxs-lookup"><span data-stu-id="50eb3-112">This example requires:</span></span>  
  
-   <span data-ttu-id="50eb3-113">Odwołania do zestawów systemu, dane systemowe i System.Drawing oraz przestrzeń nazw System.Windows.Forms.</span><span class="sxs-lookup"><span data-stu-id="50eb3-113">References to the System, System.Data, System.Drawing and System.Windows.Forms assemblies.</span></span>  
  
 <span data-ttu-id="50eb3-114">Aby dowiedzieć się, jak tworzyć aplikacje w tym przykładzie z wiersza polecenia dla języka Visual Basic lub Visual C#, zobacz [tworzenie z wiersza polecenia](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) lub [wiersza polecenia tworzenia przy użyciu csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="50eb3-114">For information about building this example from the command line for Visual Basic or Visual C#, see [Building from the Command Line](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="50eb3-115">Można także utworzyć tego przykładu w programie Visual Studio, wklejając kod do nowego projektu.</span><span class="sxs-lookup"><span data-stu-id="50eb3-115">You can also build this example in Visual Studio by pasting the code into a new project.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="50eb3-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="50eb3-116">See also</span></span>
- <xref:System.Windows.Forms.ContextMenuStrip>
- <xref:System.Windows.Forms.Control.ContextMenuStrip%2A>
- <xref:System.Windows.Forms.ToolStrip>
- [<span data-ttu-id="50eb3-117">Instrukcje: Dodawanie elementów Menu do paska ContextMenuStrip</span><span class="sxs-lookup"><span data-stu-id="50eb3-117">How to: Add Menu Items to a ContextMenuStrip</span></span>](how-to-add-menu-items-to-a-contextmenustrip.md)
- [<span data-ttu-id="50eb3-118">ContextMenuStrip, kontrolka</span><span class="sxs-lookup"><span data-stu-id="50eb3-118">ContextMenuStrip Control</span></span>](contextmenustrip-control.md)
