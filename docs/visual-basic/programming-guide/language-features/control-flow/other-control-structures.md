---
title: Inne struktury sterujące
ms.date: 07/20/2015
helpviewer_keywords:
- statements [Visual Basic], control flow
- control structures [Visual Basic]
ms.assetid: 24b811f7-98ba-40ec-8dd3-4d528cfa4574
ms.openlocfilehash: 758df361f421684655147ae288af3f350e53c4d7
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74348132"
---
# <a name="other-control-structures-visual-basic"></a><span data-ttu-id="c1536-102">Inne struktury sterujące (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c1536-102">Other Control Structures (Visual Basic)</span></span>
<span data-ttu-id="c1536-103">Visual Basic zawiera struktury kontroli, które ułatwiają usuwanie zasobu lub zmniejszają liczbę przypadków powtarzania odwołania do obiektu.</span><span class="sxs-lookup"><span data-stu-id="c1536-103">Visual Basic provides control structures that help you dispose of a resource or reduce the number of times you have to repeat an object reference.</span></span>  
  
## <a name="usingend-using-construction"></a><span data-ttu-id="c1536-104">Korzystanie z... Zakończ korzystanie z konstrukcji</span><span class="sxs-lookup"><span data-stu-id="c1536-104">Using...End Using Construction</span></span>  
 <span data-ttu-id="c1536-105">Konstrukcja `Using...End Using` ustanawia blok instrukcji, w ramach którego używany jest zasób, taki jak połączenie SQL.</span><span class="sxs-lookup"><span data-stu-id="c1536-105">The `Using...End Using` construction establishes a statement block within which you make use of a resource such as a SQL connection.</span></span> <span data-ttu-id="c1536-106">Opcjonalnie możesz uzyskać zasób z instrukcją `Using`.</span><span class="sxs-lookup"><span data-stu-id="c1536-106">You can optionally acquire the resource with the `Using` statement.</span></span> <span data-ttu-id="c1536-107">Po zamknięciu bloku `Using` Visual Basic automatycznie usunąć zasób, aby był dostępny do użycia w innym kodzie.</span><span class="sxs-lookup"><span data-stu-id="c1536-107">When you exit the `Using` block, Visual Basic automatically disposes of the resource so that it is available for other code to use.</span></span> <span data-ttu-id="c1536-108">Zasób musi być lokalny i jednorazowy.</span><span class="sxs-lookup"><span data-stu-id="c1536-108">The resource must be local and disposable.</span></span> <span data-ttu-id="c1536-109">Aby uzyskać więcej informacji, zobacz [using instrukcji](../../../../visual-basic/language-reference/statements/using-statement.md).</span><span class="sxs-lookup"><span data-stu-id="c1536-109">For more information, see [Using Statement](../../../../visual-basic/language-reference/statements/using-statement.md).</span></span>  
  
## <a name="withend-with-construction"></a><span data-ttu-id="c1536-110">Z... Zakończ z konstrukcją</span><span class="sxs-lookup"><span data-stu-id="c1536-110">With...End With Construction</span></span>  
 <span data-ttu-id="c1536-111">Konstrukcja `With...End With` pozwala określić odwołanie do obiektu jeden raz, a następnie uruchomić serię instrukcji, które uzyskują dostęp do swoich elementów członkowskich.</span><span class="sxs-lookup"><span data-stu-id="c1536-111">The `With...End With` construction lets you specify an object reference once and then run a series of statements that access its members.</span></span> <span data-ttu-id="c1536-112">Może to uprościć kod i zwiększyć wydajność, ponieważ Visual Basic nie musi ponownie ustanowić odwołania dla każdej instrukcji, która uzyskuje do niej dostęp.</span><span class="sxs-lookup"><span data-stu-id="c1536-112">This can simplify your code and improve performance because Visual Basic does not have to re-establish the reference for each statement that accesses it.</span></span> <span data-ttu-id="c1536-113">Aby uzyskać więcej informacji, zobacz temat [with... End With — instrukcja](../../../../visual-basic/language-reference/statements/with-end-with-statement.md).</span><span class="sxs-lookup"><span data-stu-id="c1536-113">For more information, see [With...End With Statement](../../../../visual-basic/language-reference/statements/with-end-with-statement.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c1536-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c1536-114">See also</span></span>

- [<span data-ttu-id="c1536-115">Przepływ sterowania</span><span class="sxs-lookup"><span data-stu-id="c1536-115">Control Flow</span></span>](../../../../visual-basic/programming-guide/language-features/control-flow/index.md)
- [<span data-ttu-id="c1536-116">Struktury decyzji</span><span class="sxs-lookup"><span data-stu-id="c1536-116">Decision Structures</span></span>](../../../../visual-basic/programming-guide/language-features/control-flow/decision-structures.md)
- [<span data-ttu-id="c1536-117">Struktury pętli</span><span class="sxs-lookup"><span data-stu-id="c1536-117">Loop Structures</span></span>](../../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md)
- [<span data-ttu-id="c1536-118">Zagnieżdżone struktury sterujące</span><span class="sxs-lookup"><span data-stu-id="c1536-118">Nested Control Structures</span></span>](../../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md)
- [<span data-ttu-id="c1536-119">Using, instrukcja</span><span class="sxs-lookup"><span data-stu-id="c1536-119">Using Statement</span></span>](../../../../visual-basic/language-reference/statements/using-statement.md)
- [<span data-ttu-id="c1536-120">With...End With, instrukcja</span><span class="sxs-lookup"><span data-stu-id="c1536-120">With...End With Statement</span></span>](../../../../visual-basic/language-reference/statements/with-end-with-statement.md)
