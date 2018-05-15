---
title: Wybierz węzeł, za pomocą wyrażenia XPath nawigacji
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 8e4450dc-56b3-472b-b467-32f5694f83ad
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 8c5a7b9113dd5a4de929f5b88569be89bc1f2c89
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="select-nodes-using-xpath-navigation"></a><span data-ttu-id="099c0-102">Wybierz węzeł, za pomocą wyrażenia XPath nawigacji</span><span class="sxs-lookup"><span data-stu-id="099c0-102">Select Nodes Using XPath Navigation</span></span>
<span data-ttu-id="099c0-103">XML modelu DOM (Document Object) zawiera metody, które umożliwiają użycie nawigacji XML Path Language (XPath) do informacji dotyczących zapytań w modelu DOM.</span><span class="sxs-lookup"><span data-stu-id="099c0-103">The XML Document Object Model (DOM) contains methods that allow you to use XML Path Language (XPath) navigation to query information in the DOM.</span></span> <span data-ttu-id="099c0-104">Można znaleźć węzła jednej, określonej lub aby znaleźć wszystkie węzły, które spełniają pewne kryteria, można użyć wyrażenia XPath.</span><span class="sxs-lookup"><span data-stu-id="099c0-104">You can use XPath to find a single, specific node or to find all nodes that match some criteria.</span></span>  
  
## <a name="xpath-select-methods"></a><span data-ttu-id="099c0-105">Wybierz XPath metody</span><span class="sxs-lookup"><span data-stu-id="099c0-105">XPath Select Methods</span></span>  
 <span data-ttu-id="099c0-106">Klasy modelu DOM Podaj dwie metody składnik elementu XPath: <xref:System.Xml.XmlNode.SelectSingleNode%2A> — metoda i <xref:System.Xml.XmlNode.SelectNodes%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="099c0-106">The DOM classes provide two methods for XPath selection: the <xref:System.Xml.XmlNode.SelectSingleNode%2A> method and the <xref:System.Xml.XmlNode.SelectNodes%2A> method.</span></span> <span data-ttu-id="099c0-107"><xref:System.Xml.XmlNode.SelectSingleNode%2A> Metoda zwraca pierwszy węzeł, który spełnia kryteria wyboru.</span><span class="sxs-lookup"><span data-stu-id="099c0-107">The <xref:System.Xml.XmlNode.SelectSingleNode%2A> method returns the first node that matches the selection criteria.</span></span> <span data-ttu-id="099c0-108"><xref:System.Xml.XmlNode.SelectNodes%2A> Metoda zwraca <xref:System.Xml.XmlNodeList> zawierający zgodne węzły.</span><span class="sxs-lookup"><span data-stu-id="099c0-108">The <xref:System.Xml.XmlNode.SelectNodes%2A> method returns an <xref:System.Xml.XmlNodeList> that contains the matching nodes.</span></span>  
  
 <span data-ttu-id="099c0-109">W poniższym przykładzie użyto <xref:System.Xml.XmlNode.SelectSingleNode%2A> metody, aby zaznaczyć pierwszy `book` węzła, w którym nazwisko autora spełnia określone kryteria.</span><span class="sxs-lookup"><span data-stu-id="099c0-109">The following example uses the <xref:System.Xml.XmlNode.SelectSingleNode%2A> method to select the first `book` node in which the author's last name meets the specified criteria.</span></span> <span data-ttu-id="099c0-110">Plik bookstore.xml (która jest dostępna na końcu tego tematu) jest używany jako plik wejściowy.</span><span class="sxs-lookup"><span data-stu-id="099c0-110">The bookstore.xml file (which is provided at the end of this topic) is used as the input file.</span></span>  
  
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
  
 <span data-ttu-id="099c0-111">W następnym przykładzie użyto <xref:System.Xml.XmlNode.SelectNodes%2A> metoda, aby wybrać wszystkie węzły książki, w których cena jest większa od określonej wartości.</span><span class="sxs-lookup"><span data-stu-id="099c0-111">The next example uses the <xref:System.Xml.XmlNode.SelectNodes%2A> method to select all the book nodes in which the price is greater than a specified amount.</span></span> <span data-ttu-id="099c0-112">Ceny dla każdej księgi na wybranej liście jest programowo zmniejszana o 10 procent.</span><span class="sxs-lookup"><span data-stu-id="099c0-112">The price for each book in the selected list is then programmatically reduced by ten percent.</span></span> <span data-ttu-id="099c0-113">Na koniec zaktualizowany plik zostanie zapisany do konsoli.</span><span class="sxs-lookup"><span data-stu-id="099c0-113">Finally, the updated file is written to the console.</span></span> <span data-ttu-id="099c0-114">Plik bookstore.xml (która jest dostępna na końcu tego tematu) jest używany jako plik wejściowy.</span><span class="sxs-lookup"><span data-stu-id="099c0-114">The bookstore.xml file (which is provided at the end of this topic) is used as the input file.</span></span>  
  
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
  
 <span data-ttu-id="099c0-115">Powyższe przykłady uruchomić zapytanie XPath w elemencie dokumentu.</span><span class="sxs-lookup"><span data-stu-id="099c0-115">The examples above start the XPath query at the document element.</span></span> <span data-ttu-id="099c0-116">Ustawianie punkt początkowy dla wyrażenia XPath zapytania ustawia węzeł kontekstu, czyli punkt początkowy dla zapytania XPath.</span><span class="sxs-lookup"><span data-stu-id="099c0-116">Setting the starting point for the XPath query sets the context node, which is the starting point for the XPath query.</span></span> <span data-ttu-id="099c0-117">Jeśli nie chcesz rozpocząć od element dokumentu, ale chcesz rozpocząć od pierwszego elementu podrzędnego elementu dokumentu, można kodu instrukcji select w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="099c0-117">If you do not want to start at the document element, but want to start from the first child of the document element, you can code the select statement as follows:</span></span>  
  
```vb  
doc.DocumentElement.FirstChild.SelectNodes(. . . )  
```  
  
```csharp  
this doc.DocumentElement.FirstChild.SelectNodes(. . .);  
```  
  
 <span data-ttu-id="099c0-118">Wszystkie <xref:System.Xml.XmlNodeList> obiekty są synchronizowane z dokumentu źródłowego.</span><span class="sxs-lookup"><span data-stu-id="099c0-118">All <xref:System.Xml.XmlNodeList> objects are synchronized with the underlying document.</span></span> <span data-ttu-id="099c0-119">W związku z tym jeśli Iterowanie za pomocą listy węzłów i zmodyfikuj wartość węzła tego węzła zostaje również zaktualizowany w dokumencie, z której pochodzi.</span><span class="sxs-lookup"><span data-stu-id="099c0-119">Therefore, if you iterate through the node list and modify the value of a node, that node is also updated in the document it came from.</span></span> <span data-ttu-id="099c0-120">W poprzednim przykładzie który modyfikacji węzła w wybranym <xref:System.Xml.XmlNodeList> dokumentu podstawowego również jest modyfikowany.</span><span class="sxs-lookup"><span data-stu-id="099c0-120">Notice in the previous example that when a node is modified in the selected <xref:System.Xml.XmlNodeList> the underlying document is also modified.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="099c0-121">Podczas modyfikacji dokumentu podstawowego zalecane jest ponowne uruchomienie wyboru.</span><span class="sxs-lookup"><span data-stu-id="099c0-121">When the underlying document is modified, it is advisable to rerun the select.</span></span> <span data-ttu-id="099c0-122">Jeśli węzeł zmodyfikowane jest taki, który może spowodować, że węzeł, które mają zostać dodane do listy węzłów, gdy nie został wcześniej lub teraz spowodowałoby ma zostać usunięty z listy węzłów, nie ma żadnej gwarancji, że listy węzłów są prawidłowe.</span><span class="sxs-lookup"><span data-stu-id="099c0-122">If the node modified is one that could cause the node to be added to the node list when it was not previously, or would now cause it to be removed from the node list, there is no guarantee that the node list is now accurate.</span></span>  
  
## <a name="namespaces-in-xpath-expressions"></a><span data-ttu-id="099c0-123">Przestrzenie nazw w wyrażeniach języka XPath</span><span class="sxs-lookup"><span data-stu-id="099c0-123">Namespaces in XPath Expressions</span></span>  
 <span data-ttu-id="099c0-124">Wyrażenia XPath mogą zawierać przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="099c0-124">XPath expressions can include namespaces.</span></span> <span data-ttu-id="099c0-125">Rozdzielczość Namespace jest obsługiwana przy użyciu <xref:System.Xml.XmlNamespaceManager>.</span><span class="sxs-lookup"><span data-stu-id="099c0-125">Namespace resolution is supported using the <xref:System.Xml.XmlNamespaceManager>.</span></span> <span data-ttu-id="099c0-126">Jeśli wyrażenie XPath zawiera prefiks, pary prefiksu i przestrzeni nazw. identyfikator URI musi zostać dodany do <xref:System.Xml.XmlNamespaceManager>i <xref:System.Xml.XmlNamespaceManager> jest przekazywana do <xref:System.Xml.XmlNode.SelectNodes%28System.String%2CSystem.Xml.XmlNamespaceManager%29> lub <xref:System.Xml.XmlNode.SelectSingleNode%28System.String%2CSystem.Xml.XmlNamespaceManager%29> metody.</span><span class="sxs-lookup"><span data-stu-id="099c0-126">If the XPath expression includes a prefix, the prefix and namespace URI pair must be added to the <xref:System.Xml.XmlNamespaceManager>, and the <xref:System.Xml.XmlNamespaceManager> is passed to the <xref:System.Xml.XmlNode.SelectNodes%28System.String%2CSystem.Xml.XmlNamespaceManager%29> or <xref:System.Xml.XmlNode.SelectSingleNode%28System.String%2CSystem.Xml.XmlNamespaceManager%29> method.</span></span> <span data-ttu-id="099c0-127">Należy zauważyć, że powyższe przykłady kodu, użyj <xref:System.Xml.XmlNamespaceManager> można rozpoznać przestrzeni nazw bookstore.xml dokumentu.</span><span class="sxs-lookup"><span data-stu-id="099c0-127">Notice that the code examples above use the <xref:System.Xml.XmlNamespaceManager> to resolve the namespace of the bookstore.xml document.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="099c0-128">Jeśli wyrażenie XPath nie zawiera prefiks, zakłada się, że identyfikator URI (Uniform Resource) przestrzeń nazw jest pusta przestrzeń nazw.</span><span class="sxs-lookup"><span data-stu-id="099c0-128">If the XPath expression does not include a prefix, it is assumed that the namespace Uniform Resource Identifier (URI) is the empty namespace.</span></span> <span data-ttu-id="099c0-129">Jeśli dane XML zawiera domyślnej przestrzeni nazw, nadal należy dodać prefiks i identyfikator URI przestrzeni nazw do <xref:System.Xml.XmlNamespaceManager>; w przeciwnym razie zostanie wybrany żadnych węzłów.</span><span class="sxs-lookup"><span data-stu-id="099c0-129">If your XML includes a default namespace, you must still add a prefix and namespace URI to the <xref:System.Xml.XmlNamespaceManager>; otherwise, no nodes will be selected.</span></span>  
  
#### <a name="input-file"></a><span data-ttu-id="099c0-130">Plik wejściowy</span><span class="sxs-lookup"><span data-stu-id="099c0-130">Input File</span></span>  
 <span data-ttu-id="099c0-131">Poniżej znajduje się plik bookstore.xml, który jest używany jako pliku wejściowego w przykładach w niniejszym temacie:</span><span class="sxs-lookup"><span data-stu-id="099c0-131">The following is the bookstore.xml file that is used as the input file in the examples in this topic:</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="099c0-132">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="099c0-132">See Also</span></span>  
 [<span data-ttu-id="099c0-133">Model DOM (XML Document Object Model)</span><span class="sxs-lookup"><span data-stu-id="099c0-133">XML Document Object Model (DOM)</span></span>](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
