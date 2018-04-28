---
title: 'Porady: zapewnianie elementów menu standardowego dla formularza'
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
- menu items [Windows Forms], standard
- ToolStrip control [Windows Forms]
ms.assetid: 75db9126-e70c-4e81-921d-b83c0a4a9f50
caps.latest.revision: 7
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: e6e2514adc2b2bbd5b2d1ab3371b48d760842140
ms.sourcegitcommit: 2042de78fcdceebb6b8ac4b7a292b93e8782cbf5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/27/2018
---
# <a name="how-to-provide-standard-menu-items-to-a-form"></a><span data-ttu-id="e3755-102">Porady: zapewnianie elementów menu standardowego dla formularza</span><span class="sxs-lookup"><span data-stu-id="e3755-102">How to: Provide Standard Menu Items to a Form</span></span>
<span data-ttu-id="e3755-103">Można zapewnić standardowe menu formularzy z <xref:System.Windows.Forms.MenuStrip> formantu.</span><span class="sxs-lookup"><span data-stu-id="e3755-103">You can provide a standard menu for your forms with the <xref:System.Windows.Forms.MenuStrip> control.</span></span>  
  
 <span data-ttu-id="e3755-104">Brak kompleksową obsługę tej funkcji w programie Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="e3755-104">There is extensive support for this feature in Visual Studio.</span></span>  
  
 <span data-ttu-id="e3755-105">Zobacz też [wskazówki: zapewnianie standardowe elementy Menu do formularza](http://msdn.microsoft.com/library/ms233662\(v=vs.110\)).</span><span class="sxs-lookup"><span data-stu-id="e3755-105">Also see [Walkthrough: Providing Standard Menu Items to a Form](http://msdn.microsoft.com/library/ms233662\(v=vs.110\)).</span></span>  
  
## <a name="example"></a><span data-ttu-id="e3755-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="e3755-106">Example</span></span>  
 <span data-ttu-id="e3755-107">Poniższy przykład kodu pokazuje sposób użycia <xref:System.Windows.Forms.MenuStrip> formantami formularza z menu standardowego.</span><span class="sxs-lookup"><span data-stu-id="e3755-107">The following code example demonstrates how to use a <xref:System.Windows.Forms.MenuStrip> control to create a form with a standard menu.</span></span> <span data-ttu-id="e3755-108">Wybór elementu menu są wyświetlane w <xref:System.Windows.Forms.StatusStrip> formantu.</span><span class="sxs-lookup"><span data-stu-id="e3755-108">Menu item selections are displayed in a <xref:System.Windows.Forms.StatusStrip> control.</span></span>  
  
 [!code-csharp[System.Windows.Forms.ToolStrip.StandardMenu#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StandardMenu/CS/Form1.cs#1)]
 [!code-vb[System.Windows.Forms.ToolStrip.StandardMenu#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StandardMenu/VB/Form1.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="e3755-109">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="e3755-109">Compiling the Code</span></span>  
 <span data-ttu-id="e3755-110">Ten przykład wymaga:</span><span class="sxs-lookup"><span data-stu-id="e3755-110">This example requires:</span></span>  
  
-   <span data-ttu-id="e3755-111">Odwołania do zestawów systemu, System.Drawing i System.Windows.Forms.</span><span class="sxs-lookup"><span data-stu-id="e3755-111">References to the System, System.Drawing and System.Windows.Forms assemblies.</span></span>  
  
 <span data-ttu-id="e3755-112">Uzyskać informacje o kompilowaniu w tym przykładzie z wiersza polecenia dla programu Visual Basic lub Visual C#, zobacz [tworzenie z wiersza polecenia](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) lub [kompilowania z wiersza polecenia csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="e3755-112">For information about building this example from the command line for Visual Basic or Visual C#, see [Building from the Command Line](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="e3755-113">Można także utworzyć w tym przykładzie w programie Visual Studio przez wklejenie kodu do nowego projektu.</span><span class="sxs-lookup"><span data-stu-id="e3755-113">You can also build this example in Visual Studio by pasting the code into a new project.</span></span>  <span data-ttu-id="e3755-114">Zobacz też [porady: kompilowanie i uruchamianie pełną Windows formularze kodu przykład za pomocą programu Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span><span class="sxs-lookup"><span data-stu-id="e3755-114">Also see [How to: Compile and Run a Complete Windows Forms Code Example Using Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e3755-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e3755-115">See Also</span></span>  
 <xref:System.Windows.Forms.MenuStrip>  
 <xref:System.Windows.Forms.ToolStrip>  
 <xref:System.Windows.Forms.StatusStrip>  
 [<span data-ttu-id="e3755-116">MenuStrip, kontrolka</span><span class="sxs-lookup"><span data-stu-id="e3755-116">MenuStrip Control</span></span>](../../../../docs/framework/winforms/controls/menustrip-control-windows-forms.md)
