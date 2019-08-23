---
title: Usuwanie danych XML przy użyciu klasy XPathNavigator
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 9f436bca-1b96-494b-a6d2-e102c7551752
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 27c19c82270b9d67b6cd308386aa93c6112d59ee
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69909683"
---
# <a name="remove-xml-data-using-xpathnavigator"></a><span data-ttu-id="ab6b9-102">Usuwanie danych XML przy użyciu klasy XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="ab6b9-102">Remove XML Data using XPathNavigator</span></span>
<span data-ttu-id="ab6b9-103"><xref:System.Xml.XPath.XPathNavigator> Klasa zawiera zestaw metod służących do usuwania węzłów i wartości z dokumentu XML.</span><span class="sxs-lookup"><span data-stu-id="ab6b9-103">The <xref:System.Xml.XPath.XPathNavigator> class provides a set of methods used to remove nodes and values from an XML document.</span></span> <span data-ttu-id="ab6b9-104">Aby można było korzystać z tych metod, <xref:System.Xml.XPath.XPathNavigator> obiekt musi być edytowalny, oznacza to, <xref:System.Xml.XPath.XPathNavigator.CanEdit%2A> że jego właściwość `true`musi być.</span><span class="sxs-lookup"><span data-stu-id="ab6b9-104">In order to use these methods, the <xref:System.Xml.XPath.XPathNavigator> object must be editable, that is, its <xref:System.Xml.XPath.XPathNavigator.CanEdit%2A> property must be `true`.</span></span>  
  
 <span data-ttu-id="ab6b9-105"><xref:System.Xml.XPath.XPathNavigator>obiekty, które mogą edytować dokument XML, są tworzone przy <xref:System.Xml.XmlDocument.CreateNavigator%2A> użyciu metody <xref:System.Xml.XmlDocument> klasy.</span><span class="sxs-lookup"><span data-stu-id="ab6b9-105"><xref:System.Xml.XPath.XPathNavigator> objects that can edit an XML document are created by the <xref:System.Xml.XmlDocument.CreateNavigator%2A> method of the <xref:System.Xml.XmlDocument> class.</span></span> <span data-ttu-id="ab6b9-106"><xref:System.Xml.XPath.XPathNavigator>obiekty utworzone przez <xref:System.Xml.XPath.XPathDocument> klasę są tylko do odczytu, a każda próba użycia metod <xref:System.Xml.XPath.XPathNavigator> edycji obiektu utworzonego przez <xref:System.Xml.XPath.XPathDocument> obiekt daje w wyniku <xref:System.NotSupportedException>.</span><span class="sxs-lookup"><span data-stu-id="ab6b9-106"><xref:System.Xml.XPath.XPathNavigator> objects created by the <xref:System.Xml.XPath.XPathDocument> class are read-only and any attempt to use the editing methods of an <xref:System.Xml.XPath.XPathNavigator> object created by an <xref:System.Xml.XPath.XPathDocument> object results in a <xref:System.NotSupportedException>.</span></span>  
  
 <span data-ttu-id="ab6b9-107">Aby uzyskać więcej informacji na temat <xref:System.Xml.XPath.XPathNavigator> tworzenia edytowalnych obiektów, zobacz [odczytywanie danych XML przy użyciu XPathDocument i XmlDocument](../../../../docs/standard/data/xml/reading-xml-data-using-xpathdocument-and-xmldocument.md).</span><span class="sxs-lookup"><span data-stu-id="ab6b9-107">For more information about creating editable <xref:System.Xml.XPath.XPathNavigator> objects, see [Reading XML Data using XPathDocument and XmlDocument](../../../../docs/standard/data/xml/reading-xml-data-using-xpathdocument-and-xmldocument.md).</span></span>  
  
## <a name="removing-nodes"></a><span data-ttu-id="ab6b9-108">Usuwanie węzłów</span><span class="sxs-lookup"><span data-stu-id="ab6b9-108">Removing Nodes</span></span>  
 <span data-ttu-id="ab6b9-109"><xref:System.Xml.XPath.XPathNavigator> Klasa<xref:System.Xml.XPath.XPathNavigator.DeleteSelf%2A> udostępnia metodę usuwania węzłów z dokumentu XML.</span><span class="sxs-lookup"><span data-stu-id="ab6b9-109">The <xref:System.Xml.XPath.XPathNavigator> class provides the <xref:System.Xml.XPath.XPathNavigator.DeleteSelf%2A> method to remove nodes from an XML document.</span></span>  
  
### <a name="removing-a-node"></a><span data-ttu-id="ab6b9-110">Usuwanie węzła</span><span class="sxs-lookup"><span data-stu-id="ab6b9-110">Removing a Node</span></span>  
 <span data-ttu-id="ab6b9-111">Klasa udostępnia metodę usuwania bieżącego węzła, <xref:System.Xml.XPath.XPathNavigator> który obiekt jest obecnie umieszczony na podstawie dokumentu XML. <xref:System.Xml.XPath.XPathNavigator.DeleteSelf%2A> <xref:System.Xml.XPath.XPathNavigator></span><span class="sxs-lookup"><span data-stu-id="ab6b9-111">The <xref:System.Xml.XPath.XPathNavigator> class provides the <xref:System.Xml.XPath.XPathNavigator.DeleteSelf%2A> method to delete the current node an <xref:System.Xml.XPath.XPathNavigator> object is currently positioned on from an XML document.</span></span>  
  
 <span data-ttu-id="ab6b9-112">Po usunięciu węzła przy użyciu <xref:System.Xml.XPath.XPathNavigator.DeleteSelf%2A> metody nie jest on już dostępny z poziomu korzenia <xref:System.Xml.XmlDocument> obiektu.</span><span class="sxs-lookup"><span data-stu-id="ab6b9-112">After a node has been deleted using the <xref:System.Xml.XPath.XPathNavigator.DeleteSelf%2A> method, it is no longer reachable from the root of the <xref:System.Xml.XmlDocument> object.</span></span> <span data-ttu-id="ab6b9-113">Po usunięciu <xref:System.Xml.XPath.XPathNavigator> węzła jest on umieszczany w węźle nadrzędnym usuniętego węzła.</span><span class="sxs-lookup"><span data-stu-id="ab6b9-113">After a node has been deleted, the <xref:System.Xml.XPath.XPathNavigator> is positioned on the parent node of the deleted node.</span></span>  
  
 <span data-ttu-id="ab6b9-114">Operacja usuwania nie wpływa na położenie żadnego <xref:System.Xml.XPath.XPathNavigator> obiektu umieszczonego w usuniętym węźle.</span><span class="sxs-lookup"><span data-stu-id="ab6b9-114">A delete operation doesn't affect the position of any <xref:System.Xml.XPath.XPathNavigator> object positioned on the deleted node.</span></span> <span data-ttu-id="ab6b9-115">Te <xref:System.Xml.XPath.XPathNavigator> obiekty są prawidłowe w tym sensie, że mogą one poruszać się w usuniętych poddrzewach, ale nie można ich przenieść do głównego drzewa węzłów przy użyciu standardowych metod <xref:System.Xml.XPath.XPathNavigator> nawigacji zestawu węzłów klasy.</span><span class="sxs-lookup"><span data-stu-id="ab6b9-115">These <xref:System.Xml.XPath.XPathNavigator> objects are valid in the sense that they can move within the deleted subtree, but cannot be moved to the main node tree using the regular node set navigation methods of the <xref:System.Xml.XPath.XPathNavigator> class.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ab6b9-116">Metoda klasy może służyć do przenoszenia tych <xref:System.Xml.XPath.XPathNavigator> obiektów z powrotem do głównego drzewa węzłów lub z drzewa głównego węzła do usuniętego poddrzewa. <xref:System.Xml.XPath.XPathNavigator> <xref:System.Xml.XPath.XPathNavigator.MoveTo%2A></span><span class="sxs-lookup"><span data-stu-id="ab6b9-116">The <xref:System.Xml.XPath.XPathNavigator.MoveTo%2A> method of the <xref:System.Xml.XPath.XPathNavigator> class can be used to move these <xref:System.Xml.XPath.XPathNavigator> objects back into the main node tree, or from the main node tree to the deleted subtree.</span></span>  
  
 <span data-ttu-id="ab6b9-117">W poniższym przykładzie `price` element pierwszego `book` elementu `contosoBooks.xml` pliku jest usuwany przy użyciu <xref:System.Xml.XPath.XPathNavigator.DeleteSelf%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="ab6b9-117">In the following example, the `price` element of the first `book` element of the `contosoBooks.xml` file is deleted using the <xref:System.Xml.XPath.XPathNavigator.DeleteSelf%2A> method.</span></span> <span data-ttu-id="ab6b9-118">Pozycja <xref:System.Xml.XPath.XPathNavigator> `book` obiektu`price` po usunięciu elementu znajduje się w elemencie nadrzędnym.</span><span class="sxs-lookup"><span data-stu-id="ab6b9-118">The position of the <xref:System.Xml.XPath.XPathNavigator> object after the `price` element is deleted is on the parent `book` element.</span></span>  
  
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
  
 <span data-ttu-id="ab6b9-119">Przykład pobiera `contosoBooks.xml` plik jako dane wejściowe.</span><span class="sxs-lookup"><span data-stu-id="ab6b9-119">The example takes the `contosoBooks.xml` file as an input.</span></span>  
  
 [!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]  
  
### <a name="removing-an-attribute-node"></a><span data-ttu-id="ab6b9-120">Usuwanie węzła atrybutu</span><span class="sxs-lookup"><span data-stu-id="ab6b9-120">Removing an Attribute Node</span></span>  
 <span data-ttu-id="ab6b9-121">Węzły atrybutów są usuwane z dokumentu XML przy użyciu <xref:System.Xml.XPath.XPathNavigator.DeleteSelf%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="ab6b9-121">Attribute nodes are removed from an XML document using the <xref:System.Xml.XPath.XPathNavigator.DeleteSelf%2A> method.</span></span>  
  
 <span data-ttu-id="ab6b9-122">Po usunięciu węzła atrybutu nie jest on już osiągalny z węzła <xref:System.Xml.XmlDocument> głównego obiektu <xref:System.Xml.XPath.XPathNavigator> , a obiekt jest umieszczony w elemencie nadrzędnym.</span><span class="sxs-lookup"><span data-stu-id="ab6b9-122">After an attribute node has been deleted, it is no longer reachable from the root node of an <xref:System.Xml.XmlDocument> object and the <xref:System.Xml.XPath.XPathNavigator> object is positioned on the parent element.</span></span>  
  
#### <a name="default-attributes"></a><span data-ttu-id="ab6b9-123">Atrybuty domyślne</span><span class="sxs-lookup"><span data-stu-id="ab6b9-123">Default Attributes</span></span>  
 <span data-ttu-id="ab6b9-124">Niezależnie od metody używanej do usuwania atrybutów istnieją specjalne ograniczenia dotyczące usuwania atrybutów, które są zdefiniowane jako atrybuty domyślne w schemacie DTD lub XML dla dokumentu XML.</span><span class="sxs-lookup"><span data-stu-id="ab6b9-124">Regardless of the method used to remove attributes, there are special limitations on removing attributes that are defined as default attributes in the DTD or XML Schema for the XML document.</span></span> <span data-ttu-id="ab6b9-125">Atrybutów domyślnych nie można usunąć, chyba że element, do którego należą, został również usunięty.</span><span class="sxs-lookup"><span data-stu-id="ab6b9-125">Default attributes cannot be removed unless the element they belong to is also removed.</span></span> <span data-ttu-id="ab6b9-126">Atrybuty domyślne są zawsze obecne dla elementów, które mają zadeklarowane atrybuty domyślne i w związku z tym usunięcie atrybutu domyślnego powoduje wstawianie atrybutu zastępczego do elementu i zainicjowanie do wartości domyślnej, która została zadeklarowana.</span><span class="sxs-lookup"><span data-stu-id="ab6b9-126">Default attributes are always present for elements that have default attributes declared, and as a result, deleting a default attribute results in a replacement attribute being inserted into the element and initialized to the default value that was declared.</span></span>  
  
## <a name="removing-values"></a><span data-ttu-id="ab6b9-127">Usuwanie wartości</span><span class="sxs-lookup"><span data-stu-id="ab6b9-127">Removing Values</span></span>  
 <span data-ttu-id="ab6b9-128">Klasa zawiera metody<xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> i do usuwania wartości typu untyped i Type z dokumentu XML. <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> <xref:System.Xml.XPath.XPathNavigator></span><span class="sxs-lookup"><span data-stu-id="ab6b9-128">The <xref:System.Xml.XPath.XPathNavigator> class provides the <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> and <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> methods to remove untyped and typed values from an XML document.</span></span>  
  
### <a name="removing-untyped-values"></a><span data-ttu-id="ab6b9-129">Usuwanie niewpisanych wartości</span><span class="sxs-lookup"><span data-stu-id="ab6b9-129">Removing Untyped Values</span></span>  
 <span data-ttu-id="ab6b9-130">Metoda po prostu wstawia `string` wartość bez typu jako parametr jako wartość węzła, na którym <xref:System.Xml.XPath.XPathNavigator> znajduje się obiekt. <xref:System.Xml.XPath.XPathNavigator.SetValue%2A></span><span class="sxs-lookup"><span data-stu-id="ab6b9-130">The <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> method simply inserts the untyped `string` value passed as a parameter as the value of the node the <xref:System.Xml.XPath.XPathNavigator> object is currently positioned on.</span></span> <span data-ttu-id="ab6b9-131">Przekazanie pustego ciągu do <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> metody powoduje usunięcie wartości bieżącego węzła.</span><span class="sxs-lookup"><span data-stu-id="ab6b9-131">Passing an empty string to the <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> method removes the value of the current node.</span></span>  
  
 <span data-ttu-id="ab6b9-132">Poniższy `price` przykład usuwa wartość elementu pierwszego `book` elementu <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> w `contosoBooks.xml` pliku przy użyciu metody.</span><span class="sxs-lookup"><span data-stu-id="ab6b9-132">The following example removes the value of the `price` element of the first `book` element in the `contosoBooks.xml` file using the <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> method.</span></span>  
  
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
  
 <span data-ttu-id="ab6b9-133">Przykład pobiera `contosoBooks.xml` plik jako dane wejściowe.</span><span class="sxs-lookup"><span data-stu-id="ab6b9-133">The example takes the `contosoBooks.xml` file as an input.</span></span>  
  
 [!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]  
  
### <a name="removing-typed-values"></a><span data-ttu-id="ab6b9-134">Usuwanie wpisanych wartości</span><span class="sxs-lookup"><span data-stu-id="ab6b9-134">Removing Typed Values</span></span>  
 <span data-ttu-id="ab6b9-135">Gdy typ węzła jest typem prostym schematu XML W3C, Nowa wartość wstawiona przez <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> metodę jest sprawdzana względem aspektów typu prostego przed ustawieniem wartości.</span><span class="sxs-lookup"><span data-stu-id="ab6b9-135">When the type of a node is a W3C XML Schema simple type, the new value inserted by the <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> method is checked against the facets of the simple type before the value is set.</span></span> <span data-ttu-id="ab6b9-136">Jeśli nowa wartość jest nieprawidłowa w zależności od typu węzła (na przykład ustawienie wartości `-1` w elemencie, którego typem jest `xs:positiveInteger`), powoduje wyjątek.</span><span class="sxs-lookup"><span data-stu-id="ab6b9-136">If the new value is not valid according to the type of the node (for example, setting a value of `-1` on an element whose type is `xs:positiveInteger`), it results in an exception.</span></span> <span data-ttu-id="ab6b9-137">Nie można również przekazywać `null` metodyjakoparametru.<xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A></span><span class="sxs-lookup"><span data-stu-id="ab6b9-137">The <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> method also cannot be passed `null` as a parameter.</span></span> <span data-ttu-id="ab6b9-138">W wyniku usunięcia wartości węzła o określonym typie musi być zgodna z typem schematu węzła.</span><span class="sxs-lookup"><span data-stu-id="ab6b9-138">As a result removing the value of a typed node must comply with the schema type of the node.</span></span>  
  
 <span data-ttu-id="ab6b9-139">`price` Poniższy przykład usuwa wartość elementu pierwszego `book` elementu <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> w `contosoBooks.xml` pliku `0`przy użyciu metody przez ustawienie wartości.</span><span class="sxs-lookup"><span data-stu-id="ab6b9-139">The following example removes the value of the `price` element of the first `book` element in the `contosoBooks.xml` file using the <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> method by setting the value to `0`.</span></span> <span data-ttu-id="ab6b9-140">Wartość węzła nie jest usuwana, ale cena księgi została usunięta przy uwzględnieniu jej typu `xs:decimal`danych.</span><span class="sxs-lookup"><span data-stu-id="ab6b9-140">The value of the node is not removed, but the price of the book has been removed according to its data type of `xs:decimal`.</span></span>  
  
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
  
## <a name="namespace-nodes"></a><span data-ttu-id="ab6b9-141">Węzły przestrzeni nazw</span><span class="sxs-lookup"><span data-stu-id="ab6b9-141">Namespace Nodes</span></span>  
 <span data-ttu-id="ab6b9-142">Nie można usunąć węzłów przestrzeni nazw z <xref:System.Xml.XmlDocument> obiektu.</span><span class="sxs-lookup"><span data-stu-id="ab6b9-142">Namespace nodes cannot be deleted from an <xref:System.Xml.XmlDocument> object.</span></span> <span data-ttu-id="ab6b9-143">Próba usunięcia węzłów przestrzeni nazw przy użyciu <xref:System.Xml.XPath.XPathNavigator.DeleteSelf%2A> metody powoduje wyjątek.</span><span class="sxs-lookup"><span data-stu-id="ab6b9-143">Attempts to delete namespace nodes using the <xref:System.Xml.XPath.XPathNavigator.DeleteSelf%2A> method results in an exception.</span></span>  
  
## <a name="the-innerxml-and-outerxml-properties"></a><span data-ttu-id="ab6b9-144">Właściwości InnerXml i OuterXml</span><span class="sxs-lookup"><span data-stu-id="ab6b9-144">The InnerXml and OuterXml Properties</span></span>  
 <span data-ttu-id="ab6b9-145">Właściwości <xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> i<xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> klasy zmieniają znaczniki XML w węzłach, w których obiektjestobecnieumieszczony.<xref:System.Xml.XPath.XPathNavigator> <xref:System.Xml.XPath.XPathNavigator></span><span class="sxs-lookup"><span data-stu-id="ab6b9-145">The <xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> and <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> properties of the <xref:System.Xml.XPath.XPathNavigator> class change the XML markup of the nodes an <xref:System.Xml.XPath.XPathNavigator> object is currently positioned on.</span></span>  
  
 <span data-ttu-id="ab6b9-146">Właściwość zmienia znaczniki XML <xref:System.Xml.XPath.XPathNavigator> węzłów podrzędnych obiekt jest obecnie umieszczony w przeanalizowanej zawartości danego kodu XML `string`. <xref:System.Xml.XPath.XPathNavigator.InnerXml%2A></span><span class="sxs-lookup"><span data-stu-id="ab6b9-146">The <xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> property changes the XML markup of the child nodes an <xref:System.Xml.XPath.XPathNavigator> object is currently positioned on with the parsed contents of the given XML `string`.</span></span> <span data-ttu-id="ab6b9-147">Podobnie <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> właściwość zmienia znaczniki XML <xref:System.Xml.XPath.XPathNavigator> węzłów podrzędnych, w których obiekt jest obecnie umieszczony, a także bieżący węzeł.</span><span class="sxs-lookup"><span data-stu-id="ab6b9-147">Similarly, the <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> property changes the XML markup of the child nodes an <xref:System.Xml.XPath.XPathNavigator> object is currently positioned on as well as the current node itself.</span></span>  
  
 <span data-ttu-id="ab6b9-148">Poza metodami opisanymi w tym temacie, <xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> właściwości i <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> mogą być używane do usuwania węzłów i wartości z dokumentu XML.</span><span class="sxs-lookup"><span data-stu-id="ab6b9-148">In addition to the methods described in this topic, the <xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> and <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> properties can be used to remove nodes and values from an XML document.</span></span> <span data-ttu-id="ab6b9-149">Aby uzyskać więcej informacji o korzystaniu <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> z <xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> właściwości i do modyfikowania węzłów, zobacz temat [modyfikowanie danych XML przy użyciu klasy XPathNavigator](../../../../docs/standard/data/xml/modify-xml-data-using-xpathnavigator.md) .</span><span class="sxs-lookup"><span data-stu-id="ab6b9-149">For more information about using the <xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> and <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> properties to modify nodes, see the [Modify XML Data using XPathNavigator](../../../../docs/standard/data/xml/modify-xml-data-using-xpathnavigator.md) topic.</span></span>  
  
## <a name="saving-an-xml-document"></a><span data-ttu-id="ab6b9-150">Zapisywanie dokumentu XML</span><span class="sxs-lookup"><span data-stu-id="ab6b9-150">Saving an XML Document</span></span>  
 <span data-ttu-id="ab6b9-151">Zapisywanie zmian wprowadzonych <xref:System.Xml.XmlDocument> w obiekcie w wyniku metod opisanych w tym temacie jest wykonywane przy użyciu metod <xref:System.Xml.XmlDocument> klasy.</span><span class="sxs-lookup"><span data-stu-id="ab6b9-151">Saving changes made to an <xref:System.Xml.XmlDocument> object as the result of the methods described in this topic is performed using the methods of the <xref:System.Xml.XmlDocument> class.</span></span> <span data-ttu-id="ab6b9-152">Aby uzyskać więcej informacji na temat zapisywania zmian wprowadzonych w <xref:System.Xml.XmlDocument> obiekcie, zobacz [Zapisywanie i pisanie dokumentu](../../../../docs/standard/data/xml/saving-and-writing-a-document.md).</span><span class="sxs-lookup"><span data-stu-id="ab6b9-152">For more information about saving changes made to an <xref:System.Xml.XmlDocument> object, see [Saving and Writing a Document](../../../../docs/standard/data/xml/saving-and-writing-a-document.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ab6b9-153">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ab6b9-153">See also</span></span>

- <xref:System.Xml.XmlDocument>
- <xref:System.Xml.XPath.XPathDocument>
- <xref:System.Xml.XPath.XPathNavigator>
- [<span data-ttu-id="ab6b9-154">Przetwarzanie danych XML przy użyciu modelu danych XPath</span><span class="sxs-lookup"><span data-stu-id="ab6b9-154">Process XML Data Using the XPath Data Model</span></span>](../../../../docs/standard/data/xml/process-xml-data-using-the-xpath-data-model.md)
- [<span data-ttu-id="ab6b9-155">Wstawianie danych XML przy użyciu klasy XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="ab6b9-155">Insert XML Data using XPathNavigator</span></span>](../../../../docs/standard/data/xml/insert-xml-data-using-xpathnavigator.md)
- [<span data-ttu-id="ab6b9-156">Modyfikowanie danych XML przy użyciu klasy XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="ab6b9-156">Modify XML Data using XPathNavigator</span></span>](../../../../docs/standard/data/xml/modify-xml-data-using-xpathnavigator.md)
