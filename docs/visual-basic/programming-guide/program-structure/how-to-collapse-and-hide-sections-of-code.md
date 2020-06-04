---
title: 'Instrukcje: Zwijanie i ukrywanie fragmentów kodu'
ms.date: 07/20/2015
helpviewer_keywords:
- Visual Basic, code collapsing
- Visual Basic, code hiding
- Visual Basic code, collapsing and hiding
ms.assetid: b770e8f5-e07d-491a-ab4b-a977980f9ba2
ms.openlocfilehash: c11affe9c4dd4251ba8ff4b87029d314970b5fcb
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84404852"
---
# <a name="how-to-collapse-and-hide-sections-of-code-visual-basic"></a><span data-ttu-id="9b81e-102">Porady: zwijanie i ukrywanie fragmentów kodu (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9b81e-102">How to: Collapse and Hide Sections of Code (Visual Basic)</span></span>

<span data-ttu-id="9b81e-103">`#Region`Dyrektywa umożliwia zwijanie i ukrywanie fragmentów kodu w plikach Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="9b81e-103">The `#Region` directive enables you to collapse and hide sections of code in Visual Basic files.</span></span> <span data-ttu-id="9b81e-104">`#Region`Dyrektywa pozwala określić blok kodu, który można rozwijać lub zwijać podczas korzystania z edytora kodu programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="9b81e-104">The `#Region` directive lets you specify a block of code that you can expand or collapse when using the Visual Studio code editor.</span></span> <span data-ttu-id="9b81e-105">Możliwość ukrycia kodu selektywnie sprawia, że pliki są bardziej łatwe do zarządzania i łatwiejsze do odczytania.</span><span class="sxs-lookup"><span data-stu-id="9b81e-105">The ability to hide code selectively makes your files more manageable and easier to read.</span></span> <span data-ttu-id="9b81e-106">Aby uzyskać więcej informacji, zobacz [Tworzenie konspektu](/visualstudio/ide/outlining).</span><span class="sxs-lookup"><span data-stu-id="9b81e-106">For more information, see [Outlining](/visualstudio/ide/outlining).</span></span>

<span data-ttu-id="9b81e-107">`#Region`dyrektywy obsługują semantykę bloków kodu, taką jak `#If...#End If` .</span><span class="sxs-lookup"><span data-stu-id="9b81e-107">`#Region` directives support code block semantics such as `#If...#End If`.</span></span> <span data-ttu-id="9b81e-108">Oznacza to, że nie mogą rozpoczynać się w jednym bloku i kończyć w innym; początkowy i końcowy musi znajdować się w tym samym bloku.</span><span class="sxs-lookup"><span data-stu-id="9b81e-108">This means they cannot begin in one block and end in another; the start and end must be in the same block.</span></span> <span data-ttu-id="9b81e-109">`#Region`dyrektywy nie są obsługiwane w funkcjach.</span><span class="sxs-lookup"><span data-stu-id="9b81e-109">`#Region` directives are not supported within functions.</span></span>

## <a name="to-collapse-and-hide-a-section-of-code"></a><span data-ttu-id="9b81e-110">Aby zwinąć i ukryć sekcję kodu</span><span class="sxs-lookup"><span data-stu-id="9b81e-110">To collapse and hide a section of code</span></span>

<span data-ttu-id="9b81e-111">Umieść sekcję kodu między `#Region` `#End Region` instrukcjami i, jak w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="9b81e-111">Place the section of code between the `#Region` and `#End Region` statements, as in the following example:</span></span>

[!code-vb[VbVbalrConditionalComp#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrConditionalComp/VB/Class1.vb#6)]

<span data-ttu-id="9b81e-112">`#Region`Blok może być używany wiele razy w pliku kodu. w ten sposób użytkownicy mogą definiować własne bloki procedur i klas, które mogą z kolei być zwinięte.</span><span class="sxs-lookup"><span data-stu-id="9b81e-112">The `#Region` block can be used multiple times in a code file; thus, users can define their own blocks of procedures and classes that can, in turn, be collapsed.</span></span> <span data-ttu-id="9b81e-113">`#Region`bloki mogą być również zagnieżdżane w innych `#Region` blokach.</span><span class="sxs-lookup"><span data-stu-id="9b81e-113">`#Region` blocks can also be nested within other `#Region` blocks.</span></span>

> [!NOTE]
> <span data-ttu-id="9b81e-114">Ukrycie kodu nie uniemożliwia jego skompilowania i nie wpływa na `#If...#End If` instrukcje.</span><span class="sxs-lookup"><span data-stu-id="9b81e-114">Hiding code does not prevent it from being compiled and does not affect `#If...#End If` statements.</span></span>

## <a name="see-also"></a><span data-ttu-id="9b81e-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="9b81e-115">See also</span></span>

- [<span data-ttu-id="9b81e-116">Kompilacja warunkowa</span><span class="sxs-lookup"><span data-stu-id="9b81e-116">Conditional Compilation</span></span>](conditional-compilation.md)
- [<span data-ttu-id="9b81e-117">#Region — dyrektywa</span><span class="sxs-lookup"><span data-stu-id="9b81e-117">#Region Directive</span></span>](../../language-reference/directives/region-directive.md)
- [<span data-ttu-id="9b81e-118">#If... Then... #Else — dyrektywy</span><span class="sxs-lookup"><span data-stu-id="9b81e-118">#If...Then...#Else Directives</span></span>](../../language-reference/directives/if-then-else-directives.md)
- [<span data-ttu-id="9b81e-119">Tworzenie konspektu</span><span class="sxs-lookup"><span data-stu-id="9b81e-119">Outlining</span></span>](/visualstudio/ide/outlining)
