---
title: "Porady: znajdowanie Element z elementu podrzędnego określonego (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b0d0a463-6a85-46c3-8453-ad25b0ecf93c
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: e6ddb35e954d709548c6b32475f37454015e0a98
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-find-an-element-with-a-specific-child-element-visual-basic"></a>Porady: znajdowanie Element z elementu podrzędnego określonego (Visual Basic)
W tym temacie pokazano, jak można znaleźć określonego elementu, który ma element podrzędny o określonej wartości.  
  
## <a name="example"></a>Przykład  
 W przykładzie są znajdowane `Test` element, który ma `CommandLine` element podrzędny o wartości "Examp2.EXE".  
  
 W tym przykładzie użyto następujących dokumentu XML: [przykładowego pliku XML: konfiguracji testu (LINQ do XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-test-configuration-linq-to-xml.md).  
  
```vb  
Dim root As XElement = XElement.Load("TestConfig.xml")  
Dim tests As IEnumerable(Of XElement) = _  
    From el In root.<Test> _  
    Where el.<CommandLine>.Value = "Examp2.EXE" _  
    Select el  
For Each el as XElement In tests  
    Console.WriteLine(el.@TestId)  
Next  
```  
  
 Ten kod generuje następujące dane wyjściowe:  
  
```  
0002  
0006  
```  
  
 Należy pamiętać, że w tym przykładzie użyto [właściwości osi elementu podrzędnego XML](../../../../visual-basic/language-reference/xml-axis/xml-child-axis-property.md), [właściwości osi atrybutu XML](../../../../visual-basic/language-reference/xml-axis/xml-attribute-axis-property.md)i [właściwość wartości XML](../../../../visual-basic/language-reference/xml-axis/xml-value-property.md).  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie pokazano tego samego zapytania w formacie XML, który znajduje się w przestrzeni nazw. Aby uzyskać więcej informacji, zobacz [Praca z przestrzeni nazw XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/working-with-xml-namespaces.md).  
  
 W tym przykładzie użyto następujących dokumentu XML: [przykładowego pliku XML: Konfiguracja testu w Namespace](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-test-configuration-in-a-namespace.md).  
  
```vb  
Imports <xmlns='http://www.adatum.com'>  
  
Module Module1  
    Sub Main()  
        Dim root As XElement = XElement.Load("TestConfigInNamespace.xml")  
        Dim tests As IEnumerable(Of XElement) = _  
            From el In root.<Test> _  
            Where el.<CommandLine>.Value = "Examp2.EXE" _  
            Select el  
        For Each el As XElement In tests  
            Console.WriteLine(el.@TestId)  
        Next  
    End Sub  
End Module  
```  
  
 Ten kod generuje następujące dane wyjściowe:  
  
```  
0002  
0006  
```  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Xml.Linq.XElement.Attribute%2A>  
 <xref:System.Xml.Linq.XContainer.Elements%2A>  
 [Podstawowe zapytania (LINQ do XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/basic-queries-linq-to-xml.md)  
 [Operatory standardowe zapytań — omówienie (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)  
 [Operacje rzutowania (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/projection-operations.md)
