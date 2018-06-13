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
ms.openlocfilehash: 3bd526b08e1ba3be856e1e823cf8ef49ea9b6c97
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33604279"
---
# <a name="rem-statement-visual-basic"></a><span data-ttu-id="2c4ac-102">REM — Instrukcja (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2c4ac-102">REM Statement (Visual Basic)</span></span>
<span data-ttu-id="2c4ac-103">Używana do włączenia uwagi wyjaśniające w kodzie źródłowym programu.</span><span class="sxs-lookup"><span data-stu-id="2c4ac-103">Used to include explanatory remarks in the source code of a program.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2c4ac-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="2c4ac-104">Syntax</span></span>  
  
```  
REM comment  
' comment  
```  
  
## <a name="parts"></a><span data-ttu-id="2c4ac-105">Części</span><span class="sxs-lookup"><span data-stu-id="2c4ac-105">Parts</span></span>  
 `comment`  
 <span data-ttu-id="2c4ac-106">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="2c4ac-106">Optional.</span></span> <span data-ttu-id="2c4ac-107">Tekst wszelkie komentarze, które chcesz dołączyć.</span><span class="sxs-lookup"><span data-stu-id="2c4ac-107">The text of any comment you want to include.</span></span> <span data-ttu-id="2c4ac-108">Odstęp jest wymagany między `REM` — słowo kluczowe i `comment`.</span><span class="sxs-lookup"><span data-stu-id="2c4ac-108">A space is required between the `REM` keyword and `comment`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2c4ac-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="2c4ac-109">Remarks</span></span>  
 <span data-ttu-id="2c4ac-110">Możesz też zaznaczyć `REM` instrukcji wyłącznie na wiersz, lub można umieścić w wierszu po instrukcji innego.</span><span class="sxs-lookup"><span data-stu-id="2c4ac-110">You can put a `REM` statement alone on a line, or you can put it on a line following another statement.</span></span> <span data-ttu-id="2c4ac-111">`REM` Instrukcja musi być ostatnią instrukcją w wierszu.</span><span class="sxs-lookup"><span data-stu-id="2c4ac-111">The `REM` statement must be the last statement on the line.</span></span> <span data-ttu-id="2c4ac-112">Jeśli wynika z inną instrukcję `REM` musi być oddzielona od tej instrukcji spacją.</span><span class="sxs-lookup"><span data-stu-id="2c4ac-112">If it follows another statement, the `REM` must be separated from that statement by a space.</span></span>  
  
 <span data-ttu-id="2c4ac-113">Można użyć pojedynczego cudzysłowu (`'`) zamiast `REM`.</span><span class="sxs-lookup"><span data-stu-id="2c4ac-113">You can use a single quotation mark (`'`) instead of `REM`.</span></span> <span data-ttu-id="2c4ac-114">Dotyczy to Twojego komentarza następuje innej instrukcji w tym samym wierszu czy samodzielnie znajduje się w wierszu.</span><span class="sxs-lookup"><span data-stu-id="2c4ac-114">This is true whether your comment follows another statement on the same line or sits alone on a line.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="2c4ac-115">Nie można kontynuować `REM` instrukcji za pomocą sekwencja kontynuacji wiersza (`_`).</span><span class="sxs-lookup"><span data-stu-id="2c4ac-115">You cannot continue a `REM` statement by using a line-continuation sequence (`_`).</span></span> <span data-ttu-id="2c4ac-116">Po rozpoczęciu komentarz, kompilator nie bada znaki specjalne znaczenie.</span><span class="sxs-lookup"><span data-stu-id="2c4ac-116">Once a comment begins, the compiler does not examine the characters for special meaning.</span></span> <span data-ttu-id="2c4ac-117">Komentarz wielu linii, użyj innego `REM` instrukcji lub symbol komentarza (`'`) w każdym wierszu.</span><span class="sxs-lookup"><span data-stu-id="2c4ac-117">For a multiple-line comment, use another `REM` statement or a comment symbol (`'`) on each line.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2c4ac-118">Przykład</span><span class="sxs-lookup"><span data-stu-id="2c4ac-118">Example</span></span>  
 <span data-ttu-id="2c4ac-119">Poniższy przykład przedstawia `REM` instrukcja, która jest używana do włączenia uwagi wyjaśniające w programie.</span><span class="sxs-lookup"><span data-stu-id="2c4ac-119">The following example illustrates the `REM` statement, which is used to include explanatory remarks in a program.</span></span> <span data-ttu-id="2c4ac-120">Przedstawiono również zamiast używania znak pojedynczego cudzysłowu (`'`) zamiast `REM`.</span><span class="sxs-lookup"><span data-stu-id="2c4ac-120">It also shows the alternative of using the single quotation-mark character (`'`) instead of `REM`.</span></span>  
  
 [!code-vb[VbVbalrStatements#6](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/rem-statement_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="2c4ac-121">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="2c4ac-121">See Also</span></span>  
 [<span data-ttu-id="2c4ac-122">Komentarze w kodzie</span><span class="sxs-lookup"><span data-stu-id="2c4ac-122">Comments in Code</span></span>](../../../visual-basic/programming-guide/program-structure/comments-in-code.md)  
 [<span data-ttu-id="2c4ac-123">Instrukcje: przerywanie i łączenie instrukcji w kodzie</span><span class="sxs-lookup"><span data-stu-id="2c4ac-123">How to: Break and Combine Statements in Code</span></span>](../../../visual-basic/programming-guide/program-structure/how-to-break-and-combine-statements-in-code.md)
