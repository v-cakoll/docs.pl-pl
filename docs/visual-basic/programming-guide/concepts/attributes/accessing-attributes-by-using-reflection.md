---
title: Uzyskiwanie dostępu do atrybutów przy użyciu odbicia (Visual Basic)
ms.date: 07/20/2015
ms.assetid: c56e41da-5433-464f-a7bf-2a722e78bc9f
ms.openlocfilehash: e5cbce8529cc7554a8edacb2d83dabb73a495eec
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/02/2019
ms.locfileid: "58827656"
---
# <a name="accessing-attributes-by-using-reflection-visual-basic"></a>Uzyskiwanie dostępu do atrybutów przy użyciu odbicia (Visual Basic)
Korzyści bez jakiś sposób pobierania tych informacji i działających na nim mogą być fakt, że można zdefiniować atrybutów niestandardowych i umieść je w kodzie źródłowym. Przy użyciu odbicia, możesz pobrać informacje, które zostało zdefiniowane przy użyciu atrybutów niestandardowych. Metoda klucza jest `GetCustomAttributes`, która zwraca tablicę obiektów, które są odpowiedników środowiska wykonawczego atrybuty kodu źródłowego. Ta metoda ma kilka przeciążone wersje. Aby uzyskać więcej informacji, zobacz <xref:System.Attribute>.  
  
 Specyfikacja atrybutu, takie jak:  
  
```vb  
<Author("P. Ackerman", Version:=1.1)>   
Class SampleClass  
    ' P. Ackerman's code goes here...  
End Class  
```  
  
 jest równoważny to:  
  
```vb  
Dim anonymousAuthorObject As Author = New Author("P. Ackerman")  
anonymousAuthorObject.version = 1.1  
```  
  
 Jednakże, kod nie jest wykonywany do momentu `SampleClass` jest wysyłane zapytanie dla atrybutów. Wywoływanie `GetCustomAttributes` na `SampleClass` powoduje, że `Author` obiekt skonstruowany i zainicjowany, tak jak powyżej. Jeśli klasa ma inne atrybuty, innych atrybutów obiektów są konstruowane podobnie. `GetCustomAttributes` następnie zwraca `Author` obiektów i innych atrybutów obiektów w tablicy. Następnie można wykonać iterację za pośrednictwem tej tablicy, określić, jakie atrybuty zostały zastosowane w oparciu o typ każdego elementu tablicy i wyodrębnianie informacji z obiektów atrybutu.  
  
## <a name="example"></a>Przykład  
 Oto kompletny przykład. Atrybut niestandardowy jest zdefiniowane, stosowania do kilku jednostek i pobierane za pomocą odbicia.  
  
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
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Reflection>
- <xref:System.Attribute>
- [Przewodnik programowania w języku Visual Basic](../../../../visual-basic/programming-guide/index.md)
- [Pobieranie informacji przechowywanych w atrybutach](../../../../standard/attributes/retrieving-information-stored-in-attributes.md)
- [Odbicie (Visual Basic)](../../../../visual-basic/programming-guide/concepts/reflection.md)
- [Atrybuty (Visual Basic)](../../../../visual-basic/language-reference/attributes.md)
- [Tworzenie atrybutów niestandardowych (Visual Basic)](../../../../visual-basic/programming-guide/concepts/attributes/creating-custom-attributes.md)
