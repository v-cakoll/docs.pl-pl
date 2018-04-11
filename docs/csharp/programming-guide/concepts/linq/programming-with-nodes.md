---
title: Programowanie z węzłami (C#)
ms.custom: ''
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-csharp
ms.topic: article
ms.assetid: c38df0f2-c805-431a-93ff-9103a4284c2f
caps.latest.revision: 3
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 92ec8445123a8b685bd6ea134aca0b792cab6d2d
ms.sourcegitcommit: b750a8e3979749b214e7e10c82efb0a0524dfcb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2018
---
# <a name="programming-with-nodes-c"></a>Programowanie z węzłami (C#)
[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] Deweloperzy, którzy musisz zapisywać programów, takich jak edytor XML, system transformacji lub zapisywania raportu często konieczne pisania programów, które działają na poziomie szczegółowości większą niż elementów i atrybutów. Często muszą pracować na poziomie węzła manipulowanie węzły tekstowe, przetwarzanie instrukcji i komentarze. Ten temat zawiera niektóre szczegóły na temat programowania na poziomie węzła.  
  
## <a name="node-details"></a>Szczegóły dotyczące węzła  
 Istnieje szereg szczegóły programowania w języku, który wiedzieć programisty, praca na poziomie węzła.  
  
### <a name="parent-property-of-children-nodes-of-xdocument-is-set-to-null"></a>Nadrzędny właściwości z elementów podrzędnych węzłów z klasy XDocument ma wartość Null  
 <xref:System.Xml.Linq.XObject.Parent%2A> Właściwość zawiera nadrzędnego <xref:System.Xml.Linq.XElement>, nie węzła nadrzędnego. Węzły podrzędne <xref:System.Xml.Linq.XDocument> ma nadrzędnej <xref:System.Xml.Linq.XElement>. Macierzysty jest dokumentu, więc <xref:System.Xml.Linq.XObject.Parent%2A> ustawiono właściwość dla tych węzłów na wartość null.  
  
 W poniższym przykładzie pokazano to:  
  
```csharp  
XDocument doc = XDocument.Parse(@"<!-- a comment --><Root/>");  
Console.WriteLine(doc.Nodes().OfType<XComment>().First().Parent == null);  
Console.WriteLine(doc.Root.Parent == null);  
```  
  
 Ten przykład generuje następujące wyniki:  
  
```  
True  
True  
```  
  
### <a name="adjacent-text-nodes-are-possible"></a>Możliwe są sąsiadujących węzły tekstowe  
 Na różne modele programowania XML zawsze są scalane węzłów sąsiadującym tekstem. Jest to czasem nazywane normalizacji węzły tekstowe. [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] nie normalizacji węzły tekstowe. Jeśli dodasz dwa węzły tekstowe do tego samego elementu spowoduje węzłów sąsiadującym tekstem. Jednak jeśli dodasz zawartość określona jako ciąg znaków, a nie jako <xref:System.Xml.Linq.XText> węzła, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] może scalić parametrów z węzłem sąsiadującym tekstem.  
  
 W poniższym przykładzie pokazano to:  
  
```csharp  
XElement xmlTree = new XElement("Root", "Content");  
  
Console.WriteLine(xmlTree.Nodes().OfType<XText>().Count());  
  
// this does not add a new text node  
xmlTree.Add("new content");  
Console.WriteLine(xmlTree.Nodes().OfType<XText>().Count());  
  
// this does add a new, adjacent text node  
xmlTree.Add(new XText("more text"));  
Console.WriteLine(xmlTree.Nodes().OfType<XText>().Count());  
```  
  
 Ten przykład generuje następujące wyniki:  
  
```  
1  
1  
2  
```  
  
### <a name="empty-text-nodes-are-possible"></a>Możliwe są puste węzły tekstowe  
 W niektórych modeli programowania XML węzły tekstowe dotrą do zawiera pusty ciąg. Przyczyny, dla których jest, że węzeł tekstowy nie ma wpływu na serializacji XML. Jednak z tej samej przyczyny, które są węzłami sąsiadującym tekstem to możliwe, jeśli usuniesz tekst z węzłem tekstowym, ustawiając wartość do ciągu pustego sam węzeł tekst nie zostaną usunięte.  
  
```csharp  
XElement xmlTree = new XElement("Root", "Content");  
XText textNode = xmlTree.Nodes().OfType<XText>().First();  
  
// the following line does not cause the removal of the text node.  
textNode.Value = "";  
  
XText textNode2 = xmlTree.Nodes().OfType<XText>().First();  
Console.WriteLine(">>{0}<<", textNode2);   
```  
  
 Ten przykład generuje następujące wyniki:  
  
```  
>><<  
```  
  
### <a name="an-empty-text-node-impacts-serialization"></a>Pusty tekst węzła ma wpływ na serializacji  
 Jeśli element zawiera tylko podrzędnego tekstu węzeł, który jest pusta, jest serializowany przy użyciu składni długich znaczników: `<Child></Child>`. Jeśli element zawiera bez jakiejkolwiek węzłów podrzędnych, jest serializowany przy użyciu składni krótkich tag: `<Child />`.  
  
```csharp  
XElement child1 = new XElement("Child1",  
    new XText("")  
);  
XElement child2 = new XElement("Child2");  
Console.WriteLine(child1);  
Console.WriteLine(child2);   
```  
  
 Ten przykład generuje następujące wyniki:  
  
```xml  
<Child1></Child1>  
<Child2 />  
```  
  
### <a name="namespaces-are-attributes-in-the-linq-to-xml-tree"></a>Są to obszary nazw atrybutów w składniku LINQ to XML drzewa  
 Mimo że deklaracje przestrzeni nazw ma identyczne składnię atrybutów, w niektórych interfejsów programowania, takie jak XSLT i wyrażenie XPath, deklaracje przestrzeni nazw nie są uważane za jako atrybuty. Jednak w [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], przestrzenie nazw są przechowywane jako <xref:System.Xml.Linq.XAttribute> obiektów w drzewie XML. Jeśli iterację atrybuty elementu, który zawiera deklarację przestrzeni nazw, zobaczysz deklaracji przestrzeni nazw jako jeden z elementów w zwracanej kolekcji.  
  
 <xref:System.Xml.Linq.XAttribute.IsNamespaceDeclaration%2A> Właściwość wskazuje, czy atrybut deklaracji przestrzeni nazw.  
  
```csharp  
XElement root = XElement.Parse(  
@"<Root  
    xmlns='http://www.adventure-works.com'  
    xmlns:fc='www.fourthcoffee.com'  
    AnAttribute='abc'/>");  
foreach (XAttribute att in root.Attributes())  
    Console.WriteLine("{0}  IsNamespaceDeclaration:{1}", att, att.IsNamespaceDeclaration);  
```  
  
 Ten przykład generuje następujące wyniki:  
  
```  
xmlns="http://www.adventure-works.com"  IsNamespaceDeclaration:True  
xmlns:fc="www.fourthcoffee.com"  IsNamespaceDeclaration:True  
AnAttribute="abc"  IsNamespaceDeclaration:False  
```  
  
### <a name="xpath-axis-methods-do-not-return-child-white-space-of-xdocument"></a>Metody osi XPath zwraca podrzędny biały znak z klasy XDocument  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] Umożliwia tekst węzły podrzędne <xref:System.Xml.Linq.XDocument>, ile węzły tekstowe zawiera tylko biały znak. Jednak model obiektów XPath nie zawiera biały znak jako węzły podrzędne dokumentu, dlatego jeśli iterację elementów podrzędnych <xref:System.Xml.Linq.XDocument> przy użyciu <xref:System.Xml.Linq.XContainer.Nodes%2A> osi, węzły tekstowe biały znak zostanie zwrócony. Jednak gdy iterację elementów podrzędnych <xref:System.Xml.Linq.XDocument> przy użyciu metod osi XPath, węzły tekstowe biały znak nie zostaną zwrócone.  
  
```csharp  
// Create a document with some white-space child nodes of the document.  
XDocument root = XDocument.Parse(  
@"<?xml version='1.0' encoding='utf-8' standalone='yes'?>  
  
<Root/>  
  
<!--a comment-->  
", LoadOptions.PreserveWhitespace);  
  
// count the white-space child nodes using LINQ to XML  
Console.WriteLine(root.Nodes().OfType<XText>().Count());  
  
// count the white-space child nodes using XPathEvaluate  
Console.WriteLine(((IEnumerable)root.XPathEvaluate("text()")).OfType<XText>().Count());   
```  
  
 Ten przykład generuje następujące wyniki:  
  
```  
3  
0  
```  
  
### <a name="xdeclaration-objects-are-not-nodes"></a>XDeclaration obiekty nie są węzłami  
 Gdy iterację węzłów podrzędnych <xref:System.Xml.Linq.XDocument>, nie będzie mógł przeglądać obiektu deklaracji XML. Jest to właściwość dokumentu nie elementem podrzędnym go.  
  
```csharp  
XDocument doc = new XDocument(  
    new XDeclaration("1.0", "utf-8", "yes"),  
    new XElement("Root")  
);  
doc.Save("Temp.xml");  
Console.WriteLine(File.ReadAllText("Temp.xml"));  
  
// this shows that there is only one child node of the document  
Console.WriteLine(doc.Nodes().Count());  
```  
  
 Ten przykład generuje następujące wyniki:  
  
```  
<?xml version="1.0" encoding="utf-8" standalone="yes"?>  
<Root />  
1  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Zaawansowane LINQ do XML programowania (C#)](../../../../csharp/programming-guide/concepts/linq/advanced-linq-to-xml-programming.md)
