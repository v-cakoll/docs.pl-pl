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
ms.openlocfilehash: e7bc66aa556738274d9bcba8e0db4e72f731cb57
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54685142"
---
# <a name="how-to-associate-a-contextmenustrip-with-a-control"></a><span data-ttu-id="de72d-102">Instrukcje: Kojarzenie kontrolki ContextMenuStrip z kontrolką</span><span class="sxs-lookup"><span data-stu-id="de72d-102">How to: Associate a ContextMenuStrip with a Control</span></span>
<span data-ttu-id="de72d-103">Po utworzeniu menu skrótów i kontrolki, na których należy użyć poniższych procedur do wyświetlenia menu skrótów danego, gdy użytkownik kliknie prawym przyciskiem myszy formant.</span><span class="sxs-lookup"><span data-stu-id="de72d-103">After creating your controls and shortcut menus, use the following procedures to display a given shortcut menu when the user right-clicks the control.</span></span> <span data-ttu-id="de72d-104">Te procedury skojarzyć <xref:System.Windows.Forms.ContextMenuStrip> z formularza Windows i <xref:System.Windows.Forms.ToolStrip> kontroli.</span><span class="sxs-lookup"><span data-stu-id="de72d-104">These procedures associate a <xref:System.Windows.Forms.ContextMenuStrip> with a Windows Form and with a <xref:System.Windows.Forms.ToolStrip> control.</span></span>  
  
### <a name="to-associate-a-contextmenustrip-with-a-windows-form"></a><span data-ttu-id="de72d-105">Aby skojarzenie właściwości ContextMenuStrip z formularzem Windows</span><span class="sxs-lookup"><span data-stu-id="de72d-105">To associate a ContextMenuStrip with a Windows Form</span></span>  
  
1.  <span data-ttu-id="de72d-106">Ustaw <xref:System.Windows.Forms.Control.ContextMenuStrip%2A> właściwość na nazwę skojarzonego <xref:System.Windows.Forms.ContextMenuStrip>.</span><span class="sxs-lookup"><span data-stu-id="de72d-106">Set the <xref:System.Windows.Forms.Control.ContextMenuStrip%2A> property to the name of the associated <xref:System.Windows.Forms.ContextMenuStrip>.</span></span>  
  
### <a name="to-associate-a-contextmenustrip-with-a-toolstrip-control"></a><span data-ttu-id="de72d-107">Aby skojarzyć kontrolki ContextMenuStrip z formantu ToolStrip</span><span class="sxs-lookup"><span data-stu-id="de72d-107">To associate a ContextMenuStrip with a ToolStrip control</span></span>  
  
1.  <span data-ttu-id="de72d-108">Ustaw dla formantu <xref:System.Windows.Forms.Control.ContextMenuStrip%2A> właściwość na nazwę skojarzonego <xref:System.Windows.Forms.ContextMenuStrip>.</span><span class="sxs-lookup"><span data-stu-id="de72d-108">Set the control's <xref:System.Windows.Forms.Control.ContextMenuStrip%2A> property to the name of the associated <xref:System.Windows.Forms.ContextMenuStrip>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="de72d-109">Przykład</span><span class="sxs-lookup"><span data-stu-id="de72d-109">Example</span></span>  
 <span data-ttu-id="de72d-110">Poniższy przykład kodu tworzy formularz Windows i <xref:System.Windows.Forms.ToolStrip>i kojarzy innego <xref:System.Windows.Forms.ContextMenuStrip> kontrolki z każdym z nich.</span><span class="sxs-lookup"><span data-stu-id="de72d-110">The following code example creates a Windows Form and a <xref:System.Windows.Forms.ToolStrip>, and associates a different <xref:System.Windows.Forms.ContextMenuStrip> control with each of them.</span></span>  
  
 [!code-csharp[System.Windows.Forms.ContextMenuStrip#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ContextMenuStrip/CS/form1.cs#1)]
 [!code-vb[System.Windows.Forms.ContextMenuStrip#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ContextMenuStrip/VB/form1.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="de72d-111">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="de72d-111">Compiling the Code</span></span>  
 <span data-ttu-id="de72d-112">Ten przykład wymaga:</span><span class="sxs-lookup"><span data-stu-id="de72d-112">This example requires:</span></span>  
  
-   <span data-ttu-id="de72d-113">Odwołania do zestawów systemu, dane systemowe i System.Drawing oraz przestrzeń nazw System.Windows.Forms.</span><span class="sxs-lookup"><span data-stu-id="de72d-113">References to the System, System.Data, System.Drawing and System.Windows.Forms assemblies.</span></span>  
  
 <span data-ttu-id="de72d-114">Aby dowiedzieć się, jak tworzyć aplikacje w tym przykładzie z wiersza polecenia dla języka Visual Basic lub Visual C#, zobacz [tworzenie z wiersza polecenia](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) lub [wiersza polecenia tworzenia przy użyciu csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="de72d-114">For information about building this example from the command line for Visual Basic or Visual C#, see [Building from the Command Line](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="de72d-115">Można także utworzyć tego przykładu w programie Visual Studio, wklejając kod do nowego projektu.</span><span class="sxs-lookup"><span data-stu-id="de72d-115">You can also build this example in Visual Studio by pasting the code into a new project.</span></span>  <span data-ttu-id="de72d-116">Zobacz też [jak: Skompilować i uruchomić przykładowy kod pełną Windows Forms przy użyciu programu Visual Studio](https://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span><span class="sxs-lookup"><span data-stu-id="de72d-116">Also see [How to: Compile and Run a Complete Windows Forms Code Example Using Visual Studio](https://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="de72d-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="de72d-117">See also</span></span>
- <xref:System.Windows.Forms.ContextMenuStrip>
- <xref:System.Windows.Forms.Control.ContextMenuStrip%2A>
- <xref:System.Windows.Forms.ToolStrip>
- [<span data-ttu-id="de72d-118">Instrukcje: Dodawanie elementów Menu do paska ContextMenuStrip</span><span class="sxs-lookup"><span data-stu-id="de72d-118">How to: Add Menu Items to a ContextMenuStrip</span></span>](../../../../docs/framework/winforms/controls/how-to-add-menu-items-to-a-contextmenustrip.md)
- [<span data-ttu-id="de72d-119">ContextMenuStrip, kontrolka</span><span class="sxs-lookup"><span data-stu-id="de72d-119">ContextMenuStrip Control</span></span>](../../../../docs/framework/winforms/controls/contextmenustrip-control.md)
