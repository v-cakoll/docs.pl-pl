---
title: 'Porady: dodawanie elementu ToolStripContainer do formularza'
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
- toolbars [Windows Forms], built-in rafting
- ToolStrip control [Windows Forms], built-in rafting
- ToolStripContainer control [Windows Forms], adding to Windows Forms
ms.assetid: d0f55095-a833-453e-be5a-644906d75d54
caps.latest.revision: 9
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 9c318ad7eaea72f928140257a833cedb8f99eb9f
ms.sourcegitcommit: 2042de78fcdceebb6b8ac4b7a292b93e8782cbf5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/27/2018
---
# <a name="how-to-add-a-toolstripcontainer-to-a-form"></a><span data-ttu-id="35e0a-102">Porady: dodawanie elementu ToolStripContainer do formularza</span><span class="sxs-lookup"><span data-stu-id="35e0a-102">How to: Add a ToolStripContainer to a Form</span></span>
<span data-ttu-id="35e0a-103">Można dodać programistycznie <xref:System.Windows.Forms.ToolStripContainer> do formularza systemu Windows i wypełnić ją kontrolki.</span><span class="sxs-lookup"><span data-stu-id="35e0a-103">You can programmatically add a <xref:System.Windows.Forms.ToolStripContainer> to a Windows Form and populate it with controls.</span></span>  
  
## <a name="example"></a><span data-ttu-id="35e0a-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="35e0a-104">Example</span></span>  
 <span data-ttu-id="35e0a-105">Poniższy przykładowy kod przedstawia sposób dodawania <xref:System.Windows.Forms.ToolStripContainer> i <xref:System.Windows.Forms.ToolStrip> do formularzy systemu Windows, jak dodać elementy do <xref:System.Windows.Forms.ToolStrip>oraz sposobu dodawania <xref:System.Windows.Forms.ToolStrip> do <xref:System.Windows.Forms.ToolStripContainer.TopToolStripPanel%2A> z <xref:System.Windows.Forms.ToolStripContainer>.</span><span class="sxs-lookup"><span data-stu-id="35e0a-105">The following code example demonstrates how to add a <xref:System.Windows.Forms.ToolStripContainer> and a <xref:System.Windows.Forms.ToolStrip> to a Windows Forms, how to add items to the <xref:System.Windows.Forms.ToolStrip>, and how to add the <xref:System.Windows.Forms.ToolStrip> to the <xref:System.Windows.Forms.ToolStripContainer.TopToolStripPanel%2A> of the <xref:System.Windows.Forms.ToolStripContainer>.</span></span>  
  
 [!code-csharp[System.Windows.Forms.ToolStripContainer2#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/system.windows.forms.toolstripcontainer2/cs/form1.cs#1)]
 [!code-vb[System.Windows.Forms.ToolStripContainer2#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/system.windows.forms.toolstripcontainer2/vb/form1.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="35e0a-106">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="35e0a-106">Compiling the Code</span></span>  
 <span data-ttu-id="35e0a-107">W tym przykładzie kodu wymaga:</span><span class="sxs-lookup"><span data-stu-id="35e0a-107">This code example requires:</span></span>  
  
-   <span data-ttu-id="35e0a-108">Odwołania do zestawów System.Drawing, System.Text i System.Windows.Forms.</span><span class="sxs-lookup"><span data-stu-id="35e0a-108">References to the System.Drawing, System.Text, and System.Windows.Forms assemblies.</span></span>  
  
 <span data-ttu-id="35e0a-109">Uzyskać informacje o kompilowaniu w tym przykładzie z wiersza polecenia dla programu Visual Basic lub Visual C#, zobacz [tworzenie z wiersza polecenia](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) lub [kompilowania z wiersza polecenia csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="35e0a-109">For information about building this example from the command line for Visual Basic or Visual C#, see [Building from the Command Line](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="35e0a-110">Można także utworzyć w tym przykładzie w programie Visual Studio przez wklejenie kodu do nowego projektu.</span><span class="sxs-lookup"><span data-stu-id="35e0a-110">You can also build this example in Visual Studio by pasting the code into a new project.</span></span>  <span data-ttu-id="35e0a-111">Zobacz też [porady: kompilowanie i uruchamianie przykładowego kodu formularzy pełną systemu Windows przy użyciu programu Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)) lub [ToolStripContainer zadania okno dialogowe](http://msdn.microsoft.com/library/ms233647\(v=vs.110\)).</span><span class="sxs-lookup"><span data-stu-id="35e0a-111">See also [How to: Compile and Run a Complete Windows Forms Code Example Using Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)) or [ToolStripContainer Tasks Dialog Box](http://msdn.microsoft.com/library/ms233647\(v=vs.110\)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="35e0a-112">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="35e0a-112">See Also</span></span>  
 <xref:System.Windows.Forms.ToolStripContainer>  
 [<span data-ttu-id="35e0a-113">ToolStripContainer, kontrolka</span><span class="sxs-lookup"><span data-stu-id="35e0a-113">ToolStripContainer Control</span></span>](../../../../docs/framework/winforms/controls/toolstripcontainer-control.md)  
 [<span data-ttu-id="35e0a-114">ToolStrip, kontrolka</span><span class="sxs-lookup"><span data-stu-id="35e0a-114">ToolStrip Control</span></span>](../../../../docs/framework/winforms/controls/toolstrip-control-windows-forms.md)
