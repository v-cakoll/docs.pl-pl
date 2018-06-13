---
title: Programowanie z węzłami (C#)
ms.date: 07/20/2015
ms.assetid: c38df0f2-c805-431a-93ff-9103a4284c2f
ms.openlocfilehash: 060f487e6e92c2ca42a685cc03afbe438106b839
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33335422"
---
# <a name="programming-with-nodes-c"></a><span data-ttu-id="1d62b-102">Programowanie z węzłami (C#)</span><span class="sxs-lookup"><span data-stu-id="1d62b-102">Programming with Nodes (C#)</span></span>
[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="1d62b-103"> Deweloperzy, którzy musisz zapisywać programów, takich jak edytor XML, system transformacji lub zapisywania raportu często konieczne pisania programów, które działają na poziomie szczegółowości większą niż elementów i atrybutów.</span><span class="sxs-lookup"><span data-stu-id="1d62b-103"> developers who need to write programs such as an XML editor, a transform system, or a report writer often need to write programs that work at a finer level of granularity than elements and attributes.</span></span> <span data-ttu-id="1d62b-104">Często muszą pracować na poziomie węzła manipulowanie węzły tekstowe, przetwarzanie instrukcji i komentarze.</span><span class="sxs-lookup"><span data-stu-id="1d62b-104">They often need to work at the node level, manipulating text nodes, processing instructions, and comments.</span></span> <span data-ttu-id="1d62b-105">Ten temat zawiera niektóre szczegóły na temat programowania na poziomie węzła.</span><span class="sxs-lookup"><span data-stu-id="1d62b-105">This topic provides some details about programming at the node level.</span></span>  
  
## <a name="node-details"></a><span data-ttu-id="1d62b-106">Szczegóły dotyczące węzła</span><span class="sxs-lookup"><span data-stu-id="1d62b-106">Node Details</span></span>  
 <span data-ttu-id="1d62b-107">Istnieje szereg szczegóły programowania w języku, który wiedzieć programisty, praca na poziomie węzła.</span><span class="sxs-lookup"><span data-stu-id="1d62b-107">There are a number of details of programming that a programmer working at the node level should know.</span></span>  
  
### <a name="parent-property-of-children-nodes-of-xdocument-is-set-to-null"></a><span data-ttu-id="1d62b-108">Nadrzędny właściwości z elementów podrzędnych węzłów z klasy XDocument ma wartość Null</span><span class="sxs-lookup"><span data-stu-id="1d62b-108">Parent Property of Children Nodes of XDocument is Set to Null</span></span>  
 <span data-ttu-id="1d62b-109"><xref:System.Xml.Linq.XObject.Parent%2A> Właściwość zawiera nadrzędnego <xref:System.Xml.Linq.XElement>, nie węzła nadrzędnego.</span><span class="sxs-lookup"><span data-stu-id="1d62b-109">The <xref:System.Xml.Linq.XObject.Parent%2A> property contains the parent <xref:System.Xml.Linq.XElement>, not the parent node.</span></span> <span data-ttu-id="1d62b-110">Węzły podrzędne <xref:System.Xml.Linq.XDocument> ma nadrzędnej <xref:System.Xml.Linq.XElement>.</span><span class="sxs-lookup"><span data-stu-id="1d62b-110">Child nodes of <xref:System.Xml.Linq.XDocument> have no parent <xref:System.Xml.Linq.XElement>.</span></span> <span data-ttu-id="1d62b-111">Macierzysty jest dokumentu, więc <xref:System.Xml.Linq.XObject.Parent%2A> ustawiono właściwość dla tych węzłów na wartość null.</span><span class="sxs-lookup"><span data-stu-id="1d62b-111">Their parent is the document, so the <xref:System.Xml.Linq.XObject.Parent%2A> property for those nodes is set to null.</span></span>  
  
 <span data-ttu-id="1d62b-112">W poniższym przykładzie pokazano to:</span><span class="sxs-lookup"><span data-stu-id="1d62b-112">The following example demonstrates this:</span></span>  
  
```csharp  
XDocument doc = XDocument.Parse(@"<!-- a comment --><Root/>");  
Console.WriteLine(doc.Nodes().OfType<XComment>().First().Parent == null);  
Console.WriteLine(doc.Root.Parent == null);  
```  
  
 <span data-ttu-id="1d62b-113">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="1d62b-113">This example produces the following output:</span></span>  
  
```  
True  
True  
```  
  
### <a name="adjacent-text-nodes-are-possible"></a><span data-ttu-id="1d62b-114">Możliwe są sąsiadujących węzły tekstowe</span><span class="sxs-lookup"><span data-stu-id="1d62b-114">Adjacent Text Nodes are Possible</span></span>  
 <span data-ttu-id="1d62b-115">Na różne modele programowania XML zawsze są scalane węzłów sąsiadującym tekstem.</span><span class="sxs-lookup"><span data-stu-id="1d62b-115">In a number of XML programming models, adjacent text nodes are always merged.</span></span> <span data-ttu-id="1d62b-116">Jest to czasem nazywane normalizacji węzły tekstowe.</span><span class="sxs-lookup"><span data-stu-id="1d62b-116">This is sometimes called normalization of text nodes.</span></span> [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="1d62b-117"> nie normalizacji węzły tekstowe.</span><span class="sxs-lookup"><span data-stu-id="1d62b-117"> does not normalize text nodes.</span></span> <span data-ttu-id="1d62b-118">Jeśli dodasz dwa węzły tekstowe do tego samego elementu spowoduje węzłów sąsiadującym tekstem.</span><span class="sxs-lookup"><span data-stu-id="1d62b-118">If you add two text nodes to the same element, it will result in adjacent text nodes.</span></span> <span data-ttu-id="1d62b-119">Jednak jeśli dodasz zawartość określona jako ciąg znaków, a nie jako <xref:System.Xml.Linq.XText> węzła, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] może scalić parametrów z węzłem sąsiadującym tekstem.</span><span class="sxs-lookup"><span data-stu-id="1d62b-119">However, if you add content specified as a string rather than as an <xref:System.Xml.Linq.XText> node, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] might merge the string with an adjacent text node.</span></span>  
  
 <span data-ttu-id="1d62b-120">W poniższym przykładzie pokazano to:</span><span class="sxs-lookup"><span data-stu-id="1d62b-120">The following example demonstrates this:</span></span>  
  
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
  
 <span data-ttu-id="1d62b-121">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="1d62b-121">This example produces the following output:</span></span>  
  
```  
1  
1  
2  
```  
  
### <a name="empty-text-nodes-are-possible"></a><span data-ttu-id="1d62b-122">Możliwe są puste węzły tekstowe</span><span class="sxs-lookup"><span data-stu-id="1d62b-122">Empty Text Nodes are Possible</span></span>  
 <span data-ttu-id="1d62b-123">W niektórych modeli programowania XML węzły tekstowe dotrą do zawiera pusty ciąg.</span><span class="sxs-lookup"><span data-stu-id="1d62b-123">In some XML programming models, text nodes are guaranteed to not contain the empty string.</span></span> <span data-ttu-id="1d62b-124">Przyczyny, dla których jest, że węzeł tekstowy nie ma wpływu na serializacji XML.</span><span class="sxs-lookup"><span data-stu-id="1d62b-124">The reasoning is that such a text node has no impact on serialization of the XML.</span></span> <span data-ttu-id="1d62b-125">Jednak z tej samej przyczyny, które są węzłami sąsiadującym tekstem to możliwe, jeśli usuniesz tekst z węzłem tekstowym, ustawiając wartość do ciągu pustego sam węzeł tekst nie zostaną usunięte.</span><span class="sxs-lookup"><span data-stu-id="1d62b-125">However, for the same reason that adjacent text nodes are possible, if you remove the text from a text node by setting its value to the empty string, the text node itself will not be deleted.</span></span>  
  
```csharp  
XElement xmlTree = new XElement("Root", "Content");  
XText textNode = xmlTree.Nodes().OfType<XText>().First();  
  
// the following line does not cause the removal of the text node.  
textNode.Value = "";  
  
XText textNode2 = xmlTree.Nodes().OfType<XText>().First();  
Console.WriteLine(">>{0}<<", textNode2);   
```  
  
 <span data-ttu-id="1d62b-126">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="1d62b-126">This example produces the following output:</span></span>  
  
```  
>><<  
```  
  
### <a name="an-empty-text-node-impacts-serialization"></a><span data-ttu-id="1d62b-127">Pusty tekst węzła ma wpływ na serializacji</span><span class="sxs-lookup"><span data-stu-id="1d62b-127">An Empty Text Node Impacts Serialization</span></span>  
 <span data-ttu-id="1d62b-128">Jeśli element zawiera tylko podrzędnego tekstu węzeł, który jest pusta, jest serializowany przy użyciu składni długich znaczników: `<Child></Child>`.</span><span class="sxs-lookup"><span data-stu-id="1d62b-128">If an element contains only a child text node that is empty, it is serialized with the long tag syntax: `<Child></Child>`.</span></span> <span data-ttu-id="1d62b-129">Jeśli element zawiera bez jakiejkolwiek węzłów podrzędnych, jest serializowany przy użyciu składni krótkich tag: `<Child />`.</span><span class="sxs-lookup"><span data-stu-id="1d62b-129">If an element contains no child nodes whatsoever, it is serialized with the short tag syntax: `<Child />`.</span></span>  
  
```csharp  
XElement child1 = new XElement("Child1",  
    new XText("")  
);  
XElement child2 = new XElement("Child2");  
Console.WriteLine(child1);  
Console.WriteLine(child2);   
```  
  
 <span data-ttu-id="1d62b-130">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="1d62b-130">This example produces the following output:</span></span>  
  
```xml  
<Child1></Child1>  
<Child2 />  
```  
  
### <a name="namespaces-are-attributes-in-the-linq-to-xml-tree"></a><span data-ttu-id="1d62b-131">Są to obszary nazw atrybutów w składniku LINQ to XML drzewa</span><span class="sxs-lookup"><span data-stu-id="1d62b-131">Namespaces are Attributes in the LINQ to XML Tree</span></span>  
 <span data-ttu-id="1d62b-132">Mimo że deklaracje przestrzeni nazw ma identyczne składnię atrybutów, w niektórych interfejsów programowania, takie jak XSLT i wyrażenie XPath, deklaracje przestrzeni nazw nie są uważane za jako atrybuty.</span><span class="sxs-lookup"><span data-stu-id="1d62b-132">Even though namespace declarations have identical syntax to attributes, in some programming interfaces, such as XSLT and XPath, namespace declarations are not considered to be attributes.</span></span> <span data-ttu-id="1d62b-133">Jednak w [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], przestrzenie nazw są przechowywane jako <xref:System.Xml.Linq.XAttribute> obiektów w drzewie XML.</span><span class="sxs-lookup"><span data-stu-id="1d62b-133">However, in [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], namespaces are stored as <xref:System.Xml.Linq.XAttribute> objects in the XML tree.</span></span> <span data-ttu-id="1d62b-134">Jeśli iterację atrybuty elementu, który zawiera deklarację przestrzeni nazw, zobaczysz deklaracji przestrzeni nazw jako jeden z elementów w zwracanej kolekcji.</span><span class="sxs-lookup"><span data-stu-id="1d62b-134">If you iterate through the attributes for an element that contains a namespace declaration, you will see the namespace declaration as one of the items in the returned collection.</span></span>  
  
 <span data-ttu-id="1d62b-135"><xref:System.Xml.Linq.XAttribute.IsNamespaceDeclaration%2A> Właściwość wskazuje, czy atrybut deklaracji przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="1d62b-135">The <xref:System.Xml.Linq.XAttribute.IsNamespaceDeclaration%2A> property indicates whether an attribute is a namespace declaration.</span></span>  
  
```csharp  
XElement root = XElement.Parse(  
@"<Root  
    xmlns='http://www.adventure-works.com'  
    xmlns:fc='www.fourthcoffee.com'  
    AnAttribute='abc'/>");  
foreach (XAttribute att in root.Attributes())  
    Console.WriteLine("{0}  IsNamespaceDeclaration:{1}", att, att.IsNamespaceDeclaration);  
```  
  
 <span data-ttu-id="1d62b-136">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="1d62b-136">This example produces the following output:</span></span>  
  
```  
xmlns="http://www.adventure-works.com"  IsNamespaceDeclaration:True  
xmlns:fc="www.fourthcoffee.com"  IsNamespaceDeclaration:True  
AnAttribute="abc"  IsNamespaceDeclaration:False  
```  
  
### <a name="xpath-axis-methods-do-not-return-child-white-space-of-xdocument"></a><span data-ttu-id="1d62b-137">Metody osi XPath zwraca podrzędny biały znak z klasy XDocument</span><span class="sxs-lookup"><span data-stu-id="1d62b-137">XPath Axis Methods Do Not Return Child White Space of XDocument</span></span>  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="1d62b-138"> Umożliwia tekst węzły podrzędne <xref:System.Xml.Linq.XDocument>, ile węzły tekstowe zawiera tylko biały znak.</span><span class="sxs-lookup"><span data-stu-id="1d62b-138"> allows for child text nodes of an <xref:System.Xml.Linq.XDocument>, as long as the text nodes contain only white space.</span></span> <span data-ttu-id="1d62b-139">Jednak model obiektów XPath nie zawiera biały znak jako węzły podrzędne dokumentu, dlatego jeśli iterację elementów podrzędnych <xref:System.Xml.Linq.XDocument> przy użyciu <xref:System.Xml.Linq.XContainer.Nodes%2A> osi, węzły tekstowe biały znak zostanie zwrócony.</span><span class="sxs-lookup"><span data-stu-id="1d62b-139">However, the XPath object model does not include white space as child nodes of a document, so when you iterate through the children of an <xref:System.Xml.Linq.XDocument> using the <xref:System.Xml.Linq.XContainer.Nodes%2A> axis, white-space text nodes will be returned.</span></span> <span data-ttu-id="1d62b-140">Jednak gdy iterację elementów podrzędnych <xref:System.Xml.Linq.XDocument> przy użyciu metod osi XPath, węzły tekstowe biały znak nie zostaną zwrócone.</span><span class="sxs-lookup"><span data-stu-id="1d62b-140">However, when you iterate through the children of an <xref:System.Xml.Linq.XDocument> using the XPath axis methods, white-space text nodes will not be returned.</span></span>  
  
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
  
 <span data-ttu-id="1d62b-141">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="1d62b-141">This example produces the following output:</span></span>  
  
```  
3  
0  
```  
  
### <a name="xdeclaration-objects-are-not-nodes"></a><span data-ttu-id="1d62b-142">XDeclaration obiekty nie są węzłami</span><span class="sxs-lookup"><span data-stu-id="1d62b-142">XDeclaration Objects are not Nodes</span></span>  
 <span data-ttu-id="1d62b-143">Gdy iterację węzłów podrzędnych <xref:System.Xml.Linq.XDocument>, nie będzie mógł przeglądać obiektu deklaracji XML.</span><span class="sxs-lookup"><span data-stu-id="1d62b-143">When you iterate through the children nodes of an <xref:System.Xml.Linq.XDocument>, you will not see the XML declaration object.</span></span> <span data-ttu-id="1d62b-144">Jest to właściwość dokumentu nie elementem podrzędnym go.</span><span class="sxs-lookup"><span data-stu-id="1d62b-144">It is a property of the document, not a child node of it.</span></span>  
  
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
  
 <span data-ttu-id="1d62b-145">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="1d62b-145">This example produces the following output:</span></span>  
  
```  
<?xml version="1.0" encoding="utf-8" standalone="yes"?>  
<Root />  
1  
```  
  
## <a name="see-also"></a><span data-ttu-id="1d62b-146">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="1d62b-146">See Also</span></span>  
 [<span data-ttu-id="1d62b-147">Zaawansowane LINQ do XML programowania (C#)</span><span class="sxs-lookup"><span data-stu-id="1d62b-147">Advanced LINQ to XML Programming (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/advanced-linq-to-xml-programming.md)
