---
title: Operator NameOf — Visual Basic
description: Dowiedz się, jak używać operatora NameOf w Visual Basic
ms.date: 10/27/2019
helpviewer_keywords:
- NameOf operator [Visual Basic]
ms.openlocfilehash: 8416bb1a1715c1c37b62cac6a9e0b427a9c72547
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/29/2019
ms.locfileid: "73041318"
---
# <a name="nameof-operator---visual-basic"></a><span data-ttu-id="7ea57-103">Operator NameOf — Visual Basic</span><span class="sxs-lookup"><span data-stu-id="7ea57-103">NameOf operator - Visual Basic</span></span>

<span data-ttu-id="7ea57-104">Operator `NameOf` uzyskuje nazwę zmiennej, typu lub składowej jako stałą typu String:</span><span class="sxs-lookup"><span data-stu-id="7ea57-104">The `NameOf` operator obtains the name of a variable, type, or member as the string constant:</span></span>

```vb
Console.WriteLine(NameOf(System.Collections.Generic))  ' output: Generic
Console.WriteLine(NameOf(List(Of Integer)))  ' output: List
Console.WriteLine(NameOf(List(Of Integer).Count))  ' output: Count
Console.WriteLine(NameOf(List(Of Integer).Add))  ' output: Add

Dim numbers As New List(Of Integer) From { 1, 2, 3 }
Console.WriteLine(NameOf(numbers))  ' output: numbers
Console.WriteLine(NameOf(numbers.Count))  ' output: Count
Console.WriteLine(NameOf(numbers.Add))  ' output: Add
```

<span data-ttu-id="7ea57-105">Jak pokazano w powyższym przykładzie, w przypadku typu i przestrzeni nazw, wygenerowana nazwa zazwyczaj nie jest w [pełni kwalifikowana](~/_csharplang/spec/basic-concepts.md#fully-qualified-names).</span><span class="sxs-lookup"><span data-stu-id="7ea57-105">As the preceding example shows, in the case of a type and a namespace, the produced name is usually not [fully qualified](~/_csharplang/spec/basic-concepts.md#fully-qualified-names).</span></span>

<span data-ttu-id="7ea57-106">Operator `NameOf` jest oceniany w czasie kompilacji i nie ma wpływu w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="7ea57-106">The `NameOf` operator is evaluated at compile time, and has no effect at run time.</span></span>

<span data-ttu-id="7ea57-107">Możesz użyć operatora `NameOf`, aby kod sprawdzania argumentów był bardziej konserwowany:</span><span class="sxs-lookup"><span data-stu-id="7ea57-107">You can use the `NameOf` operator to make the argument-checking code more maintainable:</span></span>

```vb
Private _name As String

Public Property Name As String
    Get
        Return _name
    End Get
    Set
        If value Is Nothing Then
            Throw New ArgumentNullException(NameOf(value), $"{NameOf(name)} cannot be null.")
        End If
    End Set
End Property
```

<span data-ttu-id="7ea57-108">Operator `NameOf` jest dostępny w Visual Basic 14 i nowszych.</span><span class="sxs-lookup"><span data-stu-id="7ea57-108">The `NameOf` operator is available in Visual Basic 14 and later.</span></span>

## <a name="see-also"></a><span data-ttu-id="7ea57-109">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="7ea57-109">See also</span></span>

- [<span data-ttu-id="7ea57-110">Dokumentacja języka Visual Basic</span><span class="sxs-lookup"><span data-stu-id="7ea57-110">Visual Basic Language Reference</span></span>](../index.md)
- [<span data-ttu-id="7ea57-111">Operatory (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7ea57-111">Operators (Visual Basic)</span></span>](index.md)
