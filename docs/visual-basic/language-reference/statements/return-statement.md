---
title: Return — Instrukcja (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Return
helpviewer_keywords:
- Return statement [Visual Basic], syntax
- control flow [Visual Basic], returning control to expressions
- Return statement [Visual Basic]
- expressions [Visual Basic], returning control to
ms.assetid: ac86e7f0-5a67-42c3-9834-0e0381efa3ec
ms.openlocfilehash: fb75409a2c26ca966469624de781015db621a825
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54588401"
---
# <a name="return-statement-visual-basic"></a><span data-ttu-id="69a78-102">Return — Instrukcja (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="69a78-102">Return Statement (Visual Basic)</span></span>
<span data-ttu-id="69a78-103">Zwraca kontrolę do kodu, który wywołał `Function`, `Sub`, `Get`, `Set`, lub `Operator` procedury.</span><span class="sxs-lookup"><span data-stu-id="69a78-103">Returns control to the code that called a `Function`, `Sub`, `Get`, `Set`, or `Operator` procedure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="69a78-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="69a78-104">Syntax</span></span>  
  
```  
Return  
-or-  
Return expression  
```  
  
## <a name="part"></a><span data-ttu-id="69a78-105">Część</span><span class="sxs-lookup"><span data-stu-id="69a78-105">Part</span></span>  
 `expression`  
 <span data-ttu-id="69a78-106">Wymagane w `Function`, `Get`, lub `Operator` procedury.</span><span class="sxs-lookup"><span data-stu-id="69a78-106">Required in a `Function`, `Get`, or `Operator` procedure.</span></span> <span data-ttu-id="69a78-107">Wyrażenie, która reprezentuje wartość zwracaną do wywołującego kodu.</span><span class="sxs-lookup"><span data-stu-id="69a78-107">Expression that represents the value to be returned to the calling code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="69a78-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="69a78-108">Remarks</span></span>  
 <span data-ttu-id="69a78-109">W `Sub` lub `Set` procedury `Return` instrukcja jest odpowiednikiem `Exit Sub` lub `Exit Property` instrukcji i `expression` nie musi zostać dostarczony.</span><span class="sxs-lookup"><span data-stu-id="69a78-109">In a `Sub` or `Set` procedure, the `Return` statement is equivalent to an `Exit Sub` or `Exit Property` statement, and `expression` must not be supplied.</span></span>  
  
 <span data-ttu-id="69a78-110">W `Function`, `Get`, lub `Operator` procedury `Return` instrukcja musi zawierać `expression`, i `expression` musi być typu danych, który jest konwertowany na typ zwracany procedury.</span><span class="sxs-lookup"><span data-stu-id="69a78-110">In a `Function`, `Get`, or `Operator` procedure, the `Return` statement must include `expression`, and `expression` must evaluate to a data type that is convertible to the return type of the procedure.</span></span> <span data-ttu-id="69a78-111">W `Function` lub `Get` procedury, masz także alternatywne przypisanie wyrażenia do nazwy procedury, która będzie służyć jako wartość zwracaną, a następnie wykonywanie `Exit Function` lub `Exit Property` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="69a78-111">In a `Function` or `Get` procedure, you also have the alternative of assigning an expression to the procedure name to serve as the return value, and then executing an `Exit Function` or `Exit Property` statement.</span></span> <span data-ttu-id="69a78-112">W `Operator` procedury, należy użyć `Return expression`.</span><span class="sxs-lookup"><span data-stu-id="69a78-112">In an `Operator` procedure, you must use `Return expression`.</span></span>  
  
 <span data-ttu-id="69a78-113">Może zawierać tyle `Return` instrukcji zgodnie z potrzebami w tej samej procedury.</span><span class="sxs-lookup"><span data-stu-id="69a78-113">You can include as many `Return` statements as appropriate in the same procedure.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="69a78-114">Kod w `Finally` bloku, który jest uruchamiany po `Return` instrukcji w `Try` lub `Catch` blok jest napotkano, ale wcześniej `Return` wykonywania instrukcji.</span><span class="sxs-lookup"><span data-stu-id="69a78-114">The code in a `Finally` block runs after a `Return` statement in a `Try` or `Catch` block is encountered, but before that `Return` statement executes.</span></span> <span data-ttu-id="69a78-115">A `Return` instrukcji nie można uwzględnić w `Finally` bloku.</span><span class="sxs-lookup"><span data-stu-id="69a78-115">A `Return` statement cannot be included in a `Finally` block.</span></span>  
  
## <a name="example"></a><span data-ttu-id="69a78-116">Przykład</span><span class="sxs-lookup"><span data-stu-id="69a78-116">Example</span></span>  
 <span data-ttu-id="69a78-117">W poniższym przykładzie użyto `Return` instrukcji kilka razy, aby powrócić do kodu wywołującego, gdy procedura nie trzeba nic robić.</span><span class="sxs-lookup"><span data-stu-id="69a78-117">The following example uses the `Return` statement several times to return to the calling code when the procedure does not have to do anything else.</span></span>  
  
 [!code-vb[VbVbalrStatements#53](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/return-statement_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="69a78-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="69a78-118">See also</span></span>
- [<span data-ttu-id="69a78-119">Function, instrukcja</span><span class="sxs-lookup"><span data-stu-id="69a78-119">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)
- [<span data-ttu-id="69a78-120">Sub, instrukcja</span><span class="sxs-lookup"><span data-stu-id="69a78-120">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)
- [<span data-ttu-id="69a78-121">Get, instrukcja</span><span class="sxs-lookup"><span data-stu-id="69a78-121">Get Statement</span></span>](../../../visual-basic/language-reference/statements/get-statement.md)
- [<span data-ttu-id="69a78-122">Set, instrukcja</span><span class="sxs-lookup"><span data-stu-id="69a78-122">Set Statement</span></span>](../../../visual-basic/language-reference/statements/set-statement.md)
- [<span data-ttu-id="69a78-123">Operator, instrukcja</span><span class="sxs-lookup"><span data-stu-id="69a78-123">Operator Statement</span></span>](../../../visual-basic/language-reference/statements/operator-statement.md)
- [<span data-ttu-id="69a78-124">Instrukcja Property</span><span class="sxs-lookup"><span data-stu-id="69a78-124">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)
- [<span data-ttu-id="69a78-125">Exit, instrukcja</span><span class="sxs-lookup"><span data-stu-id="69a78-125">Exit Statement</span></span>](../../../visual-basic/language-reference/statements/exit-statement.md)
- [<span data-ttu-id="69a78-126">Try...Catch...Finally, instrukcja</span><span class="sxs-lookup"><span data-stu-id="69a78-126">Try...Catch...Finally Statement</span></span>](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)
