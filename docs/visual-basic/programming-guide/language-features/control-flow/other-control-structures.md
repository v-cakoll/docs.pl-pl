---
title: Inne struktury sterujące (Visual Basic)
ms.custom: ''
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- statements [Visual Basic], control flow
- control structures [Visual Basic]
ms.assetid: 24b811f7-98ba-40ec-8dd3-4d528cfa4574
caps.latest.revision: 19
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 4e1ea44cf2f0405dc55f8df60fb842691e50a9a0
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="other-control-structures-visual-basic"></a><span data-ttu-id="1a285-102">Inne struktury sterujące (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1a285-102">Other Control Structures (Visual Basic)</span></span>
<span data-ttu-id="1a285-103">Visual Basic zapewnia struktury sterujące, które ułatwiają Usuwanie zasobu lub Zmniejsz liczbę razy, należy powtórzyć odwołanie do obiektu.</span><span class="sxs-lookup"><span data-stu-id="1a285-103">Visual Basic provides control structures that help you dispose of a resource or reduce the number of times you have to repeat an object reference.</span></span>  
  
## <a name="usingend-using-construction"></a><span data-ttu-id="1a285-104">Za pomocą... Przy użyciu konstrukcji końcowych</span><span class="sxs-lookup"><span data-stu-id="1a285-104">Using...End Using Construction</span></span>  
 <span data-ttu-id="1a285-105">`Using...End Using` Konstrukcji określa blok instrukcji, w którym należy korzystać z zasobów, takich jak połączenia SQL.</span><span class="sxs-lookup"><span data-stu-id="1a285-105">The `Using...End Using` construction establishes a statement block within which you make use of a resource such as a SQL connection.</span></span> <span data-ttu-id="1a285-106">Opcjonalnie można uzyskać zasobu o `Using` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="1a285-106">You can optionally acquire the resource with the `Using` statement.</span></span> <span data-ttu-id="1a285-107">Po zakończeniu `Using` bloku, Visual Basic automatycznie usuwa zasobu, aby była dostępna dla innych kodu do użycia.</span><span class="sxs-lookup"><span data-stu-id="1a285-107">When you exit the `Using` block, Visual Basic automatically disposes of the resource so that it is available for other code to use.</span></span> <span data-ttu-id="1a285-108">Zasób musi być lokalny i możliwe do rozporządzania.</span><span class="sxs-lookup"><span data-stu-id="1a285-108">The resource must be local and disposable.</span></span> <span data-ttu-id="1a285-109">Aby uzyskać więcej informacji, zobacz [instrukcji Using](../../../../visual-basic/language-reference/statements/using-statement.md).</span><span class="sxs-lookup"><span data-stu-id="1a285-109">For more information, see [Using Statement](../../../../visual-basic/language-reference/statements/using-statement.md).</span></span>  
  
## <a name="withend-with-construction"></a><span data-ttu-id="1a285-110">Z... Kończyć konstrukcji</span><span class="sxs-lookup"><span data-stu-id="1a285-110">With...End With Construction</span></span>  
 <span data-ttu-id="1a285-111">`With...End With` Konstrukcji pozwala określić odwołanie do obiektu raz, a następnie uruchom serię instrukcji, które uzyskują dostęp do jego elementów członkowskich.</span><span class="sxs-lookup"><span data-stu-id="1a285-111">The `With...End With` construction lets you specify an object reference once and then run a series of statements that access its members.</span></span> <span data-ttu-id="1a285-112">Może to uprościć kod i zwiększyć wydajność, ponieważ Visual Basic nie trzeba ponownie ustanowić odwołania dla każdej instrukcji, który uzyskuje dostęp do jej.</span><span class="sxs-lookup"><span data-stu-id="1a285-112">This can simplify your code and improve performance because Visual Basic does not have to re-establish the reference for each statement that accesses it.</span></span> <span data-ttu-id="1a285-113">Aby uzyskać więcej informacji, zobacz [z... End With — instrukcja](../../../../visual-basic/language-reference/statements/with-end-with-statement.md).</span><span class="sxs-lookup"><span data-stu-id="1a285-113">For more information, see [With...End With Statement](../../../../visual-basic/language-reference/statements/with-end-with-statement.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1a285-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="1a285-114">See Also</span></span>  
 [<span data-ttu-id="1a285-115">Przepływ sterowania</span><span class="sxs-lookup"><span data-stu-id="1a285-115">Control Flow</span></span>](../../../../visual-basic/programming-guide/language-features/control-flow/index.md)  
 [<span data-ttu-id="1a285-116">Struktury decyzji</span><span class="sxs-lookup"><span data-stu-id="1a285-116">Decision Structures</span></span>](../../../../visual-basic/programming-guide/language-features/control-flow/decision-structures.md)  
 [<span data-ttu-id="1a285-117">Struktury pętli</span><span class="sxs-lookup"><span data-stu-id="1a285-117">Loop Structures</span></span>](../../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md)  
 [<span data-ttu-id="1a285-118">Zagnieżdżone struktury sterujące</span><span class="sxs-lookup"><span data-stu-id="1a285-118">Nested Control Structures</span></span>](../../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md)  
 [<span data-ttu-id="1a285-119">Using, instrukcja</span><span class="sxs-lookup"><span data-stu-id="1a285-119">Using Statement</span></span>](../../../../visual-basic/language-reference/statements/using-statement.md)  
 [<span data-ttu-id="1a285-120">With...End With, instrukcja</span><span class="sxs-lookup"><span data-stu-id="1a285-120">With...End With Statement</span></span>](../../../../visual-basic/language-reference/statements/with-end-with-statement.md)
