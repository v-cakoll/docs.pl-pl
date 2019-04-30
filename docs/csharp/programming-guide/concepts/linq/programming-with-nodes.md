---
title: Programowanie za pomocą węzłów (C#)
ms.date: 07/20/2015
ms.assetid: c38df0f2-c805-431a-93ff-9103a4284c2f
ms.openlocfilehash: 0924d7b1d25a33635cc5140ca32622658b10fa0e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61681926"
---
# <a name="programming-with-nodes-c"></a><span data-ttu-id="fa677-102">Programowanie za pomocą węzłów (C#)</span><span class="sxs-lookup"><span data-stu-id="fa677-102">Programming with Nodes (C#)</span></span>
[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] <span data-ttu-id="fa677-103">Deweloperzy, którzy trzeba było pisać programy, takie jak edytora XML, system transformacji lub Edytor raportu, często trzeba było pisać programy, które działają na większym poziomie szczegółowości niż elementów i atrybutów.</span><span class="sxs-lookup"><span data-stu-id="fa677-103">developers who need to write programs such as an XML editor, a transform system, or a report writer often need to write programs that work at a finer level of granularity than elements and attributes.</span></span> <span data-ttu-id="fa677-104">Często muszą wykonywać pracę w węźle poziomu manipulowanie węzły tekstowe, instrukcje przetwarzania i komentarze.</span><span class="sxs-lookup"><span data-stu-id="fa677-104">They often need to work at the node level, manipulating text nodes, processing instructions, and comments.</span></span> <span data-ttu-id="fa677-105">Ten temat zawiera informacje na temat programowania na poziomie węzła.</span><span class="sxs-lookup"><span data-stu-id="fa677-105">This topic provides some details about programming at the node level.</span></span>  
  
## <a name="node-details"></a><span data-ttu-id="fa677-106">Szczegóły węzła</span><span class="sxs-lookup"><span data-stu-id="fa677-106">Node Details</span></span>  
 <span data-ttu-id="fa677-107">Istnieje kilka szczegóły programowania, który programistą działa na poziomie węzła należy wiedzieć.</span><span class="sxs-lookup"><span data-stu-id="fa677-107">There are a number of details of programming that a programmer working at the node level should know.</span></span>  
  
### <a name="parent-property-of-children-nodes-of-xdocument-is-set-to-null"></a><span data-ttu-id="fa677-108">Nadrzędny właściwości z podrzędnych węzłów z dokumentem ma wartość Null</span><span class="sxs-lookup"><span data-stu-id="fa677-108">Parent Property of Children Nodes of XDocument is Set to Null</span></span>  
 <span data-ttu-id="fa677-109"><xref:System.Xml.Linq.XObject.Parent%2A> Właściwość zawiera element nadrzędny <xref:System.Xml.Linq.XElement>, nie węzła nadrzędnego.</span><span class="sxs-lookup"><span data-stu-id="fa677-109">The <xref:System.Xml.Linq.XObject.Parent%2A> property contains the parent <xref:System.Xml.Linq.XElement>, not the parent node.</span></span> <span data-ttu-id="fa677-110">Węzły podrzędne <xref:System.Xml.Linq.XDocument> mają Brak elementu nadrzędnego <xref:System.Xml.Linq.XElement>.</span><span class="sxs-lookup"><span data-stu-id="fa677-110">Child nodes of <xref:System.Xml.Linq.XDocument> have no parent <xref:System.Xml.Linq.XElement>.</span></span> <span data-ttu-id="fa677-111">Jego element nadrzędny jest dokumentu, więc <xref:System.Xml.Linq.XObject.Parent%2A> do tych węzłów zostaje ustalona wartość null.</span><span class="sxs-lookup"><span data-stu-id="fa677-111">Their parent is the document, so the <xref:System.Xml.Linq.XObject.Parent%2A> property for those nodes is set to null.</span></span>  
  
 <span data-ttu-id="fa677-112">Poniższy przykład przedstawia to:</span><span class="sxs-lookup"><span data-stu-id="fa677-112">The following example demonstrates this:</span></span>  
  
```csharp  
XDocument doc = XDocument.Parse(@"<!-- a comment --><Root/>");  
Console.WriteLine(doc.Nodes().OfType<XComment>().First().Parent == null);  
Console.WriteLine(doc.Root.Parent == null);  
```  
  
 <span data-ttu-id="fa677-113">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="fa677-113">This example produces the following output:</span></span>  
  
```  
True  
True  
```  
  
### <a name="adjacent-text-nodes-are-possible"></a><span data-ttu-id="fa677-114">Sąsiadująco węzły tekstowe jest to możliwe</span><span class="sxs-lookup"><span data-stu-id="fa677-114">Adjacent Text Nodes are Possible</span></span>  
 <span data-ttu-id="fa677-115">Wiele modeli programowania XML węzły tekstowe sąsiadujących zawsze są scalane.</span><span class="sxs-lookup"><span data-stu-id="fa677-115">In a number of XML programming models, adjacent text nodes are always merged.</span></span> <span data-ttu-id="fa677-116">Jest to czasem nazywane normalizacji węzły tekstowe.</span><span class="sxs-lookup"><span data-stu-id="fa677-116">This is sometimes called normalization of text nodes.</span></span> [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] <span data-ttu-id="fa677-117">nie normalizacji węzły tekstowe.</span><span class="sxs-lookup"><span data-stu-id="fa677-117">does not normalize text nodes.</span></span> <span data-ttu-id="fa677-118">Jeśli dodasz dwa węzły tekstowe do tego samego elementu spowoduje w węzły tekstowe sąsiadująco.</span><span class="sxs-lookup"><span data-stu-id="fa677-118">If you add two text nodes to the same element, it will result in adjacent text nodes.</span></span> <span data-ttu-id="fa677-119">Jednak jeśli dodasz zawartość określona jako ciąg, a nie jako <xref:System.Xml.Linq.XText> węzła [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] może scalić ciągu z węzłem tekstem.</span><span class="sxs-lookup"><span data-stu-id="fa677-119">However, if you add content specified as a string rather than as an <xref:System.Xml.Linq.XText> node, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] might merge the string with an adjacent text node.</span></span>  
  
 <span data-ttu-id="fa677-120">Poniższy przykład przedstawia to:</span><span class="sxs-lookup"><span data-stu-id="fa677-120">The following example demonstrates this:</span></span>  
  
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
  
 <span data-ttu-id="fa677-121">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="fa677-121">This example produces the following output:</span></span>  
  
```  
1  
1  
2  
```  
  
### <a name="empty-text-nodes-are-possible"></a><span data-ttu-id="fa677-122">Pusty węzły tekstowe jest to możliwe</span><span class="sxs-lookup"><span data-stu-id="fa677-122">Empty Text Nodes are Possible</span></span>  
 <span data-ttu-id="fa677-123">W niektórych modelach programowania XML węzły tekstowe są gwarantowane zawiera pusty ciąg.</span><span class="sxs-lookup"><span data-stu-id="fa677-123">In some XML programming models, text nodes are guaranteed to not contain the empty string.</span></span> <span data-ttu-id="fa677-124">Przyczyny, dla których jest to, że węzeł tekstowy nie ma wpływu na serializacji XML.</span><span class="sxs-lookup"><span data-stu-id="fa677-124">The reasoning is that such a text node has no impact on serialization of the XML.</span></span> <span data-ttu-id="fa677-125">Jednak tego samego powodu, że węzły tekstowe sąsiadujących są możliwe, jeśli usuniesz tekst z węzła tekstowego, ustawiając jej wartość na ciąg pusty, sam węzeł tekstu nie zostaną usunięte.</span><span class="sxs-lookup"><span data-stu-id="fa677-125">However, for the same reason that adjacent text nodes are possible, if you remove the text from a text node by setting its value to the empty string, the text node itself will not be deleted.</span></span>  
  
```csharp  
XElement xmlTree = new XElement("Root", "Content");  
XText textNode = xmlTree.Nodes().OfType<XText>().First();  
  
// the following line does not cause the removal of the text node.  
textNode.Value = "";  
  
XText textNode2 = xmlTree.Nodes().OfType<XText>().First();  
Console.WriteLine(">>{0}<<", textNode2);   
```  
  
 <span data-ttu-id="fa677-126">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="fa677-126">This example produces the following output:</span></span>  
  
```  
>><<  
```  
  
### <a name="an-empty-text-node-impacts-serialization"></a><span data-ttu-id="fa677-127">Pusty węzeł tekstowy wpływa na serializacji</span><span class="sxs-lookup"><span data-stu-id="fa677-127">An Empty Text Node Impacts Serialization</span></span>  
 <span data-ttu-id="fa677-128">Jeśli element zawiera tylko tekst węzeł podrzędny, która jest pusta, jest serializowany ze składnią długich znaczników: `<Child></Child>`.</span><span class="sxs-lookup"><span data-stu-id="fa677-128">If an element contains only a child text node that is empty, it is serialized with the long tag syntax: `<Child></Child>`.</span></span> <span data-ttu-id="fa677-129">Jeśli element zawiera bez jakiejkolwiek węzłów podrzędnych, jest serializowany ze składnią krótki tagu: `<Child />`.</span><span class="sxs-lookup"><span data-stu-id="fa677-129">If an element contains no child nodes whatsoever, it is serialized with the short tag syntax: `<Child />`.</span></span>  
  
```csharp  
XElement child1 = new XElement("Child1",  
    new XText("")  
);  
XElement child2 = new XElement("Child2");  
Console.WriteLine(child1);  
Console.WriteLine(child2);   
```  
  
 <span data-ttu-id="fa677-130">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="fa677-130">This example produces the following output:</span></span>  
  
```xml  
<Child1></Child1>  
<Child2 />  
```  
  
### <a name="namespaces-are-attributes-in-the-linq-to-xml-tree"></a><span data-ttu-id="fa677-131">Przestrzenie nazw są atrybuty w składniku LINQ to drzewa XML</span><span class="sxs-lookup"><span data-stu-id="fa677-131">Namespaces are Attributes in the LINQ to XML Tree</span></span>  
 <span data-ttu-id="fa677-132">Mimo że deklaracje przestrzeni nazw mają identyczne składni atrybutów, w niektórych interfejsach programowania, takich jak XSLT i XPath, deklaracje przestrzeni nazw nie są uwzględniane jako atrybuty.</span><span class="sxs-lookup"><span data-stu-id="fa677-132">Even though namespace declarations have identical syntax to attributes, in some programming interfaces, such as XSLT and XPath, namespace declarations are not considered to be attributes.</span></span> <span data-ttu-id="fa677-133">Jednak w [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], przestrzenie nazw są przechowywane jako <xref:System.Xml.Linq.XAttribute> obiektów w drzewie XML.</span><span class="sxs-lookup"><span data-stu-id="fa677-133">However, in [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], namespaces are stored as <xref:System.Xml.Linq.XAttribute> objects in the XML tree.</span></span> <span data-ttu-id="fa677-134">Jeśli iterację atrybuty dla elementu, który zawiera deklarację przestrzeni nazw deklaracji przestrzeni nazw zostanie wyświetlona jako jeden z elementów w kolekcji zwrócone.</span><span class="sxs-lookup"><span data-stu-id="fa677-134">If you iterate through the attributes for an element that contains a namespace declaration, you will see the namespace declaration as one of the items in the returned collection.</span></span>  
  
 <span data-ttu-id="fa677-135"><xref:System.Xml.Linq.XAttribute.IsNamespaceDeclaration%2A> Właściwość wskazuje, czy atrybut deklaracji przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="fa677-135">The <xref:System.Xml.Linq.XAttribute.IsNamespaceDeclaration%2A> property indicates whether an attribute is a namespace declaration.</span></span>  
  
```csharp  
XElement root = XElement.Parse(  
@"<Root  
    xmlns='http://www.adventure-works.com'  
    xmlns:fc='www.fourthcoffee.com'  
    AnAttribute='abc'/>");  
foreach (XAttribute att in root.Attributes())  
    Console.WriteLine("{0}  IsNamespaceDeclaration:{1}", att, att.IsNamespaceDeclaration);  
```  
  
 <span data-ttu-id="fa677-136">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="fa677-136">This example produces the following output:</span></span>  
  
```  
xmlns="http://www.adventure-works.com"  IsNamespaceDeclaration:True  
xmlns:fc="www.fourthcoffee.com"  IsNamespaceDeclaration:True  
AnAttribute="abc"  IsNamespaceDeclaration:False  
```  
  
### <a name="xpath-axis-methods-do-not-return-child-white-space-of-xdocument"></a><span data-ttu-id="fa677-137">Metody osi XPath nie zwracają podrzędnych biały znak z dokumentem</span><span class="sxs-lookup"><span data-stu-id="fa677-137">XPath Axis Methods Do Not Return Child White Space of XDocument</span></span>  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] <span data-ttu-id="fa677-138">Umożliwia węzły tekstowe podrzędne <xref:System.Xml.Linq.XDocument>, tak długo, jak węzły tekstowe, zawierać samych znaków odstępu.</span><span class="sxs-lookup"><span data-stu-id="fa677-138">allows for child text nodes of an <xref:System.Xml.Linq.XDocument>, as long as the text nodes contain only white space.</span></span> <span data-ttu-id="fa677-139">Jednak model obiektów XPath nie zawiera biały znak jako węzły podrzędne dokumentu, więc podczas iteracji elementów podrzędnych <xref:System.Xml.Linq.XDocument> przy użyciu <xref:System.Xml.Linq.XContainer.Nodes%2A> osi, węzły tekstowe białe miejsca zostaną zwrócone.</span><span class="sxs-lookup"><span data-stu-id="fa677-139">However, the XPath object model does not include white space as child nodes of a document, so when you iterate through the children of an <xref:System.Xml.Linq.XDocument> using the <xref:System.Xml.Linq.XContainer.Nodes%2A> axis, white-space text nodes will be returned.</span></span> <span data-ttu-id="fa677-140">Jednak podczas iteracji przez elementy podrzędne <xref:System.Xml.Linq.XDocument> przy użyciu metody XPath osi, węzły tekstowe białe miejsca nie zostaną zwrócone.</span><span class="sxs-lookup"><span data-stu-id="fa677-140">However, when you iterate through the children of an <xref:System.Xml.Linq.XDocument> using the XPath axis methods, white-space text nodes will not be returned.</span></span>  
  
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
  
 <span data-ttu-id="fa677-141">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="fa677-141">This example produces the following output:</span></span>  
  
```  
3  
0  
```  
  
### <a name="xdeclaration-objects-are-not-nodes"></a><span data-ttu-id="fa677-142">XDeclaration obiekty nie są węzłami</span><span class="sxs-lookup"><span data-stu-id="fa677-142">XDeclaration Objects are not Nodes</span></span>  
 <span data-ttu-id="fa677-143">Podczas iteracji węzłów podrzędnych <xref:System.Xml.Linq.XDocument>, nie będą widzieć obiekt deklaracji XML.</span><span class="sxs-lookup"><span data-stu-id="fa677-143">When you iterate through the children nodes of an <xref:System.Xml.Linq.XDocument>, you will not see the XML declaration object.</span></span> <span data-ttu-id="fa677-144">Jest właściwości dokumentu nie elementem podrzędnym go.</span><span class="sxs-lookup"><span data-stu-id="fa677-144">It is a property of the document, not a child node of it.</span></span>  
  
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
  
 <span data-ttu-id="fa677-145">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="fa677-145">This example produces the following output:</span></span>  
  
```  
<?xml version="1.0" encoding="utf-8" standalone="yes"?>  
<Root />  
1  
```  
  
## <a name="see-also"></a><span data-ttu-id="fa677-146">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="fa677-146">See also</span></span>

- [<span data-ttu-id="fa677-147">Zaawansowane LINQ to XML programowania (C#)</span><span class="sxs-lookup"><span data-stu-id="fa677-147">Advanced LINQ to XML Programming (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/advanced-linq-to-xml-programming.md)
