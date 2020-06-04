---
title: 'Porady: określanie, czy dwa obiekty są jednakowe'
ms.date: 07/20/2015
helpviewer_keywords:
- testing [Visual Basic], objects
- objects [Visual Basic], comparing
- object variables [Visual Basic], determining identity
ms.assetid: 7829f817-0d1f-4749-a707-de0b95e0cf5c
ms.openlocfilehash: 67c3af8b7bdac3ad1c7e4908f1ac2684df7a87aa
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84410480"
---
# <a name="how-to-determine-whether-two-objects-are-identical-visual-basic"></a><span data-ttu-id="e88a8-102">Porady: określanie, czy dwa obiekty są jednakowe (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e88a8-102">How to: Determine Whether Two Objects Are Identical (Visual Basic)</span></span>
<span data-ttu-id="e88a8-103">W Visual Basic, dwa odwołania do zmiennych są uważane za identyczne, jeśli ich wskaźniki są takie same, czyli jeśli obie zmienne wskazują na to samo wystąpienie klasy w pamięci.</span><span class="sxs-lookup"><span data-stu-id="e88a8-103">In Visual Basic, two variable references are considered identical if their pointers are the same, that is, if both variables point to the same class instance in memory.</span></span> <span data-ttu-id="e88a8-104">Na przykład w aplikacji Windows Forms można przeprowadzić porównanie, aby określić, czy bieżące wystąpienie ( `Me` ) jest takie samo jak określone wystąpienie, takie jak `Form2` .</span><span class="sxs-lookup"><span data-stu-id="e88a8-104">For example, in a Windows Forms application, you might want to make a comparison to determine whether the current instance (`Me`) is the same as a particular instance, such as `Form2`.</span></span>  
  
 <span data-ttu-id="e88a8-105">Visual Basic udostępnia dwa operatory do porównywania wskaźników.</span><span class="sxs-lookup"><span data-stu-id="e88a8-105">Visual Basic provides two operators to compare pointers.</span></span> <span data-ttu-id="e88a8-106">[Operator is](../../../language-reference/operators/is-operator.md) zwraca `True` , jeśli obiekty są identyczne, a [operator IsNot](../../../language-reference/operators/isnot-operator.md) zwraca, `True` Jeśli nie są.</span><span class="sxs-lookup"><span data-stu-id="e88a8-106">The [Is Operator](../../../language-reference/operators/is-operator.md) returns `True` if the objects are identical, and the [IsNot Operator](../../../language-reference/operators/isnot-operator.md) returns `True` if they are not.</span></span>  
  
## <a name="determining-if-two-objects-are-identical"></a><span data-ttu-id="e88a8-107">Określanie, czy dwa obiekty są identyczne</span><span class="sxs-lookup"><span data-stu-id="e88a8-107">Determining if Two Objects Are Identical</span></span>  
  
#### <a name="to-determine-if-two-objects-are-identical"></a><span data-ttu-id="e88a8-108">Aby określić, czy dwa obiekty są identyczne</span><span class="sxs-lookup"><span data-stu-id="e88a8-108">To determine if two objects are identical</span></span>  
  
1. <span data-ttu-id="e88a8-109">Skonfiguruj `Boolean` wyrażenie, aby przetestować dwa obiekty.</span><span class="sxs-lookup"><span data-stu-id="e88a8-109">Set up a `Boolean` expression to test the two objects.</span></span>  
  
2. <span data-ttu-id="e88a8-110">W wyrażeniu testowym Użyj `Is` operatora z dwoma obiektami jako operandami.</span><span class="sxs-lookup"><span data-stu-id="e88a8-110">In your testing expression, use the `Is` operator with the two objects as operands.</span></span>  
  
     <span data-ttu-id="e88a8-111">`Is`zwraca `True` Jeśli obiekty wskazują to samo wystąpienie klasy.</span><span class="sxs-lookup"><span data-stu-id="e88a8-111">`Is` returns `True` if the objects point to the same class instance.</span></span>  
  
## <a name="determining-if-two-objects-are-not-identical"></a><span data-ttu-id="e88a8-112">Określanie, czy dwa obiekty nie są identyczne</span><span class="sxs-lookup"><span data-stu-id="e88a8-112">Determining if Two Objects Are Not Identical</span></span>  
 <span data-ttu-id="e88a8-113">Czasami chcesz wykonać akcję, jeśli dwa obiekty nie są identyczne i mogą być niewygodna do łączenia `Not` i `Is` , na przykład `If Not obj1 Is obj2` .</span><span class="sxs-lookup"><span data-stu-id="e88a8-113">Sometimes you want to perform an action if the two objects are not identical, and it can be awkward to combine `Not` and `Is`, for example `If Not obj1 Is obj2`.</span></span> <span data-ttu-id="e88a8-114">W takim przypadku można użyć `IsNot` operatora.</span><span class="sxs-lookup"><span data-stu-id="e88a8-114">In such a case you can use the `IsNot` operator.</span></span>  
  
#### <a name="to-determine-if-two-objects-are-not-identical"></a><span data-ttu-id="e88a8-115">Aby określić, czy dwa obiekty nie są identyczne</span><span class="sxs-lookup"><span data-stu-id="e88a8-115">To determine if two objects are not identical</span></span>  
  
1. <span data-ttu-id="e88a8-116">Skonfiguruj `Boolean` wyrażenie, aby przetestować dwa obiekty.</span><span class="sxs-lookup"><span data-stu-id="e88a8-116">Set up a `Boolean` expression to test the two objects.</span></span>  
  
2. <span data-ttu-id="e88a8-117">W wyrażeniu testowym Użyj `IsNot` operatora z dwoma obiektami jako operandami.</span><span class="sxs-lookup"><span data-stu-id="e88a8-117">In your testing expression, use the `IsNot` operator with the two objects as operands.</span></span>  
  
     <span data-ttu-id="e88a8-118">`IsNot`zwraca `True` czy obiekty nie wskazują tego samego wystąpienia klasy.</span><span class="sxs-lookup"><span data-stu-id="e88a8-118">`IsNot` returns `True` if the objects do not point to the same class instance.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e88a8-119">Przykład</span><span class="sxs-lookup"><span data-stu-id="e88a8-119">Example</span></span>  
 <span data-ttu-id="e88a8-120">Poniższy przykład sprawdza pary `Object` zmiennych, aby sprawdzić, czy wskazują one na to samo wystąpienie klasy.</span><span class="sxs-lookup"><span data-stu-id="e88a8-120">The following example tests pairs of `Object` variables to see if they point to the same class instance.</span></span>  
  
 [!code-vb[VbVbalrKeywords#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/class7.vb#14)]  
  
 <span data-ttu-id="e88a8-121">W poprzednim przykładzie przedstawiono następujące dane wyjściowe.</span><span class="sxs-lookup"><span data-stu-id="e88a8-121">The preceding example displays the following output.</span></span>  
  
 `objA different from objB? True`  
  
 `objA identical to objC? True`  
  
## <a name="see-also"></a><span data-ttu-id="e88a8-122">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e88a8-122">See also</span></span>

- [<span data-ttu-id="e88a8-123">Object — typ danych</span><span class="sxs-lookup"><span data-stu-id="e88a8-123">Object Data Type</span></span>](../../../language-reference/data-types/object-data-type.md)
- [<span data-ttu-id="e88a8-124">Zmienne obiektów</span><span class="sxs-lookup"><span data-stu-id="e88a8-124">Object Variables</span></span>](object-variables.md)
- [<span data-ttu-id="e88a8-125">Wartości zmiennej obiektu</span><span class="sxs-lookup"><span data-stu-id="e88a8-125">Object Variable Values</span></span>](object-variable-values.md)
- [<span data-ttu-id="e88a8-126">Is, operator</span><span class="sxs-lookup"><span data-stu-id="e88a8-126">Is Operator</span></span>](../../../language-reference/operators/is-operator.md)
- [<span data-ttu-id="e88a8-127">IsNot, operator</span><span class="sxs-lookup"><span data-stu-id="e88a8-127">IsNot Operator</span></span>](../../../language-reference/operators/isnot-operator.md)
- [<span data-ttu-id="e88a8-128">Porady: określanie, czy dwa obiekty są powiązane</span><span class="sxs-lookup"><span data-stu-id="e88a8-128">How to: Determine Whether Two Objects Are Related</span></span>](how-to-determine-whether-two-objects-are-related.md)
- [<span data-ttu-id="e88a8-129">Me, My, MyBase i MyClass</span><span class="sxs-lookup"><span data-stu-id="e88a8-129">Me, My, MyBase, and MyClass</span></span>](../../program-structure/me-my-mybase-and-myclass.md)
