---
title: "Szacowanie funkcji zostało wyłączone, ponieważ poprzednie szacowanie przekroczyło limit czasu"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- bc30957
- vbc30957
helpviewer_keywords:
- BC30957
ms.assetid: 561e593a-f50a-4b72-a708-4cab60ec7b28
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 05067e730486b443b7a508adb499f34c060d5093
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="function-evaluation-is-disabled-because-a-previous-function-evaluation-timed-out"></a><span data-ttu-id="43713-102">Szacowanie funkcji zostało wyłączone, ponieważ poprzednie szacowanie przekroczyło limit czasu</span><span class="sxs-lookup"><span data-stu-id="43713-102">Function evaluation is disabled because a previous function evaluation timed out</span></span>
<span data-ttu-id="43713-103">Szacowanie funkcji zostało wyłączone, ponieważ poprzednie szacowanie funkcji przekroczyło limit czasu. Aby ponownie włączyć Szacowanie funkcji, ponownie wykonaj krok lub uruchom ponownie debugowanie.</span><span class="sxs-lookup"><span data-stu-id="43713-103">Function evaluation is disabled because a previous function evaluation timed out. To re-enable function evaluation, step again or restart debugging.</span></span>  
  
 <span data-ttu-id="43713-104">W debugerze programu Visual Studio wyrażenie określa wywołanie procedury, ale innej obliczania został przekroczony.</span><span class="sxs-lookup"><span data-stu-id="43713-104">In the Visual Studio debugger, an expression specifies a procedure call, but another evaluation has timed out.</span></span>  
  
 <span data-ttu-id="43713-105">Możliwe przyczyny wywołania procedury limit czasu to nieskończoną pętlę lub *nieskończonej pętli*.</span><span class="sxs-lookup"><span data-stu-id="43713-105">Possible causes for a procedure call to time out include an infinite loop or *endless loop*.</span></span> <span data-ttu-id="43713-106">Aby uzyskać więcej informacji, zobacz [dla... Następna instrukcja](../../../visual-basic/language-reference/statements/for-next-statement.md).</span><span class="sxs-lookup"><span data-stu-id="43713-106">For more information, see [For...Next Statement](../../../visual-basic/language-reference/statements/for-next-statement.md).</span></span>  
  
 <span data-ttu-id="43713-107">Specjalny przypadek nieskończoną pętlę jest *rekursji*.</span><span class="sxs-lookup"><span data-stu-id="43713-107">A special case of an infinite loop is *recursion*.</span></span> <span data-ttu-id="43713-108">Aby uzyskać więcej informacji, zobacz [procedury rekurencyjne](../../../visual-basic/programming-guide/language-features/procedures/recursive-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="43713-108">For more information, see [Recursive Procedures](../../../visual-basic/programming-guide/language-features/procedures/recursive-procedures.md).</span></span>  
  
 <span data-ttu-id="43713-109">**Identyfikator błędu:** BC30957</span><span class="sxs-lookup"><span data-stu-id="43713-109">**Error ID:** BC30957</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="43713-110">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="43713-110">To correct this error</span></span>  
  
1.  <span data-ttu-id="43713-111">Jeśli to możliwe można określić, poprzednie Obliczanie funkcji zostało i przyczyn limitu czasu. W przeciwnym razie ten błąd może wystąpić ponownie.</span><span class="sxs-lookup"><span data-stu-id="43713-111">If possible, determine what the previous function evaluation was and what caused it to time out. Otherwise, you might encounter this error again.</span></span>  
  
2.  <span data-ttu-id="43713-112">Krok debuger ponownie, lub przerwanie i uruchom ponownie debugowanie.</span><span class="sxs-lookup"><span data-stu-id="43713-112">Either step the debugger again, or terminate and restart debugging.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="43713-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="43713-113">See Also</span></span>  
 [<span data-ttu-id="43713-114">Debugowanie w programie Visual Studio</span><span class="sxs-lookup"><span data-stu-id="43713-114">Debugging in Visual Studio</span></span>](/visualstudio/debugger/debugging-in-visual-studio)  
 [<span data-ttu-id="43713-115">Nawigowanie po kodzie za pomocą debugera</span><span class="sxs-lookup"><span data-stu-id="43713-115">Navigating through Code with the Debugger</span></span>](/visualstudio/debugger/navigating-through-code-with-the-debugger)
