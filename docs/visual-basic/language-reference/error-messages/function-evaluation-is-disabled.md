---
title: Szacowanie funkcji zostało wyłączone, ponieważ poprzednie szacowanie przekroczyło limit czasu
ms.date: 07/20/2015
f1_keywords:
- bc30957
- vbc30957
helpviewer_keywords:
- BC30957
ms.assetid: 561e593a-f50a-4b72-a708-4cab60ec7b28
ms.openlocfilehash: 7b0113e9c1018772da6dc180f7fc5beb0e922917
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84402956"
---
# <a name="function-evaluation-is-disabled-because-a-previous-function-evaluation-timed-out"></a><span data-ttu-id="a4d48-102">Szacowanie funkcji zostało wyłączone, ponieważ poprzednie szacowanie przekroczyło limit czasu</span><span class="sxs-lookup"><span data-stu-id="a4d48-102">Function evaluation is disabled because a previous function evaluation timed out</span></span>
<span data-ttu-id="a4d48-103">Obliczanie funkcji jest wyłączone, ponieważ Przekroczono limit czasu obliczania poprzedniej funkcji. Aby ponownie włączyć szacowanie funkcji, ponownie wykonaj krok lub ponownie uruchom debugowanie.</span><span class="sxs-lookup"><span data-stu-id="a4d48-103">Function evaluation is disabled because a previous function evaluation timed out. To re-enable function evaluation, step again or restart debugging.</span></span>  
  
 <span data-ttu-id="a4d48-104">W debugerze programu Visual Studio wyrażenie określa wywołanie procedury, ale inna Ocena przekroczyła limit czasu.</span><span class="sxs-lookup"><span data-stu-id="a4d48-104">In the Visual Studio debugger, an expression specifies a procedure call, but another evaluation has timed out.</span></span>  
  
 <span data-ttu-id="a4d48-105">Możliwe przyczyny wywołania procedury przekroczenia limitu czasu obejmują nieskończoną pętlę lub *nieskończoną pętlę*.</span><span class="sxs-lookup"><span data-stu-id="a4d48-105">Possible causes for a procedure call to time out include an infinite loop or *endless loop*.</span></span> <span data-ttu-id="a4d48-106">Aby uzyskać więcej informacji, zobacz [dla... Next — instrukcja](../statements/for-next-statement.md).</span><span class="sxs-lookup"><span data-stu-id="a4d48-106">For more information, see [For...Next Statement](../statements/for-next-statement.md).</span></span>  
  
 <span data-ttu-id="a4d48-107">Szczególnym przypadkiem nieskończoności pętli jest *rekursja*.</span><span class="sxs-lookup"><span data-stu-id="a4d48-107">A special case of an infinite loop is *recursion*.</span></span> <span data-ttu-id="a4d48-108">Aby uzyskać więcej informacji, zobacz [procedury cykliczne](../../programming-guide/language-features/procedures/recursive-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="a4d48-108">For more information, see [Recursive Procedures](../../programming-guide/language-features/procedures/recursive-procedures.md).</span></span>  
  
 <span data-ttu-id="a4d48-109">**Identyfikator błędu:** BC30957</span><span class="sxs-lookup"><span data-stu-id="a4d48-109">**Error ID:** BC30957</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="a4d48-110">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="a4d48-110">To correct this error</span></span>  
  
1. <span data-ttu-id="a4d48-111">Jeśli to możliwe, ustal, jakie poprzednie funkcje oceny były i co spowodowało przekroczenie limitu czasu. W przeciwnym razie ten błąd może się pojawić ponownie.</span><span class="sxs-lookup"><span data-stu-id="a4d48-111">If possible, determine what the previous function evaluation was and what caused it to time out. Otherwise, you might encounter this error again.</span></span>  
  
2. <span data-ttu-id="a4d48-112">Ponownie wykonaj debuger lub Przerwij i ponownie uruchom debugowanie.</span><span class="sxs-lookup"><span data-stu-id="a4d48-112">Either step the debugger again, or terminate and restart debugging.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a4d48-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a4d48-113">See also</span></span>

- [<span data-ttu-id="a4d48-114">Debugowanie w Visual Studio</span><span class="sxs-lookup"><span data-stu-id="a4d48-114">Debugging in Visual Studio</span></span>](/visualstudio/debugger/debugger-feature-tour)
- [<span data-ttu-id="a4d48-115">Nawigowanie po kodzie za pomocą debugera</span><span class="sxs-lookup"><span data-stu-id="a4d48-115">Navigating through Code with the Debugger</span></span>](/visualstudio/debugger/navigating-through-code-with-the-debugger)
