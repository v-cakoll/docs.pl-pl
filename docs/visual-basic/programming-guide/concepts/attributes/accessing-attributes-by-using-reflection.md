---
title: "Uzyskiwanie dostępu do atrybutów przy użyciu odbicia (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c56e41da-5433-464f-a7bf-2a722e78bc9f
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: a4397200b5a2aa5f337dd3479b5405c1a9f245a8
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="accessing-attributes-by-using-reflection-visual-basic"></a>Uzyskiwanie dostępu do atrybutów przy użyciu odbicia (Visual Basic)
Fakt, że można zdefiniować atrybutów niestandardowych i umieść je w kodzie źródłowym byłoby o niewielkiej wartości bez sposób pobierania tych informacji i działające na nim. Przy użyciu odbicia, można pobierać informacje, która została zdefiniowana z atrybutów niestandardowych. Metoda klucza jest `GetCustomAttributes`, która zwraca tablicę obiektów, które są odpowiedniki środowiska wykonawczego atrybutów kodu źródłowego. Ta metoda ma kilka wersji przeciążona. Aby uzyskać więcej informacji, zobacz <xref:System.Attribute>.  
  
 Specyfikacja atrybutu, takich jak:  
  
```vb  
<Author("P. Ackerman", Version:=1.1)>   
Class SampleClass  
    ' P. Ackerman's code goes here...  
End Class  
```  
  
 odpowiada koncepcyjnie to:  
  
```vb  
Dim anonymousAuthorObject As Author = New Author("P. Ackerman")  
anonymousAuthorObject.version = 1.1  
```  
  
 Jednak kod nie jest wykonywany do momentu `SampleClass` zostanie zapytany o atrybuty. Wywoływanie `GetCustomAttributes` na `SampleClass` powoduje, że `Author` obiektu utworzone i zainicjowane zgodnie z powyższym. Jeśli klasa ma inne atrybuty, inne obiekty atrybutu są zbudowane analogicznie. `GetCustomAttributes`Zwraca `Author` obiektu i innych obiektów atrybutu w tablicy. Można następnie iteracja tej tablicy, określić atrybuty zostały zastosowane w zależności od typu każdy element tablicy i wyodrębnienia informacji z obiektów atrybutu.  
  
## <a name="example"></a>Przykład  
 W tym miejscu jest pełny przykład. Atrybut niestandardowy jest zdefiniowany, stosowane do kilku jednostek i pobrać za pomocą odbicia.  
  
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
 <xref:System.Reflection>  
 <xref:System.Attribute>  
 [Przewodnik programowania w języku Visual Basic](../../../../visual-basic/programming-guide/index.md)  
 [Pobieranie informacji przechowywanych w atrybutach](../../../../standard/attributes/retrieving-information-stored-in-attributes.md)  
 [Odbicie (Visual Basic)](../../../../visual-basic/programming-guide/concepts/reflection.md)  
 [Atrybuty (Visual Basic)](../../../../visual-basic/language-reference/attributes.md)  
 [Tworzenie atrybutów niestandardowych (Visual Basic)](../../../../visual-basic/programming-guide/concepts/attributes/creating-custom-attributes.md)
