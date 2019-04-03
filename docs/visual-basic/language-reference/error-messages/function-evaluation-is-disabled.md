---
title: Szacowanie funkcji zostało wyłączone, ponieważ poprzednie szacowanie przekroczyło limit czasu
ms.date: 07/20/2015
f1_keywords:
- bc30957
- vbc30957
helpviewer_keywords:
- BC30957
ms.assetid: 561e593a-f50a-4b72-a708-4cab60ec7b28
ms.openlocfilehash: d024420fbbc3efbd3d19bb58c9379eacbafac5d3
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/02/2019
ms.locfileid: "58820740"
---
# <a name="function-evaluation-is-disabled-because-a-previous-function-evaluation-timed-out"></a><span data-ttu-id="39b5d-102">Szacowanie funkcji zostało wyłączone, ponieważ poprzednie szacowanie przekroczyło limit czasu</span><span class="sxs-lookup"><span data-stu-id="39b5d-102">Function evaluation is disabled because a previous function evaluation timed out</span></span>
<span data-ttu-id="39b5d-103">Szacowanie funkcji zostało wyłączone, ponieważ poprzednie szacowanie funkcji przekroczyło limit czasu. Aby ponownie włączyć funkcję oceny, krok ponownie, lub uruchom ponownie debugowanie.</span><span class="sxs-lookup"><span data-stu-id="39b5d-103">Function evaluation is disabled because a previous function evaluation timed out. To re-enable function evaluation, step again or restart debugging.</span></span>  
  
 <span data-ttu-id="39b5d-104">W debugerze programu Visual Studio wyrażenie określa wywołania procedury, ale upłynął limit czasu oceny innego.</span><span class="sxs-lookup"><span data-stu-id="39b5d-104">In the Visual Studio debugger, an expression specifies a procedure call, but another evaluation has timed out.</span></span>  
  
 <span data-ttu-id="39b5d-105">Możliwe przyczyny na przekroczenie limitu czasu wywołanie procedury to wejścia w nieskończoną pętlę lub *nieskończoną pętlę*.</span><span class="sxs-lookup"><span data-stu-id="39b5d-105">Possible causes for a procedure call to time out include an infinite loop or *endless loop*.</span></span> <span data-ttu-id="39b5d-106">Aby uzyskać więcej informacji, zobacz [dla... Następna instrukcja](../../../visual-basic/language-reference/statements/for-next-statement.md).</span><span class="sxs-lookup"><span data-stu-id="39b5d-106">For more information, see [For...Next Statement](../../../visual-basic/language-reference/statements/for-next-statement.md).</span></span>  
  
 <span data-ttu-id="39b5d-107">Jest przypadkiem szczególnym wejścia w nieskończoną pętlę *rekursji*.</span><span class="sxs-lookup"><span data-stu-id="39b5d-107">A special case of an infinite loop is *recursion*.</span></span> <span data-ttu-id="39b5d-108">Aby uzyskać więcej informacji, zobacz [procedury rekurencyjne](../../../visual-basic/programming-guide/language-features/procedures/recursive-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="39b5d-108">For more information, see [Recursive Procedures](../../../visual-basic/programming-guide/language-features/procedures/recursive-procedures.md).</span></span>  
  
 <span data-ttu-id="39b5d-109">**Identyfikator błędu:** BC30957</span><span class="sxs-lookup"><span data-stu-id="39b5d-109">**Error ID:** BC30957</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="39b5d-110">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="39b5d-110">To correct this error</span></span>  
  
1.  <span data-ttu-id="39b5d-111">Jeśli to możliwe Określ poprzednie szacowanie funkcji zostało i co spowodowało przekroczenie limitu czasu. W przeciwnym razie ten błąd może wystąpić ponownie.</span><span class="sxs-lookup"><span data-stu-id="39b5d-111">If possible, determine what the previous function evaluation was and what caused it to time out. Otherwise, you might encounter this error again.</span></span>  
  
2.  <span data-ttu-id="39b5d-112">Krok debuger ponownie, lub przerwać i uruchom ponownie debugowanie.</span><span class="sxs-lookup"><span data-stu-id="39b5d-112">Either step the debugger again, or terminate and restart debugging.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="39b5d-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="39b5d-113">See also</span></span>

- [<span data-ttu-id="39b5d-114">Debugowanie w programie Visual Studio</span><span class="sxs-lookup"><span data-stu-id="39b5d-114">Debugging in Visual Studio</span></span>](/visualstudio/debugger/debugging-in-visual-studio)
- [<span data-ttu-id="39b5d-115">Nawigowanie po kodzie za pomocą debugera</span><span class="sxs-lookup"><span data-stu-id="39b5d-115">Navigating through Code with the Debugger</span></span>](/visualstudio/debugger/navigating-through-code-with-the-debugger)
