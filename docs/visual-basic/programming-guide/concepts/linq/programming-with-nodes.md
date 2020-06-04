---
title: Programowanie za pomocą węzłów
ms.date: 07/20/2015
ms.assetid: d8422a9b-dd37-44a3-8aac-2237ed9561e0
ms.openlocfilehash: 4cae85d99e7e28506faad8ca39347cf8f271718e
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84396379"
---
# <a name="programming-with-nodes-visual-basic"></a><span data-ttu-id="37104-102">Programowanie z węzłami (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="37104-102">Programming with Nodes (Visual Basic)</span></span>
[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="37104-103">Deweloperzy, którzy muszą pisać programy takie jak Edytor XML, system transformacji lub moduł zapisujący raport często muszą pisać programy, które pracują na bardziej szczegółowym poziomie niż elementy i atrybuty.</span><span class="sxs-lookup"><span data-stu-id="37104-103">developers who need to write programs such as an XML editor, a transform system, or a report writer often need to write programs that work at a finer level of granularity than elements and attributes.</span></span> <span data-ttu-id="37104-104">Często muszą oni korzystać z poziomu węzła, manipulowania węzłami tekstu, instrukcjami przetwarzania i komentarzami.</span><span class="sxs-lookup"><span data-stu-id="37104-104">They often need to work at the node level, manipulating text nodes, processing instructions, and comments.</span></span> <span data-ttu-id="37104-105">W tym temacie przedstawiono szczegółowe informacje na temat programowania na poziomie węzła.</span><span class="sxs-lookup"><span data-stu-id="37104-105">This topic provides some details about programming at the node level.</span></span>  
  
## <a name="node-details"></a><span data-ttu-id="37104-106">Szczegóły węzła</span><span class="sxs-lookup"><span data-stu-id="37104-106">Node Details</span></span>  
 <span data-ttu-id="37104-107">Istnieje kilka szczegółów programowania, które programista pracuje na poziomie węzła.</span><span class="sxs-lookup"><span data-stu-id="37104-107">There are a number of details of programming that a programmer working at the node level should know.</span></span>  
  
### <a name="parent-property-of-children-nodes-of-xdocument-is-set-to-null"></a><span data-ttu-id="37104-108">Właściwość nadrzędna węzłów podrzędnych klasy XDocument ma wartość null.</span><span class="sxs-lookup"><span data-stu-id="37104-108">Parent Property of Children Nodes of XDocument is Set to Null</span></span>  
 <span data-ttu-id="37104-109"><xref:System.Xml.Linq.XObject.Parent%2A>Właściwość zawiera element nadrzędny <xref:System.Xml.Linq.XElement> , a nie węzeł nadrzędny.</span><span class="sxs-lookup"><span data-stu-id="37104-109">The <xref:System.Xml.Linq.XObject.Parent%2A> property contains the parent <xref:System.Xml.Linq.XElement>, not the parent node.</span></span> <span data-ttu-id="37104-110">Węzły podrzędne <xref:System.Xml.Linq.XDocument> nie mają elementu nadrzędnego <xref:System.Xml.Linq.XElement> .</span><span class="sxs-lookup"><span data-stu-id="37104-110">Child nodes of <xref:System.Xml.Linq.XDocument> have no parent <xref:System.Xml.Linq.XElement>.</span></span> <span data-ttu-id="37104-111">Ich element nadrzędny jest dokumentem, więc <xref:System.Xml.Linq.XObject.Parent%2A> Właściwość dla tych węzłów ma ustawioną wartość null.</span><span class="sxs-lookup"><span data-stu-id="37104-111">Their parent is the document, so the <xref:System.Xml.Linq.XObject.Parent%2A> property for those nodes is set to null.</span></span>  
  
 <span data-ttu-id="37104-112">Poniższy przykład ilustruje:</span><span class="sxs-lookup"><span data-stu-id="37104-112">The following example demonstrates this:</span></span>  
  
```vb  
Dim doc As XDocument = XDocument.Parse("<!-- a comment --><Root/>")  
Console.WriteLine(doc.Nodes().OfType(Of XComment).First().Parent Is Nothing)  
Console.WriteLine(doc.Root.Parent Is Nothing)  
```  
  
 <span data-ttu-id="37104-113">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="37104-113">This example produces the following output:</span></span>  
  
```console  
True  
True  
```  
  
### <a name="adjacent-text-nodes-are-possible"></a><span data-ttu-id="37104-114">Możliwe są sąsiadujące węzły tekstowe</span><span class="sxs-lookup"><span data-stu-id="37104-114">Adjacent Text Nodes are Possible</span></span>  
 <span data-ttu-id="37104-115">W wielu modelach programowania XML sąsiadujące węzły tekstowe są zawsze scalane.</span><span class="sxs-lookup"><span data-stu-id="37104-115">In a number of XML programming models, adjacent text nodes are always merged.</span></span> <span data-ttu-id="37104-116">Jest to czasami nazywane normalizacją węzłów tekstowych.</span><span class="sxs-lookup"><span data-stu-id="37104-116">This is sometimes called normalization of text nodes.</span></span> [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="37104-117">nie normalizuje węzłów tekstowych.</span><span class="sxs-lookup"><span data-stu-id="37104-117">does not normalize text nodes.</span></span> <span data-ttu-id="37104-118">Jeśli dodasz dwa węzły tekstowe do tego samego elementu, spowoduje to sąsiednie węzły tekstowe.</span><span class="sxs-lookup"><span data-stu-id="37104-118">If you add two text nodes to the same element, it will result in adjacent text nodes.</span></span> <span data-ttu-id="37104-119">Jeśli jednak zostanie dodana zawartość określona jako ciąg, a nie jako <xref:System.Xml.Linq.XText> węzeł, program [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] może scalić ciąg z sąsiednim węzłem tekstowym.</span><span class="sxs-lookup"><span data-stu-id="37104-119">However, if you add content specified as a string rather than as an <xref:System.Xml.Linq.XText> node, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] might merge the string with an adjacent text node.</span></span>  
  
 <span data-ttu-id="37104-120">Poniższy przykład ilustruje:</span><span class="sxs-lookup"><span data-stu-id="37104-120">The following example demonstrates this:</span></span>  
  
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
  
 <span data-ttu-id="37104-121">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="37104-121">This example produces the following output:</span></span>  
  
```console  
1  
1  
2  
```  
  
### <a name="empty-text-nodes-are-possible"></a><span data-ttu-id="37104-122">Możliwe są puste węzły tekstowe</span><span class="sxs-lookup"><span data-stu-id="37104-122">Empty Text Nodes are Possible</span></span>  
 <span data-ttu-id="37104-123">W niektórych modelach programowania XML węzły tekstowe są gwarantowane, że nie zawierają pustego ciągu.</span><span class="sxs-lookup"><span data-stu-id="37104-123">In some XML programming models, text nodes are guaranteed to not contain the empty string.</span></span> <span data-ttu-id="37104-124">Powodem jest to, że taki węzeł tekstowy nie ma wpływu na serializacji XML.</span><span class="sxs-lookup"><span data-stu-id="37104-124">The reasoning is that such a text node has no impact on serialization of the XML.</span></span> <span data-ttu-id="37104-125">Jednak z tego samego powodu, gdy jest możliwy sąsiednie węzły tekstowe, jeśli usuniesz tekst z węzła tekstowego przez ustawienie jego wartości na pusty ciąg, sam węzeł tekstu nie zostanie usunięty.</span><span class="sxs-lookup"><span data-stu-id="37104-125">However, for the same reason that adjacent text nodes are possible, if you remove the text from a text node by setting its value to the empty string, the text node itself will not be deleted.</span></span>  
  
```vb  
Dim xmlTree As XElement = <Root>Content</Root>  
Dim textNode As XText = xmlTree.Nodes().OfType(Of XText)().First()  
  
' The following line does not cause the removal of the text node.  
textNode.Value = ""  
  
Dim textNode2 As XText = xmlTree.Nodes().OfType(Of XText)().First()  
Console.WriteLine(">>{0}<<", textNode2)  
```  
  
 <span data-ttu-id="37104-126">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="37104-126">This example produces the following output:</span></span>  
  
```console  
>><<  
```  
  
### <a name="an-empty-text-node-impacts-serialization"></a><span data-ttu-id="37104-127">Pusty węzeł tekstowy wpływa na serializację</span><span class="sxs-lookup"><span data-stu-id="37104-127">An Empty Text Node Impacts Serialization</span></span>  
 <span data-ttu-id="37104-128">Jeśli element zawiera tylko podrzędny węzeł tekstowy, który jest pusty, jest serializowany z składnią długiego tagu: `<Child></Child>` .</span><span class="sxs-lookup"><span data-stu-id="37104-128">If an element contains only a child text node that is empty, it is serialized with the long tag syntax: `<Child></Child>`.</span></span> <span data-ttu-id="37104-129">Jeśli element nie zawiera żadnych węzłów podrzędnych, zostaje Zserializowany za pomocą składni krótkiej tagu: `<Child />` .</span><span class="sxs-lookup"><span data-stu-id="37104-129">If an element contains no child nodes whatsoever, it is serialized with the short tag syntax: `<Child />`.</span></span>  
  
```vb  
Dim child1 As XElement = New XElement("Child1", _  
    New XText("") _  
)  
Dim child2 As XElement = New XElement("Child2")  
Console.WriteLine(child1)  
Console.WriteLine(child2)  
```  
  
 <span data-ttu-id="37104-130">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="37104-130">This example produces the following output:</span></span>  
  
```xml  
<Child1></Child1>  
<Child2 />  
```  
  
### <a name="namespaces-are-attributes-in-the-linq-to-xml-tree"></a><span data-ttu-id="37104-131">Przestrzenie nazw są atrybutami drzewa LINQ to XML</span><span class="sxs-lookup"><span data-stu-id="37104-131">Namespaces are Attributes in the LINQ to XML Tree</span></span>  
 <span data-ttu-id="37104-132">Mimo że deklaracje przestrzeni nazw mają identyczną składnię atrybutów, w niektórych interfejsach programowania, takich jak XSLT i XPath, deklaracje przestrzeni nazw nie są uważane za atrybuty.</span><span class="sxs-lookup"><span data-stu-id="37104-132">Even though namespace declarations have identical syntax to attributes, in some programming interfaces, such as XSLT and XPath, namespace declarations are not considered to be attributes.</span></span> <span data-ttu-id="37104-133">Jednak w programie [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] przestrzenie nazw są przechowywane jako <xref:System.Xml.Linq.XAttribute> obiekty w drzewie XML.</span><span class="sxs-lookup"><span data-stu-id="37104-133">However, in [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], namespaces are stored as <xref:System.Xml.Linq.XAttribute> objects in the XML tree.</span></span> <span data-ttu-id="37104-134">W przypadku iteracji przez atrybuty elementu, który zawiera deklarację przestrzeni nazw, Deklaracja przestrzeni nazw będzie widoczna jako jeden z elementów w zwróconej kolekcji.</span><span class="sxs-lookup"><span data-stu-id="37104-134">If you iterate through the attributes for an element that contains a namespace declaration, you will see the namespace declaration as one of the items in the returned collection.</span></span>  
  
 <span data-ttu-id="37104-135"><xref:System.Xml.Linq.XAttribute.IsNamespaceDeclaration%2A>Właściwość wskazuje, czy atrybut jest deklaracją przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="37104-135">The <xref:System.Xml.Linq.XAttribute.IsNamespaceDeclaration%2A> property indicates whether an attribute is a namespace declaration.</span></span>  
  
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
  
 <span data-ttu-id="37104-136">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="37104-136">This example produces the following output:</span></span>  
  
```console  
xmlns="http://www.adventure-works.com"  IsNamespaceDeclaration:True  
xmlns:fc="www.fourthcoffee.com"  IsNamespaceDeclaration:True  
AnAttribute="abc"  IsNamespaceDeclaration:False  
```  
  
### <a name="xpath-axis-methods-do-not-return-child-white-space-of-xdocument"></a><span data-ttu-id="37104-137">Metody osi XPath nie zwracają białych znaków elementu XDocument</span><span class="sxs-lookup"><span data-stu-id="37104-137">XPath Axis Methods Do Not Return Child White Space of XDocument</span></span>  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="37104-138">zezwala na podrzędne węzły tekstowe <xref:System.Xml.Linq.XDocument> , tak długo, jak węzły tekstowe zawierają tylko biały znak.</span><span class="sxs-lookup"><span data-stu-id="37104-138">allows for child text nodes of an <xref:System.Xml.Linq.XDocument>, as long as the text nodes contain only white space.</span></span> <span data-ttu-id="37104-139">Jednak model obiektów XPath nie zawiera białych znaków jako węzłów podrzędnych dokumentu, więc gdy przejdziesz do iteracji przez elementy podrzędne <xref:System.Xml.Linq.XDocument> przy użyciu <xref:System.Xml.Linq.XContainer.Nodes%2A> osi, zostaną zwrócone węzły tekstu odstępu.</span><span class="sxs-lookup"><span data-stu-id="37104-139">However, the XPath object model does not include white space as child nodes of a document, so when you iterate through the children of an <xref:System.Xml.Linq.XDocument> using the <xref:System.Xml.Linq.XContainer.Nodes%2A> axis, white space text nodes will be returned.</span></span> <span data-ttu-id="37104-140">Jednak podczas iteracji przez elementy podrzędne z <xref:System.Xml.Linq.XDocument> użyciem metody osi XPath, węzły tekstu odstępu nie będą zwracane.</span><span class="sxs-lookup"><span data-stu-id="37104-140">However, when you iterate through the children of an <xref:System.Xml.Linq.XDocument> using the XPath axis methods, white space text nodes will not be returned.</span></span>  
  
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
  
 <span data-ttu-id="37104-141">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="37104-141">This example produces the following output:</span></span>  
  
```console  
3  
0  
```  
  
### <a name="xdeclaration-objects-are-not-nodes"></a><span data-ttu-id="37104-142">Obiekty XDeclaration nie są węzłami</span><span class="sxs-lookup"><span data-stu-id="37104-142">XDeclaration Objects are not Nodes</span></span>  
 <span data-ttu-id="37104-143">Gdy przejdziesz do iteracji między węzłami podrzędnymi <xref:System.Xml.Linq.XDocument> , nie zobaczysz obiektu deklaracji XML.</span><span class="sxs-lookup"><span data-stu-id="37104-143">When you iterate through the children nodes of an <xref:System.Xml.Linq.XDocument>, you will not see the XML declaration object.</span></span> <span data-ttu-id="37104-144">Jest to właściwość dokumentu, a nie jego węzeł podrzędny.</span><span class="sxs-lookup"><span data-stu-id="37104-144">It is a property of the document, not a child node of it.</span></span>  
  
```vb  
Dim doc As XDocument = _  
<?xml version='1.0' encoding='utf-8' standalone='yes'?>  
<Root/>  
  
doc.Save("Temp.xml")  
Console.WriteLine(File.ReadAllText("Temp.xml"))  
  
' This shows that there is only one child node of the document.  
Console.WriteLine(doc.Nodes().Count())  
```  
  
 <span data-ttu-id="37104-145">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="37104-145">This example produces the following output:</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8" standalone="yes"?>  
<Root />
1
```  
  
## <a name="see-also"></a><span data-ttu-id="37104-146">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="37104-146">See also</span></span>

- [<span data-ttu-id="37104-147">Zaawansowane programowanie LINQ to XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="37104-147">Advanced LINQ to XML Programming (Visual Basic)</span></span>](advanced-linq-to-xml-programming.md)
