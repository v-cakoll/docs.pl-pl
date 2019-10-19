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
ms.openlocfilehash: edaaf09f5a984344f7e89c9da988c529774934e9
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2019
ms.locfileid: "72583256"
---
# <a name="return-statement-visual-basic"></a><span data-ttu-id="b4fe4-102">Return — Instrukcja (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b4fe4-102">Return Statement (Visual Basic)</span></span>
<span data-ttu-id="b4fe4-103">Zwraca kontrolę do kodu, który wywołał procedurę `Function`, `Sub`, `Get`, `Set` lub `Operator`.</span><span class="sxs-lookup"><span data-stu-id="b4fe4-103">Returns control to the code that called a `Function`, `Sub`, `Get`, `Set`, or `Operator` procedure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b4fe4-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="b4fe4-104">Syntax</span></span>  
  
```vb  
Return  
' -or-  
Return expression  
```  
  
## <a name="part"></a><span data-ttu-id="b4fe4-105">Części</span><span class="sxs-lookup"><span data-stu-id="b4fe4-105">Part</span></span>  
 `expression`  
 <span data-ttu-id="b4fe4-106">Wymagane w procedurze `Function`, `Get` lub `Operator`.</span><span class="sxs-lookup"><span data-stu-id="b4fe4-106">Required in a `Function`, `Get`, or `Operator` procedure.</span></span> <span data-ttu-id="b4fe4-107">Wyrażenie, które reprezentuje wartość, która ma zostać zwrócona do kodu wywołującego.</span><span class="sxs-lookup"><span data-stu-id="b4fe4-107">Expression that represents the value to be returned to the calling code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b4fe4-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="b4fe4-108">Remarks</span></span>  
 <span data-ttu-id="b4fe4-109">W procedurze `Sub` lub `Set`, instrukcja `Return` jest równoważna z `Exit Sub` lub `Exit Property` instrukcją i nie można podać `expression`.</span><span class="sxs-lookup"><span data-stu-id="b4fe4-109">In a `Sub` or `Set` procedure, the `Return` statement is equivalent to an `Exit Sub` or `Exit Property` statement, and `expression` must not be supplied.</span></span>  
  
 <span data-ttu-id="b4fe4-110">W procedurze `Function`, `Get` lub `Operator` instrukcja `Return` musi zawierać `expression`, a `expression` musi oszacować do typu danych, który jest konwertowany na zwracany typ procedury.</span><span class="sxs-lookup"><span data-stu-id="b4fe4-110">In a `Function`, `Get`, or `Operator` procedure, the `Return` statement must include `expression`, and `expression` must evaluate to a data type that is convertible to the return type of the procedure.</span></span> <span data-ttu-id="b4fe4-111">W procedurze `Function` lub `Get` można także przypisać wyrażenie do nazwy procedury, która ma stanowić wartość zwracaną, a następnie wykonać `Exit Function` lub `Exit Property` instrukcję.</span><span class="sxs-lookup"><span data-stu-id="b4fe4-111">In a `Function` or `Get` procedure, you also have the alternative of assigning an expression to the procedure name to serve as the return value, and then executing an `Exit Function` or `Exit Property` statement.</span></span> <span data-ttu-id="b4fe4-112">W procedurze `Operator` należy użyć `Return expression`.</span><span class="sxs-lookup"><span data-stu-id="b4fe4-112">In an `Operator` procedure, you must use `Return expression`.</span></span>  
  
 <span data-ttu-id="b4fe4-113">Można dołączyć dowolną liczbę instrukcji `Return`, zgodnie z potrzebami w tej samej procedurze.</span><span class="sxs-lookup"><span data-stu-id="b4fe4-113">You can include as many `Return` statements as appropriate in the same procedure.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b4fe4-114">Kod w bloku `Finally` jest uruchamiany po napotkaniu instrukcji `Return` w bloku `Try` lub `Catch`, ale przed wykonaniem tej instrukcji `Return`.</span><span class="sxs-lookup"><span data-stu-id="b4fe4-114">The code in a `Finally` block runs after a `Return` statement in a `Try` or `Catch` block is encountered, but before that `Return` statement executes.</span></span> <span data-ttu-id="b4fe4-115">Instrukcji `Return` nie można uwzględnić w bloku `Finally`.</span><span class="sxs-lookup"><span data-stu-id="b4fe4-115">A `Return` statement cannot be included in a `Finally` block.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b4fe4-116">Przykład</span><span class="sxs-lookup"><span data-stu-id="b4fe4-116">Example</span></span>  
 <span data-ttu-id="b4fe4-117">Poniższy przykład używa instrukcji `Return` kilka razy, aby powrócić do kodu wywołującego, gdy procedura nie musi wykonywać żadnych innych czynności.</span><span class="sxs-lookup"><span data-stu-id="b4fe4-117">The following example uses the `Return` statement several times to return to the calling code when the procedure does not have to do anything else.</span></span>  
  
 [!code-vb[VbVbalrStatements#53](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#53)]  
  
## <a name="see-also"></a><span data-ttu-id="b4fe4-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b4fe4-118">See also</span></span>

- [<span data-ttu-id="b4fe4-119">Function, instrukcja</span><span class="sxs-lookup"><span data-stu-id="b4fe4-119">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)
- [<span data-ttu-id="b4fe4-120">Sub, instrukcja</span><span class="sxs-lookup"><span data-stu-id="b4fe4-120">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)
- [<span data-ttu-id="b4fe4-121">Get, instrukcja</span><span class="sxs-lookup"><span data-stu-id="b4fe4-121">Get Statement</span></span>](../../../visual-basic/language-reference/statements/get-statement.md)
- [<span data-ttu-id="b4fe4-122">Set, instrukcja</span><span class="sxs-lookup"><span data-stu-id="b4fe4-122">Set Statement</span></span>](../../../visual-basic/language-reference/statements/set-statement.md)
- [<span data-ttu-id="b4fe4-123">Operator, instrukcja</span><span class="sxs-lookup"><span data-stu-id="b4fe4-123">Operator Statement</span></span>](../../../visual-basic/language-reference/statements/operator-statement.md)
- [<span data-ttu-id="b4fe4-124">Property, instrukcja</span><span class="sxs-lookup"><span data-stu-id="b4fe4-124">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)
- [<span data-ttu-id="b4fe4-125">Exit, instrukcja</span><span class="sxs-lookup"><span data-stu-id="b4fe4-125">Exit Statement</span></span>](../../../visual-basic/language-reference/statements/exit-statement.md)
- [<span data-ttu-id="b4fe4-126">Try...Catch...Finally, instrukcja</span><span class="sxs-lookup"><span data-stu-id="b4fe4-126">Try...Catch...Finally Statement</span></span>](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)
