---
title: 'Instrukcje: Znajdowanie elementów podrzędnych z określoną nazwą elementu'
ms.date: 07/20/2015
ms.assetid: 78915518-0d25-4051-ab55-929779989510
ms.openlocfilehash: 1a8aa07a79d05e62e0d5517c1675bc715e87de42
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74344402"
---
# <a name="how-to-find-descendants-with-a-specific-element-name-visual-basic"></a>Instrukcje: Znajdowanie elementów podrzędnych z określoną nazwą elementu (Visual Basic)
Czasami chcesz znaleźć wszystkie elementy podrzędne o określonej nazwie. Można napisać kod do iteracji przez wszystkie elementy podrzędne, ale łatwiej jest użyć osi <xref:System.Xml.Linq.XContainer.Descendants%2A>.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje, jak znaleźć elementy podrzędne na podstawie nazwy elementu.  
  
```vb  
Dim root As XElement = _  
    <root>  
        <para>  
            <r>  
                <t>Some text </t>  
            </r>  
            <n>  
                <r>  
                    <t>that is broken up into </t>  
                </r>  
            </n>  
            <n>  
                <r>  
                    <t>multiple segments.</t>  
                </r>  
            </n>  
        </para>  
    </root>  
  
Dim textSegs As IEnumerable(Of String) = _  
    From seg In root...<t> _  
    Select seg.Value  
  
Dim str As String = textSegs.Aggregate( _  
    New StringBuilder, _  
    Function(sb, i) sb.Append(i), _  
    Function(sb) sb.ToString)  
  
Console.WriteLine(str)  
```  
  
 Ten kod generuje następujące dane wyjściowe:  
  
```console  
Some text that is broken up into multiple segments.  
```  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie pokazano to samo zapytanie dla kodu XML, który znajduje się w przestrzeni nazw. Aby uzyskać więcej informacji, zobacz temat [przestrzenie nazw — omówienie (LINQ to XML) (Visual Basic)](namespaces-overview-linq-to-xml.md).  
  
```vb  
Imports <xmlns='http://www.adatum.com'>  
  
Module Module1  
    Sub Main()  
        Dim root As XElement = _  
            <root>  
                <para>  
                    <r>  
                        <t>Some text </t>  
                    </r>  
                    <n>  
                        <r>  
                            <t>that is broken up into </t>  
                        </r>  
                    </n>  
                    <n>  
                        <r>  
                            <t>multiple segments.</t>  
                        </r>  
                    </n>  
                </para>  
            </root>  
  
        Dim textSegs As IEnumerable(Of String) = _  
            From seg In root...<t> _  
            Select seg.Value  
  
        Dim str As String = textSegs.Aggregate( _  
            New StringBuilder, _  
            Function(sb, i) sb.Append(i), _  
            Function(sb) sb.ToString)  
  
        Console.WriteLine(str)  
    End Sub  
End Module  
```  
  
 Ten kod generuje następujące dane wyjściowe:  
  
```console  
Some text that is broken up into multiple segments.  
```  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Xml.Linq.XContainer.Descendants%2A>
- [Zapytania podstawowe (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/basic-queries-linq-to-xml.md)
