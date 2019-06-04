---
title: Programowanie za pomocą węzłów (C#)
ms.date: 07/20/2015
ms.assetid: c38df0f2-c805-431a-93ff-9103a4284c2f
ms.openlocfilehash: 7229b03e1bbb4f7cd861cb946307867b87234a21
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2019
ms.locfileid: "66487299"
---
# <a name="programming-with-nodes-c"></a>Programowanie za pomocą węzłów (C#)
[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] Deweloperzy, którzy trzeba było pisać programy, takie jak edytora XML, system transformacji lub Edytor raportu, często trzeba było pisać programy, które działają na większym poziomie szczegółowości niż elementów i atrybutów. Często muszą wykonywać pracę w węźle poziomu manipulowanie węzły tekstowe, instrukcje przetwarzania i komentarze. Ten temat zawiera informacje na temat programowania na poziomie węzła.  
  
## <a name="node-details"></a>Szczegóły węzła  
 Istnieje kilka szczegóły programowania, który programistą działa na poziomie węzła należy wiedzieć.  
  
### <a name="parent-property-of-children-nodes-of-xdocument-is-set-to-null"></a>Nadrzędny właściwości z podrzędnych węzłów z dokumentem ma wartość Null  
 <xref:System.Xml.Linq.XObject.Parent%2A> Właściwość zawiera element nadrzędny <xref:System.Xml.Linq.XElement>, nie węzła nadrzędnego. Węzły podrzędne <xref:System.Xml.Linq.XDocument> mają Brak elementu nadrzędnego <xref:System.Xml.Linq.XElement>. Jego element nadrzędny jest dokumentu, więc <xref:System.Xml.Linq.XObject.Parent%2A> do tych węzłów zostaje ustalona wartość null.  
  
 Poniższy przykład przedstawia to:  
  
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
  
### <a name="adjacent-text-nodes-are-possible"></a>Sąsiadująco węzły tekstowe jest to możliwe  
 Wiele modeli programowania XML węzły tekstowe sąsiadujących zawsze są scalane. Jest to czasem nazywane normalizacji węzły tekstowe. [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] nie normalizacji węzły tekstowe. Jeśli dodasz dwa węzły tekstowe do tego samego elementu spowoduje w węzły tekstowe sąsiadująco. Jednak jeśli dodasz zawartość określona jako ciąg, a nie jako <xref:System.Xml.Linq.XText> węzła [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] może scalić ciągu z węzłem tekstem.  
  
 Poniższy przykład przedstawia to:  
  
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
  
### <a name="empty-text-nodes-are-possible"></a>Pusty węzły tekstowe jest to możliwe  
 W niektórych modelach programowania XML węzły tekstowe są gwarantowane zawiera pusty ciąg. Przyczyny, dla których jest to, że węzeł tekstowy nie ma wpływu na serializacji XML. Jednak tego samego powodu, że węzły tekstowe sąsiadujących są możliwe, jeśli usuniesz tekst z węzła tekstowego, ustawiając jej wartość na ciąg pusty, sam węzeł tekstu nie zostaną usunięte.  
  
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
  
### <a name="an-empty-text-node-impacts-serialization"></a>Pusty węzeł tekstowy wpływa na serializacji  
 Jeśli element zawiera tylko tekst węzeł podrzędny, która jest pusta, jest serializowany ze składnią długich znaczników: `<Child></Child>`. Jeśli element zawiera bez jakiejkolwiek węzłów podrzędnych, jest serializowany ze składnią krótki tagu: `<Child />`.  
  
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
  
### <a name="namespaces-are-attributes-in-the-linq-to-xml-tree"></a>Przestrzenie nazw są atrybuty w składniku LINQ to drzewa XML  
 Mimo że deklaracje przestrzeni nazw mają identyczne składni atrybutów, w niektórych interfejsach programowania, takich jak XSLT i XPath, deklaracje przestrzeni nazw nie są uwzględniane jako atrybuty. Jednak w [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], przestrzenie nazw są przechowywane jako <xref:System.Xml.Linq.XAttribute> obiektów w drzewie XML. Jeśli iterację atrybuty dla elementu, który zawiera deklarację przestrzeni nazw deklaracji przestrzeni nazw zostanie wyświetlona jako jeden z elementów w kolekcji zwrócone.  
  
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
  
### <a name="xpath-axis-methods-do-not-return-child-white-space-of-xdocument"></a>Metody osi XPath nie zwracają podrzędnych biały znak z dokumentem  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] Umożliwia węzły tekstowe podrzędne <xref:System.Xml.Linq.XDocument>, tak długo, jak węzły tekstowe, zawierać samych znaków odstępu. Jednak model obiektów XPath nie zawiera biały znak jako węzły podrzędne dokumentu, więc podczas iteracji elementów podrzędnych <xref:System.Xml.Linq.XDocument> przy użyciu <xref:System.Xml.Linq.XContainer.Nodes%2A> osi, węzły tekstowe białe miejsca zostaną zwrócone. Jednak podczas iteracji przez elementy podrzędne <xref:System.Xml.Linq.XDocument> przy użyciu metody XPath osi, węzły tekstowe białe miejsca nie zostaną zwrócone.  
  
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
 Podczas iteracji węzłów podrzędnych <xref:System.Xml.Linq.XDocument>, nie będą widzieć obiekt deklaracji XML. Jest właściwości dokumentu nie elementem podrzędnym go.  
  
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
  