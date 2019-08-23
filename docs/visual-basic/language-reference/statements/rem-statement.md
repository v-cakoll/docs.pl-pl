---
title: REM — Instrukcja (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.'
- vb.Rem
- Rem
- "'"
helpviewer_keywords:
- REM statement [Visual Basic]
- comments, Visual Basic code
- code comments, Visual Basic
- Visual Basic code, comments
- "' comment marker character [Visual Basic]"
ms.assetid: 34126d7f-e0f9-476d-91e6-b31b398615dc
ms.openlocfilehash: 16149ce42e3476cf07a62298f83734fee9ec7253
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69957757"
---
# <a name="rem-statement-visual-basic"></a><span data-ttu-id="cacc5-102">REM — Instrukcja (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="cacc5-102">REM Statement (Visual Basic)</span></span>
<span data-ttu-id="cacc5-103">Służy do uwzględnienia uwag objaśniających kod źródłowy programu.</span><span class="sxs-lookup"><span data-stu-id="cacc5-103">Used to include explanatory remarks in the source code of a program.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cacc5-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="cacc5-104">Syntax</span></span>  
  
```  
REM comment  
' comment  
```  
  
## <a name="parts"></a><span data-ttu-id="cacc5-105">Części</span><span class="sxs-lookup"><span data-stu-id="cacc5-105">Parts</span></span>  
 `comment`  
 <span data-ttu-id="cacc5-106">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="cacc5-106">Optional.</span></span> <span data-ttu-id="cacc5-107">Tekst komentarza, który ma zostać uwzględniony.</span><span class="sxs-lookup"><span data-stu-id="cacc5-107">The text of any comment you want to include.</span></span> <span data-ttu-id="cacc5-108">Między `REM` słowem kluczowym i `comment`.</span><span class="sxs-lookup"><span data-stu-id="cacc5-108">A space is required between the `REM` keyword and `comment`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="cacc5-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="cacc5-109">Remarks</span></span>  
 <span data-ttu-id="cacc5-110">`REM` Instrukcję można umieścić samodzielnie w wierszu lub można ją umieścić w wierszu po innej instrukcji.</span><span class="sxs-lookup"><span data-stu-id="cacc5-110">You can put a `REM` statement alone on a line, or you can put it on a line following another statement.</span></span> <span data-ttu-id="cacc5-111">`REM` Instrukcja musi być ostatnią instrukcją w wierszu.</span><span class="sxs-lookup"><span data-stu-id="cacc5-111">The `REM` statement must be the last statement on the line.</span></span> <span data-ttu-id="cacc5-112">Jeśli jest ona zgodna z inną instrukcją, `REM` musi być oddzielona od tej instrukcji spacją.</span><span class="sxs-lookup"><span data-stu-id="cacc5-112">If it follows another statement, the `REM` must be separated from that statement by a space.</span></span>  
  
 <span data-ttu-id="cacc5-113">Można użyć pojedynczego cudzysłowu (`'`) `REM`zamiast.</span><span class="sxs-lookup"><span data-stu-id="cacc5-113">You can use a single quotation mark (`'`) instead of `REM`.</span></span> <span data-ttu-id="cacc5-114">Dzieje się tak, gdy komentarz jest podążany za inną instrukcją w tym samym wierszu lub w wierszu.</span><span class="sxs-lookup"><span data-stu-id="cacc5-114">This is true whether your comment follows another statement on the same line or sits alone on a line.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="cacc5-115">Nie można kontynuować `REM` instrukcji przy użyciu sekwencji kontynuacji wiersza (`_`).</span><span class="sxs-lookup"><span data-stu-id="cacc5-115">You cannot continue a `REM` statement by using a line-continuation sequence (`_`).</span></span> <span data-ttu-id="cacc5-116">Po rozpoczęciu komentarza kompilator nie bada znaków pod kątem specjalnego znaczenia.</span><span class="sxs-lookup"><span data-stu-id="cacc5-116">Once a comment begins, the compiler does not examine the characters for special meaning.</span></span> <span data-ttu-id="cacc5-117">W przypadku komentarza z wieloma wierszami Użyj `REM` innej instrukcji lub symbolu komentarza`'`() w każdym wierszu.</span><span class="sxs-lookup"><span data-stu-id="cacc5-117">For a multiple-line comment, use another `REM` statement or a comment symbol (`'`) on each line.</span></span>  
  
## <a name="example"></a><span data-ttu-id="cacc5-118">Przykład</span><span class="sxs-lookup"><span data-stu-id="cacc5-118">Example</span></span>  
 <span data-ttu-id="cacc5-119">Poniższy przykład ilustruje `REM` instrukcję, która jest używana do dołączania uwag objaśniających do programu.</span><span class="sxs-lookup"><span data-stu-id="cacc5-119">The following example illustrates the `REM` statement, which is used to include explanatory remarks in a program.</span></span> <span data-ttu-id="cacc5-120">Pokazuje również alternatywę użycia znaku pojedynczego cudzysłowu (`'`) `REM`zamiast.</span><span class="sxs-lookup"><span data-stu-id="cacc5-120">It also shows the alternative of using the single quotation-mark character (`'`) instead of `REM`.</span></span>  
  
 [!code-vb[VbVbalrStatements#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#6)]  
  
## <a name="see-also"></a><span data-ttu-id="cacc5-121">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="cacc5-121">See also</span></span>

- [<span data-ttu-id="cacc5-122">Komentarze w kodzie</span><span class="sxs-lookup"><span data-stu-id="cacc5-122">Comments in Code</span></span>](../../../visual-basic/programming-guide/program-structure/comments-in-code.md)
- [<span data-ttu-id="cacc5-123">Instrukcje: przerywanie i łączenie instrukcji w kodzie</span><span class="sxs-lookup"><span data-stu-id="cacc5-123">How to: Break and Combine Statements in Code</span></span>](../../../visual-basic/programming-guide/program-structure/how-to-break-and-combine-statements-in-code.md)
