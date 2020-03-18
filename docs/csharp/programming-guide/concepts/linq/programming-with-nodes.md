---
title: Programowanie za pomocą węzłów (C#)
ms.date: 07/20/2015
ms.assetid: c38df0f2-c805-431a-93ff-9103a4284c2f
ms.openlocfilehash: 05c2e95fe97effda7b537a7ac2d8f5780f4e212b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79168317"
---
# <a name="programming-with-nodes-c"></a>Programowanie za pomocą węzłów (C#)
[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]deweloperzy, którzy muszą pisać programy, takie jak edytor XML, system transformacji lub autor raportów często muszą pisać programy, które działają na drobniejszym poziomie szczegółowości niż elementy i atrybuty. Często muszą pracować na poziomie węzła, manipulując węzłami tekstowymi, instrukcjami przetwarzania i komentarzami. W tym temacie przedstawiono kilka szczegółów dotyczących programowania na poziomie węzła.  
  
## <a name="node-details"></a>Szczegóły węzła  
 Istnieje wiele szczegółów programowania, które programista pracujący na poziomie węzła powinien wiedzieć.  
  
### <a name="parent-property-of-children-nodes-of-xdocument-is-set-to-null"></a>Właściwość nadrzędna węzłów podrzędnych XDocument jest ustawiona na null  
 Właściwość <xref:System.Xml.Linq.XObject.Parent%2A> zawiera nadrzędny <xref:System.Xml.Linq.XElement>, a nie węzeł nadrzędny. Podrzędne <xref:System.Xml.Linq.XDocument> węzły <xref:System.Xml.Linq.XElement>nie mają nadrzędnego . Ich element nadrzędny jest <xref:System.Xml.Linq.XObject.Parent%2A> dokumentem, więc właściwość dla tych węzłów jest ustawiona na null.  
  
 Poniższy przykład pokazuje to:  
  
```csharp  
XDocument doc = XDocument.Parse(@"<!-- a comment --><Root/>");  
Console.WriteLine(doc.Nodes().OfType<XComment>().First().Parent == null);  
Console.WriteLine(doc.Root.Parent == null);  
```  
  
 Ten przykład generuje następujące wyniki:  
  
```output  
True  
True  
```  
  
### <a name="adjacent-text-nodes-are-possible"></a>Możliwe są sąsiednie węzły tekstowe  
 W wielu modelach programowania XML sąsiadujące węzły tekstu są zawsze scalane. Jest to czasami nazywane normalizacją węzłów tekstowych. [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]nie normalizuje węzłów tekstowych. Jeśli dodasz dwa węzły tekstu do tego samego elementu, spowoduje to sąsiadujące węzły tekstu. Jeśli jednak dodasz zawartość określoną jako ciąg, <xref:System.Xml.Linq.XText> a [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] nie jako węzeł, może scalić ciąg z sąsiednim węzłem tekstowym.  
  
 Poniższy przykład pokazuje to:  
  
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
  
```output  
1  
1  
2  
```  
  
### <a name="empty-text-nodes-are-possible"></a>Puste węzły tekstowe są możliwe  
 W niektórych modelach programowania XML węzły tekstowe są gwarantowane, że nie zawierają pustego ciągu. Rozumowanie jest, że taki węzeł tekstowy nie ma wpływu na serializacji XML. Jednak z tego samego powodu, że sąsiednie węzły tekstu są możliwe, jeśli usuniesz tekst z węzła tekstowego, ustawiając jego wartość na pusty ciąg, sam węzeł tekstowy nie zostanie usunięty.  
  
```csharp  
XElement xmlTree = new XElement("Root", "Content");  
XText textNode = xmlTree.Nodes().OfType<XText>().First();  
  
// the following line does not cause the removal of the text node.  
textNode.Value = "";  
  
XText textNode2 = xmlTree.Nodes().OfType<XText>().First();  
Console.WriteLine(">>{0}<<", textNode2);
```  
  
 Ten przykład generuje następujące wyniki:  
  
```output  
>><<  
```  
  
### <a name="an-empty-text-node-impacts-serialization"></a>Opróżnianie węzła tekstu ma wpływ na serializację  
 Jeśli element zawiera tylko pusty węzeł tekstu podrzędnego, jest seryjny z `<Child></Child>`składnią znacznika długiego: . Jeśli element nie zawiera żadnych węzłów podrzędnych, jest serializowany `<Child />`z krótką składnią znacznika: .  
  
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
  
### <a name="namespaces-are-attributes-in-the-linq-to-xml-tree"></a>Przestrzenie nazw to atrybuty w drzewie LINQ do XML  
 Mimo że deklaracje obszaru nazw mają identyczną składnię do atrybutów, w niektórych interfejsach programowania, takich jak XSLT i XPath, deklaracje obszaru nazw nie są uważane za atrybuty. Jednak w [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]obszarach nazw <xref:System.Xml.Linq.XAttribute> są przechowywane jako obiekty w drzewie XML. Jeśli iterate za pomocą atrybutów dla elementu, który zawiera deklarację obszaru nazw, zobaczysz deklarację obszaru nazw jako jeden z elementów w kolekcji zwrócone.  
  
 Właściwość <xref:System.Xml.Linq.XAttribute.IsNamespaceDeclaration%2A> wskazuje, czy atrybut jest deklaracją obszaru nazw.  
  
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
  
```output  
xmlns="http://www.adventure-works.com"  IsNamespaceDeclaration:True  
xmlns:fc="www.fourthcoffee.com"  IsNamespaceDeclaration:True  
AnAttribute="abc"  IsNamespaceDeclaration:False  
```  
  
### <a name="xpath-axis-methods-do-not-return-child-white-space-of-xdocument"></a>Metody osi XPath Nie zwracają potoków xdocument  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]umożliwia podrzędne <xref:System.Xml.Linq.XDocument>węzły tekstu , o ile węzły tekstu zawierają tylko biały znak. Jednak model obiektu XPath nie zawiera biały znak jako węzły podrzędne dokumentu, więc <xref:System.Xml.Linq.XDocument> podczas <xref:System.Xml.Linq.XContainer.Nodes%2A> itetenacji przez elementy podrzędne za pomocą osi, białe węzły tekstu znak zostanie zwrócony. Jednak podczas itetenacji za pośrednictwem podrzędnych <xref:System.Xml.Linq.XDocument> metod osi XPath, białe węzły tekstu nie zostaną zwrócone.  
  
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
  
```output  
3  
0  
```  
  
### <a name="xdeclaration-objects-are-not-nodes"></a>XDeclaration Obiekty nie są węzłami  
 Podczas itetentu przez węzły <xref:System.Xml.Linq.XDocument>podrzędne , nie będzie widać obiektu deklaracji XML. Jest to właściwość dokumentu, a nie jego podrzędny węzeł.  
  
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
  
```output  
<?xml version="1.0" encoding="utf-8" standalone="yes"?>  
<Root />  
1  
```  
  