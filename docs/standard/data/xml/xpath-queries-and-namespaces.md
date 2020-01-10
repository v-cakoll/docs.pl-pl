---
title: Zapytania XPath i przestrzenie nazw
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: ef6402be-2f8e-4be2-8d3e-a80891cdef8b
ms.openlocfilehash: 91503ce0bffa1a9390432a51bff1ef10d80f563a
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75709780"
---
# <a name="xpath-queries-and-namespaces"></a><span data-ttu-id="c9061-102">Zapytania XPath i przestrzenie nazw</span><span class="sxs-lookup"><span data-stu-id="c9061-102">XPath Queries and Namespaces</span></span>
<span data-ttu-id="c9061-103">Zapytania XPath są świadome przestrzeni nazw w dokumencie XML i mogą używać prefiksów przestrzeni nazw do kwalifikowania nazw elementów i atrybutów.</span><span class="sxs-lookup"><span data-stu-id="c9061-103">XPath queries are aware of namespaces in an XML document and can use namespace prefixes to qualify element and attribute names.</span></span> <span data-ttu-id="c9061-104">Kwalifikujące się nazwy elementów i atrybutów z prefiksem przestrzeni nazw ograniczają węzły zwracane przez zapytanie XPath tylko do tych węzłów, które należą do określonej przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="c9061-104">Qualifying element and attribute names with a namespace prefix limits the nodes returned by an XPath query to only those nodes that belong to a specific namespace.</span></span>  
  
 <span data-ttu-id="c9061-105">Na przykład jeśli prefiks `books` mapowany do przestrzeni nazw `http://www.contoso.com/books`, wówczas następujące zapytanie XPath `/books:books/books:book` wybiera tylko te elementy `book` w przestrzeni nazw `http://www.contoso.com/books`.</span><span class="sxs-lookup"><span data-stu-id="c9061-105">For example if the prefix `books` maps to the namespace `http://www.contoso.com/books`, then the following XPath query `/books:books/books:book` selects only those `book` elements in the namespace `http://www.contoso.com/books`.</span></span>  
  
## <a name="the-xmlnamespacemanager"></a><span data-ttu-id="c9061-106">Nazwa XmlNamespaceManager</span><span class="sxs-lookup"><span data-stu-id="c9061-106">The XmlNamespaceManager</span></span>  
 <span data-ttu-id="c9061-107">Aby używać przestrzeni nazw w zapytaniu XPath, obiekt pochodny interfejsu <xref:System.Xml.IXmlNamespaceResolver>, jak Klasa <xref:System.Xml.XmlNamespaceManager>, jest konstruowany przy użyciu identyfikatora URI przestrzeni nazw i prefiksu do uwzględnienia w zapytaniu XPath.</span><span class="sxs-lookup"><span data-stu-id="c9061-107">To use namespaces in an XPath query, an object derived from the <xref:System.Xml.IXmlNamespaceResolver> interface like the <xref:System.Xml.XmlNamespaceManager> class is constructed with the namespace URI and prefix to include in the XPath query.</span></span>  
  
 <span data-ttu-id="c9061-108">Obiekt <xref:System.Xml.XmlNamespaceManager> może być używany w zapytaniu w każdym z poniższych sposobów.</span><span class="sxs-lookup"><span data-stu-id="c9061-108">The <xref:System.Xml.XmlNamespaceManager> object may be used in the query in each of the following ways.</span></span>  
  
- <span data-ttu-id="c9061-109">Obiekt <xref:System.Xml.XmlNamespaceManager> jest skojarzony z istniejącym obiektem <xref:System.Xml.XPath.XPathExpression> za pomocą metody <xref:System.Xml.XPath.XPathExpression.SetContext%2A> obiektu <xref:System.Xml.XPath.XPathExpression>.</span><span class="sxs-lookup"><span data-stu-id="c9061-109">The <xref:System.Xml.XmlNamespaceManager> object is associated with an existing <xref:System.Xml.XPath.XPathExpression> object by using the <xref:System.Xml.XPath.XPathExpression.SetContext%2A> method of the <xref:System.Xml.XPath.XPathExpression> object.</span></span> <span data-ttu-id="c9061-110">Możesz również skompilować nowy obiekt <xref:System.Xml.XPath.XPathExpression> przy użyciu statycznej metody <xref:System.Xml.XPath.XPathExpression.Compile%2A>, która przyjmuje ciąg reprezentujący wyrażenie XPath i obiekt <xref:System.Xml.XmlNamespaceManager> jako parametry i zwraca nowy obiekt <xref:System.Xml.XPath.XPathExpression>.</span><span class="sxs-lookup"><span data-stu-id="c9061-110">You may also compile a new <xref:System.Xml.XPath.XPathExpression> object using the static <xref:System.Xml.XPath.XPathExpression.Compile%2A> method which takes a string representing the XPath expression and an <xref:System.Xml.XmlNamespaceManager> object as parameters and returns a new <xref:System.Xml.XPath.XPathExpression> object.</span></span>  
  
- <span data-ttu-id="c9061-111">Sam obiekt <xref:System.Xml.XmlNamespaceManager> jest przenoszona jako parametr do metody akceptującej <xref:System.Xml.XPath.XPathNavigator> klasy wraz z ciągiem reprezentującym wyrażenie XPath.</span><span class="sxs-lookup"><span data-stu-id="c9061-111">The <xref:System.Xml.XmlNamespaceManager> object itself is passed as a parameter to an accepting <xref:System.Xml.XPath.XPathNavigator> class method along with a string representing the XPath expression.</span></span>  
  
 <span data-ttu-id="c9061-112">Poniżej przedstawiono metody klasy <xref:System.Xml.XPath.XPathNavigator>, które akceptują obiekt pochodny interfejsu <xref:System.Xml.IXmlNamespaceResolver> jako parametr.</span><span class="sxs-lookup"><span data-stu-id="c9061-112">The following are the methods of the <xref:System.Xml.XPath.XPathNavigator> class that accept an object derived from the <xref:System.Xml.IXmlNamespaceResolver> interface as a parameter.</span></span>  
  
- <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A>  
  
- <xref:System.Xml.XPath.XPathNavigator.Select%2A>  
  
- <xref:System.Xml.XPath.XPathNavigator.SelectSingleNode%2A>  
  
### <a name="the-default-namespace"></a><span data-ttu-id="c9061-113">Domyślna przestrzeń nazw</span><span class="sxs-lookup"><span data-stu-id="c9061-113">The Default Namespace</span></span>  
 <span data-ttu-id="c9061-114">W poniższym dokumencie XML, domyślna przestrzeń nazw z pustym prefiksem jest używana do deklarowania przestrzeni nazw `http://www.contoso.com/books`.</span><span class="sxs-lookup"><span data-stu-id="c9061-114">In the XML document that follows, the default namespace with an empty prefix is used to declare the `http://www.contoso.com/books` namespace.</span></span>  
  
```xml  
<books xmlns="http://www.contoso.com/books">  
    <book>  
        <title>Title</title>  
        <author>Author Name</author>  
        <price>5.50</price>  
    </book>  
</books>  
```  
  
 <span data-ttu-id="c9061-115">Wyrażenie XPath traktuje pusty prefiks jako przestrzeń nazw `null`.</span><span class="sxs-lookup"><span data-stu-id="c9061-115">XPath treats the empty prefix as the `null` namespace.</span></span> <span data-ttu-id="c9061-116">Innymi słowy, tylko prefiksy mapowane na przestrzenie nazw mogą być używane w zapytaniach XPath.</span><span class="sxs-lookup"><span data-stu-id="c9061-116">In other words, only prefixes mapped to namespaces can be used in XPath queries.</span></span> <span data-ttu-id="c9061-117">Oznacza to, że jeśli chcesz wykonać zapytanie względem przestrzeni nazw w dokumencie XML, nawet jeśli jest to domyślna przestrzeń nazw, musisz zdefiniować dla niej prefiks.</span><span class="sxs-lookup"><span data-stu-id="c9061-117">This means that if you want to query against a namespace in an XML document, even if it is the default namespace, you need to define a prefix for it.</span></span>  
  
 <span data-ttu-id="c9061-118">Na przykład, bez definiowania prefiksu dla dokumentu XML powyżej, zapytanie XPath `/books/book` nie zwróci żadnych wyników.</span><span class="sxs-lookup"><span data-stu-id="c9061-118">For example, without defining a prefix for the XML document above, the XPath query `/books/book` would not return any results.</span></span>  
  
 <span data-ttu-id="c9061-119">Prefiks musi być powiązany, aby zapobiec niejednoznaczności podczas wykonywania zapytania o dokumenty z niektórymi węzłami, a niektóre w domyślnej przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="c9061-119">A prefix must be bound to prevent ambiguity when querying documents with some nodes not in a namespace, and some in a default namespace.</span></span>  
  
 <span data-ttu-id="c9061-120">Poniższy kod definiuje prefiks domyślnej przestrzeni nazw i zaznacza wszystkie elementy `book` z przestrzeni nazw `http://www.contoso.com/books`.</span><span class="sxs-lookup"><span data-stu-id="c9061-120">The following code defines a prefix for the default namespace and selects all the `book` elements from the `http://www.contoso.com/books` namespace.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="c9061-121">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c9061-121">See also</span></span>

- <xref:System.Xml.XmlDocument>
- <xref:System.Xml.XPath.XPathDocument>
- <xref:System.Xml.XPath.XPathNavigator>
- [<span data-ttu-id="c9061-122">Przetwarzanie danych XML przy użyciu modelu danych XPath</span><span class="sxs-lookup"><span data-stu-id="c9061-122">Process XML Data Using the XPath Data Model</span></span>](../../../../docs/standard/data/xml/process-xml-data-using-the-xpath-data-model.md)
- [<span data-ttu-id="c9061-123">Wybieranie danych XML przy użyciu klasy XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="c9061-123">Select XML Data Using XPathNavigator</span></span>](../../../../docs/standard/data/xml/select-xml-data-using-xpathnavigator.md)
- [<span data-ttu-id="c9061-124">Obliczanie wyrażeń XPath przy użyciu klasy XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="c9061-124">Evaluate XPath Expressions using XPathNavigator</span></span>](../../../../docs/standard/data/xml/evaluate-xpath-expressions-using-xpathnavigator.md)
- [<span data-ttu-id="c9061-125">Dopasowywanie węzłów przy użyciu klasy XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="c9061-125">Matching Nodes using XPathNavigator</span></span>](../../../../docs/standard/data/xml/matching-nodes-using-xpathnavigator.md)
- [<span data-ttu-id="c9061-126">Typy węzłów rozpoznawanych w zapytaniach XPath</span><span class="sxs-lookup"><span data-stu-id="c9061-126">Node Types Recognized with XPath Queries</span></span>](../../../../docs/standard/data/xml/node-types-recognized-with-xpath-queries.md)
- [<span data-ttu-id="c9061-127">Skompilowane wyrażenia XPath</span><span class="sxs-lookup"><span data-stu-id="c9061-127">Compiled XPath Expressions</span></span>](../../../../docs/standard/data/xml/compiled-xpath-expressions.md)
