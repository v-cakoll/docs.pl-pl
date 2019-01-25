---
title: 'Instrukcje: Zwijanie i ukrywanie fragmentów kodu (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- Visual Basic, code collapsing
- Visual Basic, code hiding
- Visual Basic code, collapsing and hiding
ms.assetid: b770e8f5-e07d-491a-ab4b-a977980f9ba2
ms.openlocfilehash: 1282269f06f89645c213f3daaa1bd29e95a44d35
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54668720"
---
# <a name="how-to-collapse-and-hide-sections-of-code-visual-basic"></a><span data-ttu-id="26847-102">Instrukcje: Zwijanie i ukrywanie fragmentów kodu (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="26847-102">How to: Collapse and Hide Sections of Code (Visual Basic)</span></span>
<span data-ttu-id="26847-103">`#Region` Dyrektywy umożliwia zwijanie i ukrywanie fragmentów kodu w plikach języka Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="26847-103">The `#Region` directive enables you to collapse and hide sections of code in Visual Basic files.</span></span> <span data-ttu-id="26847-104">`#Region` Dyrektywy umożliwia określenie blok kodu, który będzie można rozszerzać lub Zwiń, korzystając z edytora kodu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="26847-104">The `#Region` directive lets you specify a block of code that you can expand or collapse when using the Visual Studio code editor.</span></span> <span data-ttu-id="26847-105">Możliwość selektywnego Ukryj kod sprawia, że pliki w zarządzaniu i czytelne.</span><span class="sxs-lookup"><span data-stu-id="26847-105">The ability to hide code selectively makes your files more manageable and easier to read.</span></span> <span data-ttu-id="26847-106">Aby uzyskać więcej informacji, zobacz [konspekt](/visualstudio/ide/outlining).</span><span class="sxs-lookup"><span data-stu-id="26847-106">For more information, see [Outlining](/visualstudio/ide/outlining).</span></span>  
  
 <span data-ttu-id="26847-107">`#Region` dyrektywy obsługują semantyki bloku kodu, takie jak `#If...#End If`.</span><span class="sxs-lookup"><span data-stu-id="26847-107">`#Region` directives support code block semantics such as `#If...#End If`.</span></span> <span data-ttu-id="26847-108">Oznacza, że ich nie może rozpoczynać się w jednym bloku i kończyć w innym; wartości początkowa i końcowa musi być w tym samym bloku.</span><span class="sxs-lookup"><span data-stu-id="26847-108">This means they cannot begin in one block and end in another; the start and end must be in the same block.</span></span> <span data-ttu-id="26847-109">`#Region` dyrektywy nie są obsługiwane w obrębie funkcji.</span><span class="sxs-lookup"><span data-stu-id="26847-109">`#Region` directives are not supported within functions.</span></span>  
  
### <a name="to-collapse-and-hide-a-section-of-code"></a><span data-ttu-id="26847-110">Aby zwinąć i ukryć sekcję kodu</span><span class="sxs-lookup"><span data-stu-id="26847-110">To collapse and hide a section of code</span></span>  
  
-   <span data-ttu-id="26847-111">Umieść części kodu między `#Region` i `#End Region` instrukcje, jak w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="26847-111">Place the section of code between the `#Region` and `#End Region` statements, as in the following example:</span></span>  
  
     [!code-vb[VbVbalrConditionalComp#6](../../../visual-basic/language-reference/directives/codesnippet/VisualBasic/how-to-collapse-and-hide-sections-of-code_1.vb)]  
  
     <span data-ttu-id="26847-112">`#Region` Bloku można używać wiele razy w pliku kodu; w związku z tym, użytkownicy mogą definiować własne bloki procedur i klas, które z kolei mogą zostać zwinięty.</span><span class="sxs-lookup"><span data-stu-id="26847-112">The `#Region` block can be used multiple times in a code file; thus, users can define their own blocks of procedures and classes that can, in turn, be collapsed.</span></span> <span data-ttu-id="26847-113">`#Region` bloki mogą być zagnieżdżone w innych `#Region` bloków.</span><span class="sxs-lookup"><span data-stu-id="26847-113">`#Region` blocks can also be nested within other `#Region` blocks.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="26847-114">Ukrywanie kodu nie zapobiega on kompilowany i nie ma wpływu na `#If...#End If` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="26847-114">Hiding code does not prevent it from being compiled and does not affect `#If...#End If` statements.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="26847-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="26847-115">See also</span></span>
- [<span data-ttu-id="26847-116">Kompilacja warunkowa</span><span class="sxs-lookup"><span data-stu-id="26847-116">Conditional Compilation</span></span>](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)
- [<span data-ttu-id="26847-117">#Region, dyrektywa</span><span class="sxs-lookup"><span data-stu-id="26847-117">#Region Directive</span></span>](../../../visual-basic/language-reference/directives/region-directive.md)
- [<span data-ttu-id="26847-118">#If...Then...#Else, dyrektywy</span><span class="sxs-lookup"><span data-stu-id="26847-118">#If...Then...#Else Directives</span></span>](../../../visual-basic/language-reference/directives/if-then-else-directives.md)
- [<span data-ttu-id="26847-119">Obramowanie</span><span class="sxs-lookup"><span data-stu-id="26847-119">Outlining</span></span>](/visualstudio/ide/outlining)
