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
ms.openlocfilehash: af49ea95d7f9d01072190ac3ccf6ba2f1041347e
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69957674"
---
# <a name="return-statement-visual-basic"></a><span data-ttu-id="b3853-102">Return — Instrukcja (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b3853-102">Return Statement (Visual Basic)</span></span>
<span data-ttu-id="b3853-103">Zwraca kontrolę do kodu, który wywołał `Function`procedurę `Sub`, `Get`, `Set`, lub `Operator` .</span><span class="sxs-lookup"><span data-stu-id="b3853-103">Returns control to the code that called a `Function`, `Sub`, `Get`, `Set`, or `Operator` procedure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b3853-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="b3853-104">Syntax</span></span>  
  
```  
Return  
-or-  
Return expression  
```  
  
## <a name="part"></a><span data-ttu-id="b3853-105">Części</span><span class="sxs-lookup"><span data-stu-id="b3853-105">Part</span></span>  
 `expression`  
 <span data-ttu-id="b3853-106">Wymagane w `Function`procedurze, `Get`lub. `Operator`</span><span class="sxs-lookup"><span data-stu-id="b3853-106">Required in a `Function`, `Get`, or `Operator` procedure.</span></span> <span data-ttu-id="b3853-107">Wyrażenie, które reprezentuje wartość, która ma zostać zwrócona do kodu wywołującego.</span><span class="sxs-lookup"><span data-stu-id="b3853-107">Expression that represents the value to be returned to the calling code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b3853-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="b3853-108">Remarks</span></span>  
 <span data-ttu-id="b3853-109">`Set` `Exit Property` `Exit Sub` `expression` W procedurze `Sub` lubinstrukcjajestrównoznacznazinstrukcją`Return` or i nie może być dostarczone.</span><span class="sxs-lookup"><span data-stu-id="b3853-109">In a `Sub` or `Set` procedure, the `Return` statement is equivalent to an `Exit Sub` or `Exit Property` statement, and `expression` must not be supplied.</span></span>  
  
 <span data-ttu-id="b3853-110">`Get` `Operator` `expression`W procedurze `expression` ,, lub, instrukcja musi zawierać, i musi oszacować do typu danych, który jest konwertowany na zwracany typ procedury. `Return` `Function`</span><span class="sxs-lookup"><span data-stu-id="b3853-110">In a `Function`, `Get`, or `Operator` procedure, the `Return` statement must include `expression`, and `expression` must evaluate to a data type that is convertible to the return type of the procedure.</span></span> <span data-ttu-id="b3853-111">W procedurze `Get` `Exit Function` lub można także przypisać wyrażenie do nazwy procedury, która ma stanowić wartość zwracaną, a następnie wykonuje instrukcję or `Exit Property`. `Function`</span><span class="sxs-lookup"><span data-stu-id="b3853-111">In a `Function` or `Get` procedure, you also have the alternative of assigning an expression to the procedure name to serve as the return value, and then executing an `Exit Function` or `Exit Property` statement.</span></span> <span data-ttu-id="b3853-112">W procedurze należy użyć `Return expression`. `Operator`</span><span class="sxs-lookup"><span data-stu-id="b3853-112">In an `Operator` procedure, you must use `Return expression`.</span></span>  
  
 <span data-ttu-id="b3853-113">W tej samej procedurze można `Return` dołączyć dowolną liczbę instrukcji.</span><span class="sxs-lookup"><span data-stu-id="b3853-113">You can include as many `Return` statements as appropriate in the same procedure.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b3853-114">Kod `Finally` w bloku jest uruchamiany `Try` `Return` po napotkaniu instrukcji w bloku lub `Catch` , ale przed wykonaniem tej `Return` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="b3853-114">The code in a `Finally` block runs after a `Return` statement in a `Try` or `Catch` block is encountered, but before that `Return` statement executes.</span></span> <span data-ttu-id="b3853-115">Instrukcja nie może być uwzględniona `Finally` w bloku. `Return`</span><span class="sxs-lookup"><span data-stu-id="b3853-115">A `Return` statement cannot be included in a `Finally` block.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b3853-116">Przykład</span><span class="sxs-lookup"><span data-stu-id="b3853-116">Example</span></span>  
 <span data-ttu-id="b3853-117">Poniższy przykład używa `Return` instrukcji kilka razy, aby powrócić do kodu wywołującego, gdy procedura nie musi wykonywać żadnych innych czynności.</span><span class="sxs-lookup"><span data-stu-id="b3853-117">The following example uses the `Return` statement several times to return to the calling code when the procedure does not have to do anything else.</span></span>  
  
 [!code-vb[VbVbalrStatements#53](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#53)]  
  
## <a name="see-also"></a><span data-ttu-id="b3853-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b3853-118">See also</span></span>

- [<span data-ttu-id="b3853-119">Function, instrukcja</span><span class="sxs-lookup"><span data-stu-id="b3853-119">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)
- [<span data-ttu-id="b3853-120">Sub, instrukcja</span><span class="sxs-lookup"><span data-stu-id="b3853-120">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)
- [<span data-ttu-id="b3853-121">Get, instrukcja</span><span class="sxs-lookup"><span data-stu-id="b3853-121">Get Statement</span></span>](../../../visual-basic/language-reference/statements/get-statement.md)
- [<span data-ttu-id="b3853-122">Set, instrukcja</span><span class="sxs-lookup"><span data-stu-id="b3853-122">Set Statement</span></span>](../../../visual-basic/language-reference/statements/set-statement.md)
- [<span data-ttu-id="b3853-123">Operator, instrukcja</span><span class="sxs-lookup"><span data-stu-id="b3853-123">Operator Statement</span></span>](../../../visual-basic/language-reference/statements/operator-statement.md)
- [<span data-ttu-id="b3853-124">Instrukcja Property</span><span class="sxs-lookup"><span data-stu-id="b3853-124">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)
- [<span data-ttu-id="b3853-125">Exit, instrukcja</span><span class="sxs-lookup"><span data-stu-id="b3853-125">Exit Statement</span></span>](../../../visual-basic/language-reference/statements/exit-statement.md)
- [<span data-ttu-id="b3853-126">Try...Catch...Finally, instrukcja</span><span class="sxs-lookup"><span data-stu-id="b3853-126">Try...Catch...Finally Statement</span></span>](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)
