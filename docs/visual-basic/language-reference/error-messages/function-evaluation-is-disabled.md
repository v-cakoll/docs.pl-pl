---
title: Szacowanie funkcji zostało wyłączone, ponieważ poprzednie szacowanie przekroczyło limit czasu
ms.date: 07/20/2015
f1_keywords:
- bc30957
- vbc30957
helpviewer_keywords:
- BC30957
ms.assetid: 561e593a-f50a-4b72-a708-4cab60ec7b28
ms.openlocfilehash: d004c89b742944622ce45e6a2be8d96116252745
ms.sourcegitcommit: 5a28f8eb071fcc09b045b0c4ae4b96898673192e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2019
ms.locfileid: "73197565"
---
# <a name="function-evaluation-is-disabled-because-a-previous-function-evaluation-timed-out"></a><span data-ttu-id="8b509-102">Szacowanie funkcji zostało wyłączone, ponieważ poprzednie szacowanie przekroczyło limit czasu</span><span class="sxs-lookup"><span data-stu-id="8b509-102">Function evaluation is disabled because a previous function evaluation timed out</span></span>
<span data-ttu-id="8b509-103">Obliczanie funkcji jest wyłączone, ponieważ Przekroczono limit czasu obliczania poprzedniej funkcji. Aby ponownie włączyć szacowanie funkcji, ponownie wykonaj krok lub ponownie uruchom debugowanie.</span><span class="sxs-lookup"><span data-stu-id="8b509-103">Function evaluation is disabled because a previous function evaluation timed out. To re-enable function evaluation, step again or restart debugging.</span></span>  
  
 <span data-ttu-id="8b509-104">W debugerze programu Visual Studio wyrażenie określa wywołanie procedury, ale inna Ocena przekroczyła limit czasu.</span><span class="sxs-lookup"><span data-stu-id="8b509-104">In the Visual Studio debugger, an expression specifies a procedure call, but another evaluation has timed out.</span></span>  
  
 <span data-ttu-id="8b509-105">Możliwe przyczyny wywołania procedury przekroczenia limitu czasu obejmują nieskończoną pętlę lub *nieskończoną pętlę*.</span><span class="sxs-lookup"><span data-stu-id="8b509-105">Possible causes for a procedure call to time out include an infinite loop or *endless loop*.</span></span> <span data-ttu-id="8b509-106">Aby uzyskać więcej informacji, zobacz [dla... Next — instrukcja](../../../visual-basic/language-reference/statements/for-next-statement.md).</span><span class="sxs-lookup"><span data-stu-id="8b509-106">For more information, see [For...Next Statement](../../../visual-basic/language-reference/statements/for-next-statement.md).</span></span>  
  
 <span data-ttu-id="8b509-107">Szczególnym przypadkiem nieskończoności pętli jest *rekursja*.</span><span class="sxs-lookup"><span data-stu-id="8b509-107">A special case of an infinite loop is *recursion*.</span></span> <span data-ttu-id="8b509-108">Aby uzyskać więcej informacji, zobacz [procedury cykliczne](../../../visual-basic/programming-guide/language-features/procedures/recursive-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="8b509-108">For more information, see [Recursive Procedures](../../../visual-basic/programming-guide/language-features/procedures/recursive-procedures.md).</span></span>  
  
 <span data-ttu-id="8b509-109">**Identyfikator błędu:** BC30957</span><span class="sxs-lookup"><span data-stu-id="8b509-109">**Error ID:** BC30957</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="8b509-110">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="8b509-110">To correct this error</span></span>  
  
1. <span data-ttu-id="8b509-111">Jeśli to możliwe, ustal, jakie poprzednie funkcje oceny były i co spowodowało przekroczenie limitu czasu. W przeciwnym razie ten błąd może się pojawić ponownie.</span><span class="sxs-lookup"><span data-stu-id="8b509-111">If possible, determine what the previous function evaluation was and what caused it to time out. Otherwise, you might encounter this error again.</span></span>  
  
2. <span data-ttu-id="8b509-112">Ponownie wykonaj debuger lub Przerwij i ponownie uruchom debugowanie.</span><span class="sxs-lookup"><span data-stu-id="8b509-112">Either step the debugger again, or terminate and restart debugging.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8b509-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="8b509-113">See also</span></span>

- [<span data-ttu-id="8b509-114">Debugowanie w programie Visual Studio</span><span class="sxs-lookup"><span data-stu-id="8b509-114">Debugging in Visual Studio</span></span>](/visualstudio/debugger/debugger-feature-tour)
- [<span data-ttu-id="8b509-115">Nawigowanie po kodzie za pomocą debugera</span><span class="sxs-lookup"><span data-stu-id="8b509-115">Navigating through Code with the Debugger</span></span>](/visualstudio/debugger/navigating-through-code-with-the-debugger)
