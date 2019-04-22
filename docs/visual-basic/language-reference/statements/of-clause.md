---
title: Of — Klauzula (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- Of
- vb.Of
- vb.of
helpviewer_keywords:
- Of keyword [Visual Basic]
- arguments [Visual Basic], data types
- constraints, Visual Basic generic types
- generic parameters
- generics [Visual Basic], constraints
- parameters [Visual Basic], type
- types [Visual Basic], generic
- parameters [Visual Basic], generic
- type parameters
- data type arguments
ms.assetid: 0db8f65c-65af-4089-ab7f-6fcfecb60444
ms.openlocfilehash: 880570c714292b0c11eef4e2cd4c4b410bb075f1
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "58823444"
---
# <a name="of-clause-visual-basic"></a><span data-ttu-id="efdd5-102">Of — Klauzula (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="efdd5-102">Of Clause (Visual Basic)</span></span>
<span data-ttu-id="efdd5-103">Wprowadza `Of` klauzula, która identyfikuje *parametr typu* na *ogólny* klasy, struktury, interfejsu, delegata lub procedury.</span><span class="sxs-lookup"><span data-stu-id="efdd5-103">Introduces an `Of` clause, which identifies a *type parameter* on a *generic* class, structure, interface, delegate, or procedure.</span></span> <span data-ttu-id="efdd5-104">Aby uzyskać informacji na temat typów ogólnych, zobacz [typów ogólnych w Visual Basic](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md).</span><span class="sxs-lookup"><span data-stu-id="efdd5-104">For information on generic types, see [Generic Types in Visual Basic](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md).</span></span>  
  
## <a name="using-the-of-keyword"></a><span data-ttu-id="efdd5-105">Za pomocą słowa kluczowego</span><span class="sxs-lookup"><span data-stu-id="efdd5-105">Using the Of Keyword</span></span>  
 <span data-ttu-id="efdd5-106">Poniższy przykład kodu wykorzystuje `Of` — słowo kluczowe do zdefiniowania konturu klasę, która przyjmuje dwa parametry typu.</span><span class="sxs-lookup"><span data-stu-id="efdd5-106">The following code example uses the `Of` keyword to define the outline of a class that takes two type parameters.</span></span> <span data-ttu-id="efdd5-107">Jego *ogranicza* `keyType` parametru przez <xref:System.IComparable> interfejsu, co oznacza, że kod konsumencki należy podać argument typu, który implementuje <xref:System.IComparable>.</span><span class="sxs-lookup"><span data-stu-id="efdd5-107">It *constrains* the `keyType` parameter by the <xref:System.IComparable> interface, which means the consuming code must supply a type argument that implements <xref:System.IComparable>.</span></span> <span data-ttu-id="efdd5-108">Jest to konieczne, aby `add` można wywołać procedury <xref:System.IComparable.CompareTo%2A?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="efdd5-108">This is necessary so that the `add` procedure can call the <xref:System.IComparable.CompareTo%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="efdd5-109">Aby uzyskać więcej informacji na temat ograniczeń, zobacz [lista typów](../../../visual-basic/language-reference/statements/type-list.md).</span><span class="sxs-lookup"><span data-stu-id="efdd5-109">For more information on constraints, see [Type List](../../../visual-basic/language-reference/statements/type-list.md).</span></span>  
  
```  
Public Class Dictionary(Of entryType, keyType As IComparable)  
    Public Sub add(ByVal e As entryType, ByVal k As keyType)  
        Dim dk As keyType  
        If k.CompareTo(dk) = 0 Then  
        End If  
    End Sub  
    Public Function find(ByVal k As keyType) As entryType  
    End Function  
End Class  
```  
  
 <span data-ttu-id="efdd5-110">Po wykonaniu poprzednich definicji klasy, można utworzyć szereg `dictionary` klas z niego.</span><span class="sxs-lookup"><span data-stu-id="efdd5-110">If you complete the preceding class definition, you can construct a variety of `dictionary` classes from it.</span></span> <span data-ttu-id="efdd5-111">Typy użytkownika `entryType` i `keyType` ustalić, jakiego typu wejścia tej klasy przechowuje i jakiego rodzaju klucz kojarzy z każdego wpisu.</span><span class="sxs-lookup"><span data-stu-id="efdd5-111">The types you supply to `entryType` and `keyType` determine what type of entry the class holds and what type of key it associates with each entry.</span></span> <span data-ttu-id="efdd5-112">Ze względu na ograniczenia, należy podać do `keyType` typu, który implementuje <xref:System.IComparable>.</span><span class="sxs-lookup"><span data-stu-id="efdd5-112">Because of the constraint, you must supply to `keyType` a type that implements <xref:System.IComparable>.</span></span>  
  
 <span data-ttu-id="efdd5-113">Poniższy przykład kodu tworzy obiekt, który zawiera `String` wpisy i kojarzy `Integer` kluczy z każdej z nich.</span><span class="sxs-lookup"><span data-stu-id="efdd5-113">The following code example creates an object that holds `String` entries and associates an `Integer` key with each one.</span></span> <span data-ttu-id="efdd5-114">`Integer` implementuje <xref:System.IComparable> i w związku z tym spełnia ograniczenia na `keyType`.</span><span class="sxs-lookup"><span data-stu-id="efdd5-114">`Integer` implements <xref:System.IComparable> and therefore satisfies the constraint on `keyType`.</span></span>  
  
```  
Dim d As New dictionary(Of String, Integer)  
```  
  
 <span data-ttu-id="efdd5-115">Słowa kluczowego `Of` można używać w następujących kontekstach:</span><span class="sxs-lookup"><span data-stu-id="efdd5-115">The `Of` keyword can be used in these contexts:</span></span>  
  
 [<span data-ttu-id="efdd5-116">Class, instrukcja</span><span class="sxs-lookup"><span data-stu-id="efdd5-116">Class Statement</span></span>](../../../visual-basic/language-reference/statements/class-statement.md)  
  
 [<span data-ttu-id="efdd5-117">Delegate, instrukcja</span><span class="sxs-lookup"><span data-stu-id="efdd5-117">Delegate Statement</span></span>](../../../visual-basic/language-reference/statements/delegate-statement.md)  
  
 [<span data-ttu-id="efdd5-118">Function, instrukcja</span><span class="sxs-lookup"><span data-stu-id="efdd5-118">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [<span data-ttu-id="efdd5-119">Instrukcja Interface</span><span class="sxs-lookup"><span data-stu-id="efdd5-119">Interface Statement</span></span>](../../../visual-basic/language-reference/statements/interface-statement.md)  
  
 [<span data-ttu-id="efdd5-120">Structure, instrukcja</span><span class="sxs-lookup"><span data-stu-id="efdd5-120">Structure Statement</span></span>](../../../visual-basic/language-reference/statements/structure-statement.md)  
  
 [<span data-ttu-id="efdd5-121">Sub, instrukcja</span><span class="sxs-lookup"><span data-stu-id="efdd5-121">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="efdd5-122">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="efdd5-122">See also</span></span>

- <xref:System.IComparable>
- [<span data-ttu-id="efdd5-123">Lista typów</span><span class="sxs-lookup"><span data-stu-id="efdd5-123">Type List</span></span>](../../../visual-basic/language-reference/statements/type-list.md)
- [<span data-ttu-id="efdd5-124">Typy ogólne w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="efdd5-124">Generic Types in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)
- [<span data-ttu-id="efdd5-125">W</span><span class="sxs-lookup"><span data-stu-id="efdd5-125">In</span></span>](../../../visual-basic/language-reference/modifiers/in-generic-modifier.md)
- [<span data-ttu-id="efdd5-126">limit</span><span class="sxs-lookup"><span data-stu-id="efdd5-126">Out</span></span>](../../../visual-basic/language-reference/modifiers/out-generic-modifier.md)
