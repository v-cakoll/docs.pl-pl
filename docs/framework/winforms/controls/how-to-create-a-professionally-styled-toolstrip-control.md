---
title: 'Instrukcje: Tworzenie profesjonalnego formantu ToolStrip'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- toolbars [Windows Forms]
- ToolStripProfessionalRenderer class [Windows Forms]
- ToolStripRenderer class [Windows Forms]
- ToolStrip control [Windows Forms]
ms.assetid: c208b2f6-8105-474b-9075-d582e1792870
ms.openlocfilehash: 1e6455ebabfa5b27301f98b89861348b28d415af
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54690205"
---
# <a name="how-to-create-a-professionally-styled-toolstrip-control"></a><span data-ttu-id="a69fd-102">Instrukcje: Tworzenie profesjonalnego formantu ToolStrip</span><span class="sxs-lookup"><span data-stu-id="a69fd-102">How to: Create a Professionally Styled ToolStrip Control</span></span>
<span data-ttu-id="a69fd-103">Możesz nadać aplikacji <xref:System.Windows.Forms.ToolStrip> kontroluje profesjonalny wygląd i zachowanie (wygląd i działanie), pisząc własne klasy pochodzącej od <xref:System.Windows.Forms.ToolStripProfessionalRenderer> typu.</span><span class="sxs-lookup"><span data-stu-id="a69fd-103">You can give your application’s <xref:System.Windows.Forms.ToolStrip> controls a professional appearance and behavior (look and feel) by writing your own class derived from the <xref:System.Windows.Forms.ToolStripProfessionalRenderer> type.</span></span>  
  
 <span data-ttu-id="a69fd-104">Brak zaawansowaną obsługę dla tej funkcji w programie Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="a69fd-104">There is extensive support for this feature in Visual Studio.</span></span>  
  
 <span data-ttu-id="a69fd-105">Zobacz [instruktażu: Tworzenie profesjonalnego formantu ToolStrip](../../../../docs/framework/winforms/controls/walkthrough-creating-a-professionally-styled-toolstrip-control.md).</span><span class="sxs-lookup"><span data-stu-id="a69fd-105">See [Walkthrough: Creating a Professionally Styled ToolStrip Control](../../../../docs/framework/winforms/controls/walkthrough-creating-a-professionally-styled-toolstrip-control.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="a69fd-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="a69fd-106">Example</span></span>  
 <span data-ttu-id="a69fd-107">Poniższy przykład kodu demonstruje sposób używania <xref:System.Windows.Forms.ToolStrip> formantów, aby utworzyć formant złożony, który naśladuje **okienka nawigacji** udostępniane przez Microsoft Outlook®.</span><span class="sxs-lookup"><span data-stu-id="a69fd-107">The following code example demonstrates how to use <xref:System.Windows.Forms.ToolStrip> controls to create a composite control that mimics the **Navigation Pane** provided by Microsoft® Outlook®.</span></span>  
  
 [!code-csharp[System.Windows.Forms.ToolStrip.StackView#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StackView/CS/StackView.cs#1)]
 [!code-vb[System.Windows.Forms.ToolStrip.StackView#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StackView/VB/StackView.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="a69fd-108">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="a69fd-108">Compiling the Code</span></span>  
 <span data-ttu-id="a69fd-109">Ten przykład wymaga:</span><span class="sxs-lookup"><span data-stu-id="a69fd-109">This example requires:</span></span>  
  
-   <span data-ttu-id="a69fd-110">Odwołania do zestawów System.Drawing i pozycję System.Windows.Forms.</span><span class="sxs-lookup"><span data-stu-id="a69fd-110">References to the System.Drawing and System.Windows.Forms assemblies.</span></span>  
  
 <span data-ttu-id="a69fd-111">Aby dowiedzieć się, jak tworzyć aplikacje w tym przykładzie z wiersza polecenia dla języka Visual Basic lub Visual C#, zobacz [tworzenie z wiersza polecenia](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) lub [wiersza polecenia tworzenia przy użyciu csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="a69fd-111">For information about building this example from the command line for Visual Basic or Visual C#, see [Building from the Command Line](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="a69fd-112">Można także utworzyć tego przykładu w programie Visual Studio, wklejając kod do nowego projektu.</span><span class="sxs-lookup"><span data-stu-id="a69fd-112">You can also build this example in Visual Studio by pasting the code into a new project.</span></span>  <span data-ttu-id="a69fd-113">Zobacz też [instruktażu: Tworzenie profesjonalnego formantu ToolStrip](walkthrough-creating-a-professionally-styled-toolstrip-control.md).</span><span class="sxs-lookup"><span data-stu-id="a69fd-113">Also see [Walkthrough: Creating a Professionally Styled ToolStrip Control](walkthrough-creating-a-professionally-styled-toolstrip-control.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a69fd-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a69fd-114">See also</span></span>
- <xref:System.Windows.Forms.MenuStrip>
- <xref:System.Windows.Forms.ToolStrip>
- <xref:System.Windows.Forms.StatusStrip>
- [<span data-ttu-id="a69fd-115">ToolStrip, kontrolka</span><span class="sxs-lookup"><span data-stu-id="a69fd-115">ToolStrip Control</span></span>](../../../../docs/framework/winforms/controls/toolstrip-control-windows-forms.md)
- [<span data-ttu-id="a69fd-116">Instrukcje: Zapewnianie elementów Menu standardowego dla formularza</span><span class="sxs-lookup"><span data-stu-id="a69fd-116">How to: Provide Standard Menu Items to a Form</span></span>](../../../../docs/framework/winforms/controls/how-to-provide-standard-menu-items-to-a-form.md)
