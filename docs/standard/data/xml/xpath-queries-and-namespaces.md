---
title: Kwerendy XPath i przestrzenie nazw
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: ef6402be-2f8e-4be2-8d3e-a80891cdef8b
author: mairaw
ms.author: mairaw
ms.openlocfilehash: a121f58df93f88af851bbcc85d75e71fc067af78
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="xpath-queries-and-namespaces"></a><span data-ttu-id="df892-102">Kwerendy XPath i przestrzenie nazw</span><span class="sxs-lookup"><span data-stu-id="df892-102">XPath Queries and Namespaces</span></span>
<span data-ttu-id="df892-103">Kwerendy XPath wiedzą z przestrzeni nazw w dokumencie XML i mogą być uprawnione nazw elementów i atrybutów prefiksy przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="df892-103">XPath queries are aware of namespaces in an XML document and can use namespace prefixes to qualify element and attribute names.</span></span> <span data-ttu-id="df892-104">Kwalifikowanie nazw elementów i atrybutów z prefiksu przestrzeni nazw ogranicza węzłów zwróconych przez zapytanie XPath tylko węzły, które należą do określonych przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="df892-104">Qualifying element and attribute names with a namespace prefix limits the nodes returned by an XPath query to only those nodes that belong to a specific namespace.</span></span>  
  
 <span data-ttu-id="df892-105">Na przykład jeśli prefiks `books` mapowania do przestrzeni nazw `http://www.contoso.com/books`, następnie następujące zapytanie XPath `/books:books/books:book` wybiera tylko te `book` elementy w przestrzeni nazw `http://www.contoso.com/books`.</span><span class="sxs-lookup"><span data-stu-id="df892-105">For example if the prefix `books` maps to the namespace `http://www.contoso.com/books`, then the following XPath query `/books:books/books:book` selects only those `book` elements in the namespace `http://www.contoso.com/books`.</span></span>  
  
## <a name="the-xmlnamespacemanager"></a><span data-ttu-id="df892-106">XmlNamespaceManager</span><span class="sxs-lookup"><span data-stu-id="df892-106">The XmlNamespaceManager</span></span>  
 <span data-ttu-id="df892-107">Aby użyć przestrzeni nazw w zapytaniu XPath, obiekt pochodzi od <xref:System.Xml.IXmlNamespaceResolver> interfejsu, takich jak <xref:System.Xml.XmlNamespaceManager> klasy jest tworzony z identyfikatorem URI przestrzeni nazw i prefiksu do uwzględnienia w zapytaniu XPath.</span><span class="sxs-lookup"><span data-stu-id="df892-107">To use namespaces in an XPath query, an object derived from the <xref:System.Xml.IXmlNamespaceResolver> interface like the <xref:System.Xml.XmlNamespaceManager> class is constructed with the namespace URI and prefix to include in the XPath query.</span></span>  
  
 <span data-ttu-id="df892-108"><xref:System.Xml.XmlNamespaceManager> Obiekt może być używany w zapytania w każdej z następujących sposobów.</span><span class="sxs-lookup"><span data-stu-id="df892-108">The <xref:System.Xml.XmlNamespaceManager> object may be used in the query in each of the following ways.</span></span>  
  
-   <span data-ttu-id="df892-109"><xref:System.Xml.XmlNamespaceManager> Obiekt jest skojarzony z istniejącym <xref:System.Xml.XPath.XPathExpression> obiektu za pomocą <xref:System.Xml.XPath.XPathExpression.SetContext%2A> metody <xref:System.Xml.XPath.XPathExpression> obiektu.</span><span class="sxs-lookup"><span data-stu-id="df892-109">The <xref:System.Xml.XmlNamespaceManager> object is associated with an existing <xref:System.Xml.XPath.XPathExpression> object by using the <xref:System.Xml.XPath.XPathExpression.SetContext%2A> method of the <xref:System.Xml.XPath.XPathExpression> object.</span></span> <span data-ttu-id="df892-110">Również skompilować nowego <xref:System.Xml.XPath.XPathExpression> przy użyciu statycznych <xref:System.Xml.XPath.XPathExpression.Compile%2A> metoda przyjmująca ciąg reprezentujący wyrażenie XPath i <xref:System.Xml.XmlNamespaceManager> obiektu jako parametrów i zwraca nowy <xref:System.Xml.XPath.XPathExpression> obiektu.</span><span class="sxs-lookup"><span data-stu-id="df892-110">You may also compile a new <xref:System.Xml.XPath.XPathExpression> object using the static <xref:System.Xml.XPath.XPathExpression.Compile%2A> method which takes a string representing the XPath expression and an <xref:System.Xml.XmlNamespaceManager> object as parameters and returns a new <xref:System.Xml.XPath.XPathExpression> object.</span></span>  
  
-   <span data-ttu-id="df892-111"><xref:System.Xml.XmlNamespaceManager> Sam obiekt jest przekazywany jako parametr do akceptowania <xref:System.Xml.XPath.XPathNavigator> metoda wraz z ciąg reprezentujący wyrażenie XPath klasy.</span><span class="sxs-lookup"><span data-stu-id="df892-111">The <xref:System.Xml.XmlNamespaceManager> object itself is passed as a parameter to an accepting <xref:System.Xml.XPath.XPathNavigator> class method along with a string representing the XPath expression.</span></span>  
  
 <span data-ttu-id="df892-112">Poniżej przedstawiono metody <xref:System.Xml.XPath.XPathNavigator> pochodną klasy, które akceptują obiektu <xref:System.Xml.IXmlNamespaceResolver> interfejsu jako parametr.</span><span class="sxs-lookup"><span data-stu-id="df892-112">The following are the methods of the <xref:System.Xml.XPath.XPathNavigator> class that accept an object derived from the <xref:System.Xml.IXmlNamespaceResolver> interface as a parameter.</span></span>  
  
-   <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A>  
  
-   <xref:System.Xml.XPath.XPathNavigator.Select%2A>  
  
-   <xref:System.Xml.XPath.XPathNavigator.SelectSingleNode%2A>  
  
### <a name="the-default-namespace"></a><span data-ttu-id="df892-113">Namespace domyślne</span><span class="sxs-lookup"><span data-stu-id="df892-113">The Default Namespace</span></span>  
 <span data-ttu-id="df892-114">W dokumencie XML, który jest zgodny, domyślnej przestrzeni nazw z pustego prefiksu służy do deklarowania `http://www.contoso.com/books` przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="df892-114">In the XML document that follows, the default namespace with an empty prefix is used to declare the `http://www.contoso.com/books` namespace.</span></span>  
  
```xml  
<books xmlns="http://www.example.com/books">  
    <book>  
        <title>Title</title>  
        <author>Author Name</author>  
        <price>5.50</price>  
    </book>  
</books>  
```  
  
 <span data-ttu-id="df892-115">Wyrażenie XPath traktuje pustego prefiksu jako `null` przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="df892-115">XPath treats the empty prefix as the `null` namespace.</span></span> <span data-ttu-id="df892-116">Innymi słowy tylko prefiksy zamapowany do przestrzeni nazw może służyć kwerendy XPath.</span><span class="sxs-lookup"><span data-stu-id="df892-116">In other words, only prefixes mapped to namespaces can be used in XPath queries.</span></span> <span data-ttu-id="df892-117">Oznacza to, że należy wykonać zapytanie względem przestrzeni nazw w dokumencie XML, nawet jeśli jest ona domyślnej przestrzeni nazw należy zdefiniować prefiksu.</span><span class="sxs-lookup"><span data-stu-id="df892-117">This means that if you want to query against a namespace in an XML document, even if it is the default namespace, you need to define a prefix for it.</span></span>  
  
 <span data-ttu-id="df892-118">Na przykład bez zdefiniowania prefiksu dla dokumentu XML powyżej XPath zapytanie `/books/book` nie zwróci żadnych wyników.</span><span class="sxs-lookup"><span data-stu-id="df892-118">For example, without defining a prefix for the XML document above, the XPath query `/books/book` would not return any results.</span></span>  
  
 <span data-ttu-id="df892-119">Aby uniknąć niejednoznaczności, podczas wykonywania zapytań dotyczących dokumentów za pomocą niektóre węzły nie w przestrzeni nazw, a niektóre w domyślnej przestrzeni nazw musi być powiązana prefiksu.</span><span class="sxs-lookup"><span data-stu-id="df892-119">A prefix must be bound to prevent ambiguity when querying documents with some nodes not in a namespace, and some in a default namespace.</span></span>  
  
 <span data-ttu-id="df892-120">Poniższy kod definiuje prefiksu dla domyślnej przestrzeni nazw i wybranie wszystkich `book` elementy z `http://www.contoso.com/books` przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="df892-120">The following code defines a prefix for the default namespace and selects all the `book` elements from the `http://www.contoso.com/books` namespace.</span></span>  
  
```vb  
Dim document As XPathDocument = New XPathDocument("books.xml")  
Dim navigator As XPathNavigator = document.CreateNavigator()  
Dim query As XPathExpression = navigator.Compile("/books:books/books:book")  
Dim manager As XmlNamespaceManager = New XmlNamespaceManager(navigator.NameTable)  
manager.AddNamespace("books", "http://www.contoso.com/books")  
query.SetContext(manager)  
Dim nodes As XPathNodeIterator = navigator.Select(query)  
```  
  
```csharp  
XPathDocument document = new XPathDocument("books.xml");  
XPathNavigator navigator = document.CreateNavigator();  
XPathExpression query = navigator.Compile("/books:books/books:book");  
XmlNamespaceManager manager = new XmlNamespaceManager(navigator.NameTable);  
manager.AddNamespace("books", "http://www.contoso.com/books");  
query.SetContext(manager);  
XPathNodeIterator nodes = navigator.Select(query);  
```  
  
## <a name="see-also"></a><span data-ttu-id="df892-121">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="df892-121">See Also</span></span>  
 <xref:System.Xml.XmlDocument>  
 <xref:System.Xml.XPath.XPathDocument>  
 <xref:System.Xml.XPath.XPathNavigator>  
 [<span data-ttu-id="df892-122">Przetwarzanie danych XML przy użyciu modelu danych XPath</span><span class="sxs-lookup"><span data-stu-id="df892-122">Process XML Data Using the XPath Data Model</span></span>](../../../../docs/standard/data/xml/process-xml-data-using-the-xpath-data-model.md)  
 [<span data-ttu-id="df892-123">Wybieranie danych XML przy użyciu klasy XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="df892-123">Select XML Data Using XPathNavigator</span></span>](../../../../docs/standard/data/xml/select-xml-data-using-xpathnavigator.md)  
 [<span data-ttu-id="df892-124">Obliczanie wyrażeń XPath przy użyciu klasy XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="df892-124">Evaluate XPath Expressions using XPathNavigator</span></span>](../../../../docs/standard/data/xml/evaluate-xpath-expressions-using-xpathnavigator.md)  
 [<span data-ttu-id="df892-125">Dopasowywanie węzłów przy użyciu klasy XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="df892-125">Matching Nodes using XPathNavigator</span></span>](../../../../docs/standard/data/xml/matching-nodes-using-xpathnavigator.md)  
 [<span data-ttu-id="df892-126">Typy węzłów rozpoznawanych w zapytaniach XPath</span><span class="sxs-lookup"><span data-stu-id="df892-126">Node Types Recognized with XPath Queries</span></span>](../../../../docs/standard/data/xml/node-types-recognized-with-xpath-queries.md)  
 [<span data-ttu-id="df892-127">Skompilowane wyrażenia XPath</span><span class="sxs-lookup"><span data-stu-id="df892-127">Compiled XPath Expressions</span></span>](../../../../docs/standard/data/xml/compiled-xpath-expressions.md)
