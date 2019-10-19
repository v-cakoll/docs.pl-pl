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
ms.openlocfilehash: c0cfbb5109d5b49f995028944e735c96440c9ab2
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2019
ms.locfileid: "72583512"
---
# <a name="of-clause-visual-basic"></a><span data-ttu-id="3439f-102">Of — Klauzula (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3439f-102">Of Clause (Visual Basic)</span></span>
<span data-ttu-id="3439f-103">Wprowadza klauzulę `Of`, która identyfikuje *parametr typu* dla klasy *ogólnej* , struktury, interfejsu, delegata lub procedury.</span><span class="sxs-lookup"><span data-stu-id="3439f-103">Introduces an `Of` clause, which identifies a *type parameter* on a *generic* class, structure, interface, delegate, or procedure.</span></span> <span data-ttu-id="3439f-104">Aby uzyskać informacje na temat typów ogólnych, zobacz [typy ogólne w Visual Basic](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md).</span><span class="sxs-lookup"><span data-stu-id="3439f-104">For information on generic types, see [Generic Types in Visual Basic](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md).</span></span>  
  
## <a name="using-the-of-keyword"></a><span data-ttu-id="3439f-105">Za pomocą słowa kluczowego</span><span class="sxs-lookup"><span data-stu-id="3439f-105">Using the Of Keyword</span></span>  
 <span data-ttu-id="3439f-106">Poniższy przykład kodu używa słowa kluczowego `Of` do definiowania konspektu klasy, która przyjmuje dwa parametry typu.</span><span class="sxs-lookup"><span data-stu-id="3439f-106">The following code example uses the `Of` keyword to define the outline of a class that takes two type parameters.</span></span> <span data-ttu-id="3439f-107">*Ogranicza* parametr `keyType` przez interfejs <xref:System.IComparable>, co oznacza, że kod zużywający musi dostarczyć argument typu, który implementuje <xref:System.IComparable>.</span><span class="sxs-lookup"><span data-stu-id="3439f-107">It *constrains* the `keyType` parameter by the <xref:System.IComparable> interface, which means the consuming code must supply a type argument that implements <xref:System.IComparable>.</span></span> <span data-ttu-id="3439f-108">Jest to konieczne, aby procedura `add` mogła wywołać metodę <xref:System.IComparable.CompareTo%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="3439f-108">This is necessary so that the `add` procedure can call the <xref:System.IComparable.CompareTo%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="3439f-109">Aby uzyskać więcej informacji o ograniczeniach, zobacz [Type list](../../../visual-basic/language-reference/statements/type-list.md).</span><span class="sxs-lookup"><span data-stu-id="3439f-109">For more information on constraints, see [Type List](../../../visual-basic/language-reference/statements/type-list.md).</span></span>  
  
```vb  
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
  
 <span data-ttu-id="3439f-110">Jeśli poprzednia definicja klasy zostanie ukończona, można utworzyć w niej wiele klas `dictionary`.</span><span class="sxs-lookup"><span data-stu-id="3439f-110">If you complete the preceding class definition, you can construct a variety of `dictionary` classes from it.</span></span> <span data-ttu-id="3439f-111">Typy, które podasz, `entryType` i `keyType` określają typ wpisu, który zawiera Klasa, oraz typ klucza, który jest kojarzony z każdym wpisem.</span><span class="sxs-lookup"><span data-stu-id="3439f-111">The types you supply to `entryType` and `keyType` determine what type of entry the class holds and what type of key it associates with each entry.</span></span> <span data-ttu-id="3439f-112">Ze względu na ograniczenie należy podać, aby `keyType` typ, który implementuje <xref:System.IComparable>.</span><span class="sxs-lookup"><span data-stu-id="3439f-112">Because of the constraint, you must supply to `keyType` a type that implements <xref:System.IComparable>.</span></span>  
  
 <span data-ttu-id="3439f-113">Poniższy przykład kodu tworzy obiekt, który przechowuje `String` wpisy i kojarzy klucz `Integer` z każdym z nich.</span><span class="sxs-lookup"><span data-stu-id="3439f-113">The following code example creates an object that holds `String` entries and associates an `Integer` key with each one.</span></span> <span data-ttu-id="3439f-114">`Integer` implementuje <xref:System.IComparable> i w związku z tym spełnia ograniczenie `keyType`.</span><span class="sxs-lookup"><span data-stu-id="3439f-114">`Integer` implements <xref:System.IComparable> and therefore satisfies the constraint on `keyType`.</span></span>  
  
```vb  
Dim d As New dictionary(Of String, Integer)  
```  
  
 <span data-ttu-id="3439f-115">Słowa kluczowego `Of` można użyć w tych kontekstach:</span><span class="sxs-lookup"><span data-stu-id="3439f-115">The `Of` keyword can be used in these contexts:</span></span>  
  
 [<span data-ttu-id="3439f-116">Class, instrukcja</span><span class="sxs-lookup"><span data-stu-id="3439f-116">Class Statement</span></span>](../../../visual-basic/language-reference/statements/class-statement.md)  
  
 [<span data-ttu-id="3439f-117">Delegate, instrukcja</span><span class="sxs-lookup"><span data-stu-id="3439f-117">Delegate Statement</span></span>](../../../visual-basic/language-reference/statements/delegate-statement.md)  
  
 [<span data-ttu-id="3439f-118">Function, instrukcja</span><span class="sxs-lookup"><span data-stu-id="3439f-118">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [<span data-ttu-id="3439f-119">Interface, instrukcja</span><span class="sxs-lookup"><span data-stu-id="3439f-119">Interface Statement</span></span>](../../../visual-basic/language-reference/statements/interface-statement.md)  
  
 [<span data-ttu-id="3439f-120">Structure, instrukcja</span><span class="sxs-lookup"><span data-stu-id="3439f-120">Structure Statement</span></span>](../../../visual-basic/language-reference/statements/structure-statement.md)  
  
 [<span data-ttu-id="3439f-121">Sub, instrukcja</span><span class="sxs-lookup"><span data-stu-id="3439f-121">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="3439f-122">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="3439f-122">See also</span></span>

- <xref:System.IComparable>
- [<span data-ttu-id="3439f-123">Lista typów</span><span class="sxs-lookup"><span data-stu-id="3439f-123">Type List</span></span>](../../../visual-basic/language-reference/statements/type-list.md)
- [<span data-ttu-id="3439f-124">Typy ogólne w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="3439f-124">Generic Types in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)
- [<span data-ttu-id="3439f-125">Podczas</span><span class="sxs-lookup"><span data-stu-id="3439f-125">In</span></span>](../../../visual-basic/language-reference/modifiers/in-generic-modifier.md)
- [<span data-ttu-id="3439f-126">Określoną</span><span class="sxs-lookup"><span data-stu-id="3439f-126">Out</span></span>](../../../visual-basic/language-reference/modifiers/out-generic-modifier.md)
