---
title: 'Instrukcje: pisanie zapytania, które znajduje elementy na podstawie kontekstu'
ms.date: 07/20/2015
ms.assetid: 0b085290-ddc1-4126-aaa0-e4c95a3d9a09
ms.openlocfilehash: d25c6d47eee2ae092c84c3db3c08c3e21e7d98d6
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74346204"
---
# <a name="how-to-write-a-query-that-finds-elements-based-on-context-visual-basic"></a>Instrukcje: pisanie zapytania, które znajduje elementy na podstawie kontekstu (Visual Basic)
Czasami może być konieczne zapisanie zapytania, które wybiera elementy na podstawie ich kontekstu. Można filtrować na podstawie poprzedzających lub następujących elementów równorzędnych. Można filtrować na podstawie elementów podrzędnych lub nadrzędnych.  
  
 Można to zrobić przez zapisanie zapytania i użycie wyników zapytania w klauzuli `where`. Jeśli konieczne jest pierwsze przetestowanie na wartość null, a następnie przetestowanie wartości, bardziej wygodne jest wykonanie zapytania w klauzuli `let`, a następnie użycie wyników w klauzuli `where`.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład zaznacza wszystkie elementy `p`, po których bezpośrednio następuje element `ul`.  
  
```vb  
Dim doc As XElement = _  
    <Root>  
        <p id='1'/>  
        <ul>abc</ul>  
        <Child>  
            <p id='2'/>  
            <notul/>  
            <p id='3'/>  
            <ul>def</ul>  
            <p id='4'/>  
        </Child>  
        <Child>  
            <p id='5'/>  
            <notul/>  
            <p id='6'/>  
            <ul>abc</ul>  
            <p id='7'/>  
        </Child>  
    </Root>  
  
Dim items As IEnumerable(Of XElement) = _  
    From e In doc...<p> _  
    Let z = e.ElementsAfterSelf().FirstOrDefault() _  
    Where z IsNot Nothing AndAlso z.Name.LocalName = "ul" _  
    Select e  
  
For Each e As XElement In items  
    Console.WriteLine("id = {0}", e.@<id>)  
Next  
```  
  
 Ten kod generuje następujące dane wyjściowe:  
  
```console  
id = 1  
id = 3  
id = 6  
```  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie pokazano to samo zapytanie dla kodu XML, który znajduje się w przestrzeni nazw. Aby uzyskać więcej informacji, zobacz temat [przestrzenie nazw — omówienie (LINQ to XML) (Visual Basic)](namespaces-overview-linq-to-xml.md).  
  
```vb  
Imports <xmlns='http://www.adatum.com'>  
  
Module Module1  
    Sub Main()  
        Dim doc As XElement = _  
            <Root>  
                <p id='1'/>  
                <ul>abc</ul>  
                <Child>  
                    <p id='2'/>  
                    <notul/>  
                    <p id='3'/>  
                    <ul>def</ul>  
                    <p id='4'/>  
                </Child>  
                <Child>  
                    <p id='5'/>  
                    <notul/>  
                    <p id='6'/>  
                    <ul>abc</ul>  
                    <p id='7'/>  
                </Child>  
            </Root>  
  
        Dim items As IEnumerable(Of XElement) = _  
            From e In doc...<p> _  
            Let z = e.ElementsAfterSelf().FirstOrDefault() _  
            Where z IsNot Nothing AndAlso z.Name = GetXmlNamespace().GetName("ul") _  
            Select e  
  
        For Each e As XElement In items  
            Console.WriteLine("id = {0}", e.@<id>)  
        Next  
    End Sub  
End Module  
```  
  
 Ten kod generuje następujące dane wyjściowe:  
  
```console  
id = 1  
id = 3  
id = 6  
```  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Xml.Linq.XElement.Parse%2A>
- <xref:System.Xml.Linq.XContainer.Descendants%2A>
- <xref:System.Xml.Linq.XNode.ElementsAfterSelf%2A>
- <xref:System.Linq.Enumerable.FirstOrDefault%2A>
- [Zapytania podstawowe (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/basic-queries-linq-to-xml.md)
