---
title: 'Porady: dostosowywanie wyglądu wierszy w formancie DataGridView formularzy systemu Windows'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data grids [Windows Forms], customizing rows
- rows [Windows Forms], customizing in DataGridView control
- DataGridView control [Windows Forms], customizing rows
ms.assetid: d40b53d2-7e7c-48c5-8570-6e79d15c3bbb
ms.openlocfilehash: 445f6a1ab272bbf818a031b6d39d87cf6b7e5706
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/01/2018
ms.locfileid: "43392675"
---
# <a name="how-to-customize-the-appearance-of-rows-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="fc52a-102">Porady: dostosowywanie wyglądu wierszy w formancie DataGridView formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="fc52a-102">How to: Customize the Appearance of Rows in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="fc52a-103">Można sterować wyglądem <xref:System.Windows.Forms.DataGridView> wierszy dzięki obsłudze jedną lub obie <xref:System.Windows.Forms.DataGridView.RowPrePaint?displayProperty=nameWithType> i <xref:System.Windows.Forms.DataGridView.RowPostPaint?displayProperty=nameWithType> zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="fc52a-103">You can control the appearance of <xref:System.Windows.Forms.DataGridView> rows by handling one or both of the <xref:System.Windows.Forms.DataGridView.RowPrePaint?displayProperty=nameWithType> and <xref:System.Windows.Forms.DataGridView.RowPostPaint?displayProperty=nameWithType> events.</span></span> <span data-ttu-id="fc52a-104">Te zdarzenia są zaprojektowane tak, aby można malować tylko co chcesz while, dzięki czemu <xref:System.Windows.Forms.DataGridView> kontroli malowanie pozostałe.</span><span class="sxs-lookup"><span data-stu-id="fc52a-104">These events are designed so that you can paint only what you want to while letting the <xref:System.Windows.Forms.DataGridView> control paint the rest.</span></span> <span data-ttu-id="fc52a-105">Na przykład, jeśli chcesz malować tło niestandardowe mogą obsługiwać <xref:System.Windows.Forms.DataGridView.RowPrePaint?displayProperty=nameWithType> zdarzeń, dzięki czemu pojedyncze komórki malowanie własne zawartość pierwszego planu.</span><span class="sxs-lookup"><span data-stu-id="fc52a-105">For example, if you want to paint a custom background, you can handle the <xref:System.Windows.Forms.DataGridView.RowPrePaint?displayProperty=nameWithType> event and let the individual cells paint their own foreground content.</span></span> <span data-ttu-id="fc52a-106">Alternatywnie można pozwolić komórek malowanie samodzielnie i Dodaj zawartość niestandardowego narzędzia w obsłudze dla <xref:System.Windows.Forms.DataGridView.RowPostPaint?displayProperty=nameWithType> zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="fc52a-106">Alternately, you can let the cells paint themselves and add custom foreground content in a handler for the <xref:System.Windows.Forms.DataGridView.RowPostPaint?displayProperty=nameWithType> event.</span></span> <span data-ttu-id="fc52a-107">Można również wyłączyć malowania komórki i malowanie wszystko samodzielnie w <xref:System.Windows.Forms.DataGridView.RowPrePaint?displayProperty=nameWithType> programu obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="fc52a-107">You can also disable cell painting and paint everything yourself in a <xref:System.Windows.Forms.DataGridView.RowPrePaint?displayProperty=nameWithType> event handler.</span></span>  
  
 <span data-ttu-id="fc52a-108">Poniższy przykładowy kod implementuje programy obsługi dla obu zdarzeń w celu zaznaczenia gradientu tła i część zawartości niestandardowych pierwszego planu, obejmującej wiele kolumn.</span><span class="sxs-lookup"><span data-stu-id="fc52a-108">The following code example implements handlers for both events in order to provide a gradient selection background and some custom foreground content that spans multiple columns.</span></span>  
  
## <a name="example"></a><span data-ttu-id="fc52a-109">Przykład</span><span class="sxs-lookup"><span data-stu-id="fc52a-109">Example</span></span>  
 [!code-csharp[System.Windows.Forms.DataGridViewRowPainting#00](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewRowPainting/CS/datagridviewrowpainting.cs#00)]
 [!code-vb[System.Windows.Forms.DataGridViewRowPainting#00](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewRowPainting/VB/datagridviewrowpainting.vb#00)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="fc52a-110">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="fc52a-110">Compiling the Code</span></span>  
 <span data-ttu-id="fc52a-111">Ten przykład wymaga:</span><span class="sxs-lookup"><span data-stu-id="fc52a-111">This example requires:</span></span>  
  
-   <span data-ttu-id="fc52a-112">Odwołania do zestawów systemu, System.Drawing i przestrzeń nazw System.Windows.Forms.</span><span class="sxs-lookup"><span data-stu-id="fc52a-112">References to the System, System.Drawing, and System.Windows.Forms assemblies.</span></span>  
  
 <span data-ttu-id="fc52a-113">Aby dowiedzieć się, jak tworzyć aplikacje w tym przykładzie z wiersza polecenia dla języka Visual Basic lub Visual C#, zobacz [tworzenie z wiersza polecenia](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) lub [wiersza polecenia tworzenia przy użyciu csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="fc52a-113">For information about building this example from the command line for Visual Basic or Visual C#, see [Building from the Command Line](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="fc52a-114">Można także utworzyć tego przykładu w programie Visual Studio, wklejając kod do nowego projektu.</span><span class="sxs-lookup"><span data-stu-id="fc52a-114">You can also build this example in Visual Studio by pasting the code into a new project.</span></span>  <span data-ttu-id="fc52a-115">Zobacz też [porady: kompilowanie i uruchamianie pełną Windows Forms kodu przykładzie przy użyciu programu Visual Studio](https://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span><span class="sxs-lookup"><span data-stu-id="fc52a-115">Also see [How to: Compile and Run a Complete Windows Forms Code Example Using Visual Studio](https://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fc52a-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="fc52a-116">See Also</span></span>  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.DataGridView.RowPrePaint?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridView.RowPostPaint?displayProperty=nameWithType>  
 [<span data-ttu-id="fc52a-117">Dostosowywanie kontrolki DataGridView formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="fc52a-117">Customizing the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/customizing-the-windows-forms-datagridview-control.md)  
 [<span data-ttu-id="fc52a-118">DataGridView, kontrolka — architektura</span><span class="sxs-lookup"><span data-stu-id="fc52a-118">DataGridView Control Architecture</span></span>](../../../../docs/framework/winforms/controls/datagridview-control-architecture-windows-forms.md)
