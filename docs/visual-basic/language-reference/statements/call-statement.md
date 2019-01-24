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
ms.openlocfilehash: e706650ac6da84d9b4e77fc549811e731be61b92
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54594164"
---
# <a name="call-statement-visual-basic"></a><span data-ttu-id="9a2c5-102">Call — Instrukcja (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9a2c5-102">Call Statement (Visual Basic)</span></span>
<span data-ttu-id="9a2c5-103">Przekazuje sterowanie do `Function`, `Sub`, lub procedury biblioteki dołączanej dynamicznie (DLL).</span><span class="sxs-lookup"><span data-stu-id="9a2c5-103">Transfers control to a `Function`, `Sub`, or dynamic-link library (DLL) procedure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9a2c5-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="9a2c5-104">Syntax</span></span>  
  
```  
[ Call ] procedureName [ (argumentList) ]  
```  
  
## <a name="parts"></a><span data-ttu-id="9a2c5-105">Części</span><span class="sxs-lookup"><span data-stu-id="9a2c5-105">Parts</span></span>  
|||
|---|---|
|`procedureName`|<span data-ttu-id="9a2c5-106">Wymagana.</span><span class="sxs-lookup"><span data-stu-id="9a2c5-106">Required.</span></span> <span data-ttu-id="9a2c5-107">Nazwa procedury do wywołania.</span><span class="sxs-lookup"><span data-stu-id="9a2c5-107">Name of the procedure to call.</span></span>|
|`argumentList`|<span data-ttu-id="9a2c5-108">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="9a2c5-108">Optional.</span></span> <span data-ttu-id="9a2c5-109">Lista zmiennych lub wyrażeń reprezentujących argumenty, które są przekazywane do procedury, gdy jest wywoływana.</span><span class="sxs-lookup"><span data-stu-id="9a2c5-109">List of variables or expressions representing arguments that are passed to the procedure when it is called.</span></span> <span data-ttu-id="9a2c5-110">Wiele argumentów są oddzielone przecinkami.</span><span class="sxs-lookup"><span data-stu-id="9a2c5-110">Multiple arguments are separated by commas.</span></span> <span data-ttu-id="9a2c5-111">Jeśli dołączysz `argumentList`, należy ująć je w nawiasach.</span><span class="sxs-lookup"><span data-stu-id="9a2c5-111">If you include `argumentList`, you must enclose it in parentheses.</span></span>|
|||
  
## <a name="remarks"></a><span data-ttu-id="9a2c5-112">Uwagi</span><span class="sxs-lookup"><span data-stu-id="9a2c5-112">Remarks</span></span>  
 <span data-ttu-id="9a2c5-113">Słowa kluczowego `Call` można użyć podczas wywoływania procedury.</span><span class="sxs-lookup"><span data-stu-id="9a2c5-113">You can use the `Call` keyword when you call a procedure.</span></span> <span data-ttu-id="9a2c5-114">W większości wywołań procedur użycie tego słowa kluczowego nie jest konieczne.</span><span class="sxs-lookup"><span data-stu-id="9a2c5-114">For most procedure calls, you aren’t required to use this  keyword.</span></span>  
  
 <span data-ttu-id="9a2c5-115">Słowa kluczowego `Call` zazwyczaj używa się, gdy wyrażenie nie zaczyna się od identyfikatora.</span><span class="sxs-lookup"><span data-stu-id="9a2c5-115">You typically use the `Call` keyword when the called expression doesn’t start with an identifier.</span></span> <span data-ttu-id="9a2c5-116">Użycie słowa `Call` w innym celu nie jest zalecane.</span><span class="sxs-lookup"><span data-stu-id="9a2c5-116">Use of the `Call` keyword for other uses isn’t recommended.</span></span>  
  
 <span data-ttu-id="9a2c5-117">Jeśli procedura zwróci wartość, instrukcja `Call` ją odrzuci.</span><span class="sxs-lookup"><span data-stu-id="9a2c5-117">If the procedure returns a value, the `Call` statement discards it.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9a2c5-118">Przykład</span><span class="sxs-lookup"><span data-stu-id="9a2c5-118">Example</span></span>  
 <span data-ttu-id="9a2c5-119">W przykładowym kodzie poniżej przedstawiono dwie sytuacje, w których słowo kluczowe `Call` jest niezbędne do wywołania procedury.</span><span class="sxs-lookup"><span data-stu-id="9a2c5-119">The following code shows two examples where the `Call` keyword is necessary to call a procedure.</span></span> <span data-ttu-id="9a2c5-120">W obu przykładach wywoływane wyrażenie nie zaczyna się od identyfikatora.</span><span class="sxs-lookup"><span data-stu-id="9a2c5-120">In both examples, the called expression doesn't start with an identifier.</span></span>  
  
 [!code-vb[VbVbalrStatements#97](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/call-statement_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="9a2c5-121">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="9a2c5-121">See also</span></span>
- [<span data-ttu-id="9a2c5-122">Function, instrukcja</span><span class="sxs-lookup"><span data-stu-id="9a2c5-122">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)
- [<span data-ttu-id="9a2c5-123">Sub, instrukcja</span><span class="sxs-lookup"><span data-stu-id="9a2c5-123">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)
- [<span data-ttu-id="9a2c5-124">Declare, instrukcja</span><span class="sxs-lookup"><span data-stu-id="9a2c5-124">Declare Statement</span></span>](../../../visual-basic/language-reference/statements/declare-statement.md)
- [<span data-ttu-id="9a2c5-125">Wyrażenia lambda</span><span class="sxs-lookup"><span data-stu-id="9a2c5-125">Lambda Expressions</span></span>](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)
