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
# <a name="nameof-operator---visual-basic"></a>Operator NameOf — Visual Basic

Operator `NameOf` uzyskuje nazwę zmiennej, typu lub składowej jako stałą typu String:

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

Jak pokazano w powyższym przykładzie, w przypadku typu i przestrzeni nazw, wygenerowana nazwa zazwyczaj nie jest w [pełni kwalifikowana](~/_csharplang/spec/basic-concepts.md#fully-qualified-names).

Operator `NameOf` jest oceniany w czasie kompilacji i nie ma wpływu w czasie wykonywania.

Możesz użyć operatora `NameOf`, aby kod sprawdzania argumentów był bardziej konserwowany:

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

Operator `NameOf` jest dostępny w Visual Basic 14 i nowszych.

## <a name="see-also"></a>Zobacz także

- [Dokumentacja języka Visual Basic](../index.md)
- [Operatory (Visual Basic)](index.md)
