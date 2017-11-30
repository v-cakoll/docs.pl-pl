---
title: "Return — Instrukcja (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.Return
helpviewer_keywords:
- Return statement [Visual Basic], syntax
- control flow [Visual Basic], returning control to expressions
- Return statement [Visual Basic]
- expressions [Visual Basic], returning control to
ms.assetid: ac86e7f0-5a67-42c3-9834-0e0381efa3ec
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: b66d16a249164b8989f05f10c785b97055bfde9e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="return-statement-visual-basic"></a><span data-ttu-id="8c518-102">Return — Instrukcja (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8c518-102">Return Statement (Visual Basic)</span></span>
<span data-ttu-id="8c518-103">Zwraca sterowania do kodu, który wywołał `Function`, `Sub`, `Get`, `Set`, lub `Operator` procedury.</span><span class="sxs-lookup"><span data-stu-id="8c518-103">Returns control to the code that called a `Function`, `Sub`, `Get`, `Set`, or `Operator` procedure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8c518-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="8c518-104">Syntax</span></span>  
  
```  
Return  
-or-  
Return expression  
```  
  
## <a name="part"></a><span data-ttu-id="8c518-105">Część</span><span class="sxs-lookup"><span data-stu-id="8c518-105">Part</span></span>  
 `expression`  
 <span data-ttu-id="8c518-106">Wymagane w `Function`, `Get`, lub `Operator` procedury.</span><span class="sxs-lookup"><span data-stu-id="8c518-106">Required in a `Function`, `Get`, or `Operator` procedure.</span></span> <span data-ttu-id="8c518-107">Wyrażenie, które reprezentuje wartość zwracana do wywołującego kodu.</span><span class="sxs-lookup"><span data-stu-id="8c518-107">Expression that represents the value to be returned to the calling code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8c518-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="8c518-108">Remarks</span></span>  
 <span data-ttu-id="8c518-109">W `Sub` lub `Set` procedury `Return` instrukcja jest odpowiednikiem `Exit Sub` lub `Exit Property` instrukcji i `expression` nie muszą być dostarczone.</span><span class="sxs-lookup"><span data-stu-id="8c518-109">In a `Sub` or `Set` procedure, the `Return` statement is equivalent to an `Exit Sub` or `Exit Property` statement, and `expression` must not be supplied.</span></span>  
  
 <span data-ttu-id="8c518-110">W `Function`, `Get`, lub `Operator` procedury `Return` instrukcja musi zawierać `expression`, i `expression` musi mieć typ danych, który można przekonwertować na typ zwracany procedury.</span><span class="sxs-lookup"><span data-stu-id="8c518-110">In a `Function`, `Get`, or `Operator` procedure, the `Return` statement must include `expression`, and `expression` must evaluate to a data type that is convertible to the return type of the procedure.</span></span> <span data-ttu-id="8c518-111">W `Function` lub `Get` procedury, masz również alternatywnej przypisywania wyrażenia na nazwę procedury jako wartość zwracaną i następnie wykonywanie `Exit Function` lub `Exit Property` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="8c518-111">In a `Function` or `Get` procedure, you also have the alternative of assigning an expression to the procedure name to serve as the return value, and then executing an `Exit Function` or `Exit Property` statement.</span></span> <span data-ttu-id="8c518-112">W `Operator` procedurę, musisz użyć `Return``expression`.</span><span class="sxs-lookup"><span data-stu-id="8c518-112">In an `Operator` procedure, you must use `Return``expression`.</span></span>  
  
 <span data-ttu-id="8c518-113">Może zawierać tyle `Return` instrukcje zgodnie z potrzebami w tej samej procedury.</span><span class="sxs-lookup"><span data-stu-id="8c518-113">You can include as many `Return` statements as appropriate in the same procedure.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8c518-114">Kod w `Finally` bloku jest uruchamiany po `Return` instrukcji w `Try` lub `Catch` blok jest napotkano, ale przed nim `Return` wykonywania instrukcji.</span><span class="sxs-lookup"><span data-stu-id="8c518-114">The code in a `Finally` block runs after a `Return` statement in a `Try` or `Catch` block is encountered, but before that `Return` statement executes.</span></span> <span data-ttu-id="8c518-115">A `Return` instrukcji nie można uwzględnić w `Finally` bloku.</span><span class="sxs-lookup"><span data-stu-id="8c518-115">A `Return` statement cannot be included in a `Finally` block.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8c518-116">Przykład</span><span class="sxs-lookup"><span data-stu-id="8c518-116">Example</span></span>  
 <span data-ttu-id="8c518-117">W poniższym przykładzie użyto `Return` instrukcji kilka razy, aby powrócić do wywołującego kodu, gdy procedura nie trzeba nic robić.</span><span class="sxs-lookup"><span data-stu-id="8c518-117">The following example uses the `Return` statement several times to return to the calling code when the procedure does not have to do anything else.</span></span>  
  
 [!code-vb[VbVbalrStatements#53](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/return-statement_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="8c518-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8c518-118">See Also</span></span>  
 [<span data-ttu-id="8c518-119">Function — instrukcja</span><span class="sxs-lookup"><span data-stu-id="8c518-119">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)  
 [<span data-ttu-id="8c518-120">Sub — instrukcja</span><span class="sxs-lookup"><span data-stu-id="8c518-120">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)  
 [<span data-ttu-id="8c518-121">Get — instrukcja</span><span class="sxs-lookup"><span data-stu-id="8c518-121">Get Statement</span></span>](../../../visual-basic/language-reference/statements/get-statement.md)  
 [<span data-ttu-id="8c518-122">Set — instrukcja</span><span class="sxs-lookup"><span data-stu-id="8c518-122">Set Statement</span></span>](../../../visual-basic/language-reference/statements/set-statement.md)  
 [<span data-ttu-id="8c518-123">Operator — instrukcja</span><span class="sxs-lookup"><span data-stu-id="8c518-123">Operator Statement</span></span>](../../../visual-basic/language-reference/statements/operator-statement.md)  
 [<span data-ttu-id="8c518-124">Property — instrukcja</span><span class="sxs-lookup"><span data-stu-id="8c518-124">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)  
 [<span data-ttu-id="8c518-125">Exit — instrukcja</span><span class="sxs-lookup"><span data-stu-id="8c518-125">Exit Statement</span></span>](../../../visual-basic/language-reference/statements/exit-statement.md)  
 [<span data-ttu-id="8c518-126">Try... CATCH... Finally — instrukcja</span><span class="sxs-lookup"><span data-stu-id="8c518-126">Try...Catch...Finally Statement</span></span>](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)
