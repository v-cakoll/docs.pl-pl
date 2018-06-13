---
title: '&#39;&lt;Właściwość TypeName&gt; &#39; jest typem delegowanym'
ms.date: 07/20/2015
f1_keywords:
- bc32008
- vbc32008
helpviewer_keywords:
- BC32008
ms.assetid: dc6abba0-a9ad-450f-8899-87265bc84abc
ms.openlocfilehash: c6d4244ce72dedee50b65ba19978149ce86b9e87
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33595651"
---
# <a name="39lttypenamegt39-is-a-delegate-type"></a><span data-ttu-id="e9448-102">&#39;&lt;Właściwość TypeName&gt; &#39; jest typem delegowanym</span><span class="sxs-lookup"><span data-stu-id="e9448-102">&#39;&lt;typename&gt;&#39; is a delegate type</span></span>
<span data-ttu-id="e9448-103">"\<typename >" jest typem delegowanym.</span><span class="sxs-lookup"><span data-stu-id="e9448-103">'\<typename>' is a delegate type.</span></span> <span data-ttu-id="e9448-104">Delegat konstrukcji zezwala na tylko jedno wyrażenie AddressOf jako listy argumentów.</span><span class="sxs-lookup"><span data-stu-id="e9448-104">Delegate construction permits only a single AddressOf expression as an argument list.</span></span> <span data-ttu-id="e9448-105">Wyrażenia AddressOf można często zamiast konstrukcji obiektu delegowanego.</span><span class="sxs-lookup"><span data-stu-id="e9448-105">Often an AddressOf expression can be used instead of a delegate construction.</span></span>  
  
 <span data-ttu-id="e9448-106">A `New` klauzuli tworzenia wystąpienia klasy delegata dostarcza listy nieprawidłowy argument do konstruktora delegata.</span><span class="sxs-lookup"><span data-stu-id="e9448-106">A `New` clause creating an instance of a delegate class supplies an invalid argument list to the delegate constructor.</span></span>  
  
 <span data-ttu-id="e9448-107">Można podać tylko jeden `AddressOf` wyrażenie podczas tworzenia nowego wystąpienia obiektu delegowanego.</span><span class="sxs-lookup"><span data-stu-id="e9448-107">You can supply only a single `AddressOf` expression when creating a new delegate instance.</span></span>  
  
 <span data-ttu-id="e9448-108">Ten błąd może spowodować żadnych argumentów nie jest przekazywany do konstruktora delegata, jeśli przekazać więcej niż jeden argument lub w przypadku przekazania pojedynczy argument który nie jest prawidłową `AddressOf` wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="e9448-108">This error can result if you do not pass any arguments to the delegate constructor, if you pass more than one argument, or if you pass a single argument that is not a valid `AddressOf` expression.</span></span>  
  
 <span data-ttu-id="e9448-109">**Identyfikator błędu:** BC32008</span><span class="sxs-lookup"><span data-stu-id="e9448-109">**Error ID:** BC32008</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="e9448-110">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="e9448-110">To correct this error</span></span>  
  
-   <span data-ttu-id="e9448-111">Użyj pojedynczego `AddressOf` wyrażenia argumentu na liście w klasie obiektów delegowanych `New` klauzuli.</span><span class="sxs-lookup"><span data-stu-id="e9448-111">Use a single `AddressOf` expression in the argument list for the delegate class in the `New` clause.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e9448-112">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e9448-112">See Also</span></span>  
 [<span data-ttu-id="e9448-113">Operator New</span><span class="sxs-lookup"><span data-stu-id="e9448-113">New Operator</span></span>](../../../visual-basic/language-reference/operators/new-operator.md)  
 [<span data-ttu-id="e9448-114">AddressOf, operator</span><span class="sxs-lookup"><span data-stu-id="e9448-114">AddressOf Operator</span></span>](../../../visual-basic/language-reference/operators/addressof-operator.md)  
 [<span data-ttu-id="e9448-115">Delegaci</span><span class="sxs-lookup"><span data-stu-id="e9448-115">Delegates</span></span>](../../../visual-basic/programming-guide/language-features/delegates/index.md)  
 [<span data-ttu-id="e9448-116">Instrukcje: wywoływanie metody delegata</span><span class="sxs-lookup"><span data-stu-id="e9448-116">How to: Invoke a Delegate Method</span></span>](../../../visual-basic/programming-guide/language-features/delegates/how-to-invoke-a-delegate-method.md)
