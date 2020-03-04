---
title: Wybieranie węzłów za pomocą nawigacji XPath
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 8e4450dc-56b3-472b-b467-32f5694f83ad
ms.openlocfilehash: 58f1487486c2802a2c64b51afcecb01c76dd291a
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/28/2020
ms.locfileid: "78155610"
---
# <a name="select-nodes-using-xpath-navigation"></a><span data-ttu-id="a2528-102">Wybieranie węzłów za pomocą nawigacji XPath</span><span class="sxs-lookup"><span data-stu-id="a2528-102">Select Nodes Using XPath Navigation</span></span>
<span data-ttu-id="a2528-103">Document Object Model XML (DOM) zawiera metody umożliwiające użycie nawigacji języka ścieżki XML (XPath) do wykonywania zapytań dotyczących informacji w modelu DOM.</span><span class="sxs-lookup"><span data-stu-id="a2528-103">The XML Document Object Model (DOM) contains methods that allow you to use XML Path Language (XPath) navigation to query information in the DOM.</span></span> <span data-ttu-id="a2528-104">Możesz użyć XPath, aby znaleźć pojedynczy, konkretny węzeł lub znaleźć wszystkie węzły, które pasują do niektórych kryteriów.</span><span class="sxs-lookup"><span data-stu-id="a2528-104">You can use XPath to find a single, specific node or to find all nodes that match some criteria.</span></span>  
  
## <a name="xpath-select-methods"></a><span data-ttu-id="a2528-105">Metody Select XPath</span><span class="sxs-lookup"><span data-stu-id="a2528-105">XPath Select Methods</span></span>  
 <span data-ttu-id="a2528-106">Klasy DOM zapewniają dwie metody wyboru XPath: metodę <xref:System.Xml.XmlNode.SelectSingleNode%2A> i metodę <xref:System.Xml.XmlNode.SelectNodes%2A>.</span><span class="sxs-lookup"><span data-stu-id="a2528-106">The DOM classes provide two methods for XPath selection: the <xref:System.Xml.XmlNode.SelectSingleNode%2A> method and the <xref:System.Xml.XmlNode.SelectNodes%2A> method.</span></span> <span data-ttu-id="a2528-107">Metoda <xref:System.Xml.XmlNode.SelectSingleNode%2A> zwraca pierwszy węzeł, który pasuje do kryteriów wyboru.</span><span class="sxs-lookup"><span data-stu-id="a2528-107">The <xref:System.Xml.XmlNode.SelectSingleNode%2A> method returns the first node that matches the selection criteria.</span></span> <span data-ttu-id="a2528-108">Metoda <xref:System.Xml.XmlNode.SelectNodes%2A> zwraca <xref:System.Xml.XmlNodeList>, który zawiera pasujące węzły.</span><span class="sxs-lookup"><span data-stu-id="a2528-108">The <xref:System.Xml.XmlNode.SelectNodes%2A> method returns an <xref:System.Xml.XmlNodeList> that contains the matching nodes.</span></span>  
  
 <span data-ttu-id="a2528-109">W poniższym przykładzie zastosowano metodę <xref:System.Xml.XmlNode.SelectSingleNode%2A>, aby wybrać pierwszy węzeł `book`, w którym nazwisko autora spełnia określone kryteria.</span><span class="sxs-lookup"><span data-stu-id="a2528-109">The following example uses the <xref:System.Xml.XmlNode.SelectSingleNode%2A> method to select the first `book` node in which the author's last name meets the specified criteria.</span></span> <span data-ttu-id="a2528-110">Plik księgarni. XML (który znajduje się na końcu tego tematu) jest używany jako plik wejściowy.</span><span class="sxs-lookup"><span data-stu-id="a2528-110">The bookstore.xml file (which is provided at the end of this topic) is used as the input file.</span></span>  
  
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
  
 <span data-ttu-id="a2528-111">W następnym przykładzie zostanie użyta metoda <xref:System.Xml.XmlNode.SelectNodes%2A>, aby wybrać wszystkie węzły książek, w których cena jest większa niż określona kwota.</span><span class="sxs-lookup"><span data-stu-id="a2528-111">The next example uses the <xref:System.Xml.XmlNode.SelectNodes%2A> method to select all the book nodes in which the price is greater than a specified amount.</span></span> <span data-ttu-id="a2528-112">Cena dla każdej książki na wybranej liście jest następnie programowo zmniejszona o dziesięć procent.</span><span class="sxs-lookup"><span data-stu-id="a2528-112">The price for each book in the selected list is then programmatically reduced by ten percent.</span></span> <span data-ttu-id="a2528-113">Na koniec zaktualizowany plik jest zapisywana w konsoli programu.</span><span class="sxs-lookup"><span data-stu-id="a2528-113">Finally, the updated file is written to the console.</span></span> <span data-ttu-id="a2528-114">Plik księgarni. XML (który znajduje się na końcu tego tematu) jest używany jako plik wejściowy.</span><span class="sxs-lookup"><span data-stu-id="a2528-114">The bookstore.xml file (which is provided at the end of this topic) is used as the input file.</span></span>  
  
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
  
 <span data-ttu-id="a2528-115">Powyższe przykłady rozpoczynają kwerendę XPath w elemencie dokumentu.</span><span class="sxs-lookup"><span data-stu-id="a2528-115">The examples above start the XPath query at the document element.</span></span> <span data-ttu-id="a2528-116">Ustawienie punktu początkowego dla zapytania XPath ustawia węzeł kontekstu, który jest punktem początkowym zapytania XPath.</span><span class="sxs-lookup"><span data-stu-id="a2528-116">Setting the starting point for the XPath query sets the context node, which is the starting point for the XPath query.</span></span> <span data-ttu-id="a2528-117">Jeśli nie chcesz zacząć od elementu dokumentu, ale chcesz zacząć od pierwszego obiektu podrzędnego elementu dokumentu, możesz kod instrukcji SELECT w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="a2528-117">If you do not want to start at the document element, but want to start from the first child of the document element, you can code the select statement as follows:</span></span>  
  
```vb  
doc.DocumentElement.FirstChild.SelectNodes(. . . )  
```  
  
```csharp  
this doc.DocumentElement.FirstChild.SelectNodes(. . .);  
```  
  
 <span data-ttu-id="a2528-118">Wszystkie obiekty <xref:System.Xml.XmlNodeList> są synchronizowane z dokumentem źródłowym.</span><span class="sxs-lookup"><span data-stu-id="a2528-118">All <xref:System.Xml.XmlNodeList> objects are synchronized with the underlying document.</span></span> <span data-ttu-id="a2528-119">W związku z tym, jeśli przeprowadzisz iterację listy węzłów i zmodyfikujesz wartość węzła, ten węzeł zostanie również zaktualizowany w dokumencie, z którego pochodzi.</span><span class="sxs-lookup"><span data-stu-id="a2528-119">Therefore, if you iterate through the node list and modify the value of a node, that node is also updated in the document it came from.</span></span> <span data-ttu-id="a2528-120">Zwróć uwagę, że w poprzednim przykładzie w przypadku zmodyfikowania węzła w wybranym <xref:System.Xml.XmlNodeList> dokument źródłowy również zostanie zmodyfikowany.</span><span class="sxs-lookup"><span data-stu-id="a2528-120">Notice in the previous example that when a node is modified in the selected <xref:System.Xml.XmlNodeList> the underlying document is also modified.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="a2528-121">Po zmodyfikowaniu dokumentu bazowego zaleca się ponowne uruchomienie SELECT.</span><span class="sxs-lookup"><span data-stu-id="a2528-121">When the underlying document is modified, it is advisable to rerun the select.</span></span> <span data-ttu-id="a2528-122">Jeśli zmodyfikowany węzeł to taki, który może spowodować dodanie węzła do listy węzłów, gdy nie był wcześniej, lub spowoduje usunięcie go z listy węzłów, nie ma gwarancji, że lista węzłów jest teraz dokładna.</span><span class="sxs-lookup"><span data-stu-id="a2528-122">If the node modified is one that could cause the node to be added to the node list when it was not previously, or would now cause it to be removed from the node list, there is no guarantee that the node list is now accurate.</span></span>  
  
## <a name="namespaces-in-xpath-expressions"></a><span data-ttu-id="a2528-123">Przestrzenie nazw w wyrażeniach XPath</span><span class="sxs-lookup"><span data-stu-id="a2528-123">Namespaces in XPath Expressions</span></span>  
 <span data-ttu-id="a2528-124">Wyrażenia XPath mogą zawierać przestrzenie nazw.</span><span class="sxs-lookup"><span data-stu-id="a2528-124">XPath expressions can include namespaces.</span></span> <span data-ttu-id="a2528-125">Rozpoznawanie przestrzeni nazw jest obsługiwane przy użyciu <xref:System.Xml.XmlNamespaceManager>.</span><span class="sxs-lookup"><span data-stu-id="a2528-125">Namespace resolution is supported using the <xref:System.Xml.XmlNamespaceManager>.</span></span> <span data-ttu-id="a2528-126">Jeśli wyrażenie XPath zawiera prefiks, para identyfikatorów URI prefiksu i przestrzeni nazw musi zostać dodana do <xref:System.Xml.XmlNamespaceManager>i <xref:System.Xml.XmlNamespaceManager> jest przenoszona do metody <xref:System.Xml.XmlNode.SelectNodes%28System.String%2CSystem.Xml.XmlNamespaceManager%29> lub <xref:System.Xml.XmlNode.SelectSingleNode%28System.String%2CSystem.Xml.XmlNamespaceManager%29>.</span><span class="sxs-lookup"><span data-stu-id="a2528-126">If the XPath expression includes a prefix, the prefix and namespace URI pair must be added to the <xref:System.Xml.XmlNamespaceManager>, and the <xref:System.Xml.XmlNamespaceManager> is passed to the <xref:System.Xml.XmlNode.SelectNodes%28System.String%2CSystem.Xml.XmlNamespaceManager%29> or <xref:System.Xml.XmlNode.SelectSingleNode%28System.String%2CSystem.Xml.XmlNamespaceManager%29> method.</span></span> <span data-ttu-id="a2528-127">Zwróć uwagę, że przykłady kodu używają <xref:System.Xml.XmlNamespaceManager>, aby rozpoznać przestrzeń nazw dokumentu księgarni. XML.</span><span class="sxs-lookup"><span data-stu-id="a2528-127">Notice that the code examples above use the <xref:System.Xml.XmlNamespaceManager> to resolve the namespace of the bookstore.xml document.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="a2528-128">Jeśli wyrażenie XPath nie zawiera prefiksu, zakłada się, że przestrzeń nazw Uniform Resource Identifier (URI) jest pustą przestrzenią nazw.</span><span class="sxs-lookup"><span data-stu-id="a2528-128">If the XPath expression does not include a prefix, it is assumed that the namespace Uniform Resource Identifier (URI) is the empty namespace.</span></span> <span data-ttu-id="a2528-129">Jeśli plik XML zawiera domyślną przestrzeń nazw, nadal trzeba dodać prefiks i identyfikator URI przestrzeni nazw do <xref:System.Xml.XmlNamespaceManager>; w przeciwnym razie nie zostaną wybrane żadne węzły.</span><span class="sxs-lookup"><span data-stu-id="a2528-129">If your XML includes a default namespace, you must still add a prefix and namespace URI to the <xref:System.Xml.XmlNamespaceManager>; otherwise, no nodes will be selected.</span></span>  
  
#### <a name="input-file"></a><span data-ttu-id="a2528-130">Plik wejściowy</span><span class="sxs-lookup"><span data-stu-id="a2528-130">Input File</span></span>  
 <span data-ttu-id="a2528-131">Poniżej znajduje się plik księgarni. XML, który jest używany jako plik wejściowy w przykładach w tym temacie:</span><span class="sxs-lookup"><span data-stu-id="a2528-131">The following is the bookstore.xml file that is used as the input file in the examples in this topic:</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="a2528-132">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a2528-132">See also</span></span>

- [<span data-ttu-id="a2528-133">Model DOM (XML Document Object Model)</span><span class="sxs-lookup"><span data-stu-id="a2528-133">XML Document Object Model (DOM)</span></span>](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
