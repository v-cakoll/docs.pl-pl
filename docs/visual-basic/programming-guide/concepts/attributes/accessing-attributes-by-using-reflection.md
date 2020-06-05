---
title: Dostęp do atrybutów przy użyciu odbicia
ms.date: 07/20/2015
ms.assetid: c56e41da-5433-464f-a7bf-2a722e78bc9f
ms.openlocfilehash: c0da5c4ae00eb2bc80b10f63f4bfd39763445e55
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84400761"
---
# <a name="accessing-attributes-by-using-reflection-visual-basic"></a>Uzyskiwanie dostępu do atrybutów przy użyciu odbicia (Visual Basic)

Fakt, że można zdefiniować atrybuty niestandardowe i umieścić je w kodzie źródłowym, będzie miał małą wartość bez konieczności pobierania tych informacji i działania na nich. Za pomocą odbicia można pobrać informacje, które zostały zdefiniowane przy użyciu atrybutów niestandardowych. Kluczową metodą jest `GetCustomAttributes` , która zwraca tablicę obiektów, które są odpowiednikami w czasie wykonywania dla atrybutów kodu źródłowego. Ta metoda ma kilka przeciążonych wersji. Aby uzyskać więcej informacji, zobacz <xref:System.Attribute>.

Specyfikacja atrybutu, taka jak:

```vb
<Author("P. Ackerman", Version:=1.1)>
Class SampleClass
    ' P. Ackerman's code goes here...
End Class
```

 jest koncepcyjnie równoważne:

```vb
Dim anonymousAuthorObject As Author = New Author("P. Ackerman")
anonymousAuthorObject.version = 1.1
```

Jednak kod nie jest wykonywany do momentu `SampleClass` zapytania o atrybuty. Wywołanie metody powoduje, że `GetCustomAttributes` `SampleClass` `Author` obiekt ma być skonstruowany i zainicjowany jak powyżej. Jeśli klasa ma inne atrybuty, inne obiekty atrybutów są konstruowane podobnie. `GetCustomAttributes`następnie zwraca `Author` obiekt i wszystkie inne obiekty atrybutu w tablicy. Następnie można wykonać iterację tej tablicy, określić, jakie atrybuty zostały zastosowane na podstawie typu każdego elementu tablicy, i wyodrębnić informacje z obiektów atrybutów.

## <a name="example"></a>Przykład

Oto kompletny przykład. Atrybut niestandardowy jest zdefiniowany, stosowany do kilku jednostek i pobierany za pośrednictwem odbicia.

```vb
' Multiuse attribute
<System.AttributeUsage(System.AttributeTargets.Class Or
                       System.AttributeTargets.Struct,
                       AllowMultiple:=True)>
Public Class Author
    Inherits System.Attribute
    Private name As String
    Public version As Double
    Sub New(ByVal authorName As String)
        name = authorName

        ' Default value
        version = 1.0
    End Sub

    Function GetName() As String
        Return name
    End Function
End Class

' Class with the Author attribute
<Author("P. Ackerman")>
Public Class FirstClass
End Class

' Class without the Author attribute
Public Class SecondClass
End Class

' Class with multiple Author attributes.
<Author("P. Ackerman"), Author("R. Koch", Version:=2.0)>
Public Class ThirdClass
End Class

Class TestAuthorAttribute
    Sub Main()
        PrintAuthorInfo(GetType(FirstClass))
        PrintAuthorInfo(GetType(SecondClass))
        PrintAuthorInfo(GetType(ThirdClass))
    End Sub

    Private Shared Sub PrintAuthorInfo(ByVal t As System.Type)
        System.Console.WriteLine("Author information for {0}", t)

        ' Using reflection
        Dim attrs() As System.Attribute = System.Attribute.GetCustomAttributes(t)

        ' Displaying output
        For Each attr In attrs
            Dim a As Author = CType(attr, Author)
            System.Console.WriteLine("   {0}, version {1:f}", a.GetName(), a.version)
        Next
    End Sub

    ' Output:
    '   Author information for FirstClass
    '     P. Ackerman, version 1.00
    ' Author information for SecondClass
    ' Author information for ThirdClass
    '  R. Koch, version 2.00
    '  P. Ackerman, version 1.00

End Class
```

## <a name="see-also"></a>Zobacz też

- <xref:System.Reflection>
- <xref:System.Attribute>
- [Przewodnik programowania w Visual Basic](../../index.md)
- [Pobieranie informacji przechowywanych w atrybutach](../../../../standard/attributes/retrieving-information-stored-in-attributes.md)
- [Odbicie (Visual Basic)](../reflection.md)
- [Atrybuty (Visual Basic)](../../../language-reference/attributes.md)
- [Tworzenie atrybutów niestandardowych (Visual Basic)](creating-custom-attributes.md)
