---
title: "Usuwanie danych XML przy użyciu parametrem XPathNavigator"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 9f436bca-1b96-494b-a6d2-e102c7551752
caps.latest.revision: "2"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 29faf92b26908a37fb122dec00b2d4d6b5f3bf16
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="remove-xml-data-using-xpathnavigator"></a><span data-ttu-id="f3bad-102">Usuwanie danych XML przy użyciu parametrem XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="f3bad-102">Remove XML Data using XPathNavigator</span></span>
<span data-ttu-id="f3bad-103"><xref:System.Xml.XPath.XPathNavigator> Klasa udostępnia zestaw metod służy do usuwania węzłów i wartości z dokumentu XML.</span><span class="sxs-lookup"><span data-stu-id="f3bad-103">The <xref:System.Xml.XPath.XPathNavigator> class provides a set of methods used to remove nodes and values from an XML document.</span></span> <span data-ttu-id="f3bad-104">Aby można było używać tych metod <xref:System.Xml.XPath.XPathNavigator> obiekt musi być edytowalny, czyli jego <xref:System.Xml.XPath.XPathNavigator.CanEdit%2A> właściwość musi być `true`.</span><span class="sxs-lookup"><span data-stu-id="f3bad-104">In order to use these methods, the <xref:System.Xml.XPath.XPathNavigator> object must be editable, that is, its <xref:System.Xml.XPath.XPathNavigator.CanEdit%2A> property must be `true`.</span></span>  
  
 <span data-ttu-id="f3bad-105"><xref:System.Xml.XPath.XPathNavigator>obiekty, które można edytować dokumentu XML są tworzone przez <xref:System.Xml.XmlDocument.CreateNavigator%2A> metody <xref:System.Xml.XmlDocument> klasy.</span><span class="sxs-lookup"><span data-stu-id="f3bad-105"><xref:System.Xml.XPath.XPathNavigator> objects that can edit an XML document are created by the <xref:System.Xml.XmlDocument.CreateNavigator%2A> method of the <xref:System.Xml.XmlDocument> class.</span></span> <span data-ttu-id="f3bad-106"><xref:System.Xml.XPath.XPathNavigator>obiekty utworzone przez <xref:System.Xml.XPath.XPathDocument> klasy są tylko do odczytu i próby użycia metody edycji <xref:System.Xml.XPath.XPathNavigator> obiekt utworzony przez <xref:System.Xml.XPath.XPathDocument> obiektu powoduje <xref:System.NotSupportedException>.</span><span class="sxs-lookup"><span data-stu-id="f3bad-106"><xref:System.Xml.XPath.XPathNavigator> objects created by the <xref:System.Xml.XPath.XPathDocument> class are read-only and any attempt to use the editing methods of an <xref:System.Xml.XPath.XPathNavigator> object created by an <xref:System.Xml.XPath.XPathDocument> object results in a <xref:System.NotSupportedException>.</span></span>  
  
 <span data-ttu-id="f3bad-107">Aby uzyskać więcej informacji o tworzeniu można edytować <xref:System.Xml.XPath.XPathNavigator> obiekty, zobacz [odczytywania danych XML przy użyciu XPathDocument i XmlDocument](../../../../docs/standard/data/xml/reading-xml-data-using-xpathdocument-and-xmldocument.md).</span><span class="sxs-lookup"><span data-stu-id="f3bad-107">For more information about creating editable <xref:System.Xml.XPath.XPathNavigator> objects, see [Reading XML Data using XPathDocument and XmlDocument](../../../../docs/standard/data/xml/reading-xml-data-using-xpathdocument-and-xmldocument.md).</span></span>  
  
## <a name="removing-nodes"></a><span data-ttu-id="f3bad-108">Usuwanie węzłów</span><span class="sxs-lookup"><span data-stu-id="f3bad-108">Removing Nodes</span></span>  
 <span data-ttu-id="f3bad-109"><xref:System.Xml.XPath.XPathNavigator> Klasa udostępnia <xref:System.Xml.XPath.XPathNavigator.DeleteSelf%2A> metody do usuwania węzłów z dokumentu XML.</span><span class="sxs-lookup"><span data-stu-id="f3bad-109">The <xref:System.Xml.XPath.XPathNavigator> class provides the <xref:System.Xml.XPath.XPathNavigator.DeleteSelf%2A> method to remove nodes from an XML document.</span></span>  
  
### <a name="removing-a-node"></a><span data-ttu-id="f3bad-110">Usunięcie węzła</span><span class="sxs-lookup"><span data-stu-id="f3bad-110">Removing a Node</span></span>  
 <span data-ttu-id="f3bad-111"><xref:System.Xml.XPath.XPathNavigator> Klasa udostępnia <xref:System.Xml.XPath.XPathNavigator.DeleteSelf%2A> do usunięcia z bieżącego węzła <xref:System.Xml.XPath.XPathNavigator> obiekt aktualnie znajduje się na z dokumentu XML.</span><span class="sxs-lookup"><span data-stu-id="f3bad-111">The <xref:System.Xml.XPath.XPathNavigator> class provides the <xref:System.Xml.XPath.XPathNavigator.DeleteSelf%2A> method to delete the current node an <xref:System.Xml.XPath.XPathNavigator> object is currently positioned on from an XML document.</span></span>  
  
 <span data-ttu-id="f3bad-112">Po usunięciu węzła przy użyciu <xref:System.Xml.XPath.XPathNavigator.DeleteSelf%2A> metody, nie jest już dostępny od elementu głównego <xref:System.Xml.XmlDocument> obiektu.</span><span class="sxs-lookup"><span data-stu-id="f3bad-112">After a node has been deleted using the <xref:System.Xml.XPath.XPathNavigator.DeleteSelf%2A> method, it is no longer reachable from the root of the <xref:System.Xml.XmlDocument> object.</span></span> <span data-ttu-id="f3bad-113">Po usunięciu węzła <xref:System.Xml.XPath.XPathNavigator> znajduje się w węźle nadrzędnym usuniętego węzła.</span><span class="sxs-lookup"><span data-stu-id="f3bad-113">After a node has been deleted, the <xref:System.Xml.XPath.XPathNavigator> is positioned on the parent node of the deleted node.</span></span>  
  
 <span data-ttu-id="f3bad-114">Operacja usuwania nie ma wpływu na pozycję żadnego <xref:System.Xml.XPath.XPathNavigator> znajduje się w węźle usuniętego obiektu.</span><span class="sxs-lookup"><span data-stu-id="f3bad-114">A delete operation doesn't affect the position of any <xref:System.Xml.XPath.XPathNavigator> object positioned on the deleted node.</span></span> <span data-ttu-id="f3bad-115">Te <xref:System.Xml.XPath.XPathNavigator> obiektów są dozwolone w tym sensie, że można przenosić między usunięto poddrzewo, ale nie można przenieść węzła głównego drzewa przy użyciu węzła regularne Ustaw metody nawigacji <xref:System.Xml.XPath.XPathNavigator> klasy.</span><span class="sxs-lookup"><span data-stu-id="f3bad-115">These <xref:System.Xml.XPath.XPathNavigator> objects are valid in the sense that they can move within the deleted subtree, but cannot be moved to the main node tree using the regular node set navigation methods of the <xref:System.Xml.XPath.XPathNavigator> class.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f3bad-116"><xref:System.Xml.XPath.XPathNavigator.MoveTo%2A> Metody <xref:System.Xml.XPath.XPathNavigator> klasa umożliwia przeniesienie tych <xref:System.Xml.XPath.XPathNavigator> obiektów z powrotem do węzła głównego drzewa lub z węzła głównego drzewa do usuniętego poddrzewo.</span><span class="sxs-lookup"><span data-stu-id="f3bad-116">The <xref:System.Xml.XPath.XPathNavigator.MoveTo%2A> method of the <xref:System.Xml.XPath.XPathNavigator> class can be used to move these <xref:System.Xml.XPath.XPathNavigator> objects back into the main node tree, or from the main node tree to the deleted subtree.</span></span>  
  
 <span data-ttu-id="f3bad-117">W poniższym przykładzie `price` element pierwszego `book` elementu `contosoBooks.xml` plik zostanie usunięty przy użyciu <xref:System.Xml.XPath.XPathNavigator.DeleteSelf%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="f3bad-117">In the following example, the `price` element of the first `book` element of the `contosoBooks.xml` file is deleted using the <xref:System.Xml.XPath.XPathNavigator.DeleteSelf%2A> method.</span></span> <span data-ttu-id="f3bad-118">Pozycja <xref:System.Xml.XPath.XPathNavigator> obiektu po `price` usuwany element znajduje się na element nadrzędny `book` elementu.</span><span class="sxs-lookup"><span data-stu-id="f3bad-118">The position of the <xref:System.Xml.XPath.XPathNavigator> object after the `price` element is deleted is on the parent `book` element.</span></span>  
  
```vb  
Dim document As XmlDocument = New XmlDocument()  
document.Load("contosoBooks.xml")  
Dim navigator As XPathNavigator = document.CreateNavigator()  
  
navigator.MoveToChild("bookstore", "http://www.contoso.com/books")  
navigator.MoveToChild("book", "http://www.contoso.com/books")  
navigator.MoveToChild("price", "http://www.contoso.com/books")  
  
navigator.DeleteSelf()  
  
Console.WriteLine("Position after delete: {0}", navigator.Name)  
Console.WriteLine(navigator.OuterXml)  
```  
  
```csharp  
XmlDocument document = new XmlDocument();  
document.Load("contosoBooks.xml");  
XPathNavigator navigator = document.CreateNavigator();  
  
navigator.MoveToChild("bookstore", "http://www.contoso.com/books");  
navigator.MoveToChild("book", "http://www.contoso.com/books");  
navigator.MoveToChild("price", "http://www.contoso.com/books");  
  
navigator.DeleteSelf();  
  
Console.WriteLine("Position after delete: {0}", navigator.Name);  
Console.WriteLine(navigator.OuterXml);  
```  
  
 <span data-ttu-id="f3bad-119">Przykład przyjmuje `contosoBooks.xml` pliku jako danych wejściowych.</span><span class="sxs-lookup"><span data-stu-id="f3bad-119">The example takes the `contosoBooks.xml` file as an input.</span></span>  
  
 [!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]  
  
### <a name="removing-an-attribute-node"></a><span data-ttu-id="f3bad-120">Usunięcie węzła atrybutu</span><span class="sxs-lookup"><span data-stu-id="f3bad-120">Removing an Attribute Node</span></span>  
 <span data-ttu-id="f3bad-121">Atrybut węzły są usuwane z dokumentu XML przy użyciu <xref:System.Xml.XPath.XPathNavigator.DeleteSelf%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="f3bad-121">Attribute nodes are removed from an XML document using the <xref:System.Xml.XPath.XPathNavigator.DeleteSelf%2A> method.</span></span>  
  
 <span data-ttu-id="f3bad-122">Po usunięciu węzła atrybutu nie jest już dostępny od węzła głównego z <xref:System.Xml.XmlDocument> obiektu i <xref:System.Xml.XPath.XPathNavigator> obiekt znajduje się na elemencie nadrzędnym.</span><span class="sxs-lookup"><span data-stu-id="f3bad-122">After an attribute node has been deleted, it is no longer reachable from the root node of an <xref:System.Xml.XmlDocument> object and the <xref:System.Xml.XPath.XPathNavigator> object is positioned on the parent element.</span></span>  
  
#### <a name="default-attributes"></a><span data-ttu-id="f3bad-123">Domyślne atrybuty</span><span class="sxs-lookup"><span data-stu-id="f3bad-123">Default Attributes</span></span>  
 <span data-ttu-id="f3bad-124">Niezależnie od metody umożliwia usuwanie atrybutów ma ograniczeń specjalnych na usuwanie atrybutów, które są zdefiniowane jako domyślne atrybuty w definicji DTD lub schemat XML dokumentu XML.</span><span class="sxs-lookup"><span data-stu-id="f3bad-124">Regardless of the method used to remove attributes, there are special limitations on removing attributes that are defined as default attributes in the DTD or XML Schema for the XML document.</span></span> <span data-ttu-id="f3bad-125">Nie można usunąć atrybutów domyślnych, chyba że element, do którego należą również zostanie usunięty.</span><span class="sxs-lookup"><span data-stu-id="f3bad-125">Default attributes cannot be removed unless the element they belong to is also removed.</span></span> <span data-ttu-id="f3bad-126">Domyślne atrybuty zawsze znajdują się dla elementów, które mają domyślne atrybuty został zadeklarowany i w związku z tym usuwanie wyników atrybut domyślny atrybut zastępczy wstawiane do elementu i zainicjować przy użyciu wartości domyślnej, który został zadeklarowany.</span><span class="sxs-lookup"><span data-stu-id="f3bad-126">Default attributes are always present for elements that have default attributes declared, and as a result, deleting a default attribute results in a replacement attribute being inserted into the element and initialized to the default value that was declared.</span></span>  
  
## <a name="removing-values"></a><span data-ttu-id="f3bad-127">Usuwanie wartości</span><span class="sxs-lookup"><span data-stu-id="f3bad-127">Removing Values</span></span>  
 <span data-ttu-id="f3bad-128"><xref:System.Xml.XPath.XPathNavigator> Klasa udostępnia <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> i <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> metody, aby usunąć bez typu i wpisane wartości z dokumentu XML.</span><span class="sxs-lookup"><span data-stu-id="f3bad-128">The <xref:System.Xml.XPath.XPathNavigator> class provides the <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> and <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> methods to remove untyped and typed values from an XML document.</span></span>  
  
### <a name="removing-untyped-values"></a><span data-ttu-id="f3bad-129">Usuwanie nieuwzględniające typów wartości</span><span class="sxs-lookup"><span data-stu-id="f3bad-129">Removing Untyped Values</span></span>  
 <span data-ttu-id="f3bad-130"><xref:System.Xml.XPath.XPathNavigator.SetValue%2A> Metoda po prostu wstawia bez typu `string` wartość przekazywana jako parametr jako wartość węzła <xref:System.Xml.XPath.XPathNavigator> obiekt znajduje się obecnie na.</span><span class="sxs-lookup"><span data-stu-id="f3bad-130">The <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> method simply inserts the untyped `string` value passed as a parameter as the value of the node the <xref:System.Xml.XPath.XPathNavigator> object is currently positioned on.</span></span> <span data-ttu-id="f3bad-131">Przekazywanie pusty ciąg, aby <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> metoda usuwa wartość bieżącego węzła.</span><span class="sxs-lookup"><span data-stu-id="f3bad-131">Passing an empty string to the <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> method removes the value of the current node.</span></span>  
  
 <span data-ttu-id="f3bad-132">Poniższy przykład umożliwia usunięcie wartości `price` element pierwszego `book` element w `contosoBooks.xml` plik za pomocą <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="f3bad-132">The following example removes the value of the `price` element of the first `book` element in the `contosoBooks.xml` file using the <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> method.</span></span>  
  
```vb  
Dim document As XmlDocument = New XmlDocument()  
document.Load("contosoBooks.xml")  
Dim navigator As XPathNavigator = document.CreateNavigator()  
  
navigator.MoveToChild("bookstore", "http://www.contoso.com/books")  
navigator.MoveToChild("book", "http://www.contoso.com/books")  
navigator.MoveToChild("price", "http://www.contoso.com/books")  
  
navigator.SetValue("")  
  
navigator.MoveToRoot()  
Console.WriteLine(navigator.OuterXml)  
```  
  
```csharp  
XmlDocument document = new XmlDocument();  
document.Load("contosoBooks.xml");  
XPathNavigator navigator = document.CreateNavigator();  
  
navigator.MoveToChild("bookstore", "http://www.contoso.com/books");  
navigator.MoveToChild("book", "http://www.contoso.com/books");  
navigator.MoveToChild("price", "http://www.contoso.com/books");  
  
navigator.SetValue("");  
  
navigator.MoveToRoot();  
Console.WriteLine(navigator.OuterXml);  
```  
  
 <span data-ttu-id="f3bad-133">Przykład przyjmuje `contosoBooks.xml` pliku jako danych wejściowych.</span><span class="sxs-lookup"><span data-stu-id="f3bad-133">The example takes the `contosoBooks.xml` file as an input.</span></span>  
  
 [!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]  
  
### <a name="removing-typed-values"></a><span data-ttu-id="f3bad-134">Usuwanie typu wartości</span><span class="sxs-lookup"><span data-stu-id="f3bad-134">Removing Typed Values</span></span>  
 <span data-ttu-id="f3bad-135">Gdy typ węzła to proste schematu W3C XML typ, nowa wartość wstawiane przez <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> przed ma wartość metody zostaje sprawdzony pod kątem aspekty typu prostego.</span><span class="sxs-lookup"><span data-stu-id="f3bad-135">When the type of a node is a W3C XML Schema simple type, the new value inserted by the <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> method is checked against the facets of the simple type before the value is set.</span></span> <span data-ttu-id="f3bad-136">Jeśli nowa wartość nie jest prawidłowa dla typu węzła (na przykład ustawienie wartości `-1` w elemencie o typie `xs:positiveInteger`), powoduje wygenerowanie wyjątku.</span><span class="sxs-lookup"><span data-stu-id="f3bad-136">If the new value is not valid according to the type of the node (for example, setting a value of `-1` on an element whose type is `xs:positiveInteger`), it results in an exception.</span></span> <span data-ttu-id="f3bad-137"><xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> Również nie mogą być przekazywane metody `null` jako parametr.</span><span class="sxs-lookup"><span data-stu-id="f3bad-137">The <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> method also cannot be passed `null` as a parameter.</span></span> <span data-ttu-id="f3bad-138">W związku z tym usuwanie wartość węzła typu muszą być zgodne z typem schematu węzła.</span><span class="sxs-lookup"><span data-stu-id="f3bad-138">As a result removing the value of a typed node must comply with the schema type of the node.</span></span>  
  
 <span data-ttu-id="f3bad-139">Poniższy przykład umożliwia usunięcie wartości `price` element pierwszego `book` element `contosoBooks.xml` plik za pomocą <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> metody przez ustawienie wartości `0`.</span><span class="sxs-lookup"><span data-stu-id="f3bad-139">The following example removes the value of the `price` element of the first `book` element in the `contosoBooks.xml` file using the <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> method by setting the value to `0`.</span></span> <span data-ttu-id="f3bad-140">Wartość węzła nie jest usuwany, ale została usunięta cen książki zgodnie z jego typu danych `xs:decimal`.</span><span class="sxs-lookup"><span data-stu-id="f3bad-140">The value of the node is not removed, but the price of the book has been removed according to its data type of `xs:decimal`.</span></span>  
  
```vb  
Dim settings As XmlReaderSettings = New XmlReaderSettings()  
settings.Schemas.Add("http://www.contoso.com/books", "contosoBooks.xsd")  
settings.ValidationType = ValidationType.Schema  
  
Dim reader As XmlReader = XmlReader.Create("contosoBooks.xml", settings)  
  
Dim document As XmlDocument = New XmlDocument()  
document.Load(reader)  
Dim navigator As XPathNavigator = document.CreateNavigator()  
  
navigator.MoveToChild("bookstore", "http://www.contoso.com/books")  
navigator.MoveToChild("book", "http://www.contoso.com/books")  
navigator.MoveToChild("price", "http://www.contoso.com/books")  
  
navigator.SetTypedValue(0)  
  
navigator.MoveToRoot()  
Console.WriteLine(navigator.OuterXml)  
```  
  
```csharp  
XmlReaderSettings settings = new XmlReaderSettings();  
settings.Schemas.Add("http://www.contoso.com/books", "contosoBooks.xsd");  
settings.ValidationType = ValidationType.Schema;  
  
XmlReader reader = XmlReader.Create("contosoBooks.xml", settings);  
  
XmlDocument document = new XmlDocument();  
document.Load(reader);  
XPathNavigator navigator = document.CreateNavigator();  
  
navigator.MoveToChild("bookstore", "http://www.contoso.com/books");  
navigator.MoveToChild("book", "http://www.contoso.com/books");  
navigator.MoveToChild("price", "http://www.contoso.com/books");  
  
navigator.SetTypedValue(0);  
  
navigator.MoveToRoot();  
Console.WriteLine(navigator.OuterXml);  
```  
  
## <a name="namespace-nodes"></a><span data-ttu-id="f3bad-141">Namespace węzłów</span><span class="sxs-lookup"><span data-stu-id="f3bad-141">Namespace Nodes</span></span>  
 <span data-ttu-id="f3bad-142">Nie można usunąć węzłów Namespace z <xref:System.Xml.XmlDocument> obiektu.</span><span class="sxs-lookup"><span data-stu-id="f3bad-142">Namespace nodes cannot be deleted from an <xref:System.Xml.XmlDocument> object.</span></span> <span data-ttu-id="f3bad-143">Próbuje usunąć węzłów przestrzeni nazw przy użyciu <xref:System.Xml.XPath.XPathNavigator.DeleteSelf%2A> metoda powoduje wygenerowanie wyjątku.</span><span class="sxs-lookup"><span data-stu-id="f3bad-143">Attempts to delete namespace nodes using the <xref:System.Xml.XPath.XPathNavigator.DeleteSelf%2A> method results in an exception.</span></span>  
  
## <a name="the-innerxml-and-outerxml-properties"></a><span data-ttu-id="f3bad-144">Właściwości OuterXml i InnerXml</span><span class="sxs-lookup"><span data-stu-id="f3bad-144">The InnerXml and OuterXml Properties</span></span>  
 <span data-ttu-id="f3bad-145"><xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> i <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> właściwości <xref:System.Xml.XPath.XPathNavigator> klasy Zmień adiustację XML węzłów <xref:System.Xml.XPath.XPathNavigator> obiekt znajduje się obecnie na.</span><span class="sxs-lookup"><span data-stu-id="f3bad-145">The <xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> and <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> properties of the <xref:System.Xml.XPath.XPathNavigator> class change the XML markup of the nodes an <xref:System.Xml.XPath.XPathNavigator> object is currently positioned on.</span></span>  
  
 <span data-ttu-id="f3bad-146"><xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> Znaczników XML węzłów podrzędnych zmiany właściwości <xref:System.Xml.XPath.XPathNavigator> obiekt aktualnie znajduje się na przy użyciu analizowanej zawartości danego XML `string`.</span><span class="sxs-lookup"><span data-stu-id="f3bad-146">The <xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> property changes the XML markup of the child nodes an <xref:System.Xml.XPath.XPathNavigator> object is currently positioned on with the parsed contents of the given XML `string`.</span></span> <span data-ttu-id="f3bad-147">Podobnie <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> znaczników XML węzłów podrzędnych zmiany właściwości <xref:System.Xml.XPath.XPathNavigator> obiekt aktualnie znajduje się na oraz bieżącego węzła.</span><span class="sxs-lookup"><span data-stu-id="f3bad-147">Similarly, the <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> property changes the XML markup of the child nodes an <xref:System.Xml.XPath.XPathNavigator> object is currently positioned on as well as the current node itself.</span></span>  
  
 <span data-ttu-id="f3bad-148">Oprócz metod opisanych w tym temacie <xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> i <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> właściwości mogą służyć do usuwania węzłów i wartości z dokumentu XML.</span><span class="sxs-lookup"><span data-stu-id="f3bad-148">In addition to the methods described in this topic, the <xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> and <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> properties can be used to remove nodes and values from an XML document.</span></span> <span data-ttu-id="f3bad-149">Aby uzyskać więcej informacji o korzystaniu z <xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> i <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> właściwości, aby zmodyfikować węzłów, zobacz [zmodyfikować danych XML przy użyciu Element XPathNavigator](../../../../docs/standard/data/xml/modify-xml-data-using-xpathnavigator.md) tematu.</span><span class="sxs-lookup"><span data-stu-id="f3bad-149">For more information about using the <xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> and <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> properties to modify nodes, see the [Modify XML Data using XPathNavigator](../../../../docs/standard/data/xml/modify-xml-data-using-xpathnavigator.md) topic.</span></span>  
  
## <a name="saving-an-xml-document"></a><span data-ttu-id="f3bad-150">Zapisywanie dokumentu XML</span><span class="sxs-lookup"><span data-stu-id="f3bad-150">Saving an XML Document</span></span>  
 <span data-ttu-id="f3bad-151">Zapisywanie zmian <xref:System.Xml.XmlDocument> obiekt jako wynik metod opisanych w tym temacie odbywa się przy użyciu metody <xref:System.Xml.XmlDocument> klasy.</span><span class="sxs-lookup"><span data-stu-id="f3bad-151">Saving changes made to an <xref:System.Xml.XmlDocument> object as the result of the methods described in this topic is performed using the methods of the <xref:System.Xml.XmlDocument> class.</span></span> <span data-ttu-id="f3bad-152">Aby uzyskać więcej informacji na temat zapisywania zmian w <xref:System.Xml.XmlDocument> obiektów, zobacz [zapisywania i zapisywanie dokumentu](../../../../docs/standard/data/xml/saving-and-writing-a-document.md).</span><span class="sxs-lookup"><span data-stu-id="f3bad-152">For more information about saving changes made to an <xref:System.Xml.XmlDocument> object, see [Saving and Writing a Document](../../../../docs/standard/data/xml/saving-and-writing-a-document.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f3bad-153">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f3bad-153">See Also</span></span>  
 <xref:System.Xml.XmlDocument>  
 <xref:System.Xml.XPath.XPathDocument>  
 <xref:System.Xml.XPath.XPathNavigator>  
 [<span data-ttu-id="f3bad-154">Przetwarzania danych XML przy użyciu modelu danych XPath</span><span class="sxs-lookup"><span data-stu-id="f3bad-154">Process XML Data Using the XPath Data Model</span></span>](../../../../docs/standard/data/xml/process-xml-data-using-the-xpath-data-model.md)  
 [<span data-ttu-id="f3bad-155">Wstawianie danych XML przy użyciu parametrem XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="f3bad-155">Insert XML Data using XPathNavigator</span></span>](../../../../docs/standard/data/xml/insert-xml-data-using-xpathnavigator.md)  
 [<span data-ttu-id="f3bad-156">Modyfikowanie danych XML przy użyciu parametrem XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="f3bad-156">Modify XML Data using XPathNavigator</span></span>](../../../../docs/standard/data/xml/modify-xml-data-using-xpathnavigator.md)
