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
ms.openlocfilehash: fe200add4e29fe4bbe0fdf335dcd94107b8ff1eb
ms.sourcegitcommit: dfb2a100cfb4d3902c042f17b3204f49bc7635e7
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/21/2018
ms.locfileid: "46517214"
---
# <a name="return-statement-visual-basic"></a><span data-ttu-id="b6ef5-102">Return — Instrukcja (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b6ef5-102">Return Statement (Visual Basic)</span></span>
<span data-ttu-id="b6ef5-103">Zwraca kontrolę do kodu, który wywołał `Function`, `Sub`, `Get`, `Set`, lub `Operator` procedury.</span><span class="sxs-lookup"><span data-stu-id="b6ef5-103">Returns control to the code that called a `Function`, `Sub`, `Get`, `Set`, or `Operator` procedure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b6ef5-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="b6ef5-104">Syntax</span></span>  
  
```  
Return  
-or-  
Return expression  
```  
  
## <a name="part"></a><span data-ttu-id="b6ef5-105">Część</span><span class="sxs-lookup"><span data-stu-id="b6ef5-105">Part</span></span>  
 `expression`  
 <span data-ttu-id="b6ef5-106">Wymagane w `Function`, `Get`, lub `Operator` procedury.</span><span class="sxs-lookup"><span data-stu-id="b6ef5-106">Required in a `Function`, `Get`, or `Operator` procedure.</span></span> <span data-ttu-id="b6ef5-107">Wyrażenie, która reprezentuje wartość zwracaną do wywołującego kodu.</span><span class="sxs-lookup"><span data-stu-id="b6ef5-107">Expression that represents the value to be returned to the calling code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b6ef5-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="b6ef5-108">Remarks</span></span>  
 <span data-ttu-id="b6ef5-109">W `Sub` lub `Set` procedury `Return` instrukcja jest odpowiednikiem `Exit Sub` lub `Exit Property` instrukcji i `expression` nie musi zostać dostarczony.</span><span class="sxs-lookup"><span data-stu-id="b6ef5-109">In a `Sub` or `Set` procedure, the `Return` statement is equivalent to an `Exit Sub` or `Exit Property` statement, and `expression` must not be supplied.</span></span>  
  
 <span data-ttu-id="b6ef5-110">W `Function`, `Get`, lub `Operator` procedury `Return` instrukcja musi zawierać `expression`, i `expression` musi być typu danych, który jest konwertowany na typ zwracany procedury.</span><span class="sxs-lookup"><span data-stu-id="b6ef5-110">In a `Function`, `Get`, or `Operator` procedure, the `Return` statement must include `expression`, and `expression` must evaluate to a data type that is convertible to the return type of the procedure.</span></span> <span data-ttu-id="b6ef5-111">W `Function` lub `Get` procedury, masz także alternatywne przypisanie wyrażenia do nazwy procedury, która będzie służyć jako wartość zwracaną, a następnie wykonywanie `Exit Function` lub `Exit Property` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="b6ef5-111">In a `Function` or `Get` procedure, you also have the alternative of assigning an expression to the procedure name to serve as the return value, and then executing an `Exit Function` or `Exit Property` statement.</span></span> <span data-ttu-id="b6ef5-112">W `Operator` procedury, należy użyć `Return expression`.</span><span class="sxs-lookup"><span data-stu-id="b6ef5-112">In an `Operator` procedure, you must use `Return expression`.</span></span>  
  
 <span data-ttu-id="b6ef5-113">Może zawierać tyle `Return` instrukcji zgodnie z potrzebami w tej samej procedury.</span><span class="sxs-lookup"><span data-stu-id="b6ef5-113">You can include as many `Return` statements as appropriate in the same procedure.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b6ef5-114">Kod w `Finally` bloku, który jest uruchamiany po `Return` instrukcji w `Try` lub `Catch` blok jest napotkano, ale wcześniej `Return` wykonywania instrukcji.</span><span class="sxs-lookup"><span data-stu-id="b6ef5-114">The code in a `Finally` block runs after a `Return` statement in a `Try` or `Catch` block is encountered, but before that `Return` statement executes.</span></span> <span data-ttu-id="b6ef5-115">A `Return` instrukcji nie można uwzględnić w `Finally` bloku.</span><span class="sxs-lookup"><span data-stu-id="b6ef5-115">A `Return` statement cannot be included in a `Finally` block.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b6ef5-116">Przykład</span><span class="sxs-lookup"><span data-stu-id="b6ef5-116">Example</span></span>  
 <span data-ttu-id="b6ef5-117">W poniższym przykładzie użyto `Return` instrukcji kilka razy, aby powrócić do kodu wywołującego, gdy procedura nie trzeba nic robić.</span><span class="sxs-lookup"><span data-stu-id="b6ef5-117">The following example uses the `Return` statement several times to return to the calling code when the procedure does not have to do anything else.</span></span>  
  
 [!code-vb[VbVbalrStatements#53](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/return-statement_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="b6ef5-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b6ef5-118">See Also</span></span>  
 [<span data-ttu-id="b6ef5-119">Function, instrukcja</span><span class="sxs-lookup"><span data-stu-id="b6ef5-119">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)  
 [<span data-ttu-id="b6ef5-120">Sub, instrukcja</span><span class="sxs-lookup"><span data-stu-id="b6ef5-120">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)  
 [<span data-ttu-id="b6ef5-121">Get, instrukcja</span><span class="sxs-lookup"><span data-stu-id="b6ef5-121">Get Statement</span></span>](../../../visual-basic/language-reference/statements/get-statement.md)  
 [<span data-ttu-id="b6ef5-122">Set, instrukcja</span><span class="sxs-lookup"><span data-stu-id="b6ef5-122">Set Statement</span></span>](../../../visual-basic/language-reference/statements/set-statement.md)  
 [<span data-ttu-id="b6ef5-123">Operator, instrukcja</span><span class="sxs-lookup"><span data-stu-id="b6ef5-123">Operator Statement</span></span>](../../../visual-basic/language-reference/statements/operator-statement.md)  
 [<span data-ttu-id="b6ef5-124">Instrukcja Property</span><span class="sxs-lookup"><span data-stu-id="b6ef5-124">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)  
 [<span data-ttu-id="b6ef5-125">Exit, instrukcja</span><span class="sxs-lookup"><span data-stu-id="b6ef5-125">Exit Statement</span></span>](../../../visual-basic/language-reference/statements/exit-statement.md)  
 [<span data-ttu-id="b6ef5-126">Try...Catch...Finally, instrukcja</span><span class="sxs-lookup"><span data-stu-id="b6ef5-126">Try...Catch...Finally Statement</span></span>](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)
