---
title: Wybieranie węzłów za pomocą nawigacji XPath
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 8e4450dc-56b3-472b-b467-32f5694f83ad
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 9e02dd304893e4d9354144c5b412dfd145161c6e
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/14/2018
ms.locfileid: "45596952"
---
# <a name="select-nodes-using-xpath-navigation"></a><span data-ttu-id="6c159-102">Wybieranie węzłów za pomocą nawigacji XPath</span><span class="sxs-lookup"><span data-stu-id="6c159-102">Select Nodes Using XPath Navigation</span></span>
<span data-ttu-id="6c159-103">XML Document Object Model (DOM) zawiera metody, które pozwalają na korzystanie z nawigacji z XML Path Language (XPath) do zapytania w modelu DOM.</span><span class="sxs-lookup"><span data-stu-id="6c159-103">The XML Document Object Model (DOM) contains methods that allow you to use XML Path Language (XPath) navigation to query information in the DOM.</span></span> <span data-ttu-id="6c159-104">Można odnaleźć węzła jednej, określonej lub aby znaleźć wszystkie węzły, które spełniają pewne kryteria, można użyć języka XPath.</span><span class="sxs-lookup"><span data-stu-id="6c159-104">You can use XPath to find a single, specific node or to find all nodes that match some criteria.</span></span>  
  
## <a name="xpath-select-methods"></a><span data-ttu-id="6c159-105">Metody Wybierz wyrażenie XPath</span><span class="sxs-lookup"><span data-stu-id="6c159-105">XPath Select Methods</span></span>  
 <span data-ttu-id="6c159-106">Klasy modelu DOM zapewniają dwie metody elementu XPath: <xref:System.Xml.XmlNode.SelectSingleNode%2A> metody i <xref:System.Xml.XmlNode.SelectNodes%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="6c159-106">The DOM classes provide two methods for XPath selection: the <xref:System.Xml.XmlNode.SelectSingleNode%2A> method and the <xref:System.Xml.XmlNode.SelectNodes%2A> method.</span></span> <span data-ttu-id="6c159-107"><xref:System.Xml.XmlNode.SelectSingleNode%2A> Metoda zwraca pierwszy węzeł, który pasuje do kryteriów wyboru.</span><span class="sxs-lookup"><span data-stu-id="6c159-107">The <xref:System.Xml.XmlNode.SelectSingleNode%2A> method returns the first node that matches the selection criteria.</span></span> <span data-ttu-id="6c159-108"><xref:System.Xml.XmlNode.SelectNodes%2A> Metoda zwraca <xref:System.Xml.XmlNodeList> zawierający pasujące węzły.</span><span class="sxs-lookup"><span data-stu-id="6c159-108">The <xref:System.Xml.XmlNode.SelectNodes%2A> method returns an <xref:System.Xml.XmlNodeList> that contains the matching nodes.</span></span>  
  
 <span data-ttu-id="6c159-109">W poniższym przykładzie użyto <xref:System.Xml.XmlNode.SelectSingleNode%2A> metody, zaznacz pierwszą pozycję `book` węzła, w którym nazwisko autora spełnia określone kryteria.</span><span class="sxs-lookup"><span data-stu-id="6c159-109">The following example uses the <xref:System.Xml.XmlNode.SelectSingleNode%2A> method to select the first `book` node in which the author's last name meets the specified criteria.</span></span> <span data-ttu-id="6c159-110">Plik bookstore.xml, (która znajduje się na końcu tego tematu) jest używany jako plik wejściowy.</span><span class="sxs-lookup"><span data-stu-id="6c159-110">The bookstore.xml file (which is provided at the end of this topic) is used as the input file.</span></span>  
  
```vb  
Dim doc As New XmlDocument()  
doc.Load("bookstore.xml")  
Dim root As XmlNode = doc.DocumentElement  
  
' Add the namespace.  
Dim nsmgr As New XmlNamespaceManager(doc.NameTable)  
nsmgr.AddNamespace("bk", "urn:newbooks-schema")  
  
' Select and display the first node in which the author's   
' last name is Kingsolver.  
Dim node As XmlNode = root.SelectSingleNode( _  
     "descendant::bk:book[bk:author/bk:last-name='Kingsolver']", nsmgr)  
Console.WriteLine(node.InnerXml)  
```  
  
```csharp  
// Load the document and set the root element.  
XmlDocument doc = new XmlDocument();  
doc.Load("bookstore.xml");  
XmlNode root = doc.DocumentElement;  
  
// Add the namespace.  
XmlNamespaceManager nsmgr = new XmlNamespaceManager(doc.NameTable);  
nsmgr.AddNamespace("bk", "urn:newbooks-schema");  
  
// Select and display the first node in which the author's   
// last name is Kingsolver.  
XmlNode node = root.SelectSingleNode(  
    "descendant::bk:book[bk:author/bk:last-name='Kingsolver']", nsmgr);  
Console.WriteLine(node.InnerXml);  
```  
  
 <span data-ttu-id="6c159-111">W następnym przykładzie użyto <xref:System.Xml.XmlNode.SelectNodes%2A> metodę, aby zaznaczyć wszystkie węzły książki, w których cena jest większy niż określony.</span><span class="sxs-lookup"><span data-stu-id="6c159-111">The next example uses the <xref:System.Xml.XmlNode.SelectNodes%2A> method to select all the book nodes in which the price is greater than a specified amount.</span></span> <span data-ttu-id="6c159-112">Dziesięć procent następnie zmniejszono programowo w ceny dla każdej książki z wybranej listy.</span><span class="sxs-lookup"><span data-stu-id="6c159-112">The price for each book in the selected list is then programmatically reduced by ten percent.</span></span> <span data-ttu-id="6c159-113">Na koniec zaktualizowany plik jest zapisywany do konsoli.</span><span class="sxs-lookup"><span data-stu-id="6c159-113">Finally, the updated file is written to the console.</span></span> <span data-ttu-id="6c159-114">Plik bookstore.xml, (która znajduje się na końcu tego tematu) jest używany jako plik wejściowy.</span><span class="sxs-lookup"><span data-stu-id="6c159-114">The bookstore.xml file (which is provided at the end of this topic) is used as the input file.</span></span>  
  
```vb  
' Load the document and set the root element.  
Dim doc As New XmlDocument()  
doc.Load("bookstore.xml")  
Dim root As XmlNode = doc.DocumentElement  
  
' Add the namespace.  
Dim nsmgr As New XmlNamespaceManager(doc.NameTable)  
nsmgr.AddNamespace("bk", "urn:newbooks-schema")  
  
' Select all nodes where the book price is greater than 10.00.  
Dim nodeList As XmlNodeList = root.SelectNodes( _  
     "descendant::bk:book[bk:price>10.00]", nsmgr)  
For Each book As XmlNode In nodeList  
     Dim price As Double  
     price = Math.Round(Convert.ToSingle( _  
          book.LastChild.InnerText) * 0.9, 2)  
     book.LastChild.InnerText = price.ToString()  
Next  
  
' Display the updated document.  
doc.Save(Console.Out)  
```  
  
```csharp  
// Load the document and set the root element.  
XmlDocument doc = new XmlDocument();  
doc.Load("bookstore.xml");  
XmlNode root = doc.DocumentElement;  
  
// Add the namespace.  
XmlNamespaceManager nsmgr = new XmlNamespaceManager(doc.NameTable);  
nsmgr.AddNamespace("bk", "urn:newbooks-schema");  
  
// Select all nodes where the book price is greater than 10.00.  
XmlNodeList nodeList = root.SelectNodes(  
     "descendant::bk:book[bk:price>10.00]", nsmgr);  
foreach (XmlNode book in nodeList)  
{  
     // Discount prices by 10%.  
     double price;  
     price = Math.Round(Convert.ToSingle(  
          book.LastChild.InnerText) * 0.9, 2);  
     book.LastChild.InnerText = price.ToString();  
}  
  
// Display the updated document.  
doc.Save(Console.Out);  
```  
  
 <span data-ttu-id="6c159-115">Powyższe przykłady uruchom zapytanie XPath w element dokumentu.</span><span class="sxs-lookup"><span data-stu-id="6c159-115">The examples above start the XPath query at the document element.</span></span> <span data-ttu-id="6c159-116">Ustawienie punkt początkowy dla wyrażenia XPath zapytania ustawia węzła kontekstu, który jest punktem wyjścia dla kwerendy XPath.</span><span class="sxs-lookup"><span data-stu-id="6c159-116">Setting the starting point for the XPath query sets the context node, which is the starting point for the XPath query.</span></span> <span data-ttu-id="6c159-117">Jeśli nie chcesz rozpocząć od element dokumentu, ale chcesz rozpocząć od pierwszego elementu podrzędnego elementu dokumentu, możesz programować instrukcji select w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="6c159-117">If you do not want to start at the document element, but want to start from the first child of the document element, you can code the select statement as follows:</span></span>  
  
```vb  
doc.DocumentElement.FirstChild.SelectNodes(. . . )  
```  
  
```csharp  
this doc.DocumentElement.FirstChild.SelectNodes(. . .);  
```  
  
 <span data-ttu-id="6c159-118">Wszystkie <xref:System.Xml.XmlNodeList> obiekty są synchronizowane z podstawowej dokumentu.</span><span class="sxs-lookup"><span data-stu-id="6c159-118">All <xref:System.Xml.XmlNodeList> objects are synchronized with the underlying document.</span></span> <span data-ttu-id="6c159-119">W związku z tym jeśli iteracji przez listę węzłów, a następnie zmodyfikuj wartość węzła, węzeł zostaje również zaktualizowany w dokumencie, z której pochodzi.</span><span class="sxs-lookup"><span data-stu-id="6c159-119">Therefore, if you iterate through the node list and modify the value of a node, that node is also updated in the document it came from.</span></span> <span data-ttu-id="6c159-120">Powiadomienie w poprzednim przykładzie, gdy węzeł zostanie zmodyfikowany w wybranym <xref:System.Xml.XmlNodeList> dokumentu podstawowego jest modyfikowana również.</span><span class="sxs-lookup"><span data-stu-id="6c159-120">Notice in the previous example that when a node is modified in the selected <xref:System.Xml.XmlNodeList> the underlying document is also modified.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="6c159-121">Po zmodyfikowaniu dokumentu podstawowego, zalecane jest ponowne uruchomienie wyboru.</span><span class="sxs-lookup"><span data-stu-id="6c159-121">When the underlying document is modified, it is advisable to rerun the select.</span></span> <span data-ttu-id="6c159-122">Jeśli węzeł zmodyfikowane jest taki, który może spowodować, że węzeł, który ma zostać dodany do listy węzłów, gdy nie był wcześniej lub teraz spowoduje usunięcie z listy węzłów, ma żadnej gwarancji, że listy węzłów jest prawidłowo wprowadzony.</span><span class="sxs-lookup"><span data-stu-id="6c159-122">If the node modified is one that could cause the node to be added to the node list when it was not previously, or would now cause it to be removed from the node list, there is no guarantee that the node list is now accurate.</span></span>  
  
## <a name="namespaces-in-xpath-expressions"></a><span data-ttu-id="6c159-123">Przestrzenie nazw w wyrażeniach języka XPath</span><span class="sxs-lookup"><span data-stu-id="6c159-123">Namespaces in XPath Expressions</span></span>  
 <span data-ttu-id="6c159-124">Wyrażenia XPath mogą obejmować obszary nazw.</span><span class="sxs-lookup"><span data-stu-id="6c159-124">XPath expressions can include namespaces.</span></span> <span data-ttu-id="6c159-125">Rozpoznawanie Namespace jest obsługiwane przy użyciu <xref:System.Xml.XmlNamespaceManager>.</span><span class="sxs-lookup"><span data-stu-id="6c159-125">Namespace resolution is supported using the <xref:System.Xml.XmlNamespaceManager>.</span></span> <span data-ttu-id="6c159-126">Jeśli wyrażenie XPath zawiera prefiks, pary prefiksu i obszaru nazw. identyfikator URI musi zostać dodany do <xref:System.Xml.XmlNamespaceManager>i <xref:System.Xml.XmlNamespaceManager> jest przekazywany do <xref:System.Xml.XmlNode.SelectNodes%28System.String%2CSystem.Xml.XmlNamespaceManager%29> lub <xref:System.Xml.XmlNode.SelectSingleNode%28System.String%2CSystem.Xml.XmlNamespaceManager%29> metody.</span><span class="sxs-lookup"><span data-stu-id="6c159-126">If the XPath expression includes a prefix, the prefix and namespace URI pair must be added to the <xref:System.Xml.XmlNamespaceManager>, and the <xref:System.Xml.XmlNamespaceManager> is passed to the <xref:System.Xml.XmlNode.SelectNodes%28System.String%2CSystem.Xml.XmlNamespaceManager%29> or <xref:System.Xml.XmlNode.SelectSingleNode%28System.String%2CSystem.Xml.XmlNamespaceManager%29> method.</span></span> <span data-ttu-id="6c159-127">Należy zauważyć, że powyższe przykłady kodu, użyj <xref:System.Xml.XmlNamespaceManager> można rozpoznać przestrzeni nazw dokumentu bookstore.xml.</span><span class="sxs-lookup"><span data-stu-id="6c159-127">Notice that the code examples above use the <xref:System.Xml.XmlNamespaceManager> to resolve the namespace of the bookstore.xml document.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="6c159-128">Jeśli wyrażenie XPath nie zawiera prefiksu, zakłada się, że przestrzeń nazw identyfikator (URI) jest pusta przestrzeń nazw.</span><span class="sxs-lookup"><span data-stu-id="6c159-128">If the XPath expression does not include a prefix, it is assumed that the namespace Uniform Resource Identifier (URI) is the empty namespace.</span></span> <span data-ttu-id="6c159-129">Jeśli dane XML zawiera domyślny obszar nazw, nadal należy dodać prefiksu i identyfikator URI przestrzeni nazw do <xref:System.Xml.XmlNamespaceManager>; w przeciwnym razie zostanie wybrany żadnych węzłów.</span><span class="sxs-lookup"><span data-stu-id="6c159-129">If your XML includes a default namespace, you must still add a prefix and namespace URI to the <xref:System.Xml.XmlNamespaceManager>; otherwise, no nodes will be selected.</span></span>  
  
#### <a name="input-file"></a><span data-ttu-id="6c159-130">Plik wejściowy</span><span class="sxs-lookup"><span data-stu-id="6c159-130">Input File</span></span>  
 <span data-ttu-id="6c159-131">Poniżej znajduje się plik bookstore.xml, która jest używana jako plik wejściowy w przykładach w tym temacie:</span><span class="sxs-lookup"><span data-stu-id="6c159-131">The following is the bookstore.xml file that is used as the input file in the examples in this topic:</span></span>  
  
```xml  
<?xml version='1.0'?>  
<bookstore xmlns="urn:newbooks-schema">  
  <book genre="novel" style="hardcover">  
    <title>The Handmaid's Tale</title>  
    <author>  
      <first-name>Margaret</first-name>  
      <last-name>Atwood</last-name>  
    </author>  
    <price>19.95</price>  
  </book>  
  <book genre="novel" style="other">  
    <title>The Poisonwood Bible</title>  
    <author>  
      <first-name>Barbara</first-name>  
      <last-name>Kingsolver</last-name>  
    </author>  
    <price>11.99</price>  
  </book>  
  <book genre="novel" style="paperback">  
    <title>The Bean Trees</title>  
    <author>  
      <first-name>Barbara</first-name>  
      <last-name>Kingsolver</last-name>  
    </author>  
    <price>5.99</price>  
  </book>  
</bookstore>  
```  
  
## <a name="see-also"></a><span data-ttu-id="6c159-132">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="6c159-132">See also</span></span>

- [<span data-ttu-id="6c159-133">Model DOM (XML Document Object Model)</span><span class="sxs-lookup"><span data-stu-id="6c159-133">XML Document Object Model (DOM)</span></span>](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
