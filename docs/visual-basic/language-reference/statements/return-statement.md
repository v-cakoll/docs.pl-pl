---
title: Return, instrukcja
ms.date: 07/20/2015
f1_keywords:
- vb.Return
helpviewer_keywords:
- Return statement [Visual Basic], syntax
- control flow [Visual Basic], returning control to expressions
- Return statement [Visual Basic]
- expressions [Visual Basic], returning control to
ms.assetid: ac86e7f0-5a67-42c3-9834-0e0381efa3ec
ms.openlocfilehash: cdb58e32c30c8e6c1662fb698ac5576c3f71258c
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84404203"
---
# <a name="return-statement-visual-basic"></a><span data-ttu-id="3146c-102">Return — Instrukcja (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3146c-102">Return Statement (Visual Basic)</span></span>
<span data-ttu-id="3146c-103">Zwraca kontrolę do kodu, który wywołał `Function` `Sub` procedurę,,, `Get` `Set` lub `Operator` .</span><span class="sxs-lookup"><span data-stu-id="3146c-103">Returns control to the code that called a `Function`, `Sub`, `Get`, `Set`, or `Operator` procedure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3146c-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="3146c-104">Syntax</span></span>  
  
```vb  
Return  
' -or-  
Return expression  
```  
  
## <a name="part"></a><span data-ttu-id="3146c-105">Część</span><span class="sxs-lookup"><span data-stu-id="3146c-105">Part</span></span>  
 `expression`  
 <span data-ttu-id="3146c-106">Wymagane w `Function` procedurze, `Get` lub `Operator` .</span><span class="sxs-lookup"><span data-stu-id="3146c-106">Required in a `Function`, `Get`, or `Operator` procedure.</span></span> <span data-ttu-id="3146c-107">Wyrażenie, które reprezentuje wartość, która ma zostać zwrócona do kodu wywołującego.</span><span class="sxs-lookup"><span data-stu-id="3146c-107">Expression that represents the value to be returned to the calling code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3146c-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="3146c-108">Remarks</span></span>  
 <span data-ttu-id="3146c-109">W `Sub` procedurze lub `Set` `Return` instrukcja jest równoznaczna z `Exit Sub` `Exit Property` instrukcją or i `expression` nie może być dostarczone.</span><span class="sxs-lookup"><span data-stu-id="3146c-109">In a `Sub` or `Set` procedure, the `Return` statement is equivalent to an `Exit Sub` or `Exit Property` statement, and `expression` must not be supplied.</span></span>  
  
 <span data-ttu-id="3146c-110">W `Function` procedurze, `Get` , lub `Operator` , `Return` instrukcja musi zawierać `expression` , i `expression` musi oszacować do typu danych, który jest konwertowany na zwracany typ procedury.</span><span class="sxs-lookup"><span data-stu-id="3146c-110">In a `Function`, `Get`, or `Operator` procedure, the `Return` statement must include `expression`, and `expression` must evaluate to a data type that is convertible to the return type of the procedure.</span></span> <span data-ttu-id="3146c-111">W `Function` procedurze lub `Get` można także przypisać wyrażenie do nazwy procedury, która ma stanowić wartość zwracaną, a następnie wykonuje `Exit Function` `Exit Property` instrukcję or.</span><span class="sxs-lookup"><span data-stu-id="3146c-111">In a `Function` or `Get` procedure, you also have the alternative of assigning an expression to the procedure name to serve as the return value, and then executing an `Exit Function` or `Exit Property` statement.</span></span> <span data-ttu-id="3146c-112">W `Operator` procedurze należy użyć `Return expression` .</span><span class="sxs-lookup"><span data-stu-id="3146c-112">In an `Operator` procedure, you must use `Return expression`.</span></span>  
  
 <span data-ttu-id="3146c-113">`Return`W tej samej procedurze można dołączyć dowolną liczbę instrukcji.</span><span class="sxs-lookup"><span data-stu-id="3146c-113">You can include as many `Return` statements as appropriate in the same procedure.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="3146c-114">Kod w bloku jest `Finally` uruchamiany po `Return` `Try` napotkaniu instrukcji w bloku lub `Catch` , ale przed wykonaniem tej `Return` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="3146c-114">The code in a `Finally` block runs after a `Return` statement in a `Try` or `Catch` block is encountered, but before that `Return` statement executes.</span></span> <span data-ttu-id="3146c-115">`Return`Instrukcja nie może być uwzględniona w `Finally` bloku.</span><span class="sxs-lookup"><span data-stu-id="3146c-115">A `Return` statement cannot be included in a `Finally` block.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3146c-116">Przykład</span><span class="sxs-lookup"><span data-stu-id="3146c-116">Example</span></span>  
 <span data-ttu-id="3146c-117">Poniższy przykład używa `Return` instrukcji kilka razy, aby powrócić do kodu wywołującego, gdy procedura nie musi wykonywać żadnych innych czynności.</span><span class="sxs-lookup"><span data-stu-id="3146c-117">The following example uses the `Return` statement several times to return to the calling code when the procedure does not have to do anything else.</span></span>  
  
 [!code-vb[VbVbalrStatements#53](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#53)]  
  
## <a name="see-also"></a><span data-ttu-id="3146c-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="3146c-118">See also</span></span>

- [<span data-ttu-id="3146c-119">Function, instrukcja</span><span class="sxs-lookup"><span data-stu-id="3146c-119">Function Statement</span></span>](function-statement.md)
- [<span data-ttu-id="3146c-120">Sub, instrukcja</span><span class="sxs-lookup"><span data-stu-id="3146c-120">Sub Statement</span></span>](sub-statement.md)
- [<span data-ttu-id="3146c-121">Get — Instrukcja</span><span class="sxs-lookup"><span data-stu-id="3146c-121">Get Statement</span></span>](get-statement.md)
- [<span data-ttu-id="3146c-122">Set — Instrukcja</span><span class="sxs-lookup"><span data-stu-id="3146c-122">Set Statement</span></span>](set-statement.md)
- [<span data-ttu-id="3146c-123">Operator — Instrukcja</span><span class="sxs-lookup"><span data-stu-id="3146c-123">Operator Statement</span></span>](operator-statement.md)
- [<span data-ttu-id="3146c-124">Property — Instrukcja</span><span class="sxs-lookup"><span data-stu-id="3146c-124">Property Statement</span></span>](property-statement.md)
- [<span data-ttu-id="3146c-125">Exit, instrukcja</span><span class="sxs-lookup"><span data-stu-id="3146c-125">Exit Statement</span></span>](exit-statement.md)
- [<span data-ttu-id="3146c-126">Try...Catch...Finally, instrukcja</span><span class="sxs-lookup"><span data-stu-id="3146c-126">Try...Catch...Finally Statement</span></span>](try-catch-finally-statement.md)
