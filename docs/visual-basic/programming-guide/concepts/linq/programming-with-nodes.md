---
title: Programowanie za pomocą węzłów
ms.date: 07/20/2015
ms.assetid: d8422a9b-dd37-44a3-8aac-2237ed9561e0
ms.openlocfilehash: b2c9022cb57cf122af47bbe6d1a7fe2b4d41327c
ms.sourcegitcommit: 43d10ef65f0f1fd6c3b515e363bde11a3fcd8d6d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/04/2020
ms.locfileid: "78266966"
---
# <a name="programming-with-nodes-visual-basic"></a>Programowanie za pomocą węzłów (Visual Basic)
[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]deweloperzy, którzy muszą pisać programy, takie jak edytor XML, system przekształcania lub moduł zapisujący raporty, często muszą pisać programy, które działają na drobniejszym poziomie szczegółowości niż elementy i atrybuty. Często muszą pracować na poziomie węzła, manipulując węzłami tekstowymi, przetwarzając instrukcje i komentarze. Ten temat zawiera szczegółowe informacje na temat programowania na poziomie węzła.  
  
## <a name="node-details"></a>Szczegóły węzła  
 Istnieje wiele szczegółów programowania, które programista pracujący na poziomie węzła powinien wiedzieć.  
  
### <a name="parent-property-of-children-nodes-of-xdocument-is-set-to-null"></a>Właściwość nadrzędna węzłów podrzędnych XDocument jest ustawiona na wartość null  
 Właściwość <xref:System.Xml.Linq.XObject.Parent%2A> zawiera <xref:System.Xml.Linq.XElement>element nadrzędny, a nie węzeł nadrzędny. Węzły podrzędne nie <xref:System.Xml.Linq.XElement>mają nadrzędnego <xref:System.Xml.Linq.XDocument> . Ich element nadrzędny jest <xref:System.Xml.Linq.XObject.Parent%2A> dokumentem, więc właściwość dla tych węzłów jest ustawiona na wartość null.  
  
 Poniższy przykład pokazuje to:  
  
```vb  
Dim doc As XDocument = XDocument.Parse("<!-- a comment --><Root/>")  
Console.WriteLine(doc.Nodes().OfType(Of XComment).First().Parent Is Nothing)  
Console.WriteLine(doc.Root.Parent Is Nothing)  
```  
  
 Ten przykład generuje następujące wyniki:  
  
```console  
True  
True  
```  
  
### <a name="adjacent-text-nodes-are-possible"></a>Możliwe są sąsiednie węzły tekstowe  
 W wielu modelach programowania XML sąsiednie węzły tekstowe są zawsze scalane. Jest to czasami nazywane normalizacją węzłów tekstowych. [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]nie normalizuje węzłów tekstowych. Jeśli dodasz dwa węzły tekstowe do tego samego elementu, spowoduje to sąsiednie węzły tekstowe. Jednak jeśli dodasz zawartość określoną jako <xref:System.Xml.Linq.XText> ciąg, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] a nie jako węzeł, może scalić ciąg z sąsiednim węzłem tekstowym.  
  
 Poniższy przykład pokazuje to:  
  
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
  
 Ten przykład generuje następujące wyniki:  
  
```console  
1  
1  
2  
```  
  
### <a name="empty-text-nodes-are-possible"></a>Puste węzły tekstowe są możliwe  
 W niektórych modelach programowania XML węzły tekstowe nie zawierają pustego ciągu. Rozumowanie jest, że taki węzeł tekstu nie ma wpływu na serializacji XML. Jednak z tego samego powodu, że sąsiednie węzły tekstu są możliwe, jeśli usuniesz tekst z węzła tekstowego, ustawiając jego wartość na pusty ciąg, sam węzeł tekstowy nie zostanie usunięty.  
  
```vb  
Dim xmlTree As XElement = <Root>Content</Root>  
Dim textNode As XText = xmlTree.Nodes().OfType(Of XText)().First()  
  
' The following line does not cause the removal of the text node.  
textNode.Value = ""  
  
Dim textNode2 As XText = xmlTree.Nodes().OfType(Of XText)().First()  
Console.WriteLine(">>{0}<<", textNode2)  
```  
  
 Ten przykład generuje następujące wyniki:  
  
```console  
>><<  
```  
  
### <a name="an-empty-text-node-impacts-serialization"></a>Pusty węzeł tekstowy wpływa na serializację  
 Jeśli element zawiera tylko pusty węzeł tekstu podrzędnego, jest on serializowany `<Child></Child>`ze składnią długiego znacznika: . Jeśli element nie zawiera żadnych węzłów podrzędnych, jest serializowany ze `<Child />`składnią krótkiego znacznika: .  
  
```vb  
Dim child1 As XElement = New XElement("Child1", _  
    New XText("") _  
)  
Dim child2 As XElement = New XElement("Child2")  
Console.WriteLine(child1)  
Console.WriteLine(child2)  
```  
  
 Ten przykład generuje następujące wyniki:  
  
```xml  
<Child1></Child1>  
<Child2 />  
```  
  
### <a name="namespaces-are-attributes-in-the-linq-to-xml-tree"></a>Przestrzenie nazw są atrybutami w drzewie LINQ do XML  
 Mimo że deklaracje obszaru nazw mają identyczną składnię do atrybutów, w niektórych interfejsach programowania, takich jak XSLT i XPath, deklaracje obszaru nazw nie są uważane za atrybuty. Jednak w [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]obszarze nazw są <xref:System.Xml.Linq.XAttribute> przechowywane jako obiekty w drzewie XML. Jeśli iteracji za pośrednictwem atrybutów dla elementu, który zawiera deklarację obszaru nazw, zostanie wyświetlona deklaracja obszaru nazw jako jeden z elementów w zwróconej kolekcji.  
  
 Właściwość <xref:System.Xml.Linq.XAttribute.IsNamespaceDeclaration%2A> wskazuje, czy atrybut jest deklaracją obszaru nazw.  
  
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
  
 Ten przykład generuje następujące wyniki:  
  
```console  
xmlns="http://www.adventure-works.com"  IsNamespaceDeclaration:True  
xmlns:fc="www.fourthcoffee.com"  IsNamespaceDeclaration:True  
AnAttribute="abc"  IsNamespaceDeclaration:False  
```  
  
### <a name="xpath-axis-methods-do-not-return-child-white-space-of-xdocument"></a>Metody osi XPath nie zwracają podrzędnego białego obszaru XDocument  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]umożliwia podrzędne węzły <xref:System.Xml.Linq.XDocument>tekstowe , o ile węzły tekstowe zawierają tylko biały znak. Jednak model obiektu XPath nie zawiera biały znak jako węzły podrzędne dokumentu, więc po <xref:System.Xml.Linq.XDocument> iteracji przez elementy podrzędne przy użyciu <xref:System.Xml.Linq.XContainer.Nodes%2A> osi, białe węzły tekstu znak zostaną zwrócone. Jednak po iteracji za pośrednictwem <xref:System.Xml.Linq.XDocument> trzęt.  
  
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
  
 Ten przykład generuje następujące wyniki:  
  
```console  
3  
0  
```  
  
### <a name="xdeclaration-objects-are-not-nodes"></a>XDajnopodobne obiekty nie są węzłami  
 Podczas iterowania przez węzły podrzędne <xref:System.Xml.Linq.XDocument>, nie będzie widoczny obiekt deklaracji XML. Jest to właściwość dokumentu, a nie węzeł podrzędny.  
  
```vb  
Dim doc As XDocument = _  
<?xml version='1.0' encoding='utf-8' standalone='yes'?>  
<Root/>  
  
doc.Save("Temp.xml")  
Console.WriteLine(File.ReadAllText("Temp.xml"))  
  
' This shows that there is only one child node of the document.  
Console.WriteLine(doc.Nodes().Count())  
```  
  
 Ten przykład generuje następujące wyniki:  
  
```xml  
<?xml version="1.0" encoding="utf-8" standalone="yes"?>  
<Root />  
1  
```  
  
## <a name="see-also"></a>Zobacz też

- [Zaawansowane programowanie LINQ na XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/advanced-linq-to-xml-programming.md)
