---
title: Operator NameOf
description: Dowiedz się, jak używać operatora NameOf w Visual Basic
ms.date: 10/27/2019
helpviewer_keywords:
- NameOf operator [Visual Basic]
ms.openlocfilehash: e7dd55bfd98b34449b9f1a35375198598f57b46f
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/25/2019
ms.locfileid: "75347019"
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
