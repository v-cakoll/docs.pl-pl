---
title: Programowanie z węzłamiC#()
ms.date: 07/20/2015
ms.assetid: c38df0f2-c805-431a-93ff-9103a4284c2f
ms.openlocfilehash: 8c4c858cbc1fad4041c2e5ce62ca8a01dd1cfb2c
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2019
ms.locfileid: "70253148"
---
# <a name="programming-with-nodes-c"></a>Programowanie z węzłamiC#()
[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]Deweloperzy, którzy muszą pisać programy takie jak Edytor XML, system transformacji lub moduł zapisujący raport często muszą pisać programy, które pracują na bardziej szczegółowym poziomie niż elementy i atrybuty. Często muszą oni korzystać z poziomu węzła, manipulowania węzłami tekstu, instrukcjami przetwarzania i komentarzami. W tym temacie przedstawiono szczegółowe informacje na temat programowania na poziomie węzła.  
  
## <a name="node-details"></a>Szczegóły węzła  
 Istnieje kilka szczegółów programowania, które programista pracuje na poziomie węzła.  
  
### <a name="parent-property-of-children-nodes-of-xdocument-is-set-to-null"></a>Właściwość nadrzędna węzłów podrzędnych klasy XDocument ma wartość null.  
 Właściwość zawiera element nadrzędny <xref:System.Xml.Linq.XElement>, a nie węzeł nadrzędny. <xref:System.Xml.Linq.XObject.Parent%2A> Węzły <xref:System.Xml.Linq.XDocument> podrzędne nie mają elementu nadrzędnego <xref:System.Xml.Linq.XElement>. Ich element nadrzędny jest dokumentem, więc <xref:System.Xml.Linq.XObject.Parent%2A> właściwość dla tych węzłów ma ustawioną wartość null.  
  
 Poniższy przykład ilustruje:  
  
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
  
### <a name="adjacent-text-nodes-are-possible"></a>Możliwe są sąsiadujące węzły tekstowe  
 W wielu modelach programowania XML sąsiadujące węzły tekstowe są zawsze scalane. Jest to czasami nazywane normalizacją węzłów tekstowych. [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]nie normalizuje węzłów tekstowych. Jeśli dodasz dwa węzły tekstowe do tego samego elementu, spowoduje to sąsiednie węzły tekstowe. Jeśli jednak zostanie dodana zawartość określona jako ciąg, a nie jako <xref:System.Xml.Linq.XText> węzeł, program [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] może scalić ciąg z sąsiednim węzłem tekstowym.  
  
 Poniższy przykład ilustruje:  
  
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
  
### <a name="empty-text-nodes-are-possible"></a>Możliwe są puste węzły tekstowe  
 W niektórych modelach programowania XML węzły tekstowe są gwarantowane, że nie zawierają pustego ciągu. Powodem jest to, że taki węzeł tekstowy nie ma wpływu na serializacji XML. Jednak z tego samego powodu, gdy jest możliwy sąsiednie węzły tekstowe, jeśli usuniesz tekst z węzła tekstowego przez ustawienie jego wartości na pusty ciąg, sam węzeł tekstu nie zostanie usunięty.  
  
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
  
### <a name="an-empty-text-node-impacts-serialization"></a>Pusty węzeł tekstowy wpływa na serializację  
 Jeśli element zawiera tylko podrzędny węzeł tekstowy, który jest pusty, jest serializowany z składnią długiego tagu: `<Child></Child>`. Jeśli element nie zawiera żadnych węzłów podrzędnych, zostaje Zserializowany za pomocą składni krótkiej tagu: `<Child />`.  
  
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
  
### <a name="namespaces-are-attributes-in-the-linq-to-xml-tree"></a>Przestrzenie nazw są atrybutami drzewa LINQ to XML  
 Mimo że deklaracje przestrzeni nazw mają identyczną składnię atrybutów, w niektórych interfejsach programowania, takich jak XSLT i XPath, deklaracje przestrzeni nazw nie są uważane za atrybuty. Jednak w programie [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]przestrzenie nazw są przechowywane <xref:System.Xml.Linq.XAttribute> jako obiekty w drzewie XML. W przypadku iteracji przez atrybuty elementu, który zawiera deklarację przestrzeni nazw, Deklaracja przestrzeni nazw będzie widoczna jako jeden z elementów w zwróconej kolekcji.  
  
 Właściwość <xref:System.Xml.Linq.XAttribute.IsNamespaceDeclaration%2A> wskazuje, czy atrybut jest deklaracją przestrzeni nazw.  
  
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
  
### <a name="xpath-axis-methods-do-not-return-child-white-space-of-xdocument"></a>Metody osi XPath nie zwracają białych znaków elementu XDocument  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]zezwala na podrzędne węzły <xref:System.Xml.Linq.XDocument>tekstowe, tak długo, jak węzły tekstowe zawierają tylko biały znak. Jednak model obiektów XPath nie zawiera białych znaków jako węzłów podrzędnych dokumentu, więc gdy przejdziesz do iteracji przez elementy podrzędne <xref:System.Xml.Linq.XDocument> <xref:System.Xml.Linq.XContainer.Nodes%2A> przy użyciu osi, zostaną zwrócone węzły tekstu białych znaków. Jednak podczas iteracji przez elementy podrzędne z <xref:System.Xml.Linq.XDocument> użyciem metody osi XPath, węzły tekstu białych znaków nie zostaną zwrócone.  
  
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
  
### <a name="xdeclaration-objects-are-not-nodes"></a>Obiekty XDeclaration nie są węzłami  
 Gdy przejdziesz do iteracji między węzłami <xref:System.Xml.Linq.XDocument>podrzędnymi, nie zobaczysz obiektu deklaracji XML. Jest to właściwość dokumentu, a nie jego węzeł podrzędny.  
  
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
  