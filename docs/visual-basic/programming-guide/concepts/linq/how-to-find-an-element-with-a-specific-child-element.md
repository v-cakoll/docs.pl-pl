---
title: 'Instrukcje: wyszukiwanie elementu o określonym elemencie podrzędnym'
ms.date: 07/20/2015
ms.assetid: b0d0a463-6a85-46c3-8453-ad25b0ecf93c
ms.openlocfilehash: a05504070fe3d2ea5eb6135fd3bf697b131686c6
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84405290"
---
# <a name="how-to-find-an-element-with-a-specific-child-element-visual-basic"></a>Instrukcje: Znajdowanie elementu z określonym elementem podrzędnym (Visual Basic)
W tym temacie pokazano, jak znaleźć konkretny element, który ma element podrzędny o określonej wartości.  
  
## <a name="example"></a>Przykład  
 Przykład znajduje `Test` element, który ma `CommandLine` element podrzędny o wartości "EXAMP2. exe".  
  
 W tym przykładzie zastosowano następujący dokument XML: [przykładowy plik XML: Konfiguracja testu (LINQ to XML)](sample-xml-file-test-configuration-linq-to-xml.md).  
  
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
  
```console  
0002  
0006  
```  
  
 Należy zauważyć, że w tym przykładzie jest stosowana [Właściwość osi elementu podrzędnego XML](../../../language-reference/xml-axis/xml-child-axis-property.md), [Właściwość osi atrybutu XML](../../../language-reference/xml-axis/xml-attribute-axis-property.md)i [właściwość wartość XML](../../../language-reference/xml-axis/xml-value-property.md).  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie pokazano to samo zapytanie dla kodu XML, który znajduje się w przestrzeni nazw. Aby uzyskać więcej informacji, zobacz temat [przestrzenie nazw — omówienie (LINQ to XML) (Visual Basic)](namespaces-overview-linq-to-xml.md).  
  
 W tym przykładzie zastosowano następujący dokument XML: [przykładowy plik XML: Konfiguracja testowa w przestrzeni nazw](sample-xml-file-test-configuration-in-a-namespace.md).  
  
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
  
```console  
0002  
0006  
```  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Xml.Linq.XElement.Attribute%2A>
- <xref:System.Xml.Linq.XContainer.Elements%2A>
- [Zapytania podstawowe (LINQ to XML) (Visual Basic)](basic-queries-linq-to-xml.md)
- [Standardowe operatory zapytań — Omówienie (Visual Basic)](standard-query-operators-overview.md)
- [Operacje projekcji (Visual Basic)](projection-operations.md)
