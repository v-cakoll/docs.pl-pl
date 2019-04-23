---
title: 'Instrukcje: Określanie, czy dwa obiekty są jednakowe (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- testing [Visual Basic], objects
- objects [Visual Basic], comparing
- object variables [Visual Basic], determining identity
ms.assetid: 7829f817-0d1f-4749-a707-de0b95e0cf5c
ms.openlocfilehash: aae053ae0473ed6ced0f28da3d5e5afc0be629df
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59295043"
---
# <a name="how-to-determine-whether-two-objects-are-identical-visual-basic"></a><span data-ttu-id="5270a-102">Instrukcje: Określanie, czy dwa obiekty są jednakowe (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5270a-102">How to: Determine Whether Two Objects Are Identical (Visual Basic)</span></span>
<span data-ttu-id="5270a-103">W języku Visual Basic dwóch odwołań do zmiennych są traktowane jako identyczne, jeśli ich wskaźniki są takie same, oznacza to, jeśli obie zmienne wskazywać tego samego wystąpienia klasy w pamięci.</span><span class="sxs-lookup"><span data-stu-id="5270a-103">In Visual Basic, two variable references are considered identical if their pointers are the same, that is, if both variables point to the same class instance in memory.</span></span> <span data-ttu-id="5270a-104">Na przykład w aplikacji Windows Forms, warto wykonania porównania, aby określić, czy bieżące wystąpienie (`Me`) jest taka sama jak konkretnego wystąpienia, takie jak `Form2`.</span><span class="sxs-lookup"><span data-stu-id="5270a-104">For example, in a Windows Forms application, you might want to make a comparison to determine whether the current instance (`Me`) is the same as a particular instance, such as `Form2`.</span></span>  
  
 <span data-ttu-id="5270a-105">Visual Basic oferuje dwa operatory porównanie wskaźników.</span><span class="sxs-lookup"><span data-stu-id="5270a-105">Visual Basic provides two operators to compare pointers.</span></span> <span data-ttu-id="5270a-106">[Operatora Is](../../../../visual-basic/language-reference/operators/is-operator.md) zwraca `True` Jeśli obiekty są identyczne i [IsNot Operator](../../../../visual-basic/language-reference/operators/isnot-operator.md) zwraca `True` Jeśli nie są.</span><span class="sxs-lookup"><span data-stu-id="5270a-106">The [Is Operator](../../../../visual-basic/language-reference/operators/is-operator.md) returns `True` if the objects are identical, and the [IsNot Operator](../../../../visual-basic/language-reference/operators/isnot-operator.md) returns `True` if they are not.</span></span>  
  
## <a name="determining-if-two-objects-are-identical"></a><span data-ttu-id="5270a-107">Określanie, jeśli dwa obiekty są jednakowe</span><span class="sxs-lookup"><span data-stu-id="5270a-107">Determining if Two Objects Are Identical</span></span>  
  
#### <a name="to-determine-if-two-objects-are-identical"></a><span data-ttu-id="5270a-108">Aby określić, jeśli dwa obiekty są jednakowe</span><span class="sxs-lookup"><span data-stu-id="5270a-108">To determine if two objects are identical</span></span>  
  
1. <span data-ttu-id="5270a-109">Konfigurowanie `Boolean` wyrażenie do przetestowania dwóch obiektów.</span><span class="sxs-lookup"><span data-stu-id="5270a-109">Set up a `Boolean` expression to test the two objects.</span></span>  
  
2. <span data-ttu-id="5270a-110">W wyrażeniu testowania za pomocą `Is` dwa obiekty jako argumenty operacji operatora.</span><span class="sxs-lookup"><span data-stu-id="5270a-110">In your testing expression, use the `Is` operator with the two objects as operands.</span></span>  
  
     <span data-ttu-id="5270a-111">`Is` Zwraca `True` Jeśli obiekty wskazywać tego samego wystąpienia klasy.</span><span class="sxs-lookup"><span data-stu-id="5270a-111">`Is` returns `True` if the objects point to the same class instance.</span></span>  
  
## <a name="determining-if-two-objects-are-not-identical"></a><span data-ttu-id="5270a-112">Określanie, jeśli dwa obiekty nie są identyczne</span><span class="sxs-lookup"><span data-stu-id="5270a-112">Determining if Two Objects Are Not Identical</span></span>  
 <span data-ttu-id="5270a-113">Czasami trzeba wykonać akcję, jeśli dwa obiekty nie są identyczne i mogą być niewygodna połączyć `Not` i `Is`, na przykład `If Not obj1 Is obj2`.</span><span class="sxs-lookup"><span data-stu-id="5270a-113">Sometimes you want to perform an action if the two objects are not identical, and it can be awkward to combine `Not` and `Is`, for example `If Not obj1 Is obj2`.</span></span> <span data-ttu-id="5270a-114">W takim przypadku można użyć `IsNot` operatora.</span><span class="sxs-lookup"><span data-stu-id="5270a-114">In such a case you can use the `IsNot` operator.</span></span>  
  
#### <a name="to-determine-if-two-objects-are-not-identical"></a><span data-ttu-id="5270a-115">Aby sprawdzić, czy dwa obiekty nie są identyczne</span><span class="sxs-lookup"><span data-stu-id="5270a-115">To determine if two objects are not identical</span></span>  
  
1. <span data-ttu-id="5270a-116">Konfigurowanie `Boolean` wyrażenie do przetestowania dwóch obiektów.</span><span class="sxs-lookup"><span data-stu-id="5270a-116">Set up a `Boolean` expression to test the two objects.</span></span>  
  
2. <span data-ttu-id="5270a-117">W wyrażeniu testowania za pomocą `IsNot` dwa obiekty jako argumenty operacji operatora.</span><span class="sxs-lookup"><span data-stu-id="5270a-117">In your testing expression, use the `IsNot` operator with the two objects as operands.</span></span>  
  
     <span data-ttu-id="5270a-118">`IsNot` Zwraca `True` Jeśli obiekty nie mogą wskazywać tego samego wystąpienia klasy.</span><span class="sxs-lookup"><span data-stu-id="5270a-118">`IsNot` returns `True` if the objects do not point to the same class instance.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5270a-119">Przykład</span><span class="sxs-lookup"><span data-stu-id="5270a-119">Example</span></span>  
 <span data-ttu-id="5270a-120">Następujący przykład sprawdza pary `Object` zmienne, aby zobaczyć, jeśli wskazują na to samo wystąpienie klasy.</span><span class="sxs-lookup"><span data-stu-id="5270a-120">The following example tests pairs of `Object` variables to see if they point to the same class instance.</span></span>  
  
 [!code-vb[VbVbalrKeywords#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/class7.vb#14)]  
  
 <span data-ttu-id="5270a-121">Poprzedni przykład wyświetla następujące dane wyjściowe.</span><span class="sxs-lookup"><span data-stu-id="5270a-121">The preceding example displays the following output.</span></span>  
  
 `objA different from objB? True`  
  
 `objA identical to objC? True`  
  
## <a name="see-also"></a><span data-ttu-id="5270a-122">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="5270a-122">See also</span></span>

- [<span data-ttu-id="5270a-123">Object, typ danych</span><span class="sxs-lookup"><span data-stu-id="5270a-123">Object Data Type</span></span>](../../../../visual-basic/language-reference/data-types/object-data-type.md)
- [<span data-ttu-id="5270a-124">Zmienne obiektów</span><span class="sxs-lookup"><span data-stu-id="5270a-124">Object Variables</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)
- [<span data-ttu-id="5270a-125">Wartości zmiennej obiektu</span><span class="sxs-lookup"><span data-stu-id="5270a-125">Object Variable Values</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variable-values.md)
- [<span data-ttu-id="5270a-126">Is, operator</span><span class="sxs-lookup"><span data-stu-id="5270a-126">Is Operator</span></span>](../../../../visual-basic/language-reference/operators/is-operator.md)
- [<span data-ttu-id="5270a-127">IsNot, operator</span><span class="sxs-lookup"><span data-stu-id="5270a-127">IsNot Operator</span></span>](../../../../visual-basic/language-reference/operators/isnot-operator.md)
- [<span data-ttu-id="5270a-128">Instrukcje: Określanie, czy dwa obiekty są powiązane</span><span class="sxs-lookup"><span data-stu-id="5270a-128">How to: Determine Whether Two Objects Are Related</span></span>](../../../../visual-basic/programming-guide/language-features/variables/how-to-determine-whether-two-objects-are-related.md)
- [<span data-ttu-id="5270a-129">Me, My, MyBase i MyClass</span><span class="sxs-lookup"><span data-stu-id="5270a-129">Me, My, MyBase, and MyClass</span></span>](../../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)
