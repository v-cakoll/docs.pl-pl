---
title: Inne struktury sterujące
ms.date: 07/20/2015
helpviewer_keywords:
- statements [Visual Basic], control flow
- control structures [Visual Basic]
ms.assetid: 24b811f7-98ba-40ec-8dd3-4d528cfa4574
ms.openlocfilehash: c6d80b237c7c3512c2904547842fdeb3c69bef68
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84402021"
---
# <a name="other-control-structures-visual-basic"></a><span data-ttu-id="82d54-102">Inne struktury sterujące (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="82d54-102">Other Control Structures (Visual Basic)</span></span>
<span data-ttu-id="82d54-103">Visual Basic zawiera struktury kontroli, które ułatwiają usuwanie zasobu lub zmniejszają liczbę przypadków powtarzania odwołania do obiektu.</span><span class="sxs-lookup"><span data-stu-id="82d54-103">Visual Basic provides control structures that help you dispose of a resource or reduce the number of times you have to repeat an object reference.</span></span>  
  
## <a name="usingend-using-construction"></a><span data-ttu-id="82d54-104">Korzystanie z... Zakończ korzystanie z konstrukcji</span><span class="sxs-lookup"><span data-stu-id="82d54-104">Using...End Using Construction</span></span>  
 <span data-ttu-id="82d54-105">`Using...End Using`Konstrukcja ustanawia blok instrukcji, w ramach którego używany jest zasób, taki jak połączenie SQL.</span><span class="sxs-lookup"><span data-stu-id="82d54-105">The `Using...End Using` construction establishes a statement block within which you make use of a resource such as a SQL connection.</span></span> <span data-ttu-id="82d54-106">Opcjonalnie możesz uzyskać zasób za pomocą `Using` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="82d54-106">You can optionally acquire the resource with the `Using` statement.</span></span> <span data-ttu-id="82d54-107">Po zamknięciu `Using` bloku Visual Basic automatycznie usunąć zasób, aby był dostępny do użycia przez inny kod.</span><span class="sxs-lookup"><span data-stu-id="82d54-107">When you exit the `Using` block, Visual Basic automatically disposes of the resource so that it is available for other code to use.</span></span> <span data-ttu-id="82d54-108">Zasób musi być lokalny i jednorazowy.</span><span class="sxs-lookup"><span data-stu-id="82d54-108">The resource must be local and disposable.</span></span> <span data-ttu-id="82d54-109">Aby uzyskać więcej informacji, zobacz [using instrukcji](../../../language-reference/statements/using-statement.md).</span><span class="sxs-lookup"><span data-stu-id="82d54-109">For more information, see [Using Statement](../../../language-reference/statements/using-statement.md).</span></span>  
  
## <a name="withend-with-construction"></a><span data-ttu-id="82d54-110">Z... Zakończ z konstrukcją</span><span class="sxs-lookup"><span data-stu-id="82d54-110">With...End With Construction</span></span>  
 <span data-ttu-id="82d54-111">`With...End With`Konstrukcja pozwala określić odwołanie do obiektu jeden raz, a następnie uruchomić serię instrukcji, które uzyskują dostęp do swoich elementów członkowskich.</span><span class="sxs-lookup"><span data-stu-id="82d54-111">The `With...End With` construction lets you specify an object reference once and then run a series of statements that access its members.</span></span> <span data-ttu-id="82d54-112">Może to uprościć kod i zwiększyć wydajność, ponieważ Visual Basic nie musi ponownie ustanowić odwołania dla każdej instrukcji, która uzyskuje do niej dostęp.</span><span class="sxs-lookup"><span data-stu-id="82d54-112">This can simplify your code and improve performance because Visual Basic does not have to re-establish the reference for each statement that accesses it.</span></span> <span data-ttu-id="82d54-113">Aby uzyskać więcej informacji, zobacz temat [with... End With — instrukcja](../../../language-reference/statements/with-end-with-statement.md).</span><span class="sxs-lookup"><span data-stu-id="82d54-113">For more information, see [With...End With Statement](../../../language-reference/statements/with-end-with-statement.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="82d54-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="82d54-114">See also</span></span>

- [<span data-ttu-id="82d54-115">Przepływ sterowania</span><span class="sxs-lookup"><span data-stu-id="82d54-115">Control Flow</span></span>](index.md)
- [<span data-ttu-id="82d54-116">Struktury decyzji</span><span class="sxs-lookup"><span data-stu-id="82d54-116">Decision Structures</span></span>](decision-structures.md)
- [<span data-ttu-id="82d54-117">Struktury pętli</span><span class="sxs-lookup"><span data-stu-id="82d54-117">Loop Structures</span></span>](loop-structures.md)
- [<span data-ttu-id="82d54-118">Zagnieżdżone struktury sterujące</span><span class="sxs-lookup"><span data-stu-id="82d54-118">Nested Control Structures</span></span>](nested-control-structures.md)
- [<span data-ttu-id="82d54-119">Using, instrukcja</span><span class="sxs-lookup"><span data-stu-id="82d54-119">Using Statement</span></span>](../../../language-reference/statements/using-statement.md)
- [<span data-ttu-id="82d54-120">With...End With, instrukcja</span><span class="sxs-lookup"><span data-stu-id="82d54-120">With...End With Statement</span></span>](../../../language-reference/statements/with-end-with-statement.md)
