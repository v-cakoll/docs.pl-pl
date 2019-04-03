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
ms.openlocfilehash: 3c63c5613b40cb2014c77a0a996e3acb2cc304d4
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/02/2019
ms.locfileid: "58817022"
---
# <a name="rem-statement-visual-basic"></a><span data-ttu-id="50fa9-102">REM — Instrukcja (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="50fa9-102">REM Statement (Visual Basic)</span></span>
<span data-ttu-id="50fa9-103">Używane, aby uwzględnić uwagi wyjaśniające w kodzie źródłowym programu.</span><span class="sxs-lookup"><span data-stu-id="50fa9-103">Used to include explanatory remarks in the source code of a program.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="50fa9-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="50fa9-104">Syntax</span></span>  
  
```  
REM comment  
' comment  
```  
  
## <a name="parts"></a><span data-ttu-id="50fa9-105">Części</span><span class="sxs-lookup"><span data-stu-id="50fa9-105">Parts</span></span>  
 `comment`  
 <span data-ttu-id="50fa9-106">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="50fa9-106">Optional.</span></span> <span data-ttu-id="50fa9-107">Tekst dodatkowe uwagi, które chcesz dołączyć.</span><span class="sxs-lookup"><span data-stu-id="50fa9-107">The text of any comment you want to include.</span></span> <span data-ttu-id="50fa9-108">Obszar jest wymagany między `REM` — słowo kluczowe i `comment`.</span><span class="sxs-lookup"><span data-stu-id="50fa9-108">A space is required between the `REM` keyword and `comment`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="50fa9-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="50fa9-109">Remarks</span></span>  
 <span data-ttu-id="50fa9-110">Możesz umieścić `REM` instrukcji wyłącznie w wierszu, możesz ją umieścić w wierszu po innej instrukcji.</span><span class="sxs-lookup"><span data-stu-id="50fa9-110">You can put a `REM` statement alone on a line, or you can put it on a line following another statement.</span></span> <span data-ttu-id="50fa9-111">`REM` Instrukcja musi być ostatnią instrukcją w wierszu.</span><span class="sxs-lookup"><span data-stu-id="50fa9-111">The `REM` statement must be the last statement on the line.</span></span> <span data-ttu-id="50fa9-112">Jeśli jest zgodna z innej instrukcji `REM` muszą być oddzielone od tej instrukcji spacjami.</span><span class="sxs-lookup"><span data-stu-id="50fa9-112">If it follows another statement, the `REM` must be separated from that statement by a space.</span></span>  
  
 <span data-ttu-id="50fa9-113">Można użyć pojedynczego cudzysłowu (`'`) zamiast `REM`.</span><span class="sxs-lookup"><span data-stu-id="50fa9-113">You can use a single quotation mark (`'`) instead of `REM`.</span></span> <span data-ttu-id="50fa9-114">Ta zasada obowiązuje, czy Twój komentarz poniżej innej instrukcji w tym samym wierszu lub samodzielnie znajduje się w wierszu.</span><span class="sxs-lookup"><span data-stu-id="50fa9-114">This is true whether your comment follows another statement on the same line or sits alone on a line.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="50fa9-115">Nie można kontynuować `REM` instrukcji przy użyciu sekwencji kontynuacji wiersza (`_`).</span><span class="sxs-lookup"><span data-stu-id="50fa9-115">You cannot continue a `REM` statement by using a line-continuation sequence (`_`).</span></span> <span data-ttu-id="50fa9-116">Po rozpoczęciu komentarz, kompilator nie analizuje znaki specjalne znaczenie.</span><span class="sxs-lookup"><span data-stu-id="50fa9-116">Once a comment begins, the compiler does not examine the characters for special meaning.</span></span> <span data-ttu-id="50fa9-117">Komentarz do wielu linii, użyj innego `REM` instrukcji lub symbol komentarza (`'`) w każdym wierszu.</span><span class="sxs-lookup"><span data-stu-id="50fa9-117">For a multiple-line comment, use another `REM` statement or a comment symbol (`'`) on each line.</span></span>  
  
## <a name="example"></a><span data-ttu-id="50fa9-118">Przykład</span><span class="sxs-lookup"><span data-stu-id="50fa9-118">Example</span></span>  
 <span data-ttu-id="50fa9-119">W poniższym przykładzie pokazano `REM` instrukcję, która jest używana do włączenia uwagi wyjaśniające w programie.</span><span class="sxs-lookup"><span data-stu-id="50fa9-119">The following example illustrates the `REM` statement, which is used to include explanatory remarks in a program.</span></span> <span data-ttu-id="50fa9-120">Pokazuje także alternatywne przy użyciu znaku pojedynczego cudzysłowu (`'`) zamiast `REM`.</span><span class="sxs-lookup"><span data-stu-id="50fa9-120">It also shows the alternative of using the single quotation-mark character (`'`) instead of `REM`.</span></span>  
  
 [!code-vb[VbVbalrStatements#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#6)]  
  
## <a name="see-also"></a><span data-ttu-id="50fa9-121">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="50fa9-121">See also</span></span>

- [<span data-ttu-id="50fa9-122">Komentarze w kodzie</span><span class="sxs-lookup"><span data-stu-id="50fa9-122">Comments in Code</span></span>](../../../visual-basic/programming-guide/program-structure/comments-in-code.md)
- [<span data-ttu-id="50fa9-123">Instrukcje: przerywanie i łączenie instrukcji w kodzie</span><span class="sxs-lookup"><span data-stu-id="50fa9-123">How to: Break and Combine Statements in Code</span></span>](../../../visual-basic/programming-guide/program-structure/how-to-break-and-combine-statements-in-code.md)
