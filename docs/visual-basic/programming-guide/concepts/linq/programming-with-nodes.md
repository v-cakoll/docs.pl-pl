---
title: Programowanie z węzłami (Visual Basic)
ms.date: 07/20/2015
ms.assetid: d8422a9b-dd37-44a3-8aac-2237ed9561e0
ms.openlocfilehash: 2a331d77f1c54f6428d36b6ccb403dcc01094c98
ms.sourcegitcommit: 8a0fe8a2227af612f8b8941bdb8b19d6268748e7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/03/2019
ms.locfileid: "71834931"
---
# <a name="programming-with-nodes-visual-basic"></a>Programowanie z węzłami (Visual Basic)
[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] deweloperów, którzy muszą pisać programy takie jak Edytor XML, system transformacji lub moduł zapisujący raport często muszą pisać programy, które pracują na bardziej szczegółowym poziomie niż elementy i atrybuty. Często muszą oni korzystać z poziomu węzła, manipulowania węzłami tekstu, instrukcjami przetwarzania i komentarzami. W tym temacie przedstawiono szczegółowe informacje na temat programowania na poziomie węzła.  
  
## <a name="node-details"></a>Szczegóły węzła  
 Istnieje kilka szczegółów programowania, które programista pracuje na poziomie węzła.  
  
### <a name="parent-property-of-children-nodes-of-xdocument-is-set-to-null"></a>Właściwość nadrzędna węzłów podrzędnych klasy XDocument ma wartość null.  
 Właściwość <xref:System.Xml.Linq.XObject.Parent%2A> zawiera nadrzędny <xref:System.Xml.Linq.XElement>, a nie węzeł nadrzędny. Węzły podrzędne <xref:System.Xml.Linq.XDocument> nie mają elementu nadrzędnego <xref:System.Xml.Linq.XElement>. Ich element nadrzędny jest dokumentem, więc Właściwość <xref:System.Xml.Linq.XObject.Parent%2A> dla tych węzłów ma wartość null.  
  
 Poniższy przykład ilustruje:  
  
```vb  
Dim doc As XDocument = XDocument.Parse("<!-- a comment --><Root/>")  
Console.WriteLine(doc.Nodes().OfType(Of XComment).First().Parent Is Nothing)  
Console.WriteLine(doc.Root.Parent Is Nothing)  
```  
  
 Ten przykład generuje następujące dane wyjściowe:  
  
```console  
True  
True  
```  
  
### <a name="adjacent-text-nodes-are-possible"></a>Możliwe są sąsiadujące węzły tekstowe  
 W wielu modelach programowania XML sąsiadujące węzły tekstowe są zawsze scalane. Jest to czasami nazywane normalizacją węzłów tekstowych. [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] nie normalizuje węzłów tekstowych. Jeśli dodasz dwa węzły tekstowe do tego samego elementu, spowoduje to sąsiednie węzły tekstowe. Jeśli jednak zostanie dodana zawartość określona jako ciąg, a nie jako węzeł <xref:System.Xml.Linq.XText>, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] może scalić ciąg z sąsiednim węzłem tekstowym.  
  
 Poniższy przykład ilustruje:  
  
```vb  
Dim xmlTree As XElement = <Root>Content</Root>  
Console.WriteLine(xmlTree.Nodes().OfType(Of XText)().Count())  
  
' This does not add a new text node.  
xmlTree.Add("new content")  
Console.WriteLine(xmlTree.Nodes().OfType(Of XText)().Count())  
  
'// This does add a new, adjacent text node.  
xmlTree.Add(New XText("more text"))  
Console.WriteLine(xmlTree.Nodes().OfType(Of XText)().Count())  
```  
  
 Ten przykład generuje następujące dane wyjściowe:  
  
```console  
1  
1  
2  
```  
  
### <a name="empty-text-nodes-are-possible"></a>Możliwe są puste węzły tekstowe  
 W niektórych modelach programowania XML węzły tekstowe są gwarantowane, że nie zawierają pustego ciągu. Powodem jest to, że taki węzeł tekstowy nie ma wpływu na serializacji XML. Jednak z tego samego powodu, gdy jest możliwy sąsiednie węzły tekstowe, jeśli usuniesz tekst z węzła tekstowego przez ustawienie jego wartości na pusty ciąg, sam węzeł tekstu nie zostanie usunięty.  
  
```vb  
Dim xmlTree As XElement = <Root>Content</Root>  
Dim textNode As XText = xmlTree.Nodes().OfType(Of XText)().First()  
  
' The following line does not cause the removal of the text node.  
textNode.Value = ""  
  
Dim textNode2 As XText = xmlTree.Nodes().OfType(Of XText)().First()  
Console.WriteLine(">>{0}<<", textNode2)  
```  
  
 Ten przykład generuje następujące dane wyjściowe:  
  
```console  
>><<  
```  
  
### <a name="an-empty-text-node-impacts-serialization"></a>Pusty węzeł tekstowy wpływa na serializację  
 Jeśli element zawiera tylko podrzędny węzeł tekstowy, który jest pusty, jest serializowany z składnią długiego tagu: `<Child></Child>`. Jeśli element nie zawiera żadnych węzłów podrzędnych, zostaje Zserializowany za pomocą składni krótkiej tagu: `<Child />`.  
  
```vb  
Dim child1 As XElement = New XElement("Child1", _  
    New XText("") _  
)  
Dim child2 As XElement = New XElement("Child2")  
Console.WriteLine(child1)  
Console.WriteLine(child2)  
```  
  
 Ten przykład generuje następujące dane wyjściowe:  
  
```xml  
<Child1></Child1>  
<Child2 />  
```  
  
### <a name="namespaces-are-attributes-in-the-linq-to-xml-tree"></a>Przestrzenie nazw są atrybutami drzewa LINQ to XML  
 Mimo że deklaracje przestrzeni nazw mają identyczną składnię atrybutów, w niektórych interfejsach programowania, takich jak XSLT i XPath, deklaracje przestrzeni nazw nie są uważane za atrybuty. Jednak w [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] przestrzenie nazw są przechowywane jako obiekty <xref:System.Xml.Linq.XAttribute> w drzewie XML. W przypadku iteracji przez atrybuty elementu, który zawiera deklarację przestrzeni nazw, Deklaracja przestrzeni nazw będzie widoczna jako jeden z elementów w zwróconej kolekcji.  
  
 Właściwość <xref:System.Xml.Linq.XAttribute.IsNamespaceDeclaration%2A> wskazuje, czy atrybut jest deklaracją przestrzeni nazw.  
  
```vb  
Dim root As XElement = _   
<Root  
    xmlns='http://www.adventure-works.com'  
    xmlns:fc='www.fourthcoffee.com'  
    AnAttribute='abc'/>  
For Each att As XAttribute In root.Attributes()  
    Console.WriteLine("{0}  IsNamespaceDeclaration:{1}", att, _  
                      att.IsNamespaceDeclaration)  
Next  
```  
  
 Ten przykład generuje następujące dane wyjściowe:  
  
```console  
xmlns="http://www.adventure-works.com"  IsNamespaceDeclaration:True  
xmlns:fc="www.fourthcoffee.com"  IsNamespaceDeclaration:True  
AnAttribute="abc"  IsNamespaceDeclaration:False  
```  
  
### <a name="xpath-axis-methods-do-not-return-child-white-space-of-xdocument"></a>Metody osi XPath nie zwracają białych znaków elementu XDocument  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] zezwala na podrzędne węzły tekstowe <xref:System.Xml.Linq.XDocument>, tak długo, jak węzły tekstowe zawierają tylko biały znak. Jednak model obiektów XPath nie zawiera białych znaków jako węzłów podrzędnych dokumentu, więc gdy przejdziesz do iteracji przez elementy podrzędne <xref:System.Xml.Linq.XDocument> przy użyciu osi <xref:System.Xml.Linq.XContainer.Nodes%2A>, zostaną zwrócone wolne węzły tekstu. Jednak podczas iteracji przez elementy podrzędne <xref:System.Xml.Linq.XDocument> przy użyciu metod osi XPath, węzły tekstu odstępu nie zostaną zwrócone.  
  
```vb  
' Create a document with some white space child nodes of the document.  
Dim root As XDocument = XDocument.Parse( _  
"<?xml version='1.0' encoding='utf-8' standalone='yes'?>" & _  
vbNewLine & "<Root/>" & vbNewLine & "<!--a comment-->" & vbNewLine, _  
LoadOptions.PreserveWhitespace)  
  
' Count the white space child nodes using LINQ to XML.  
Console.WriteLine(root.Nodes().OfType(Of XText)().Count())  
  
' Count the white space child nodes using XPathEvaluate.  
Dim nodes As IEnumerable = CType(root.XPathEvaluate("text()"), IEnumerable)  
Console.WriteLine(nodes.OfType(Of XText)().Count())  
```  
  
 Ten przykład generuje następujące dane wyjściowe:  
  
```console  
3  
0  
```  
  
### <a name="xdeclaration-objects-are-not-nodes"></a>Obiekty XDeclaration nie są węzłami  
 Gdy przejdziesz do iteracji węzłów podrzędnych <xref:System.Xml.Linq.XDocument>, obiekt deklaracji XML nie zostanie wyświetlony. Jest to właściwość dokumentu, a nie jego węzeł podrzędny.  
  
```vb  
Dim doc As XDocument = _  
<?xml version='1.0' encoding='utf-8' standalone='yes'?>  
<Root/>  
  
doc.Save("Temp.xml")  
Console.WriteLine(File.ReadAllText("Temp.xml"))  
  
' This shows that there is only one child node of the document.  
Console.WriteLine(doc.Nodes().Count())  
```  
  
 Ten przykład generuje następujące dane wyjściowe:  
  
```xml  
<?xml version="1.0" encoding="utf-8" standalone="yes"?>  
<Root />  
1  
```  
  
## <a name="see-also"></a>Zobacz także

- [Zaawansowane programowanie LINQ to XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/advanced-linq-to-xml-programming.md)
