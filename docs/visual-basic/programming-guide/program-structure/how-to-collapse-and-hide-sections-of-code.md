---
title: 'Instrukcje: Zwijanie i ukrywanie fragmentów kodu (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- Visual Basic, code collapsing
- Visual Basic, code hiding
- Visual Basic code, collapsing and hiding
ms.assetid: b770e8f5-e07d-491a-ab4b-a977980f9ba2
ms.openlocfilehash: bf2a7188456097ac227039e4d902a14eb182664c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61758278"
---
# <a name="how-to-collapse-and-hide-sections-of-code-visual-basic"></a><span data-ttu-id="4b359-102">Instrukcje: Zwijanie i ukrywanie fragmentów kodu (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4b359-102">How to: Collapse and Hide Sections of Code (Visual Basic)</span></span>
<span data-ttu-id="4b359-103">`#Region` Dyrektywy umożliwia zwijanie i ukrywanie fragmentów kodu w plikach języka Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="4b359-103">The `#Region` directive enables you to collapse and hide sections of code in Visual Basic files.</span></span> <span data-ttu-id="4b359-104">`#Region` Dyrektywy umożliwia określenie blok kodu, który będzie można rozszerzać lub Zwiń, korzystając z edytora kodu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="4b359-104">The `#Region` directive lets you specify a block of code that you can expand or collapse when using the Visual Studio code editor.</span></span> <span data-ttu-id="4b359-105">Możliwość selektywnego Ukryj kod sprawia, że pliki w zarządzaniu i czytelne.</span><span class="sxs-lookup"><span data-stu-id="4b359-105">The ability to hide code selectively makes your files more manageable and easier to read.</span></span> <span data-ttu-id="4b359-106">Aby uzyskać więcej informacji, zobacz [konspekt](/visualstudio/ide/outlining).</span><span class="sxs-lookup"><span data-stu-id="4b359-106">For more information, see [Outlining](/visualstudio/ide/outlining).</span></span>  
  
 <span data-ttu-id="4b359-107">`#Region` dyrektywy obsługują semantyki bloku kodu, takie jak `#If...#End If`.</span><span class="sxs-lookup"><span data-stu-id="4b359-107">`#Region` directives support code block semantics such as `#If...#End If`.</span></span> <span data-ttu-id="4b359-108">Oznacza, że ich nie może rozpoczynać się w jednym bloku i kończyć w innym; wartości początkowa i końcowa musi być w tym samym bloku.</span><span class="sxs-lookup"><span data-stu-id="4b359-108">This means they cannot begin in one block and end in another; the start and end must be in the same block.</span></span> <span data-ttu-id="4b359-109">`#Region` dyrektywy nie są obsługiwane w obrębie funkcji.</span><span class="sxs-lookup"><span data-stu-id="4b359-109">`#Region` directives are not supported within functions.</span></span>  
  
### <a name="to-collapse-and-hide-a-section-of-code"></a><span data-ttu-id="4b359-110">Aby zwinąć i ukryć sekcję kodu</span><span class="sxs-lookup"><span data-stu-id="4b359-110">To collapse and hide a section of code</span></span>  
  
- <span data-ttu-id="4b359-111">Umieść części kodu między `#Region` i `#End Region` instrukcje, jak w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="4b359-111">Place the section of code between the `#Region` and `#End Region` statements, as in the following example:</span></span>  
  
     [!code-vb[VbVbalrConditionalComp#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrConditionalComp/VB/Class1.vb#6)]  
  
     <span data-ttu-id="4b359-112">`#Region` Bloku można używać wiele razy w pliku kodu; w związku z tym, użytkownicy mogą definiować własne bloki procedur i klas, które z kolei mogą zostać zwinięty.</span><span class="sxs-lookup"><span data-stu-id="4b359-112">The `#Region` block can be used multiple times in a code file; thus, users can define their own blocks of procedures and classes that can, in turn, be collapsed.</span></span> <span data-ttu-id="4b359-113">`#Region` bloki mogą być zagnieżdżone w innych `#Region` bloków.</span><span class="sxs-lookup"><span data-stu-id="4b359-113">`#Region` blocks can also be nested within other `#Region` blocks.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="4b359-114">Ukrywanie kodu nie zapobiega on kompilowany i nie ma wpływu na `#If...#End If` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="4b359-114">Hiding code does not prevent it from being compiled and does not affect `#If...#End If` statements.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4b359-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="4b359-115">See also</span></span>

- [<span data-ttu-id="4b359-116">Kompilacja warunkowa</span><span class="sxs-lookup"><span data-stu-id="4b359-116">Conditional Compilation</span></span>](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)
- [<span data-ttu-id="4b359-117">#Region, dyrektywa</span><span class="sxs-lookup"><span data-stu-id="4b359-117">#Region Directive</span></span>](../../../visual-basic/language-reference/directives/region-directive.md)
- [<span data-ttu-id="4b359-118">#If...Then...#Else, dyrektywy</span><span class="sxs-lookup"><span data-stu-id="4b359-118">#If...Then...#Else Directives</span></span>](../../../visual-basic/language-reference/directives/if-then-else-directives.md)
- [<span data-ttu-id="4b359-119">Obramowanie</span><span class="sxs-lookup"><span data-stu-id="4b359-119">Outlining</span></span>](/visualstudio/ide/outlining)
