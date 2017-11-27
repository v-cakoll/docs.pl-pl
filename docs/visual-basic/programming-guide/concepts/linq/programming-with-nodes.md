---
title: "Programowanie z węzłami (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d8422a9b-dd37-44a3-8aac-2237ed9561e0
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 5f56e98d4a732b6cc69dde87d0efe8e87506b48b
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="programming-with-nodes-visual-basic"></a><span data-ttu-id="00ff7-102">Programowanie z węzłami (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="00ff7-102">Programming with Nodes (Visual Basic)</span></span>
[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="00ff7-103">Deweloperzy, którzy musisz zapisywać programów, takich jak edytor XML, system transformacji lub zapisywania raportu często konieczne pisania programów, które działają na poziomie szczegółowości większą niż elementów i atrybutów.</span><span class="sxs-lookup"><span data-stu-id="00ff7-103"> developers who need to write programs such as an XML editor, a transform system, or a report writer often need to write programs that work at a finer level of granularity than elements and attributes.</span></span> <span data-ttu-id="00ff7-104">Często muszą pracować na poziomie węzła manipulowanie węzły tekstowe, przetwarzanie instrukcji i komentarze.</span><span class="sxs-lookup"><span data-stu-id="00ff7-104">They often need to work at the node level, manipulating text nodes, processing instructions, and comments.</span></span> <span data-ttu-id="00ff7-105">Ten temat zawiera niektóre szczegóły na temat programowania na poziomie węzła.</span><span class="sxs-lookup"><span data-stu-id="00ff7-105">This topic provides some details about programming at the node level.</span></span>  
  
## <a name="node-details"></a><span data-ttu-id="00ff7-106">Szczegóły dotyczące węzła</span><span class="sxs-lookup"><span data-stu-id="00ff7-106">Node Details</span></span>  
 <span data-ttu-id="00ff7-107">Istnieje szereg szczegóły programowania w języku, który wiedzieć programisty, praca na poziomie węzła.</span><span class="sxs-lookup"><span data-stu-id="00ff7-107">There are a number of details of programming that a programmer working at the node level should know.</span></span>  
  
### <a name="parent-property-of-children-nodes-of-xdocument-is-set-to-null"></a><span data-ttu-id="00ff7-108">Nadrzędny właściwości z elementów podrzędnych węzłów z klasy XDocument ma wartość Null</span><span class="sxs-lookup"><span data-stu-id="00ff7-108">Parent Property of Children Nodes of XDocument is Set to Null</span></span>  
 <span data-ttu-id="00ff7-109"><xref:System.Xml.Linq.XObject.Parent%2A> Właściwość zawiera nadrzędnego <xref:System.Xml.Linq.XElement>, nie węzła nadrzędnego.</span><span class="sxs-lookup"><span data-stu-id="00ff7-109">The <xref:System.Xml.Linq.XObject.Parent%2A> property contains the parent <xref:System.Xml.Linq.XElement>, not the parent node.</span></span> <span data-ttu-id="00ff7-110">Węzły podrzędne <xref:System.Xml.Linq.XDocument> ma nadrzędnej <xref:System.Xml.Linq.XElement>.</span><span class="sxs-lookup"><span data-stu-id="00ff7-110">Child nodes of <xref:System.Xml.Linq.XDocument> have no parent <xref:System.Xml.Linq.XElement>.</span></span> <span data-ttu-id="00ff7-111">Macierzysty jest dokumentu, więc <xref:System.Xml.Linq.XObject.Parent%2A> ustawiono właściwość dla tych węzłów na wartość null.</span><span class="sxs-lookup"><span data-stu-id="00ff7-111">Their parent is the document, so the <xref:System.Xml.Linq.XObject.Parent%2A> property for those nodes is set to null.</span></span>  
  
 <span data-ttu-id="00ff7-112">W poniższym przykładzie pokazano to:</span><span class="sxs-lookup"><span data-stu-id="00ff7-112">The following example demonstrates this:</span></span>  
  
```vb  
Dim doc As XDocument = XDocument.Parse("<!-- a comment --><Root/>")  
Console.WriteLine(doc.Nodes().OfType(Of XComment).First().Parent Is Nothing)  
Console.WriteLine(doc.Root.Parent Is Nothing)  
```  
  
 <span data-ttu-id="00ff7-113">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="00ff7-113">This example produces the following output:</span></span>  
  
```  
True  
True  
```  
  
### <a name="adjacent-text-nodes-are-possible"></a><span data-ttu-id="00ff7-114">Możliwe są sąsiadujących węzły tekstowe</span><span class="sxs-lookup"><span data-stu-id="00ff7-114">Adjacent Text Nodes are Possible</span></span>  
 <span data-ttu-id="00ff7-115">Na różne modele programowania XML zawsze są scalane węzłów sąsiadującym tekstem.</span><span class="sxs-lookup"><span data-stu-id="00ff7-115">In a number of XML programming models, adjacent text nodes are always merged.</span></span> <span data-ttu-id="00ff7-116">Jest to czasem nazywane normalizacji węzły tekstowe.</span><span class="sxs-lookup"><span data-stu-id="00ff7-116">This is sometimes called normalization of text nodes.</span></span> [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="00ff7-117">nie normalizacji węzły tekstowe.</span><span class="sxs-lookup"><span data-stu-id="00ff7-117"> does not normalize text nodes.</span></span> <span data-ttu-id="00ff7-118">Jeśli dodasz dwa węzły tekstowe do tego samego elementu spowoduje węzłów sąsiadującym tekstem.</span><span class="sxs-lookup"><span data-stu-id="00ff7-118">If you add two text nodes to the same element, it will result in adjacent text nodes.</span></span> <span data-ttu-id="00ff7-119">Jednak jeśli dodasz zawartość określona jako ciąg znaków, a nie jako <xref:System.Xml.Linq.XText> węzła, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] może scalić parametrów z węzłem sąsiadującym tekstem.</span><span class="sxs-lookup"><span data-stu-id="00ff7-119">However, if you add content specified as a string rather than as an <xref:System.Xml.Linq.XText> node, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] might merge the string with an adjacent text node.</span></span>  
  
 <span data-ttu-id="00ff7-120">W poniższym przykładzie pokazano to:</span><span class="sxs-lookup"><span data-stu-id="00ff7-120">The following example demonstrates this:</span></span>  
  
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
  
 <span data-ttu-id="00ff7-121">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="00ff7-121">This example produces the following output:</span></span>  
  
```  
1  
1  
2  
```  
  
### <a name="empty-text-nodes-are-possible"></a><span data-ttu-id="00ff7-122">Możliwe są puste węzły tekstowe</span><span class="sxs-lookup"><span data-stu-id="00ff7-122">Empty Text Nodes are Possible</span></span>  
 <span data-ttu-id="00ff7-123">W niektórych modeli programowania XML węzły tekstowe dotrą do zawiera pusty ciąg.</span><span class="sxs-lookup"><span data-stu-id="00ff7-123">In some XML programming models, text nodes are guaranteed to not contain the empty string.</span></span> <span data-ttu-id="00ff7-124">Przyczyny, dla których jest, że węzeł tekstowy nie ma wpływu na serializacji XML.</span><span class="sxs-lookup"><span data-stu-id="00ff7-124">The reasoning is that such a text node has no impact on serialization of the XML.</span></span> <span data-ttu-id="00ff7-125">Jednak z tej samej przyczyny, które są węzłami sąsiadującym tekstem to możliwe, jeśli usuniesz tekst z węzłem tekstowym, ustawiając wartość do ciągu pustego sam węzeł tekst nie zostaną usunięte.</span><span class="sxs-lookup"><span data-stu-id="00ff7-125">However, for the same reason that adjacent text nodes are possible, if you remove the text from a text node by setting its value to the empty string, the text node itself will not be deleted.</span></span>  
  
```vb  
Dim xmlTree As XElement = <Root>Content</Root>  
Dim textNode As XText = xmlTree.Nodes().OfType(Of XText)().First()  
  
' The following line does not cause the removal of the text node.  
textNode.Value = ""  
  
Dim textNode2 As XText = xmlTree.Nodes().OfType(Of XText)().First()  
Console.WriteLine(">>{0}<<", textNode2)  
```  
  
 <span data-ttu-id="00ff7-126">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="00ff7-126">This example produces the following output:</span></span>  
  
```  
>><<  
```  
  
### <a name="an-empty-text-node-impacts-serialization"></a><span data-ttu-id="00ff7-127">Pusty tekst węzła ma wpływ na serializacji</span><span class="sxs-lookup"><span data-stu-id="00ff7-127">An Empty Text Node Impacts Serialization</span></span>  
 <span data-ttu-id="00ff7-128">Jeśli element zawiera tylko podrzędnego tekstu węzeł, który jest pusta, jest serializowany przy użyciu składni długich znaczników: `<Child></Child>`.</span><span class="sxs-lookup"><span data-stu-id="00ff7-128">If an element contains only a child text node that is empty, it is serialized with the long tag syntax: `<Child></Child>`.</span></span> <span data-ttu-id="00ff7-129">Jeśli element zawiera bez jakiejkolwiek węzłów podrzędnych, jest serializowany przy użyciu składni krótkich tag: `<Child />`.</span><span class="sxs-lookup"><span data-stu-id="00ff7-129">If an element contains no child nodes whatsoever, it is serialized with the short tag syntax: `<Child />`.</span></span>  
  
```vb  
Dim child1 As XElement = New XElement("Child1", _  
    New XText("") _  
)  
Dim child2 As XElement = New XElement("Child2")  
Console.WriteLine(child1)  
Console.WriteLine(child2)  
```  
  
 <span data-ttu-id="00ff7-130">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="00ff7-130">This example produces the following output:</span></span>  
  
```xml  
<Child1></Child1>  
<Child2 />  
```  
  
### <a name="namespaces-are-attributes-in-the-linq-to-xml-tree"></a><span data-ttu-id="00ff7-131">Są to obszary nazw atrybutów w składniku LINQ to XML drzewa</span><span class="sxs-lookup"><span data-stu-id="00ff7-131">Namespaces are Attributes in the LINQ to XML Tree</span></span>  
 <span data-ttu-id="00ff7-132">Mimo że deklaracje przestrzeni nazw ma identyczne składnię atrybutów, w niektórych interfejsów programowania, takie jak XSLT i wyrażenie XPath, deklaracje przestrzeni nazw nie są uważane za jako atrybuty.</span><span class="sxs-lookup"><span data-stu-id="00ff7-132">Even though namespace declarations have identical syntax to attributes, in some programming interfaces, such as XSLT and XPath, namespace declarations are not considered to be attributes.</span></span> <span data-ttu-id="00ff7-133">Jednak w [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], przestrzenie nazw są przechowywane jako <xref:System.Xml.Linq.XAttribute> obiektów w drzewie XML.</span><span class="sxs-lookup"><span data-stu-id="00ff7-133">However, in [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], namespaces are stored as <xref:System.Xml.Linq.XAttribute> objects in the XML tree.</span></span> <span data-ttu-id="00ff7-134">Jeśli iterację atrybuty elementu, który zawiera deklarację przestrzeni nazw, zobaczysz deklaracji przestrzeni nazw jako jeden z elementów w zwracanej kolekcji.</span><span class="sxs-lookup"><span data-stu-id="00ff7-134">If you iterate through the attributes for an element that contains a namespace declaration, you will see the namespace declaration as one of the items in the returned collection.</span></span>  
  
 <span data-ttu-id="00ff7-135"><xref:System.Xml.Linq.XAttribute.IsNamespaceDeclaration%2A> Właściwość wskazuje, czy atrybut deklaracji przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="00ff7-135">The <xref:System.Xml.Linq.XAttribute.IsNamespaceDeclaration%2A> property indicates whether an attribute is a namespace declaration.</span></span>  
  
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
  
 <span data-ttu-id="00ff7-136">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="00ff7-136">This example produces the following output:</span></span>  
  
```  
xmlns="http://www.adventure-works.com"  IsNamespaceDeclaration:True  
xmlns:fc="www.fourthcoffee.com"  IsNamespaceDeclaration:True  
AnAttribute="abc"  IsNamespaceDeclaration:False  
```  
  
### <a name="xpath-axis-methods-do-not-return-child-white-space-of-xdocument"></a><span data-ttu-id="00ff7-137">Metody osi XPath zwraca podrzędny biały znak z klasy XDocument</span><span class="sxs-lookup"><span data-stu-id="00ff7-137">XPath Axis Methods Do Not Return Child White Space of XDocument</span></span>  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="00ff7-138">Umożliwia tekst węzły podrzędne <xref:System.Xml.Linq.XDocument>, ile węzły tekstowe zawiera tylko biały znak.</span><span class="sxs-lookup"><span data-stu-id="00ff7-138"> allows for child text nodes of an <xref:System.Xml.Linq.XDocument>, as long as the text nodes contain only white space.</span></span> <span data-ttu-id="00ff7-139">Jednak model obiektów XPath nie zawiera biały znak jako węzły podrzędne dokumentu, dlatego podczas iteracji elementów podrzędnych <xref:System.Xml.Linq.XDocument> przy użyciu <xref:System.Xml.Linq.XContainer.Nodes%2A> osi, białe węzły tekstowe zostaną zwrócone.</span><span class="sxs-lookup"><span data-stu-id="00ff7-139">However, the XPath object model does not include white space as child nodes of a document, so when you iterate through the children of an <xref:System.Xml.Linq.XDocument> using the <xref:System.Xml.Linq.XContainer.Nodes%2A> axis, white space text nodes will be returned.</span></span> <span data-ttu-id="00ff7-140">Jednak gdy iterację elementów podrzędnych <xref:System.Xml.Linq.XDocument> przy użyciu metod osi XPath, białe węzły tekstowe nie zostaną zwrócone.</span><span class="sxs-lookup"><span data-stu-id="00ff7-140">However, when you iterate through the children of an <xref:System.Xml.Linq.XDocument> using the XPath axis methods, white space text nodes will not be returned.</span></span>  
  
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
  
 <span data-ttu-id="00ff7-141">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="00ff7-141">This example produces the following output:</span></span>  
  
```  
3  
0  
```  
  
### <a name="xdeclaration-objects-are-not-nodes"></a><span data-ttu-id="00ff7-142">XDeclaration obiekty nie są węzłami</span><span class="sxs-lookup"><span data-stu-id="00ff7-142">XDeclaration Objects are not Nodes</span></span>  
 <span data-ttu-id="00ff7-143">Gdy iterację węzłów podrzędnych <xref:System.Xml.Linq.XDocument>, nie będzie mógł przeglądać obiektu deklaracji XML.</span><span class="sxs-lookup"><span data-stu-id="00ff7-143">When you iterate through the children nodes of an <xref:System.Xml.Linq.XDocument>, you will not see the XML declaration object.</span></span> <span data-ttu-id="00ff7-144">Jest to właściwość dokumentu nie elementem podrzędnym go.</span><span class="sxs-lookup"><span data-stu-id="00ff7-144">It is a property of the document, not a child node of it.</span></span>  
  
```vb  
Dim doc As XDocument = _  
<?xml version='1.0' encoding='utf-8' standalone='yes'?>  
<Root/>  
  
doc.Save("Temp.xml")  
Console.WriteLine(File.ReadAllText("Temp.xml"))  
  
' This shows that there is only one child node of the document.  
Console.WriteLine(doc.Nodes().Count())  
```  
  
 <span data-ttu-id="00ff7-145">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="00ff7-145">This example produces the following output:</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8" standalone="yes"?>  
<Root />  
1  
```  
  
## <a name="see-also"></a><span data-ttu-id="00ff7-146">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="00ff7-146">See Also</span></span>  
 [<span data-ttu-id="00ff7-147">Zaawansowane LINQ do XML programowania (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="00ff7-147">Advanced LINQ to XML Programming (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/advanced-linq-to-xml-programming.md)
