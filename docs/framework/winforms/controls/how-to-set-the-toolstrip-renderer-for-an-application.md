---
title: 'Porady: ustawienie modułu renderowania ToolStrip dla aplikacji'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Renderer property [Windows Forms]
- ToolStripProfessionalRenderer class [Windows Forms]
- ToolStrip control [Windows Forms]
- MenuStrip control [Windows Forms]
- toolbars [Windows Forms], customizing
ms.assetid: 46acef3e-9844-4ae8-9a2e-3006fe99cadf
ms.openlocfilehash: b86724bda83c701ad5c5872ae8d97bb490158e76
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/14/2018
ms.locfileid: "45618993"
---
# <a name="how-to-set-the-toolstrip-renderer-for-an-application"></a><span data-ttu-id="e0f42-102">Porady: ustawienie modułu renderowania ToolStrip dla aplikacji</span><span class="sxs-lookup"><span data-stu-id="e0f42-102">How to: Set the ToolStrip Renderer for an Application</span></span>
<span data-ttu-id="e0f42-103">Można dostosować wygląd Twojego <xref:System.Windows.Forms.ToolStrip> kontroluje indywidualnie lub dla wszystkich <xref:System.Windows.Forms.ToolStrip> formantów w aplikacji.</span><span class="sxs-lookup"><span data-stu-id="e0f42-103">You can customize the appearance of your <xref:System.Windows.Forms.ToolStrip> controls individually or for all the <xref:System.Windows.Forms.ToolStrip> controls in your application.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e0f42-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="e0f42-104">Example</span></span>  
 <span data-ttu-id="e0f42-105">Poniższy przykład kodu demonstruje sposób selektywnego stosowania niestandardowego modułu renderowania do <xref:System.Windows.Forms.ToolStrip> kontroli i <xref:System.Windows.Forms.MenuStrip> kontroli.</span><span class="sxs-lookup"><span data-stu-id="e0f42-105">The following code example demonstrates how to selectively apply a custom renderer to a <xref:System.Windows.Forms.ToolStrip> control and a <xref:System.Windows.Forms.MenuStrip> control.</span></span>  
  
 <span data-ttu-id="e0f42-106">Aby wykorzystać ten przykład kodu, skompiluj i uruchom aplikację, a następnie wybierz powodującym niestandardowe z zakresu <xref:System.Windows.Forms.ComboBox> kontroli.</span><span class="sxs-lookup"><span data-stu-id="e0f42-106">To use this code example, compile and run the application, and then select the scope of the custom rending from the <xref:System.Windows.Forms.ComboBox> control.</span></span> <span data-ttu-id="e0f42-107">Kliknij przycisk **Zastosuj** na ustawienie modułu renderowania.</span><span class="sxs-lookup"><span data-stu-id="e0f42-107">Click **Apply** to set the renderer.</span></span>  
  
 <span data-ttu-id="e0f42-108">Aby wyświetlić renderowanie elementów niestandardowych menu, wybierz <xref:System.Windows.Forms.MenuStrip> opcję <xref:System.Windows.Forms.ComboBox> sterowania, kliknij przycisk **Zastosuj**, a następnie otwórz **pliku** elementu menu.</span><span class="sxs-lookup"><span data-stu-id="e0f42-108">To see custom menu item rendering, select the <xref:System.Windows.Forms.MenuStrip> option from the <xref:System.Windows.Forms.ComboBox> control, click **Apply**, and then open the **File** menu item.</span></span>  
  
 [!code-csharp[System.Windows.Forms.ToolStrip.Misc#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/CS/Program.cs#1)]
 [!code-vb[System.Windows.Forms.ToolStrip.Misc#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/VB/Program.vb#1)]  
[!code-csharp[System.Windows.Forms.ToolStrip.Misc#70](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/CS/Program.cs#70)]
[!code-vb[System.Windows.Forms.ToolStrip.Misc#70](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/VB/Program.vb#70)]  
  
 <span data-ttu-id="e0f42-109">Ustaw <xref:System.Windows.Forms.ToolStripManager.Renderer%2A?displayProperty=nameWithType> właściwości do stosowania niestandardowego modułu renderowania dla wszystkich <xref:System.Windows.Forms.ToolStrip> formantów w aplikacji.</span><span class="sxs-lookup"><span data-stu-id="e0f42-109">Set the <xref:System.Windows.Forms.ToolStripManager.Renderer%2A?displayProperty=nameWithType> property to apply a custom renderer to all the <xref:System.Windows.Forms.ToolStrip> controls in your application.</span></span>  
  
 <span data-ttu-id="e0f42-110">Ustaw <xref:System.Windows.Forms.ToolStrip.Renderer%2A?displayProperty=nameWithType> właściwości do stosowania niestandardowego modułu renderowania z określoną osobą <xref:System.Windows.Forms.ToolStrip> kontroli.</span><span class="sxs-lookup"><span data-stu-id="e0f42-110">Set the <xref:System.Windows.Forms.ToolStrip.Renderer%2A?displayProperty=nameWithType> property to apply a custom renderer to an individual <xref:System.Windows.Forms.ToolStrip> control.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="e0f42-111">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="e0f42-111">Compiling the Code</span></span>  
 <span data-ttu-id="e0f42-112">Ten przykład wymaga:</span><span class="sxs-lookup"><span data-stu-id="e0f42-112">This example requires:</span></span>  
  
-   <span data-ttu-id="e0f42-113">Odwołania do zestawów System.Design System.Drawing i przestrzeń nazw System.Windows.Forms.</span><span class="sxs-lookup"><span data-stu-id="e0f42-113">References to the System.Design, System.Drawing, and System.Windows.Forms assemblies.</span></span>  
  
 <span data-ttu-id="e0f42-114">Aby uzyskać informacje o tworzeniu tego przykładu z wiersza polecenia dla programu visual Basic lub Visual C#, zobacz [tworzenie z wiersza polecenia](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) lub [wiersza polecenia tworzenia przy użyciu csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="e0f42-114">For information about building this example from the command line for visual Basic or Visual C#, see [Building from the Command Line](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="e0f42-115">Można także utworzyć tego przykładu w programie Visual Studio, wklejając kod do nowego projektu.</span><span class="sxs-lookup"><span data-stu-id="e0f42-115">You can also build this example in Visual Studio by pasting the code into a new project.</span></span>  <span data-ttu-id="e0f42-116">Zobacz też [porady: kompilowanie i uruchamianie pełną Windows Forms kodu przykładzie przy użyciu programu Visual Studio](https://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span><span class="sxs-lookup"><span data-stu-id="e0f42-116">Also see [How to: Compile and Run a Complete Windows Forms Code Example Using Visual Studio](https://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e0f42-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e0f42-117">See Also</span></span>  
 <xref:System.Windows.Forms.ToolStripManager>  
 <xref:System.Windows.Forms.MenuStrip>  
 <xref:System.Windows.Forms.ToolStrip>  
 <xref:System.Windows.Forms.ToolStripProfessionalRenderer>  
 [<span data-ttu-id="e0f42-118">ToolStrip, kontrolka</span><span class="sxs-lookup"><span data-stu-id="e0f42-118">ToolStrip Control</span></span>](../../../../docs/framework/winforms/controls/toolstrip-control-windows-forms.md)
