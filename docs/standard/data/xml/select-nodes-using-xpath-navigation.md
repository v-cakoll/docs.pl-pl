---
title: Wybieranie węzłów za pomocą nawigacji XPath
description: Dowiedz się, jak wybrać węzły XML w programie .NET. Użyj metod Document Object Model (DOM), aby móc używać nawigacji języka ścieżki XML (XPath) do wykonywania zapytań dotyczących informacji DOM.
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 8e4450dc-56b3-472b-b467-32f5694f83ad
ms.openlocfilehash: aa8b6d93e25d974a0e1b53ae8be9868f6bf64be6
ms.sourcegitcommit: 7137e12f54c4e83a94ae43ec320f8cf59c1772ea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/10/2020
ms.locfileid: "84662514"
---
# <a name="select-nodes-using-xpath-navigation"></a><span data-ttu-id="8b9a3-104">Wybieranie węzłów za pomocą nawigacji XPath</span><span class="sxs-lookup"><span data-stu-id="8b9a3-104">Select Nodes Using XPath Navigation</span></span>
<span data-ttu-id="8b9a3-105">Document Object Model XML (DOM) zawiera metody umożliwiające użycie nawigacji języka ścieżki XML (XPath) do wykonywania zapytań dotyczących informacji w modelu DOM.</span><span class="sxs-lookup"><span data-stu-id="8b9a3-105">The XML Document Object Model (DOM) contains methods that allow you to use XML Path Language (XPath) navigation to query information in the DOM.</span></span> <span data-ttu-id="8b9a3-106">Możesz użyć XPath, aby znaleźć pojedynczy, konkretny węzeł lub znaleźć wszystkie węzły, które pasują do niektórych kryteriów.</span><span class="sxs-lookup"><span data-stu-id="8b9a3-106">You can use XPath to find a single, specific node or to find all nodes that match some criteria.</span></span>  
  
## <a name="xpath-select-methods"></a><span data-ttu-id="8b9a3-107">Metody Select XPath</span><span class="sxs-lookup"><span data-stu-id="8b9a3-107">XPath Select Methods</span></span>  
 <span data-ttu-id="8b9a3-108">Klasy DOM zapewniają dwie metody wyboru XPath: <xref:System.Xml.XmlNode.SelectSingleNode%2A> metodę i <xref:System.Xml.XmlNode.SelectNodes%2A> metodę.</span><span class="sxs-lookup"><span data-stu-id="8b9a3-108">The DOM classes provide two methods for XPath selection: the <xref:System.Xml.XmlNode.SelectSingleNode%2A> method and the <xref:System.Xml.XmlNode.SelectNodes%2A> method.</span></span> <span data-ttu-id="8b9a3-109"><xref:System.Xml.XmlNode.SelectSingleNode%2A>Metoda zwraca pierwszy węzeł, który pasuje do kryteriów wyboru.</span><span class="sxs-lookup"><span data-stu-id="8b9a3-109">The <xref:System.Xml.XmlNode.SelectSingleNode%2A> method returns the first node that matches the selection criteria.</span></span> <span data-ttu-id="8b9a3-110"><xref:System.Xml.XmlNode.SelectNodes%2A>Metoda zwraca obiekt <xref:System.Xml.XmlNodeList> , który zawiera pasujące węzły.</span><span class="sxs-lookup"><span data-stu-id="8b9a3-110">The <xref:System.Xml.XmlNode.SelectNodes%2A> method returns an <xref:System.Xml.XmlNodeList> that contains the matching nodes.</span></span>  
  
 <span data-ttu-id="8b9a3-111">W poniższym przykładzie zastosowano <xref:System.Xml.XmlNode.SelectSingleNode%2A> metodę, aby wybrać pierwszy `book` węzeł, w którym nazwisko autora spełnia określone kryteria.</span><span class="sxs-lookup"><span data-stu-id="8b9a3-111">The following example uses the <xref:System.Xml.XmlNode.SelectSingleNode%2A> method to select the first `book` node in which the author's last name meets the specified criteria.</span></span> <span data-ttu-id="8b9a3-112">Plik bookstore.xml (który znajduje się na końcu tego tematu) jest używany jako plik wejściowy.</span><span class="sxs-lookup"><span data-stu-id="8b9a3-112">The bookstore.xml file (which is provided at the end of this topic) is used as the input file.</span></span>  
  
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
  
 <span data-ttu-id="8b9a3-113">W następnym przykładzie używa się <xref:System.Xml.XmlNode.SelectNodes%2A> metody, aby wybrać wszystkie węzły książek, w których cena jest większa niż określona wartość.</span><span class="sxs-lookup"><span data-stu-id="8b9a3-113">The next example uses the <xref:System.Xml.XmlNode.SelectNodes%2A> method to select all the book nodes in which the price is greater than a specified amount.</span></span> <span data-ttu-id="8b9a3-114">Cena dla każdej książki na wybranej liście jest następnie programowo zmniejszona o dziesięć procent.</span><span class="sxs-lookup"><span data-stu-id="8b9a3-114">The price for each book in the selected list is then programmatically reduced by ten percent.</span></span> <span data-ttu-id="8b9a3-115">Na koniec zaktualizowany plik jest zapisywana w konsoli programu.</span><span class="sxs-lookup"><span data-stu-id="8b9a3-115">Finally, the updated file is written to the console.</span></span> <span data-ttu-id="8b9a3-116">Plik bookstore.xml (który znajduje się na końcu tego tematu) jest używany jako plik wejściowy.</span><span class="sxs-lookup"><span data-stu-id="8b9a3-116">The bookstore.xml file (which is provided at the end of this topic) is used as the input file.</span></span>  
  
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
  
 <span data-ttu-id="8b9a3-117">Powyższe przykłady rozpoczynają kwerendę XPath w elemencie dokumentu.</span><span class="sxs-lookup"><span data-stu-id="8b9a3-117">The examples above start the XPath query at the document element.</span></span> <span data-ttu-id="8b9a3-118">Ustawienie punktu początkowego dla zapytania XPath ustawia węzeł kontekstu, który jest punktem początkowym zapytania XPath.</span><span class="sxs-lookup"><span data-stu-id="8b9a3-118">Setting the starting point for the XPath query sets the context node, which is the starting point for the XPath query.</span></span> <span data-ttu-id="8b9a3-119">Jeśli nie chcesz zacząć od elementu dokumentu, ale chcesz zacząć od pierwszego obiektu podrzędnego elementu dokumentu, możesz kod instrukcji SELECT w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="8b9a3-119">If you do not want to start at the document element, but want to start from the first child of the document element, you can code the select statement as follows:</span></span>  
  
```vb  
doc.DocumentElement.FirstChild.SelectNodes(. . . )  
```  
  
```csharp  
this doc.DocumentElement.FirstChild.SelectNodes(. . .);  
```  
  
 <span data-ttu-id="8b9a3-120">Wszystkie <xref:System.Xml.XmlNodeList> obiekty są synchronizowane z dokumentem źródłowym.</span><span class="sxs-lookup"><span data-stu-id="8b9a3-120">All <xref:System.Xml.XmlNodeList> objects are synchronized with the underlying document.</span></span> <span data-ttu-id="8b9a3-121">W związku z tym, jeśli przeprowadzisz iterację listy węzłów i zmodyfikujesz wartość węzła, ten węzeł zostanie również zaktualizowany w dokumencie, z którego pochodzi.</span><span class="sxs-lookup"><span data-stu-id="8b9a3-121">Therefore, if you iterate through the node list and modify the value of a node, that node is also updated in the document it came from.</span></span> <span data-ttu-id="8b9a3-122">Zwróć uwagę, że w poprzednim przykładzie modyfikowany jest również węzeł w wybranym <xref:System.Xml.XmlNodeList> dokumencie źródłowym.</span><span class="sxs-lookup"><span data-stu-id="8b9a3-122">Notice in the previous example that when a node is modified in the selected <xref:System.Xml.XmlNodeList> the underlying document is also modified.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="8b9a3-123">Po zmodyfikowaniu dokumentu bazowego zaleca się ponowne uruchomienie SELECT.</span><span class="sxs-lookup"><span data-stu-id="8b9a3-123">When the underlying document is modified, it is advisable to rerun the select.</span></span> <span data-ttu-id="8b9a3-124">Jeśli zmodyfikowany węzeł to taki, który może spowodować dodanie węzła do listy węzłów, gdy nie był wcześniej, lub spowoduje usunięcie go z listy węzłów, nie ma gwarancji, że lista węzłów jest teraz dokładna.</span><span class="sxs-lookup"><span data-stu-id="8b9a3-124">If the node modified is one that could cause the node to be added to the node list when it was not previously, or would now cause it to be removed from the node list, there is no guarantee that the node list is now accurate.</span></span>  
  
## <a name="namespaces-in-xpath-expressions"></a><span data-ttu-id="8b9a3-125">Przestrzenie nazw w wyrażeniach XPath</span><span class="sxs-lookup"><span data-stu-id="8b9a3-125">Namespaces in XPath Expressions</span></span>  
 <span data-ttu-id="8b9a3-126">Wyrażenia XPath mogą zawierać przestrzenie nazw.</span><span class="sxs-lookup"><span data-stu-id="8b9a3-126">XPath expressions can include namespaces.</span></span> <span data-ttu-id="8b9a3-127">Rozpoznawanie przestrzeni nazw jest obsługiwane przy użyciu <xref:System.Xml.XmlNamespaceManager> .</span><span class="sxs-lookup"><span data-stu-id="8b9a3-127">Namespace resolution is supported using the <xref:System.Xml.XmlNamespaceManager>.</span></span> <span data-ttu-id="8b9a3-128">Jeśli wyrażenie XPath zawiera prefiks, para identyfikatorów URI prefiksu i przestrzeni nazw musi zostać dodana do <xref:System.Xml.XmlNamespaceManager> i <xref:System.Xml.XmlNamespaceManager> jest przenoszona do <xref:System.Xml.XmlNode.SelectNodes%28System.String%2CSystem.Xml.XmlNamespaceManager%29> <xref:System.Xml.XmlNode.SelectSingleNode%28System.String%2CSystem.Xml.XmlNamespaceManager%29> metody lub.</span><span class="sxs-lookup"><span data-stu-id="8b9a3-128">If the XPath expression includes a prefix, the prefix and namespace URI pair must be added to the <xref:System.Xml.XmlNamespaceManager>, and the <xref:System.Xml.XmlNamespaceManager> is passed to the <xref:System.Xml.XmlNode.SelectNodes%28System.String%2CSystem.Xml.XmlNamespaceManager%29> or <xref:System.Xml.XmlNode.SelectSingleNode%28System.String%2CSystem.Xml.XmlNamespaceManager%29> method.</span></span> <span data-ttu-id="8b9a3-129">Zauważ, że w przykładach kodu Użyj, <xref:System.Xml.XmlNamespaceManager> Aby rozpoznać przestrzeń nazw bookstore.xml dokumentu.</span><span class="sxs-lookup"><span data-stu-id="8b9a3-129">Notice that the code examples above use the <xref:System.Xml.XmlNamespaceManager> to resolve the namespace of the bookstore.xml document.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="8b9a3-130">Jeśli wyrażenie XPath nie zawiera prefiksu, zakłada się, że przestrzeń nazw Uniform Resource Identifier (URI) jest pustą przestrzenią nazw.</span><span class="sxs-lookup"><span data-stu-id="8b9a3-130">If the XPath expression does not include a prefix, it is assumed that the namespace Uniform Resource Identifier (URI) is the empty namespace.</span></span> <span data-ttu-id="8b9a3-131">Jeśli plik XML zawiera domyślną przestrzeń nazw, nadal trzeba dodać prefiks i identyfikator URI przestrzeni nazw do <xref:System.Xml.XmlNamespaceManager> ; w przeciwnym razie nie zostaną wybrane węzły.</span><span class="sxs-lookup"><span data-stu-id="8b9a3-131">If your XML includes a default namespace, you must still add a prefix and namespace URI to the <xref:System.Xml.XmlNamespaceManager>; otherwise, no nodes will be selected.</span></span>  
  
#### <a name="input-file"></a><span data-ttu-id="8b9a3-132">Plik wejściowy</span><span class="sxs-lookup"><span data-stu-id="8b9a3-132">Input File</span></span>  
 <span data-ttu-id="8b9a3-133">Poniżej znajduje się plik bookstore.xml, który jest używany jako plik wejściowy w przykładach w tym temacie:</span><span class="sxs-lookup"><span data-stu-id="8b9a3-133">The following is the bookstore.xml file that is used as the input file in the examples in this topic:</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="8b9a3-134">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="8b9a3-134">See also</span></span>

- [<span data-ttu-id="8b9a3-135">XML Document Object Model (DOM)</span><span class="sxs-lookup"><span data-stu-id="8b9a3-135">XML Document Object Model (DOM)</span></span>](xml-document-object-model-dom.md)
