---
title: Programowanie z węzłami (Visual Basic)
ms.date: 07/20/2015
ms.assetid: d8422a9b-dd37-44a3-8aac-2237ed9561e0
ms.openlocfilehash: 871755ef0293513f07c60b1d5735c47692163b78
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="programming-with-nodes-visual-basic"></a>Programowanie z węzłami (Visual Basic)
[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] Deweloperzy, którzy musisz zapisywać programów, takich jak edytor XML, system transformacji lub zapisywania raportu często konieczne pisania programów, które działają na poziomie szczegółowości większą niż elementów i atrybutów. Często muszą pracować na poziomie węzła manipulowanie węzły tekstowe, przetwarzanie instrukcji i komentarze. Ten temat zawiera niektóre szczegóły na temat programowania na poziomie węzła.  
  
## <a name="node-details"></a>Szczegóły dotyczące węzła  
 Istnieje szereg szczegóły programowania w języku, który wiedzieć programisty, praca na poziomie węzła.  
  
### <a name="parent-property-of-children-nodes-of-xdocument-is-set-to-null"></a>Nadrzędny właściwości z elementów podrzędnych węzłów z klasy XDocument ma wartość Null  
 <xref:System.Xml.Linq.XObject.Parent%2A> Właściwość zawiera nadrzędnego <xref:System.Xml.Linq.XElement>, nie węzła nadrzędnego. Węzły podrzędne <xref:System.Xml.Linq.XDocument> ma nadrzędnej <xref:System.Xml.Linq.XElement>. Macierzysty jest dokumentu, więc <xref:System.Xml.Linq.XObject.Parent%2A> ustawiono właściwość dla tych węzłów na wartość null.  
  
 W poniższym przykładzie pokazano to:  
  
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
  
### <a name="adjacent-text-nodes-are-possible"></a>Możliwe są sąsiadujących węzły tekstowe  
 Na różne modele programowania XML zawsze są scalane węzłów sąsiadującym tekstem. Jest to czasem nazywane normalizacji węzły tekstowe. [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] nie normalizacji węzły tekstowe. Jeśli dodasz dwa węzły tekstowe do tego samego elementu spowoduje węzłów sąsiadującym tekstem. Jednak jeśli dodasz zawartość określona jako ciąg znaków, a nie jako <xref:System.Xml.Linq.XText> węzła, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] może scalić parametrów z węzłem sąsiadującym tekstem.  
  
 W poniższym przykładzie pokazano to:  
  
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
  
### <a name="empty-text-nodes-are-possible"></a>Możliwe są puste węzły tekstowe  
 W niektórych modeli programowania XML węzły tekstowe dotrą do zawiera pusty ciąg. Przyczyny, dla których jest, że węzeł tekstowy nie ma wpływu na serializacji XML. Jednak z tej samej przyczyny, które są węzłami sąsiadującym tekstem to możliwe, jeśli usuniesz tekst z węzłem tekstowym, ustawiając wartość do ciągu pustego sam węzeł tekst nie zostaną usunięte.  
  
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
  
### <a name="an-empty-text-node-impacts-serialization"></a>Pusty tekst węzła ma wpływ na serializacji  
 Jeśli element zawiera tylko podrzędnego tekstu węzeł, który jest pusta, jest serializowany przy użyciu składni długich znaczników: `<Child></Child>`. Jeśli element zawiera bez jakiejkolwiek węzłów podrzędnych, jest serializowany przy użyciu składni krótkich tag: `<Child />`.  
  
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
  
### <a name="namespaces-are-attributes-in-the-linq-to-xml-tree"></a>Są to obszary nazw atrybutów w składniku LINQ to XML drzewa  
 Mimo że deklaracje przestrzeni nazw ma identyczne składnię atrybutów, w niektórych interfejsów programowania, takie jak XSLT i wyrażenie XPath, deklaracje przestrzeni nazw nie są uważane za jako atrybuty. Jednak w [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], przestrzenie nazw są przechowywane jako <xref:System.Xml.Linq.XAttribute> obiektów w drzewie XML. Jeśli iterację atrybuty elementu, który zawiera deklarację przestrzeni nazw, zobaczysz deklaracji przestrzeni nazw jako jeden z elementów w zwracanej kolekcji.  
  
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
  
### <a name="xpath-axis-methods-do-not-return-child-white-space-of-xdocument"></a>Metody osi XPath zwraca podrzędny biały znak z klasy XDocument  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] Umożliwia tekst węzły podrzędne <xref:System.Xml.Linq.XDocument>, ile węzły tekstowe zawiera tylko biały znak. Jednak model obiektów XPath nie zawiera biały znak jako węzły podrzędne dokumentu, dlatego podczas iteracji elementów podrzędnych <xref:System.Xml.Linq.XDocument> przy użyciu <xref:System.Xml.Linq.XContainer.Nodes%2A> osi, białe węzły tekstowe zostaną zwrócone. Jednak gdy iterację elementów podrzędnych <xref:System.Xml.Linq.XDocument> przy użyciu metod osi XPath, białe węzły tekstowe nie zostaną zwrócone.  
  
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
 Gdy iterację węzłów podrzędnych <xref:System.Xml.Linq.XDocument>, nie będzie mógł przeglądać obiektu deklaracji XML. Jest to właściwość dokumentu nie elementem podrzędnym go.  
  
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
 [Zaawansowane LINQ do XML programowania (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/advanced-linq-to-xml-programming.md)
