---
title: Call — Instrukcja (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Call
helpviewer_keywords:
- procedures [Visual Basic], Call statement
- Call statement [Visual Basic]
- procedures [Visual Basic], calling
ms.assetid: e5b31571-6867-406f-b8e7-a3f9aae4723a
ms.openlocfilehash: 2074f44aedf59f1570e73c898a9bf64e57034923
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33603395"
---
# <a name="call-statement-visual-basic"></a><span data-ttu-id="5806b-102">Call — Instrukcja (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5806b-102">Call Statement (Visual Basic)</span></span>
<span data-ttu-id="5806b-103">Przekazuje sterowanie do `Function`, `Sub`, lub procedury biblioteki dołączanej (dynamicznie DLL).</span><span class="sxs-lookup"><span data-stu-id="5806b-103">Transfers control to a `Function`, `Sub`, or dynamic-link library (DLL) procedure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5806b-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="5806b-104">Syntax</span></span>  
  
```  
[ Call ] procedureName [ (argumentList) ]  
```  
  
## <a name="parts"></a><span data-ttu-id="5806b-105">Części</span><span class="sxs-lookup"><span data-stu-id="5806b-105">Parts</span></span>  
 `procedureName`  
 <span data-ttu-id="5806b-106">Wymagana.</span><span class="sxs-lookup"><span data-stu-id="5806b-106">Required.</span></span> <span data-ttu-id="5806b-107">Nazwa wywoływanej procedury.</span><span class="sxs-lookup"><span data-stu-id="5806b-107">Name of the procedure to call.</span></span>  
  
 `argumentList`  
 <span data-ttu-id="5806b-108">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="5806b-108">Optional.</span></span> <span data-ttu-id="5806b-109">Lista zmiennych lub wyrażeń reprezentujących argumenty, które są przekazywane do procedury, gdy jest wywoływana.</span><span class="sxs-lookup"><span data-stu-id="5806b-109">List of variables or expressions representing arguments that are passed to the procedure when it is called.</span></span> <span data-ttu-id="5806b-110">Używanie wielu argumentów są oddzielone przecinkami.</span><span class="sxs-lookup"><span data-stu-id="5806b-110">Multiple arguments are separated by commas.</span></span> <span data-ttu-id="5806b-111">Jeśli dołączysz `argumentList`, musisz ją ująć go w nawiasach.</span><span class="sxs-lookup"><span data-stu-id="5806b-111">If you include `argumentList`, you must enclose it in parentheses.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5806b-112">Uwagi</span><span class="sxs-lookup"><span data-stu-id="5806b-112">Remarks</span></span>  
 <span data-ttu-id="5806b-113">Można użyć `Call` — słowo kluczowe po wywołaniu procedury.</span><span class="sxs-lookup"><span data-stu-id="5806b-113">You can use the `Call` keyword when you call a procedure.</span></span> <span data-ttu-id="5806b-114">Dla większości wywołań procedur nie są wymagane do używania słowa kluczowego.</span><span class="sxs-lookup"><span data-stu-id="5806b-114">For most procedure calls, you aren’t required to use this  keyword.</span></span>  
  
 <span data-ttu-id="5806b-115">Zazwyczaj używają `Call` — słowo kluczowe po nazwie wyrażenia nie zaczyna się od identyfikatora.</span><span class="sxs-lookup"><span data-stu-id="5806b-115">You typically use the `Call` keyword when the called expression doesn’t start with an identifier.</span></span> <span data-ttu-id="5806b-116">Użycie `Call` — słowo kluczowe do innych celów nie jest zalecane.</span><span class="sxs-lookup"><span data-stu-id="5806b-116">Use of the `Call` keyword for other uses isn’t recommended.</span></span>  
  
 <span data-ttu-id="5806b-117">Jeśli procedura zwróci wartość, `Call` instrukcji odrzuca je.</span><span class="sxs-lookup"><span data-stu-id="5806b-117">If the procedure returns a value, the `Call` statement discards it.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5806b-118">Przykład</span><span class="sxs-lookup"><span data-stu-id="5806b-118">Example</span></span>  
 <span data-ttu-id="5806b-119">Poniższy kod przedstawia dwa przykłady gdzie `Call` — słowo kluczowe jest niezbędne wywołać procedurę.</span><span class="sxs-lookup"><span data-stu-id="5806b-119">The following code shows two examples where the `Call` keyword is necessary to call a procedure.</span></span> <span data-ttu-id="5806b-120">W obu przykładach wyrażenie wywoływanego nie zaczyna się od identyfikatora.</span><span class="sxs-lookup"><span data-stu-id="5806b-120">In both examples, the called expression doesn't start with an identifier.</span></span>  
  
 [!code-vb[VbVbalrStatements#97](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/call-statement_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="5806b-121">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="5806b-121">See Also</span></span>  
 [<span data-ttu-id="5806b-122">Function, instrukcja</span><span class="sxs-lookup"><span data-stu-id="5806b-122">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)  
 [<span data-ttu-id="5806b-123">Sub, instrukcja</span><span class="sxs-lookup"><span data-stu-id="5806b-123">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)  
 [<span data-ttu-id="5806b-124">Declare, instrukcja</span><span class="sxs-lookup"><span data-stu-id="5806b-124">Declare Statement</span></span>](../../../visual-basic/language-reference/statements/declare-statement.md)  
 [<span data-ttu-id="5806b-125">Wyrażenia lambda</span><span class="sxs-lookup"><span data-stu-id="5806b-125">Lambda Expressions</span></span>](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)
