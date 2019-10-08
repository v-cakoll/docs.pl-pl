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
ms.openlocfilehash: a04ebddc7db176188876da1082e1e6946e1e8eec
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/07/2019
ms.locfileid: "72005170"
---
# <a name="call-statement-visual-basic"></a><span data-ttu-id="9147b-102">Call — Instrukcja (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9147b-102">Call Statement (Visual Basic)</span></span>

<span data-ttu-id="9147b-103">Przenosi kontrolę do procedury `Function`, `Sub` lub biblioteki dołączanej dynamicznie (DLL).</span><span class="sxs-lookup"><span data-stu-id="9147b-103">Transfers control to a `Function`, `Sub`, or dynamic-link library (DLL) procedure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9147b-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="9147b-104">Syntax</span></span>  
  
```vb  
[ Call ] procedureName [ (argumentList) ]  
```  
  
## <a name="parts"></a><span data-ttu-id="9147b-105">Części</span><span class="sxs-lookup"><span data-stu-id="9147b-105">Parts</span></span>  

|||
|---|---|
|`procedureName`|<span data-ttu-id="9147b-106">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="9147b-106">Required.</span></span> <span data-ttu-id="9147b-107">Nazwa procedury do wywołania.</span><span class="sxs-lookup"><span data-stu-id="9147b-107">Name of the procedure to call.</span></span>|
|`argumentList`|<span data-ttu-id="9147b-108">Opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="9147b-108">Optional.</span></span> <span data-ttu-id="9147b-109">Lista zmiennych lub wyrażeń reprezentujących argumenty, które są przekazane do procedury po wywołaniu.</span><span class="sxs-lookup"><span data-stu-id="9147b-109">List of variables or expressions representing arguments that are passed to the procedure when it is called.</span></span> <span data-ttu-id="9147b-110">Wiele argumentów jest oddzielonych przecinkami.</span><span class="sxs-lookup"><span data-stu-id="9147b-110">Multiple arguments are separated by commas.</span></span> <span data-ttu-id="9147b-111">Jeśli dołączysz `argumentList`, należy ująć ją w nawiasy.</span><span class="sxs-lookup"><span data-stu-id="9147b-111">If you include `argumentList`, you must enclose it in parentheses.</span></span>|
|||
  
## <a name="remarks"></a><span data-ttu-id="9147b-112">Uwagi</span><span class="sxs-lookup"><span data-stu-id="9147b-112">Remarks</span></span>

 <span data-ttu-id="9147b-113">Po wywołaniu procedury można użyć słowa kluczowego `Call`.</span><span class="sxs-lookup"><span data-stu-id="9147b-113">You can use the `Call` keyword when you call a procedure.</span></span> <span data-ttu-id="9147b-114">W przypadku większości wywołań procedur nie jest wymagane użycie tego słowa kluczowego.</span><span class="sxs-lookup"><span data-stu-id="9147b-114">For most procedure calls, you aren’t required to use this  keyword.</span></span>

 <span data-ttu-id="9147b-115">Użycie słowa kluczowego `Call` jest zazwyczaj możliwe, gdy wywołane wyrażenie nie zaczyna się od identyfikatora.</span><span class="sxs-lookup"><span data-stu-id="9147b-115">You typically use the `Call` keyword when the called expression doesn’t start with an identifier.</span></span> <span data-ttu-id="9147b-116">Użycie słowa kluczowego `Call` do innych celów nie jest zalecane.</span><span class="sxs-lookup"><span data-stu-id="9147b-116">Use of the `Call` keyword for other uses isn't recommended.</span></span>

 <span data-ttu-id="9147b-117">Jeśli procedura zwróci wartość, instrukcja `Call` odrzuca ją.</span><span class="sxs-lookup"><span data-stu-id="9147b-117">If the procedure returns a value, the `Call` statement discards it.</span></span>

## <a name="example"></a><span data-ttu-id="9147b-118">Przykład</span><span class="sxs-lookup"><span data-stu-id="9147b-118">Example</span></span>

 <span data-ttu-id="9147b-119">Poniższy kod przedstawia dwa przykłady, w których słowo kluczowe `Call` jest niezbędne do wywołania procedury.</span><span class="sxs-lookup"><span data-stu-id="9147b-119">The following code shows two examples where the `Call` keyword is necessary to call a procedure.</span></span> <span data-ttu-id="9147b-120">W obu przykładach wywołane wyrażenie nie zaczyna się od identyfikatora.</span><span class="sxs-lookup"><span data-stu-id="9147b-120">In both examples, the called expression doesn't start with an identifier.</span></span>

 [!code-vb[VbVbalrStatements#97](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#97)]  
  
## <a name="see-also"></a><span data-ttu-id="9147b-121">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="9147b-121">See also</span></span>

- [<span data-ttu-id="9147b-122">Function, instrukcja</span><span class="sxs-lookup"><span data-stu-id="9147b-122">Function Statement</span></span>](function-statement.md)
- [<span data-ttu-id="9147b-123">Sub, instrukcja</span><span class="sxs-lookup"><span data-stu-id="9147b-123">Sub Statement</span></span>](sub-statement.md)
- [<span data-ttu-id="9147b-124">Declare, instrukcja</span><span class="sxs-lookup"><span data-stu-id="9147b-124">Declare Statement</span></span>](declare-statement.md)
- [<span data-ttu-id="9147b-125">Wyrażenia lambda</span><span class="sxs-lookup"><span data-stu-id="9147b-125">Lambda Expressions</span></span>](../../programming-guide/language-features/procedures/lambda-expressions.md)
