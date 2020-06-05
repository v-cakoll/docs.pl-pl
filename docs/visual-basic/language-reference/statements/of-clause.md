---
title: Of, klauzula
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
ms.openlocfilehash: 8497f46453d586fb94e1f7c82c81c6b923dd6f60
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84404424"
---
# <a name="of-clause-visual-basic"></a><span data-ttu-id="7a65b-102">Of — Klauzula (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7a65b-102">Of Clause (Visual Basic)</span></span>
<span data-ttu-id="7a65b-103">Wprowadza `Of` klauzulę, która identyfikuje *parametr typu* dla klasy *ogólnej* , struktury, interfejsu, delegata lub procedury.</span><span class="sxs-lookup"><span data-stu-id="7a65b-103">Introduces an `Of` clause, which identifies a *type parameter* on a *generic* class, structure, interface, delegate, or procedure.</span></span> <span data-ttu-id="7a65b-104">Aby uzyskać informacje na temat typów ogólnych, zobacz [typy ogólne w Visual Basic](../../programming-guide/language-features/data-types/generic-types.md).</span><span class="sxs-lookup"><span data-stu-id="7a65b-104">For information on generic types, see [Generic Types in Visual Basic](../../programming-guide/language-features/data-types/generic-types.md).</span></span>  
  
## <a name="using-the-of-keyword"></a><span data-ttu-id="7a65b-105">Za pomocą słowa kluczowego</span><span class="sxs-lookup"><span data-stu-id="7a65b-105">Using the Of Keyword</span></span>  
 <span data-ttu-id="7a65b-106">Poniższy przykład kodu używa `Of` słowa kluczowego do definiowania konspektu klasy, która przyjmuje dwa parametry typu.</span><span class="sxs-lookup"><span data-stu-id="7a65b-106">The following code example uses the `Of` keyword to define the outline of a class that takes two type parameters.</span></span> <span data-ttu-id="7a65b-107">*Ogranicza* `keyType` parametr według <xref:System.IComparable> interfejsu, co oznacza, że kod zużywający musi dostarczyć argument typu, który implementuje <xref:System.IComparable> .</span><span class="sxs-lookup"><span data-stu-id="7a65b-107">It *constrains* the `keyType` parameter by the <xref:System.IComparable> interface, which means the consuming code must supply a type argument that implements <xref:System.IComparable>.</span></span> <span data-ttu-id="7a65b-108">Jest to konieczne, aby `add` procedura mogła wywołać <xref:System.IComparable.CompareTo%2A?displayProperty=nameWithType> metodę.</span><span class="sxs-lookup"><span data-stu-id="7a65b-108">This is necessary so that the `add` procedure can call the <xref:System.IComparable.CompareTo%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="7a65b-109">Aby uzyskać więcej informacji o ograniczeniach, zobacz [Type list](type-list.md).</span><span class="sxs-lookup"><span data-stu-id="7a65b-109">For more information on constraints, see [Type List](type-list.md).</span></span>  
  
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
  
 <span data-ttu-id="7a65b-110">Jeśli poprzednia definicja klasy zostanie ukończona, można utworzyć `dictionary` z niej różne klasy.</span><span class="sxs-lookup"><span data-stu-id="7a65b-110">If you complete the preceding class definition, you can construct a variety of `dictionary` classes from it.</span></span> <span data-ttu-id="7a65b-111">Typy, które dostarczasz, `entryType` i `keyType` określają typ wpisu, który zawiera Klasa, oraz typ klucza, który jest kojarzony z każdym wpisem.</span><span class="sxs-lookup"><span data-stu-id="7a65b-111">The types you supply to `entryType` and `keyType` determine what type of entry the class holds and what type of key it associates with each entry.</span></span> <span data-ttu-id="7a65b-112">Ze względu na ograniczenie należy dostarczyć do `keyType` typu, który implementuje <xref:System.IComparable> .</span><span class="sxs-lookup"><span data-stu-id="7a65b-112">Because of the constraint, you must supply to `keyType` a type that implements <xref:System.IComparable>.</span></span>  
  
 <span data-ttu-id="7a65b-113">Poniższy przykład kodu tworzy obiekt, który zawiera `String` wpisy i kojarzy `Integer` klucz z każdym z nich.</span><span class="sxs-lookup"><span data-stu-id="7a65b-113">The following code example creates an object that holds `String` entries and associates an `Integer` key with each one.</span></span> <span data-ttu-id="7a65b-114">`Integer`implementuje <xref:System.IComparable> i w związku z tym spełnia ograniczenie dotyczące `keyType` .</span><span class="sxs-lookup"><span data-stu-id="7a65b-114">`Integer` implements <xref:System.IComparable> and therefore satisfies the constraint on `keyType`.</span></span>  
  
```vb  
Dim d As New dictionary(Of String, Integer)  
```  
  
 <span data-ttu-id="7a65b-115">`Of`Słowo kluczowe może być używane w tych kontekstach:</span><span class="sxs-lookup"><span data-stu-id="7a65b-115">The `Of` keyword can be used in these contexts:</span></span>  
  
 [<span data-ttu-id="7a65b-116">Class, instrukcja</span><span class="sxs-lookup"><span data-stu-id="7a65b-116">Class Statement</span></span>](class-statement.md)  
  
 [<span data-ttu-id="7a65b-117">Delegate — Instrukcja</span><span class="sxs-lookup"><span data-stu-id="7a65b-117">Delegate Statement</span></span>](delegate-statement.md)  
  
 [<span data-ttu-id="7a65b-118">Function, instrukcja</span><span class="sxs-lookup"><span data-stu-id="7a65b-118">Function Statement</span></span>](function-statement.md)  
  
 [<span data-ttu-id="7a65b-119">Interface, instrukcja</span><span class="sxs-lookup"><span data-stu-id="7a65b-119">Interface Statement</span></span>](interface-statement.md)  
  
 [<span data-ttu-id="7a65b-120">Structure — Instrukcja</span><span class="sxs-lookup"><span data-stu-id="7a65b-120">Structure Statement</span></span>](structure-statement.md)  
  
 [<span data-ttu-id="7a65b-121">Sub, instrukcja</span><span class="sxs-lookup"><span data-stu-id="7a65b-121">Sub Statement</span></span>](sub-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="7a65b-122">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="7a65b-122">See also</span></span>

- <xref:System.IComparable>
- [<span data-ttu-id="7a65b-123">Lista typów</span><span class="sxs-lookup"><span data-stu-id="7a65b-123">Type List</span></span>](type-list.md)
- [<span data-ttu-id="7a65b-124">Typy ogólne w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="7a65b-124">Generic Types in Visual Basic</span></span>](../../programming-guide/language-features/data-types/generic-types.md)
- [<span data-ttu-id="7a65b-125">W</span><span class="sxs-lookup"><span data-stu-id="7a65b-125">In</span></span>](../modifiers/in-generic-modifier.md)
- [<span data-ttu-id="7a65b-126">Określoną</span><span class="sxs-lookup"><span data-stu-id="7a65b-126">Out</span></span>](../modifiers/out-generic-modifier.md)
