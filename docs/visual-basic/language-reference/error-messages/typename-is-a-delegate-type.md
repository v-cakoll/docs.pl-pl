---
title: Typ „<typename>” jest typem delegowanym
ms.date: 07/20/2015
f1_keywords:
- bc32008
- vbc32008
helpviewer_keywords:
- BC32008
ms.assetid: dc6abba0-a9ad-450f-8899-87265bc84abc
ms.openlocfilehash: 45dc0403468fa40888a6c5e6bdfe6ca782e98325
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64664198"
---
# <a name="typename-is-a-delegate-type"></a><span data-ttu-id="9263a-102">"\<typename >" jest typem delegowanym</span><span class="sxs-lookup"><span data-stu-id="9263a-102">'\<typename>' is a delegate type</span></span>
<span data-ttu-id="9263a-103">"\<typename >" jest typem delegowanym.</span><span class="sxs-lookup"><span data-stu-id="9263a-103">'\<typename>' is a delegate type.</span></span> <span data-ttu-id="9263a-104">Konstrukcja delegata zezwala na tylko pojedyncze wyrażenie AddressOf listy argumentów.</span><span class="sxs-lookup"><span data-stu-id="9263a-104">Delegate construction permits only a single AddressOf expression as an argument list.</span></span> <span data-ttu-id="9263a-105">Często można używać wyrażenia AddressOf zamiast tworzenia delegata.</span><span class="sxs-lookup"><span data-stu-id="9263a-105">Often an AddressOf expression can be used instead of a delegate construction.</span></span>  
  
 <span data-ttu-id="9263a-106">A `New` klauzuli tworzenia wystąpienia klasy delegata dostarcza listę nieprawidłowy argument dla konstruktora delegata.</span><span class="sxs-lookup"><span data-stu-id="9263a-106">A `New` clause creating an instance of a delegate class supplies an invalid argument list to the delegate constructor.</span></span>  
  
 <span data-ttu-id="9263a-107">Można podać tylko jeden `AddressOf` wyrażenia, tworząc nowe wystąpienie delegata.</span><span class="sxs-lookup"><span data-stu-id="9263a-107">You can supply only a single `AddressOf` expression when creating a new delegate instance.</span></span>  
  
 <span data-ttu-id="9263a-108">Ten błąd może spowodować, jeżeli nie przepuszczasz argumentów do konstruktora delegata przekazać więcej niż jeden argument, czy w przypadku przekazania jeden argument, nie jest prawidłowym `AddressOf` wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="9263a-108">This error can result if you do not pass any arguments to the delegate constructor, if you pass more than one argument, or if you pass a single argument that is not a valid `AddressOf` expression.</span></span>  
  
 <span data-ttu-id="9263a-109">**Identyfikator błędu:** BC32008</span><span class="sxs-lookup"><span data-stu-id="9263a-109">**Error ID:** BC32008</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="9263a-110">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="9263a-110">To correct this error</span></span>  
  
- <span data-ttu-id="9263a-111">Używanie pojedynczej `AddressOf` wyrażenia na liście argumentów dla klasy delegata w `New` klauzuli.</span><span class="sxs-lookup"><span data-stu-id="9263a-111">Use a single `AddressOf` expression in the argument list for the delegate class in the `New` clause.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9263a-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="9263a-112">See also</span></span>

- [<span data-ttu-id="9263a-113">New, operator</span><span class="sxs-lookup"><span data-stu-id="9263a-113">New Operator</span></span>](../../../visual-basic/language-reference/operators/new-operator.md)
- [<span data-ttu-id="9263a-114">AddressOf, operator</span><span class="sxs-lookup"><span data-stu-id="9263a-114">AddressOf Operator</span></span>](../../../visual-basic/language-reference/operators/addressof-operator.md)
- [<span data-ttu-id="9263a-115">Delegaty</span><span class="sxs-lookup"><span data-stu-id="9263a-115">Delegates</span></span>](../../../visual-basic/programming-guide/language-features/delegates/index.md)
- [<span data-ttu-id="9263a-116">Instrukcje: Wywoływanie metody delegata</span><span class="sxs-lookup"><span data-stu-id="9263a-116">How to: Invoke a Delegate Method</span></span>](../../../visual-basic/programming-guide/language-features/delegates/how-to-invoke-a-delegate-method.md)
