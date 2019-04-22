---
title: Programowanie za pomocą węzłów (Visual Basic)
ms.date: 07/20/2015
ms.assetid: d8422a9b-dd37-44a3-8aac-2237ed9561e0
ms.openlocfilehash: ed7f460b441a5973c33841f1f53ce4679b627071
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "58817113"
---
# <a name="programming-with-nodes-visual-basic"></a>Programowanie za pomocą węzłów (Visual Basic)
[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] Deweloperzy, którzy trzeba było pisać programy, takie jak edytora XML, system transformacji lub Edytor raportu, często trzeba było pisać programy, które działają na większym poziomie szczegółowości niż elementów i atrybutów. Często muszą wykonywać pracę w węźle poziomu manipulowanie węzły tekstowe, instrukcje przetwarzania i komentarze. Ten temat zawiera informacje na temat programowania na poziomie węzła.  
  
## <a name="node-details"></a>Szczegóły węzła  
 Istnieje kilka szczegóły programowania, który programistą działa na poziomie węzła należy wiedzieć.  
  
### <a name="parent-property-of-children-nodes-of-xdocument-is-set-to-null"></a>Nadrzędny właściwości z podrzędnych węzłów z dokumentem ma wartość Null  
 <xref:System.Xml.Linq.XObject.Parent%2A> Właściwość zawiera element nadrzędny <xref:System.Xml.Linq.XElement>, nie węzła nadrzędnego. Węzły podrzędne <xref:System.Xml.Linq.XDocument> mają Brak elementu nadrzędnego <xref:System.Xml.Linq.XElement>. Jego element nadrzędny jest dokumentu, więc <xref:System.Xml.Linq.XObject.Parent%2A> do tych węzłów zostaje ustalona wartość null.  
  
 Poniższy przykład przedstawia to:  
  
```vb  
Dim doc As XDocument = XDocument.Parse("<!-- a comment --><Root/>")  
Console.WriteLine(doc.Nodes().OfType(Of XComment).First().Parent Is Nothing)  
Console.WriteLine(doc.Root.Parent Is Nothing)  
```  
  
 Ten przykład generuje następujące wyniki:  
  
```  
True  
True  
```  
  
### <a name="adjacent-text-nodes-are-possible"></a>Sąsiadująco węzły tekstowe jest to możliwe  
 Wiele modeli programowania XML węzły tekstowe sąsiadujących zawsze są scalane. Jest to czasem nazywane normalizacji węzły tekstowe. [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] nie normalizacji węzły tekstowe. Jeśli dodasz dwa węzły tekstowe do tego samego elementu spowoduje w węzły tekstowe sąsiadująco. Jednak jeśli dodasz zawartość określona jako ciąg, a nie jako <xref:System.Xml.Linq.XText> węzła [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] może scalić ciągu z węzłem tekstem.  
  
 Poniższy przykład przedstawia to:  
  
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
  
```  
1  
1  
2  
```  
  
### <a name="empty-text-nodes-are-possible"></a>Pusty węzły tekstowe jest to możliwe  
 W niektórych modelach programowania XML węzły tekstowe są gwarantowane zawiera pusty ciąg. Przyczyny, dla których jest to, że węzeł tekstowy nie ma wpływu na serializacji XML. Jednak tego samego powodu, że węzły tekstowe sąsiadujących są możliwe, jeśli usuniesz tekst z węzła tekstowego, ustawiając jej wartość na ciąg pusty, sam węzeł tekstu nie zostaną usunięte.  
  
```vb  
Dim xmlTree As XElement = <Root>Content</Root>  
Dim textNode As XText = xmlTree.Nodes().OfType(Of XText)().First()  
  
' The following line does not cause the removal of the text node.  
textNode.Value = ""  
  
Dim textNode2 As XText = xmlTree.Nodes().OfType(Of XText)().First()  
Console.WriteLine(">>{0}<<", textNode2)  
```  
  
 Ten przykład generuje następujące wyniki:  
  
```  
>><<  
```  
  
### <a name="an-empty-text-node-impacts-serialization"></a>Pusty węzeł tekstowy wpływa na serializacji  
 Jeśli element zawiera tylko tekst węzeł podrzędny, która jest pusta, jest serializowany ze składnią długich znaczników: `<Child></Child>`. Jeśli element zawiera bez jakiejkolwiek węzłów podrzędnych, jest serializowany ze składnią krótki tagu: `<Child />`.  
  
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
  
### <a name="namespaces-are-attributes-in-the-linq-to-xml-tree"></a>Przestrzenie nazw są atrybuty w składniku LINQ to drzewa XML  
 Mimo że deklaracje przestrzeni nazw mają identyczne składni atrybutów, w niektórych interfejsach programowania, takich jak XSLT i XPath, deklaracje przestrzeni nazw nie są uwzględniane jako atrybuty. Jednak w [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], przestrzenie nazw są przechowywane jako <xref:System.Xml.Linq.XAttribute> obiektów w drzewie XML. Jeśli iterację atrybuty dla elementu, który zawiera deklarację przestrzeni nazw deklaracji przestrzeni nazw zostanie wyświetlona jako jeden z elementów w kolekcji zwrócone.  
  
 <xref:System.Xml.Linq.XAttribute.IsNamespaceDeclaration%2A> Właściwość wskazuje, czy atrybut deklaracji przestrzeni nazw.  
  
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
  
```  
xmlns="http://www.adventure-works.com"  IsNamespaceDeclaration:True  
xmlns:fc="www.fourthcoffee.com"  IsNamespaceDeclaration:True  
AnAttribute="abc"  IsNamespaceDeclaration:False  
```  
  
### <a name="xpath-axis-methods-do-not-return-child-white-space-of-xdocument"></a>Metody osi XPath nie zwracają podrzędnych biały znak z dokumentem  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] Umożliwia węzły tekstowe podrzędne <xref:System.Xml.Linq.XDocument>, tak długo, jak węzły tekstowe, zawierać samych znaków odstępu. Jednak model obiektów XPath nie zawiera biały znak jako węzły podrzędne dokumentu, więc podczas iteracji elementów podrzędnych <xref:System.Xml.Linq.XDocument> przy użyciu <xref:System.Xml.Linq.XContainer.Nodes%2A> osi, węzły tekstowe białe miejsca zostaną zwrócone. Jednak podczas iteracji przez elementy podrzędne <xref:System.Xml.Linq.XDocument> przy użyciu metody XPath osi, węzły tekstowe białe miejsca nie zostaną zwrócone.  
  
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
  
```  
3  
0  
```  
  
### <a name="xdeclaration-objects-are-not-nodes"></a>XDeclaration obiekty nie są węzłami  
 Podczas iteracji węzłów podrzędnych <xref:System.Xml.Linq.XDocument>, nie będą widzieć obiekt deklaracji XML. Jest właściwości dokumentu nie elementem podrzędnym go.  
  
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
  
## <a name="see-also"></a>Zobacz także

- [Zaawansowane LINQ to XML programowania (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/advanced-linq-to-xml-programming.md)
