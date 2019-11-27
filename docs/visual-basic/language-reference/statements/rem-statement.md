---
title: REM — Instrukcja
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
ms.openlocfilehash: bdde4beae242c3175b02cd2af252babb850416f6
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74346726"
---
# <a name="rem-statement-visual-basic"></a><span data-ttu-id="444c8-102">REM — Instrukcja (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="444c8-102">REM Statement (Visual Basic)</span></span>
<span data-ttu-id="444c8-103">Służy do uwzględnienia uwag objaśniających kod źródłowy programu.</span><span class="sxs-lookup"><span data-stu-id="444c8-103">Used to include explanatory remarks in the source code of a program.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="444c8-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="444c8-104">Syntax</span></span>  
  
```vb  
REM comment  
' comment  
```  
  
## <a name="parts"></a><span data-ttu-id="444c8-105">Części</span><span class="sxs-lookup"><span data-stu-id="444c8-105">Parts</span></span>  
 `comment`  
 <span data-ttu-id="444c8-106">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="444c8-106">Optional.</span></span> <span data-ttu-id="444c8-107">Tekst komentarza, który ma zostać uwzględniony.</span><span class="sxs-lookup"><span data-stu-id="444c8-107">The text of any comment you want to include.</span></span> <span data-ttu-id="444c8-108">Między słowem kluczowym `REM` i `comment`jest wymagana spacja.</span><span class="sxs-lookup"><span data-stu-id="444c8-108">A space is required between the `REM` keyword and `comment`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="444c8-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="444c8-109">Remarks</span></span>  
 <span data-ttu-id="444c8-110">Można umieścić instrukcję `REM` w wierszu lub można ją umieścić w wierszu po innej instrukcji.</span><span class="sxs-lookup"><span data-stu-id="444c8-110">You can put a `REM` statement alone on a line, or you can put it on a line following another statement.</span></span> <span data-ttu-id="444c8-111">Instrukcja `REM` musi być ostatnią instrukcją w wierszu.</span><span class="sxs-lookup"><span data-stu-id="444c8-111">The `REM` statement must be the last statement on the line.</span></span> <span data-ttu-id="444c8-112">Jeśli jest ona zgodna z inną instrukcją, `REM` musi być oddzielona od tej instrukcji przez spację.</span><span class="sxs-lookup"><span data-stu-id="444c8-112">If it follows another statement, the `REM` must be separated from that statement by a space.</span></span>  
  
 <span data-ttu-id="444c8-113">Możesz użyć pojedynczego cudzysłowu (`'`), a nie `REM`.</span><span class="sxs-lookup"><span data-stu-id="444c8-113">You can use a single quotation mark (`'`) instead of `REM`.</span></span> <span data-ttu-id="444c8-114">Dzieje się tak, gdy komentarz jest podążany za inną instrukcją w tym samym wierszu lub w wierszu.</span><span class="sxs-lookup"><span data-stu-id="444c8-114">This is true whether your comment follows another statement on the same line or sits alone on a line.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="444c8-115">Nie można kontynuować instrukcji `REM` przy użyciu sekwencji kontynuacji wiersza (`_`).</span><span class="sxs-lookup"><span data-stu-id="444c8-115">You cannot continue a `REM` statement by using a line-continuation sequence (`_`).</span></span> <span data-ttu-id="444c8-116">Po rozpoczęciu komentarza kompilator nie bada znaków pod kątem specjalnego znaczenia.</span><span class="sxs-lookup"><span data-stu-id="444c8-116">Once a comment begins, the compiler does not examine the characters for special meaning.</span></span> <span data-ttu-id="444c8-117">W przypadku komentarza z wieloma wierszami Użyj innej instrukcji `REM` lub symbolu komentarza (`'`) w każdym wierszu.</span><span class="sxs-lookup"><span data-stu-id="444c8-117">For a multiple-line comment, use another `REM` statement or a comment symbol (`'`) on each line.</span></span>  
  
## <a name="example"></a><span data-ttu-id="444c8-118">Przykład</span><span class="sxs-lookup"><span data-stu-id="444c8-118">Example</span></span>  
 <span data-ttu-id="444c8-119">Poniższy przykład ilustruje instrukcję `REM`, która jest używana do dołączania uwag objaśniających do programu.</span><span class="sxs-lookup"><span data-stu-id="444c8-119">The following example illustrates the `REM` statement, which is used to include explanatory remarks in a program.</span></span> <span data-ttu-id="444c8-120">Pokazuje również alternatywę użycia znaku pojedynczego cudzysłowu (`'`), a nie `REM`.</span><span class="sxs-lookup"><span data-stu-id="444c8-120">It also shows the alternative of using the single quotation-mark character (`'`) instead of `REM`.</span></span>  
  
 [!code-vb[VbVbalrStatements#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#6)]  
  
## <a name="see-also"></a><span data-ttu-id="444c8-121">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="444c8-121">See also</span></span>

- [<span data-ttu-id="444c8-122">Komentarze w kodzie</span><span class="sxs-lookup"><span data-stu-id="444c8-122">Comments in Code</span></span>](../../../visual-basic/programming-guide/program-structure/comments-in-code.md)
- [<span data-ttu-id="444c8-123">Instrukcje: przerywanie i łączenie instrukcji w kodzie</span><span class="sxs-lookup"><span data-stu-id="444c8-123">How to: Break and Combine Statements in Code</span></span>](../../../visual-basic/programming-guide/program-structure/how-to-break-and-combine-statements-in-code.md)
