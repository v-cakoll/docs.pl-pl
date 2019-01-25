---
title: Inne struktury sterujące (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- statements [Visual Basic], control flow
- control structures [Visual Basic]
ms.assetid: 24b811f7-98ba-40ec-8dd3-4d528cfa4574
ms.openlocfilehash: a383d0c95de5286cce722c05bd8888d5acffb173
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54590003"
---
# <a name="other-control-structures-visual-basic"></a><span data-ttu-id="8392c-102">Inne struktury sterujące (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8392c-102">Other Control Structures (Visual Basic)</span></span>
<span data-ttu-id="8392c-103">Visual Basic zapewnia struktury sterujące, które ułatwiają Usuwanie zasobu lub Zmniejsz liczbę razy, należy powtórzyć odwołanie do obiektu.</span><span class="sxs-lookup"><span data-stu-id="8392c-103">Visual Basic provides control structures that help you dispose of a resource or reduce the number of times you have to repeat an object reference.</span></span>  
  
## <a name="usingend-using-construction"></a><span data-ttu-id="8392c-104">Za pomocą... Za pomocą konstrukcji końcowych</span><span class="sxs-lookup"><span data-stu-id="8392c-104">Using...End Using Construction</span></span>  
 <span data-ttu-id="8392c-105">`Using...End Using` Konstrukcji ustanawia blok instrukcji, w którym możesz wprowadzić korzystanie z zasobów, takich jak połączenia SQL.</span><span class="sxs-lookup"><span data-stu-id="8392c-105">The `Using...End Using` construction establishes a statement block within which you make use of a resource such as a SQL connection.</span></span> <span data-ttu-id="8392c-106">Opcjonalnie można pobrać zasobu o `Using` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="8392c-106">You can optionally acquire the resource with the `Using` statement.</span></span> <span data-ttu-id="8392c-107">Po zakończeniu `Using` bloku, Visual Basic automatycznie usuwa zasobu tak, że jest dostępny dla innego kodu do użycia.</span><span class="sxs-lookup"><span data-stu-id="8392c-107">When you exit the `Using` block, Visual Basic automatically disposes of the resource so that it is available for other code to use.</span></span> <span data-ttu-id="8392c-108">Zasób musi być lokalny i możliwe do likwidacji.</span><span class="sxs-lookup"><span data-stu-id="8392c-108">The resource must be local and disposable.</span></span> <span data-ttu-id="8392c-109">Aby uzyskać więcej informacji, zobacz [instrukcji Using](../../../../visual-basic/language-reference/statements/using-statement.md).</span><span class="sxs-lookup"><span data-stu-id="8392c-109">For more information, see [Using Statement](../../../../visual-basic/language-reference/statements/using-statement.md).</span></span>  
  
## <a name="withend-with-construction"></a><span data-ttu-id="8392c-110">Za pomocą... Kończy się konstrukcji</span><span class="sxs-lookup"><span data-stu-id="8392c-110">With...End With Construction</span></span>  
 <span data-ttu-id="8392c-111">`With...End With` Konstrukcji pozwala określić odwołanie do obiektu tylko raz, a następnie uruchom serię instrukcji uzyskujących dostęp do jego członków.</span><span class="sxs-lookup"><span data-stu-id="8392c-111">The `With...End With` construction lets you specify an object reference once and then run a series of statements that access its members.</span></span> <span data-ttu-id="8392c-112">Może to uprościć kod i zwiększyć wydajność, ponieważ Visual Basic nie trzeba ponownie ustanowić odwołanie dla każdej instrukcji, która uzyskuje do niej dostęp.</span><span class="sxs-lookup"><span data-stu-id="8392c-112">This can simplify your code and improve performance because Visual Basic does not have to re-establish the reference for each statement that accesses it.</span></span> <span data-ttu-id="8392c-113">Aby uzyskać więcej informacji, zobacz [za pomocą... End With — instrukcja](../../../../visual-basic/language-reference/statements/with-end-with-statement.md).</span><span class="sxs-lookup"><span data-stu-id="8392c-113">For more information, see [With...End With Statement](../../../../visual-basic/language-reference/statements/with-end-with-statement.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8392c-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="8392c-114">See also</span></span>
- [<span data-ttu-id="8392c-115">Przepływ sterowania</span><span class="sxs-lookup"><span data-stu-id="8392c-115">Control Flow</span></span>](../../../../visual-basic/programming-guide/language-features/control-flow/index.md)
- [<span data-ttu-id="8392c-116">Struktury decyzji</span><span class="sxs-lookup"><span data-stu-id="8392c-116">Decision Structures</span></span>](../../../../visual-basic/programming-guide/language-features/control-flow/decision-structures.md)
- [<span data-ttu-id="8392c-117">Struktury pętli</span><span class="sxs-lookup"><span data-stu-id="8392c-117">Loop Structures</span></span>](../../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md)
- [<span data-ttu-id="8392c-118">Zagnieżdżone struktury sterujące</span><span class="sxs-lookup"><span data-stu-id="8392c-118">Nested Control Structures</span></span>](../../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md)
- [<span data-ttu-id="8392c-119">Using, instrukcja</span><span class="sxs-lookup"><span data-stu-id="8392c-119">Using Statement</span></span>](../../../../visual-basic/language-reference/statements/using-statement.md)
- [<span data-ttu-id="8392c-120">With...End With, instrukcja</span><span class="sxs-lookup"><span data-stu-id="8392c-120">With...End With Statement</span></span>](../../../../visual-basic/language-reference/statements/with-end-with-statement.md)
