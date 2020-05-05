---
title: Modyfikowanie danych XML przy użyciu klasy XPathNavigator
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
ms.assetid: 03a7c5a1-b296-4af4-b209-043c958dc0a5
ms.openlocfilehash: 1770eb08055fd244bd0f220fed6d1641c35174fd
ms.sourcegitcommit: de7f589de07a9979b6ac28f54c3e534a617d9425
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/05/2020
ms.locfileid: "82794354"
---
# <a name="modify-xml-data-using-xpathnavigator"></a><span data-ttu-id="55c5e-102">Modyfikowanie danych XML przy użyciu klasy XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="55c5e-102">Modify XML Data using XPathNavigator</span></span>
<span data-ttu-id="55c5e-103"><xref:System.Xml.XPath.XPathNavigator> Klasa zawiera zestaw metod służących do modyfikowania węzłów i wartości w dokumencie XML.</span><span class="sxs-lookup"><span data-stu-id="55c5e-103">The <xref:System.Xml.XPath.XPathNavigator> class provides a set of methods used to modify nodes and values in an XML document.</span></span> <span data-ttu-id="55c5e-104">Aby można było korzystać z tych metod, <xref:System.Xml.XPath.XPathNavigator> obiekt musi być edytowalny, oznacza to, <xref:System.Xml.XPath.XPathNavigator.CanEdit%2A> że jego właściwość `true`musi być.</span><span class="sxs-lookup"><span data-stu-id="55c5e-104">In order to use these methods, the <xref:System.Xml.XPath.XPathNavigator> object must be editable, that is, its <xref:System.Xml.XPath.XPathNavigator.CanEdit%2A> property must be `true`.</span></span>  
  
 <span data-ttu-id="55c5e-105"><xref:System.Xml.XPath.XPathNavigator>obiekty, które mogą edytować dokument XML, są tworzone przy <xref:System.Xml.XmlDocument.CreateNavigator%2A> użyciu metody <xref:System.Xml.XmlDocument> klasy.</span><span class="sxs-lookup"><span data-stu-id="55c5e-105"><xref:System.Xml.XPath.XPathNavigator> objects that can edit an XML document are created by the <xref:System.Xml.XmlDocument.CreateNavigator%2A> method of the <xref:System.Xml.XmlDocument> class.</span></span> <span data-ttu-id="55c5e-106"><xref:System.Xml.XPath.XPathNavigator>obiekty utworzone <xref:System.Xml.XPath.XPathDocument> przez klasę są tylko do odczytu, a wszystkie próby użycia metod <xref:System.Xml.XPath.XPathNavigator> edycji obiektu utworzonego przez <xref:System.Xml.XPath.XPathDocument> obiekt powodują. <xref:System.NotSupportedException></span><span class="sxs-lookup"><span data-stu-id="55c5e-106"><xref:System.Xml.XPath.XPathNavigator> objects created by the <xref:System.Xml.XPath.XPathDocument> class are read-only and any attempt to use the editing methods of an <xref:System.Xml.XPath.XPathNavigator> object created by an <xref:System.Xml.XPath.XPathDocument> object result in a <xref:System.NotSupportedException>.</span></span>  
  
 <span data-ttu-id="55c5e-107">Aby uzyskać więcej informacji na temat <xref:System.Xml.XPath.XPathNavigator> tworzenia edytowalnych obiektów, zobacz [odczytywanie danych XML przy użyciu XPathDocument i XmlDocument](../../../../docs/standard/data/xml/reading-xml-data-using-xpathdocument-and-xmldocument.md).</span><span class="sxs-lookup"><span data-stu-id="55c5e-107">For more information about creating editable <xref:System.Xml.XPath.XPathNavigator> objects, see [Reading XML Data using XPathDocument and XmlDocument](../../../../docs/standard/data/xml/reading-xml-data-using-xpathdocument-and-xmldocument.md).</span></span>  
  
## <a name="modifying-nodes"></a><span data-ttu-id="55c5e-108">Modyfikowanie węzłów</span><span class="sxs-lookup"><span data-stu-id="55c5e-108">Modifying Nodes</span></span>  
 <span data-ttu-id="55c5e-109">Prostą techniką zmiany wartości węzła jest użycie metod <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> i <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> <xref:System.Xml.XPath.XPathNavigator> klasy.</span><span class="sxs-lookup"><span data-stu-id="55c5e-109">A simple technique for changing the value of a node is to use the <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> and <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> methods of the <xref:System.Xml.XPath.XPathNavigator> class.</span></span>  
  
 <span data-ttu-id="55c5e-110">Poniższa tabela zawiera listę efektów tych metod dla różnych typów węzłów.</span><span class="sxs-lookup"><span data-stu-id="55c5e-110">The following table lists the effects of these methods on different node types.</span></span>  
  
|<xref:System.Xml.XPath.XPathNodeType>|<span data-ttu-id="55c5e-111">Zmieniono dane</span><span class="sxs-lookup"><span data-stu-id="55c5e-111">Data Changed</span></span>|  
|---------------------------------------------------------------------------------------------------------------------------------------------|------------------|  
|<xref:System.Xml.XPath.XPathNodeType.Root>|<span data-ttu-id="55c5e-112">Nieobsługiwane.</span><span class="sxs-lookup"><span data-stu-id="55c5e-112">Not supported.</span></span>|  
|<xref:System.Xml.XPath.XPathNodeType.Element>|<span data-ttu-id="55c5e-113">Zawartość elementu.</span><span class="sxs-lookup"><span data-stu-id="55c5e-113">The content of the element.</span></span>|  
|<xref:System.Xml.XPath.XPathNodeType.Attribute>|<span data-ttu-id="55c5e-114">Wartość atrybutu.</span><span class="sxs-lookup"><span data-stu-id="55c5e-114">The value of the attribute.</span></span>|  
|<xref:System.Xml.XPath.XPathNodeType.Text>|<span data-ttu-id="55c5e-115">Zawartość tekstowa.</span><span class="sxs-lookup"><span data-stu-id="55c5e-115">The text content.</span></span>|  
|<xref:System.Xml.XPath.XPathNodeType.ProcessingInstruction>|<span data-ttu-id="55c5e-116">Zawartość, z wyłączeniem celu.</span><span class="sxs-lookup"><span data-stu-id="55c5e-116">The content, excluding the target.</span></span>|  
|<xref:System.Xml.XPath.XPathNodeType.Comment>|<span data-ttu-id="55c5e-117">Zawartość komentarza.</span><span class="sxs-lookup"><span data-stu-id="55c5e-117">The content of the comment.</span></span>|  
|<xref:System.Xml.XPath.XPathNodeType.Namespace>|<span data-ttu-id="55c5e-118">Nieobsługiwane.</span><span class="sxs-lookup"><span data-stu-id="55c5e-118">Not Supported.</span></span>|  
  
> [!NOTE]
> <span data-ttu-id="55c5e-119">Edytowanie <xref:System.Xml.XPath.XPathNodeType.Namespace> węzłów lub <xref:System.Xml.XPath.XPathNodeType.Root> węzła nie jest obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="55c5e-119">Editing <xref:System.Xml.XPath.XPathNodeType.Namespace> nodes or the <xref:System.Xml.XPath.XPathNodeType.Root> node is not supported.</span></span>  
  
 <span data-ttu-id="55c5e-120"><xref:System.Xml.XPath.XPathNavigator> Klasa zawiera również zestaw metod służących do wstawiania i usuwania węzłów.</span><span class="sxs-lookup"><span data-stu-id="55c5e-120">The <xref:System.Xml.XPath.XPathNavigator> class also provides a set of methods used to insert and remove nodes.</span></span> <span data-ttu-id="55c5e-121">Aby uzyskać więcej informacji na temat wstawiania i usuwania węzłów z dokumentu XML, zobacz temat [Wstawianie danych XML przy użyciu klasy XPathNavigator](../../../../docs/standard/data/xml/insert-xml-data-using-xpathnavigator.md) i [usuwanie danych XML przy użyciu klasy XPathNavigator](../../../../docs/standard/data/xml/remove-xml-data-using-xpathnavigator.md) .</span><span class="sxs-lookup"><span data-stu-id="55c5e-121">For more information about inserting and removing nodes from an XML document, see the [Insert XML Data using XPathNavigator](../../../../docs/standard/data/xml/insert-xml-data-using-xpathnavigator.md) and [Remove XML Data using XPathNavigator](../../../../docs/standard/data/xml/remove-xml-data-using-xpathnavigator.md) topics.</span></span>  
  
### <a name="modifying-untyped-values"></a><span data-ttu-id="55c5e-122">Modyfikowanie wartości niewpisanych</span><span class="sxs-lookup"><span data-stu-id="55c5e-122">Modifying Untyped Values</span></span>  
 <span data-ttu-id="55c5e-123"><xref:System.Xml.XPath.XPathNavigator.SetValue%2A> Metoda po prostu wstawia `string` wartość bez typu jako parametr jako wartość węzła, na którym <xref:System.Xml.XPath.XPathNavigator> znajduje się obiekt.</span><span class="sxs-lookup"><span data-stu-id="55c5e-123">The <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> method simply inserts the untyped `string` value passed as a parameter as the value of the node the <xref:System.Xml.XPath.XPathNavigator> object is currently positioned on.</span></span> <span data-ttu-id="55c5e-124">Wartość jest wstawiana bez żadnego typu lub bez weryfikowania, czy nowa wartość jest prawidłowa zgodnie z typem węzła, jeśli dostępne są informacje o schemacie.</span><span class="sxs-lookup"><span data-stu-id="55c5e-124">The value is inserted without any type or without verifying that the new value is valid according to the type of the node if schema information is available.</span></span>  
  
 <span data-ttu-id="55c5e-125">W poniższym przykładzie <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> Metoda jest używana do aktualizowania wszystkich `price` elementów w `contosoBooks.xml` pliku.</span><span class="sxs-lookup"><span data-stu-id="55c5e-125">In the following example, the <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> method is used to update all `price` elements in the `contosoBooks.xml` file.</span></span>  
  
 [!code-cpp[XPathNavigatorMethods#47](../../../../samples/snippets/cpp/VS_Snippets_Data/XPathNavigatorMethods/CPP/xpathnavigatormethods.cpp#47)]
 [!code-csharp[XPathNavigatorMethods#47](../../../../samples/snippets/csharp/VS_Snippets_Data/XPathNavigatorMethods/CS/xpathnavigatormethods.cs#47)]
 [!code-vb[XPathNavigatorMethods#47](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XPathNavigatorMethods/VB/xpathnavigatormethods.vb#47)]  
  
 <span data-ttu-id="55c5e-126">Przykład pobiera `contosoBooks.xml` plik jako dane wejściowe.</span><span class="sxs-lookup"><span data-stu-id="55c5e-126">The example takes the `contosoBooks.xml` file as an input.</span></span>  
  
 [!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]  
  
### <a name="modifying-typed-values"></a><span data-ttu-id="55c5e-127">Modyfikowanie wpisanych wartości</span><span class="sxs-lookup"><span data-stu-id="55c5e-127">Modifying Typed Values</span></span>  
 <span data-ttu-id="55c5e-128">Gdy typ węzła jest typem prostym schematu XML W3C, Nowa wartość wstawiona przez <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> metodę jest sprawdzana względem aspektów typu prostego przed ustawieniem wartości.</span><span class="sxs-lookup"><span data-stu-id="55c5e-128">When the type of a node is a W3C XML Schema simple type, the new value inserted by the <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> method is checked against the facets of the simple type before the value is set.</span></span> <span data-ttu-id="55c5e-129">Jeśli nowa wartość jest nieprawidłowa w zależności od typu węzła (na przykład ustawienie wartości `-1` w elemencie, którego typem jest `xs:positiveInteger`), powoduje wyjątek.</span><span class="sxs-lookup"><span data-stu-id="55c5e-129">If the new value is not valid according to the type of the node (for example, setting a value of `-1` on an element whose type is `xs:positiveInteger`), it results in an exception.</span></span>  
  
 <span data-ttu-id="55c5e-130">`price` Poniższy przykład próbuje zmienić wartość elementu pierwszego `book` elementu w `contosoBooks.xml` pliku na <xref:System.DateTime> wartość.</span><span class="sxs-lookup"><span data-stu-id="55c5e-130">The following example attempts to change the value of the `price` element of the first `book` element in the `contosoBooks.xml` file to a <xref:System.DateTime> value.</span></span> <span data-ttu-id="55c5e-131">Ponieważ typ schematu XML `price` elementu jest zdefiniowany jako `xs:decimal` w `contosoBooks.xsd` plikach, spowoduje to wyjątek.</span><span class="sxs-lookup"><span data-stu-id="55c5e-131">Because the XML Schema type of the `price` element is defined as `xs:decimal` in the `contosoBooks.xsd` files, this results in an exception.</span></span>  
  
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
  
navigator.SetTypedValue(DateTime.Now)  
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
  
navigator.SetTypedValue(DateTime.Now);  
```  
  
 <span data-ttu-id="55c5e-132">Przykład pobiera `contosoBooks.xml` plik jako dane wejściowe.</span><span class="sxs-lookup"><span data-stu-id="55c5e-132">The example takes the `contosoBooks.xml` file as an input.</span></span>  
  
 [!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]  
  
 <span data-ttu-id="55c5e-133">Przykład pobiera również `contosoBooks.xsd` jako dane wejściowe.</span><span class="sxs-lookup"><span data-stu-id="55c5e-133">The example also takes the `contosoBooks.xsd` as an input.</span></span>  
  
 [!code-xml[XPathXMLExamples#3](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xsd#3)]  
  
#### <a name="the-effects-of-editing-strongly-typed-xml-data"></a><span data-ttu-id="55c5e-134">Efekty edytowania danych XML o jednoznacznie określonym typie</span><span class="sxs-lookup"><span data-stu-id="55c5e-134">The Effects of Editing Strongly Typed XML Data</span></span>  
 <span data-ttu-id="55c5e-135"><xref:System.Xml.XPath.XPathNavigator> Klasa używa schematu W3C XML jako podstawy do opisywania XML o jednoznacznie określonym typie.</span><span class="sxs-lookup"><span data-stu-id="55c5e-135">The <xref:System.Xml.XPath.XPathNavigator> class uses the W3C XML Schema as a basis for describing strongly-typed XML.</span></span> <span data-ttu-id="55c5e-136">Elementy i atrybuty mogą być opatrzone adnotacją z informacjami o typie na podstawie walidacji dokumentu XML schematu W3C.</span><span class="sxs-lookup"><span data-stu-id="55c5e-136">Elements and attributes can be annotated with type information based on validation against a W3C XML Schema document.</span></span> <span data-ttu-id="55c5e-137">Elementy, które mogą zawierać inne elementy lub atrybuty, są nazywane typami złożonymi, natomiast te, które mogą zawierać tylko tekstową zawartość, są nazywane typami prostymi.</span><span class="sxs-lookup"><span data-stu-id="55c5e-137">Elements that can contain other elements or attributes are called complex types, while those that can only contain textual content are called simple types.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="55c5e-138">Atrybuty mogą mieć tylko typy proste.</span><span class="sxs-lookup"><span data-stu-id="55c5e-138">Attributes can only have simple types.</span></span>  
  
 <span data-ttu-id="55c5e-139">Element lub atrybut może być uznawany za schemat-prawidłowy, jeśli jest zgodny ze wszystkimi regułami specyficznymi dla definicji typu.</span><span class="sxs-lookup"><span data-stu-id="55c5e-139">An element or attribute can be considered to be schema-valid if it conforms to all the rules specific to its type definition.</span></span> <span data-ttu-id="55c5e-140">Element, który ma typ `xs:int` prosty, musi zawierać wartość liczbową z przedziału od-2147483648 do 2147483647, aby był prawidłowym schematem.</span><span class="sxs-lookup"><span data-stu-id="55c5e-140">An element that has the simple type `xs:int` has to contain a numeric value between -2147483648 and 2147483647 to be schema-valid.</span></span> <span data-ttu-id="55c5e-141">W przypadku typów złożonych, walidacja schematu elementu jest zależna od poprawności schematu, jego elementów podrzędnych i atrybutów.</span><span class="sxs-lookup"><span data-stu-id="55c5e-141">For complex types, the schema-validity of the element is dependent on the schema-validity of its child elements and attributes.</span></span> <span data-ttu-id="55c5e-142">W tym przypadku, jeśli element jest prawidłowy względem definicji typu złożonego, wszystkie jego elementy podrzędne i atrybuty są prawidłowe względem ich definicji typów.</span><span class="sxs-lookup"><span data-stu-id="55c5e-142">Thus if an element is valid against its complex type definition, all its child elements and attributes are valid against their type definitions.</span></span> <span data-ttu-id="55c5e-143">Podobnie, jeśli nawet jeden z elementów podrzędnych lub atrybutów elementu jest nieprawidłowy względem definicji typu lub ma nieznane ważność, element jest również nieprawidłowy lub nieznanej ważności.</span><span class="sxs-lookup"><span data-stu-id="55c5e-143">Similarly, if even one of the child elements or attributes of an element is invalid against its type definition, or has an unknown validity, the element is also either invalid or of unknown validity.</span></span>  
  
 <span data-ttu-id="55c5e-144">Uwzględniając, że ważność elementu jest zależna od ważności jego elementów podrzędnych i atrybutów, modyfikacje w wyniku zmiany ważności elementu, jeśli były wcześniej ważne.</span><span class="sxs-lookup"><span data-stu-id="55c5e-144">Given that the validity of an element is dependent on the validity of its child elements and attributes, modifications to either result in altering the validity of the element if it was previously valid.</span></span> <span data-ttu-id="55c5e-145">W przypadku, gdy elementy podrzędne lub atrybuty elementu są wstawiane, aktualizowane lub usuwane, ważność elementu jest nieznana.</span><span class="sxs-lookup"><span data-stu-id="55c5e-145">Specifically, if the child elements or attributes of an element are inserted, updated, or deleted, then the validity of the element becomes unknown.</span></span> <span data-ttu-id="55c5e-146">Jest to reprezentowane przez <xref:System.Xml.Schema.IXmlSchemaInfo.Validity%2A> właściwość elementu <xref:System.Xml.XPath.XPathNavigator.SchemaInfo%2A> , który jest ustawiany na. <xref:System.Xml.Schema.XmlSchemaValidity.NotKnown></span><span class="sxs-lookup"><span data-stu-id="55c5e-146">This is represented by the <xref:System.Xml.Schema.IXmlSchemaInfo.Validity%2A> property of the element's <xref:System.Xml.XPath.XPathNavigator.SchemaInfo%2A> property being set to <xref:System.Xml.Schema.XmlSchemaValidity.NotKnown>.</span></span> <span data-ttu-id="55c5e-147">Co więcej, ten efekt kaskadowo umieszcza w całym dokumencie XML, ponieważ ważność elementu nadrzędnego elementu (i jego elementu nadrzędnego itd.) również będzie nieznana.</span><span class="sxs-lookup"><span data-stu-id="55c5e-147">Furthermore, this effect cascades upwards recursively across the XML document, because the validity of the element's parent element (and its parent element, and so on) also becomes unknown.</span></span>  
  
 <span data-ttu-id="55c5e-148">Aby uzyskać więcej informacji o walidacji schematu <xref:System.Xml.XPath.XPathNavigator> i klasie, zobacz [Walidacja schematu przy użyciu elementu XPathNavigator](../../../../docs/standard/data/xml/schema-validation-using-xpathnavigator.md).</span><span class="sxs-lookup"><span data-stu-id="55c5e-148">For more information about schema validation and the <xref:System.Xml.XPath.XPathNavigator> class, see [Schema Validation using XPathNavigator](../../../../docs/standard/data/xml/schema-validation-using-xpathnavigator.md).</span></span>  
  
### <a name="modifying-attributes"></a><span data-ttu-id="55c5e-149">Modyfikowanie atrybutów</span><span class="sxs-lookup"><span data-stu-id="55c5e-149">Modifying Attributes</span></span>  
 <span data-ttu-id="55c5e-150">Metody <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> i <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> mogą być używane do modyfikowania węzłów atrybutów nietypów i typów, jak również inne typy węzłów wymienione w sekcji "Modyfikowanie węzłów".</span><span class="sxs-lookup"><span data-stu-id="55c5e-150">The <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> and <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> methods can be used to modify untyped and typed attribute nodes as well as the other node types listed in the "Modifying Nodes" section.</span></span>  
  
 <span data-ttu-id="55c5e-151">Poniższy przykład zmienia wartość `genre` atrybutu pierwszego `book` elementu w `books.xml` pliku.</span><span class="sxs-lookup"><span data-stu-id="55c5e-151">The following example changes the value of the `genre` attribute of the first `book` element in the `books.xml` file.</span></span>  
  
```vb  
Dim document As XmlDocument = New XmlDocument()  
document.Load("books.xml")  
Dim navigator As XPathNavigator = document.CreateNavigator()  
  
navigator.MoveToChild("bookstore", String.Empty)  
navigator.MoveToChild("book", String.Empty)  
navigator.MoveToAttribute("genre", String.Empty)  
  
navigator.SetValue("non-fiction")  
  
navigator.MoveToRoot()  
Console.WriteLine(navigator.OuterXml)  
```  
  
```csharp  
XmlDocument document = new XmlDocument();  
document.Load("books.xml");  
XPathNavigator navigator = document.CreateNavigator();  
  
navigator.MoveToChild("bookstore", String.Empty);  
navigator.MoveToChild("book", String.Empty);  
navigator.MoveToAttribute("genre", String.Empty);  
  
navigator.SetValue("non-fiction");  
  
navigator.MoveToRoot();  
Console.WriteLine(navigator.OuterXml);  
```  
  
 <span data-ttu-id="55c5e-152">Aby uzyskać więcej informacji o <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> metodach i <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> , zobacz sekcję "Modyfikowanie wartości niewpisanych" i "Modyfikowanie wartości wpisanych".</span><span class="sxs-lookup"><span data-stu-id="55c5e-152">For more information about the <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> and <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> methods, see the "Modifying Untyped Values" and "Modifying Typed Values" sections.</span></span>  
  
## <a name="innerxml-and-outerxml-properties"></a><span data-ttu-id="55c5e-153">Właściwości InnerXml i OuterXml</span><span class="sxs-lookup"><span data-stu-id="55c5e-153">InnerXml and OuterXml Properties</span></span>  
 <span data-ttu-id="55c5e-154">Właściwości <xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> i <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> <xref:System.Xml.XPath.XPathNavigator> klasy zmieniają znaczniki XML w węzłach, w których <xref:System.Xml.XPath.XPathNavigator> obiekt jest obecnie umieszczony.</span><span class="sxs-lookup"><span data-stu-id="55c5e-154">The <xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> and <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> properties of the <xref:System.Xml.XPath.XPathNavigator> class change the XML markup of the nodes an <xref:System.Xml.XPath.XPathNavigator> object is currently positioned on.</span></span>  
  
 <span data-ttu-id="55c5e-155"><xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> Właściwość zmienia znaczniki XML węzłów podrzędnych <xref:System.Xml.XPath.XPathNavigator> obiekt jest obecnie umieszczony w przeanalizowanej zawartości danego kodu XML `string`.</span><span class="sxs-lookup"><span data-stu-id="55c5e-155">The <xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> property changes the XML markup of the child nodes an <xref:System.Xml.XPath.XPathNavigator> object is currently positioned on with the parsed contents of the given XML `string`.</span></span> <span data-ttu-id="55c5e-156">Podobnie <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> właściwość zmienia znaczniki XML węzłów podrzędnych, w których <xref:System.Xml.XPath.XPathNavigator> obiekt jest obecnie umieszczony, a także bieżący węzeł.</span><span class="sxs-lookup"><span data-stu-id="55c5e-156">Similarly, the <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> property changes the XML markup of the child nodes an <xref:System.Xml.XPath.XPathNavigator> object is currently positioned on as well as the current node itself.</span></span>  
  
 <span data-ttu-id="55c5e-157">Poniższy przykład używa <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> właściwości, aby zmodyfikować wartość `price` elementu i wstawić nowy `discount` atrybut pierwszego `book` elementu w `contosoBooks.xml` pliku.</span><span class="sxs-lookup"><span data-stu-id="55c5e-157">The following example uses the <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> property to modify the value of the `price` element and insert a new `discount` attribute on the first `book` element in the `contosoBooks.xml` file.</span></span>  
  
```vb  
Dim document As XmlDocument = New XmlDocument()  
document.Load("contosoBooks.xml");  
Dim navigator As XPathNavigator = document.CreateNavigator()  
  
navigator.MoveToChild("bookstore", "http://www.contoso.com/books")  
navigator.MoveToChild("book", "http://www.contoso.com/books")  
navigator.MoveToChild("price", "http://www.contoso.com/books")  
  
navigator.OuterXml = "<price discount=\"0\">10.99</price>"  
  
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
  
navigator.OuterXml = "<price discount=\"0\">10.99</price>";  
  
navigator.MoveToRoot();  
Console.WriteLine(navigator.OuterXml);  
```  
  
 <span data-ttu-id="55c5e-158">Przykład pobiera `contosoBooks.xml` plik jako dane wejściowe.</span><span class="sxs-lookup"><span data-stu-id="55c5e-158">The example takes the `contosoBooks.xml` file as an input.</span></span>  
  
 [!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]  
  
## <a name="modifying-namespace-nodes"></a><span data-ttu-id="55c5e-159">Modyfikowanie węzłów przestrzeni nazw</span><span class="sxs-lookup"><span data-stu-id="55c5e-159">Modifying Namespace Nodes</span></span>  
 <span data-ttu-id="55c5e-160">W Document Object Model (DOM) deklaracje przestrzeni nazw są traktowane tak, jakby były zwykłymi atrybutami, które można wstawiać, aktualizować i usuwać.</span><span class="sxs-lookup"><span data-stu-id="55c5e-160">In the Document Object Model (DOM), namespace declarations are treated as if they are regular attributes that can be inserted, updated and deleted.</span></span> <span data-ttu-id="55c5e-161"><xref:System.Xml.XPath.XPathNavigator> Klasa nie zezwala na takie operacje w węzłach przestrzeni nazw, ponieważ zmiana wartości węzła przestrzeni nazw może zmienić tożsamość elementów i atrybutów w zakresie węzła przestrzeni nazw, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="55c5e-161">The <xref:System.Xml.XPath.XPathNavigator> class does not allow such operations on namespace nodes because altering the value of a namespace node can change the identity of the elements and attributes within the scope of the namespace node as illustrated in the following example.</span></span>  
  
```xml  
<root xmlns="http://www.contoso.com">  
    <child />  
</root>  
```  
  
 <span data-ttu-id="55c5e-162">Jeśli powyższy przykład XML zostanie zmieniony w następujący sposób, to efektywnie zmienia nazwę każdego elementu w dokumencie, ponieważ wartość identyfikatora URI każdego elementu jest zmieniana.</span><span class="sxs-lookup"><span data-stu-id="55c5e-162">If the XML example above is changed in the following way, this effectively renames every element in the document because the value of each element's namespace URI is changed.</span></span>  
  
```xml  
<root xmlns="urn:contoso.com">  
    <child />  
</root>  
```  
  
 <span data-ttu-id="55c5e-163">Wstawianie węzłów przestrzeni nazw, które nie powodują konfliktu z deklaracjami przestrzeni nazw w zakresie, w którym są wstawiane <xref:System.Xml.XPath.XPathNavigator> , jest dozwolone przez klasę.</span><span class="sxs-lookup"><span data-stu-id="55c5e-163">Inserting namespace nodes that do not conflict with namespace declarations at the scope that they are inserted in is allowed by the <xref:System.Xml.XPath.XPathNavigator> class.</span></span> <span data-ttu-id="55c5e-164">W takim przypadku deklaracje przestrzeni nazw nie są deklarowane w niższych zakresach dokumentu XML i nie powoduje zmiany nazwy, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="55c5e-164">In this case, the namespace declarations are not declared at lower scopes in the XML document and does not result in renaming as illustrated in the following example.</span></span>  
  
```xml  
<root xmlns:a="http://www.contoso.com">  
    <parent>  
        <a:child />  
    </parent>  
</root>  
```  
  
 <span data-ttu-id="55c5e-165">Jeśli przykładowy kod XML został zmieniony w następujący sposób, deklaracje przestrzeni nazw są poprawnie propagowane w dokumencie XML poniżej zakresu innej deklaracji przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="55c5e-165">If the XML example above is changed in the following way, the namespace declarations are correctly propagated across the XML document below the scope of the other namespace declaration.</span></span>  
  
```xml  
<root xmlns:a="http://www.contoso.com">  
    <parent a:parent-id="1234" xmlns:a="http://www.contoso.com/parent-id">  
        <a:child xmlns:a="http://www.contoso.com/" />  
    </parent>  
</root>  
```  
  
 <span data-ttu-id="55c5e-166">W powyższym przykładzie XML atrybut `a:parent-id` jest wstawiany do `parent` elementu w `http://www.contoso.com/parent-id` przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="55c5e-166">In the XML example above, the attribute `a:parent-id` is inserted on the `parent` element in the `http://www.contoso.com/parent-id` namespace.</span></span> <span data-ttu-id="55c5e-167"><xref:System.Xml.XPath.XPathNavigator.CreateAttribute%2A> Metoda jest używana do wstawiania atrybutu podczas umieszczania w `parent` elemencie.</span><span class="sxs-lookup"><span data-stu-id="55c5e-167">The <xref:System.Xml.XPath.XPathNavigator.CreateAttribute%2A> method is used to insert the attribute while positioned on the `parent` element.</span></span> <span data-ttu-id="55c5e-168">Deklaracja `http://www.contoso.com` przestrzeni nazw jest automatycznie wstawiana przez <xref:System.Xml.XPath.XPathNavigator> klasę, aby zachować spójność reszty dokumentu XML.</span><span class="sxs-lookup"><span data-stu-id="55c5e-168">The `http://www.contoso.com` namespace declaration is automatically inserted by the <xref:System.Xml.XPath.XPathNavigator> class to preserve the consistency of the rest of the XML document.</span></span>  
  
## <a name="modifying-entity-reference-nodes"></a><span data-ttu-id="55c5e-169">Modyfikowanie węzłów odwołań do jednostek</span><span class="sxs-lookup"><span data-stu-id="55c5e-169">Modifying Entity Reference Nodes</span></span>  
 <span data-ttu-id="55c5e-170">Węzły odwołania jednostki w <xref:System.Xml.XmlDocument> obiekcie są tylko do odczytu i nie można ich edytować przy użyciu klas <xref:System.Xml.XPath.XPathNavigator> lub <xref:System.Xml.XmlNode> .</span><span class="sxs-lookup"><span data-stu-id="55c5e-170">Entity reference nodes in an <xref:System.Xml.XmlDocument> object are read-only and cannot be edited using either the <xref:System.Xml.XPath.XPathNavigator> or <xref:System.Xml.XmlNode> classes.</span></span> <span data-ttu-id="55c5e-171">Każda próba zmodyfikowania węzła odwołania do jednostki spowoduje wystąpienie elementu <xref:System.InvalidOperationException>.</span><span class="sxs-lookup"><span data-stu-id="55c5e-171">Any attempt to modify an entity reference node results in an <xref:System.InvalidOperationException>.</span></span>  
  
## <a name="modifying-xsinil-nodes"></a><span data-ttu-id="55c5e-172">Modyfikowanie węzłów xsi: nil</span><span class="sxs-lookup"><span data-stu-id="55c5e-172">Modifying xsi:nil Nodes</span></span>  
 <span data-ttu-id="55c5e-173">Zalecenie dotyczące schematu W3C XML wprowadza koncepcję elementu, który jest nillable.</span><span class="sxs-lookup"><span data-stu-id="55c5e-173">The W3C XML Schema recommendation introduces the concept of an element being nillable.</span></span> <span data-ttu-id="55c5e-174">Gdy element jest nillable, możliwe jest, aby element nie miał zawartości i nadal był prawidłowy.</span><span class="sxs-lookup"><span data-stu-id="55c5e-174">When an element is nillable, it is possible for the element to have no content and still be valid.</span></span> <span data-ttu-id="55c5e-175">Koncepcja elementu nillable jest podobna do koncepcji obiektu `null`.</span><span class="sxs-lookup"><span data-stu-id="55c5e-175">The concept of an element being nillable is similar to the concept of an object being `null`.</span></span> <span data-ttu-id="55c5e-176">Główną różnicą jest to, `null` że nie można uzyskać dostępu do obiektu w jakikolwiek sposób `xsi:nil` , podczas gdy element ma nadal właściwości, takie jak atrybuty, do których można uzyskać dostęp, ale nie ma zawartości (elementy podrzędne lub tekst).</span><span class="sxs-lookup"><span data-stu-id="55c5e-176">The main difference is that a `null` object cannot be accessed in any way, while an `xsi:nil` element still has properties such as attributes that can be accessed, but has no content (child elements or text).</span></span> <span data-ttu-id="55c5e-177">Istnienie `xsi:nil` atrybutu o wartości `true` elementu w dokumencie XML umożliwia wskazanie, że element nie ma zawartości.</span><span class="sxs-lookup"><span data-stu-id="55c5e-177">The existence of the `xsi:nil` attribute with a value of `true` on an element in an XML document is used to indicate that an element has no content.</span></span>  
  
 <span data-ttu-id="55c5e-178">Jeśli <xref:System.Xml.XPath.XPathNavigator> `xsi:nil` obiekt jest używany do dodawania zawartości do prawidłowego elementu z atrybutem o wartości `true`, wartość `xsi:nil` atrybutu jest ustawiona na. `false`</span><span class="sxs-lookup"><span data-stu-id="55c5e-178">If an <xref:System.Xml.XPath.XPathNavigator> object is used to add content to a valid element with an `xsi:nil` attribute with a value of `true`, the value of its `xsi:nil` attribute is set to `false`.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="55c5e-179">Jeśli zawartość elementu z `xsi:nil` atrybutem ustawionym na `false` jest usuwana, wartość atrybutu nie zostanie zmieniona na. `true`</span><span class="sxs-lookup"><span data-stu-id="55c5e-179">If the content of an element with an `xsi:nil` attribute set to `false` is deleted, the value of the attribute is not changed to `true`.</span></span>  
  
## <a name="saving-an-xml-document"></a><span data-ttu-id="55c5e-180">Zapisywanie dokumentu XML</span><span class="sxs-lookup"><span data-stu-id="55c5e-180">Saving an XML Document</span></span>  
 <span data-ttu-id="55c5e-181">Zapisywanie zmian wprowadzonych w <xref:System.Xml.XmlDocument> obiekcie w wyniku metod edycji opisanych w tym temacie jest wykonywane przy użyciu metod <xref:System.Xml.XmlDocument> klasy.</span><span class="sxs-lookup"><span data-stu-id="55c5e-181">Saving changes made to an <xref:System.Xml.XmlDocument> object as the result of the editing methods described in this topic is performed using the methods of the <xref:System.Xml.XmlDocument> class.</span></span> <span data-ttu-id="55c5e-182">Aby uzyskać więcej informacji na temat zapisywania zmian wprowadzonych w <xref:System.Xml.XmlDocument> obiekcie, zobacz [Zapisywanie i pisanie dokumentu](../../../../docs/standard/data/xml/saving-and-writing-a-document.md).</span><span class="sxs-lookup"><span data-stu-id="55c5e-182">For more information about saving changes made to an <xref:System.Xml.XmlDocument> object, see [Saving and Writing a Document](../../../../docs/standard/data/xml/saving-and-writing-a-document.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="55c5e-183">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="55c5e-183">See also</span></span>

- <xref:System.Xml.XmlDocument>
- <xref:System.Xml.XPath.XPathDocument>
- <xref:System.Xml.XPath.XPathNavigator>
- [<span data-ttu-id="55c5e-184">Przetwarzanie danych XML przy użyciu modelu danych XPath</span><span class="sxs-lookup"><span data-stu-id="55c5e-184">Process XML Data Using the XPath Data Model</span></span>](../../../../docs/standard/data/xml/process-xml-data-using-the-xpath-data-model.md)
- [<span data-ttu-id="55c5e-185">Wstawianie danych XML przy użyciu klasy XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="55c5e-185">Insert XML Data using XPathNavigator</span></span>](../../../../docs/standard/data/xml/insert-xml-data-using-xpathnavigator.md)
- [<span data-ttu-id="55c5e-186">Usuwanie danych XML przy użyciu klasy XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="55c5e-186">Remove XML Data using XPathNavigator</span></span>](../../../../docs/standard/data/xml/remove-xml-data-using-xpathnavigator.md)
