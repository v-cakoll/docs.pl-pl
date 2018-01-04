---
title: "Modyfikowanie danych XML przy użyciu parametrem XPathNavigator"
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
- cpp
ms.assetid: 03a7c5a1-b296-4af4-b209-043c958dc0a5
caps.latest.revision: "2"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: cc46aeda6efe9f21bc094a4bc9d211fc282e9b65
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/23/2017
---
# <a name="modify-xml-data-using-xpathnavigator"></a><span data-ttu-id="a6995-102">Modyfikowanie danych XML przy użyciu parametrem XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="a6995-102">Modify XML Data using XPathNavigator</span></span>
<span data-ttu-id="a6995-103"><xref:System.Xml.XPath.XPathNavigator> Klasa udostępnia zestaw metod używane do modyfikowania węzły i wartości w dokumencie XML.</span><span class="sxs-lookup"><span data-stu-id="a6995-103">The <xref:System.Xml.XPath.XPathNavigator> class provides a set of methods used to modify nodes and values in an XML document.</span></span> <span data-ttu-id="a6995-104">Aby można było używać tych metod <xref:System.Xml.XPath.XPathNavigator> obiekt musi być edytowalny, czyli jego <xref:System.Xml.XPath.XPathNavigator.CanEdit%2A> właściwość musi być `true`.</span><span class="sxs-lookup"><span data-stu-id="a6995-104">In order to use these methods, the <xref:System.Xml.XPath.XPathNavigator> object must be editable, that is, its <xref:System.Xml.XPath.XPathNavigator.CanEdit%2A> property must be `true`.</span></span>  
  
 <span data-ttu-id="a6995-105"><xref:System.Xml.XPath.XPathNavigator>obiekty, które można edytować dokumentu XML są tworzone przez <xref:System.Xml.XmlDocument.CreateNavigator%2A> metody <xref:System.Xml.XmlDocument> klasy.</span><span class="sxs-lookup"><span data-stu-id="a6995-105"><xref:System.Xml.XPath.XPathNavigator> objects that can edit an XML document are created by the <xref:System.Xml.XmlDocument.CreateNavigator%2A> method of the <xref:System.Xml.XmlDocument> class.</span></span> <span data-ttu-id="a6995-106"><xref:System.Xml.XPath.XPathNavigator>obiekty utworzone przez <xref:System.Xml.XPath.XPathDocument> klasy są tylko do odczytu i próby użycia metody edycji <xref:System.Xml.XPath.XPathNavigator> obiekt utworzony przez <xref:System.Xml.XPath.XPathDocument> obiektów wyników w <xref:System.NotSupportedException>.</span><span class="sxs-lookup"><span data-stu-id="a6995-106"><xref:System.Xml.XPath.XPathNavigator> objects created by the <xref:System.Xml.XPath.XPathDocument> class are read-only and any attempt to use the editing methods of an <xref:System.Xml.XPath.XPathNavigator> object created by an <xref:System.Xml.XPath.XPathDocument> object result in a <xref:System.NotSupportedException>.</span></span>  
  
 <span data-ttu-id="a6995-107">Aby uzyskać więcej informacji o tworzeniu można edytować <xref:System.Xml.XPath.XPathNavigator> obiekty, zobacz [odczytywania danych XML przy użyciu XPathDocument i XmlDocument](../../../../docs/standard/data/xml/reading-xml-data-using-xpathdocument-and-xmldocument.md).</span><span class="sxs-lookup"><span data-stu-id="a6995-107">For more information about creating editable <xref:System.Xml.XPath.XPathNavigator> objects, see [Reading XML Data using XPathDocument and XmlDocument](../../../../docs/standard/data/xml/reading-xml-data-using-xpathdocument-and-xmldocument.md).</span></span>  
  
## <a name="modifying-nodes"></a><span data-ttu-id="a6995-108">Modyfikowanie węzłów</span><span class="sxs-lookup"><span data-stu-id="a6995-108">Modifying Nodes</span></span>  
 <span data-ttu-id="a6995-109">Prosta technika w przypadku zmiany wartości węzła jest użycie <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> i <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> metody <xref:System.Xml.XPath.XPathNavigator> klasy.</span><span class="sxs-lookup"><span data-stu-id="a6995-109">A simple technique for changing the value of a node is to use the <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> and <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> methods of the <xref:System.Xml.XPath.XPathNavigator> class.</span></span>  
  
 <span data-ttu-id="a6995-110">W poniższej tabeli wymieniono wpływu tych metod na inny węzeł typów.</span><span class="sxs-lookup"><span data-stu-id="a6995-110">The following table lists the effects of these methods on different node types.</span></span>  
  
|<xref:System.Xml.XPath.XPathNodeType>|<span data-ttu-id="a6995-111">Zmienione dane</span><span class="sxs-lookup"><span data-stu-id="a6995-111">Data Changed</span></span>|  
|---------------------------------------------------------------------------------------------------------------------------------------------|------------------|  
|<xref:System.Xml.XPath.XPathNodeType.Root>|<span data-ttu-id="a6995-112">Nieobsługiwane.</span><span class="sxs-lookup"><span data-stu-id="a6995-112">Not supported.</span></span>|  
|<xref:System.Xml.XPath.XPathNodeType.Element>|<span data-ttu-id="a6995-113">Zawartość elementu.</span><span class="sxs-lookup"><span data-stu-id="a6995-113">The content of the element.</span></span>|  
|<xref:System.Xml.XPath.XPathNodeType.Attribute>|<span data-ttu-id="a6995-114">Wartość atrybutu.</span><span class="sxs-lookup"><span data-stu-id="a6995-114">The value of the attribute.</span></span>|  
|<xref:System.Xml.XPath.XPathNodeType.Text>|<span data-ttu-id="a6995-115">Zawartość tekstowa.</span><span class="sxs-lookup"><span data-stu-id="a6995-115">The text content.</span></span>|  
|<xref:System.Xml.XPath.XPathNodeType.ProcessingInstruction>|<span data-ttu-id="a6995-116">Zawartość, z wyłączeniem obiektu docelowego.</span><span class="sxs-lookup"><span data-stu-id="a6995-116">The content, excluding the target.</span></span>|  
|<xref:System.Xml.XPath.XPathNodeType.Comment>|<span data-ttu-id="a6995-117">Zawartość komentarza.</span><span class="sxs-lookup"><span data-stu-id="a6995-117">The content of the comment.</span></span>|  
|<xref:System.Xml.XPath.XPathNodeType.Namespace>|<span data-ttu-id="a6995-118">Nie jest obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="a6995-118">Not Supported.</span></span>|  
  
> [!NOTE]
>  <span data-ttu-id="a6995-119">Edytowanie <xref:System.Xml.XPath.XPathNodeType.Namespace> węzłów lub <xref:System.Xml.XPath.XPathNodeType.Root> węzeł nie jest obsługiwany.</span><span class="sxs-lookup"><span data-stu-id="a6995-119">Editing <xref:System.Xml.XPath.XPathNodeType.Namespace> nodes or the <xref:System.Xml.XPath.XPathNodeType.Root> node is not supported.</span></span>  
  
 <span data-ttu-id="a6995-120"><xref:System.Xml.XPath.XPathNavigator> Klasa udostępnia również zestaw metody używane do wstawiania i usuwania węzłów.</span><span class="sxs-lookup"><span data-stu-id="a6995-120">The <xref:System.Xml.XPath.XPathNavigator> class also provides a set of methods used to insert and remove nodes.</span></span> <span data-ttu-id="a6995-121">Aby uzyskać więcej informacji na temat Wstawianie i usuwanie węzłów z dokumentu XML, zobacz [wstawiania danych XML przy użyciu Element XPathNavigator](../../../../docs/standard/data/xml/insert-xml-data-using-xpathnavigator.md) i [Usuń danych XML przy użyciu Element XPathNavigator](../../../../docs/standard/data/xml/remove-xml-data-using-xpathnavigator.md) tematów.</span><span class="sxs-lookup"><span data-stu-id="a6995-121">For more information about inserting and removing nodes from an XML document, see the [Insert XML Data using XPathNavigator](../../../../docs/standard/data/xml/insert-xml-data-using-xpathnavigator.md) and [Remove XML Data using XPathNavigator](../../../../docs/standard/data/xml/remove-xml-data-using-xpathnavigator.md) topics.</span></span>  
  
### <a name="modifying-untyped-values"></a><span data-ttu-id="a6995-122">Modyfikowanie nieuwzględniające typów wartości</span><span class="sxs-lookup"><span data-stu-id="a6995-122">Modifying Untyped Values</span></span>  
 <span data-ttu-id="a6995-123"><xref:System.Xml.XPath.XPathNavigator.SetValue%2A> Metoda po prostu wstawia bez typu `string` wartość przekazywana jako parametr jako wartość węzła <xref:System.Xml.XPath.XPathNavigator> obiekt znajduje się obecnie na.</span><span class="sxs-lookup"><span data-stu-id="a6995-123">The <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> method simply inserts the untyped `string` value passed as a parameter as the value of the node the <xref:System.Xml.XPath.XPathNavigator> object is currently positioned on.</span></span> <span data-ttu-id="a6995-124">Wartość jest wstawiany bez dowolnego typu lub bez sprawdzenia, czy nowa wartość jest prawidłowa zgodnie z typem węzła, jeśli informacje o schemacie są dostępne.</span><span class="sxs-lookup"><span data-stu-id="a6995-124">The value is inserted without any type or without verifying that the new value is valid according to the type of the node if schema information is available.</span></span>  
  
 <span data-ttu-id="a6995-125">W poniższym przykładzie <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> metody używane do aktualizowania wszystkich `price` elementów w `contosoBooks.xml` pliku.</span><span class="sxs-lookup"><span data-stu-id="a6995-125">In the following example, the <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> method is used to update all `price` elements in the `contosoBooks.xml` file.</span></span>  
  
 [!code-cpp[XPathNavigatorMethods#47](../../../../samples/snippets/cpp/VS_Snippets_Data/XPathNavigatorMethods/CPP/xpathnavigatormethods.cpp#47)]
 [!code-csharp[XPathNavigatorMethods#47](../../../../samples/snippets/csharp/VS_Snippets_Data/XPathNavigatorMethods/CS/xpathnavigatormethods.cs#47)]
 [!code-vb[XPathNavigatorMethods#47](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XPathNavigatorMethods/VB/xpathnavigatormethods.vb#47)]  
  
 <span data-ttu-id="a6995-126">Przykład przyjmuje `contosoBooks.xml` pliku jako danych wejściowych.</span><span class="sxs-lookup"><span data-stu-id="a6995-126">The example takes the `contosoBooks.xml` file as an input.</span></span>  
  
 [!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]  
  
### <a name="modifying-typed-values"></a><span data-ttu-id="a6995-127">Modyfikowanie typu wartości</span><span class="sxs-lookup"><span data-stu-id="a6995-127">Modifying Typed Values</span></span>  
 <span data-ttu-id="a6995-128">Gdy typ węzła to proste schematu W3C XML typ, nowa wartość wstawiane przez <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> przed ma wartość metody zostaje sprawdzony pod kątem aspekty typu prostego.</span><span class="sxs-lookup"><span data-stu-id="a6995-128">When the type of a node is a W3C XML Schema simple type, the new value inserted by the <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> method is checked against the facets of the simple type before the value is set.</span></span> <span data-ttu-id="a6995-129">Jeśli nowa wartość nie jest prawidłowa dla typu węzła (na przykład ustawienie wartości `-1` w elemencie o typie `xs:positiveInteger`), powoduje wygenerowanie wyjątku.</span><span class="sxs-lookup"><span data-stu-id="a6995-129">If the new value is not valid according to the type of the node (for example, setting a value of `-1` on an element whose type is `xs:positiveInteger`), it results in an exception.</span></span>  
  
 <span data-ttu-id="a6995-130">Poniższy przykład próbuje zmienić wartość `price` element pierwszego `book` element `contosoBooks.xml` pliku na <xref:System.DateTime> wartość.</span><span class="sxs-lookup"><span data-stu-id="a6995-130">The following example attempts to change the value of the `price` element of the first `book` element in the `contosoBooks.xml` file to a <xref:System.DateTime> value.</span></span> <span data-ttu-id="a6995-131">Ponieważ typ schematu XML `price` element jest zdefiniowany jako `xs:decimal` w `contosoBooks.xsd` pliki, powoduje to wygenerowanie wyjątku.</span><span class="sxs-lookup"><span data-stu-id="a6995-131">Because the XML Schema type of the `price` element is defined as `xs:decimal` in the `contosoBooks.xsd` files, this results in an exception.</span></span>  
  
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
  
 <span data-ttu-id="a6995-132">Przykład przyjmuje `contosoBooks.xml` pliku jako danych wejściowych.</span><span class="sxs-lookup"><span data-stu-id="a6995-132">The example takes the `contosoBooks.xml` file as an input.</span></span>  
  
 [!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]  
  
 <span data-ttu-id="a6995-133">Przykład również przyjmuje `contosoBooks.xsd` jako danych wejściowych.</span><span class="sxs-lookup"><span data-stu-id="a6995-133">The example also takes the `contosoBooks.xsd` as an input.</span></span>  
  
 [!code-xml[XPathXMLExamples#3](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xsd#3)]  
  
#### <a name="the-effects-of-editing-strongly-typed-xml-data"></a><span data-ttu-id="a6995-134">Edytowanie danych XML jednoznacznie efekty</span><span class="sxs-lookup"><span data-stu-id="a6995-134">The Effects of Editing Strongly Typed XML Data</span></span>  
 <span data-ttu-id="a6995-135"><xref:System.Xml.XPath.XPathNavigator> Klasy używa schematu W3C XML jako podstawa dla opisu jednoznacznie XML.</span><span class="sxs-lookup"><span data-stu-id="a6995-135">The <xref:System.Xml.XPath.XPathNavigator> class uses the W3C XML Schema as a basis for describing strongly-typed XML.</span></span> <span data-ttu-id="a6995-136">Elementy i atrybuty mogą być adnotowany przy informacje typu, w zależności od sprawdzenia poprawności względem schematu W3C XML dokumentu.</span><span class="sxs-lookup"><span data-stu-id="a6995-136">Elements and attributes can be annotated with type information based on validation against a W3C XML Schema document.</span></span> <span data-ttu-id="a6995-137">Elementy, które mogą zawierać innych elementów lub atrybutów są nazywane typów złożonych, gdy te, które mogą zawierać tylko zawartość tekstową są nazywane typów prostych.</span><span class="sxs-lookup"><span data-stu-id="a6995-137">Elements that can contain other elements or attributes are called complex types, while those that can only contain textual content are called simple types.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a6995-138">Atrybuty mogą mieć tylko proste typy.</span><span class="sxs-lookup"><span data-stu-id="a6995-138">Attributes can only have simple types.</span></span>  
  
 <span data-ttu-id="a6995-139">Element lub atrybut jest uznawana za schematu-ważność, jeśli odpowiada wszystkich reguł określonych do jego definicji typu.</span><span class="sxs-lookup"><span data-stu-id="a6995-139">An element or attribute can be considered to be schema-valid if it conforms to all the rules specific to its type definition.</span></span> <span data-ttu-id="a6995-140">Element, który ma typ prosty `xs:int` musi zawierać liczbą z zakresu od -2147483648 do 2147483647 jest nieprawidłowy schemat.</span><span class="sxs-lookup"><span data-stu-id="a6995-140">An element that has the simple type `xs:int` has to contain a numeric value between -2147483648 and 2147483647 to be schema-valid.</span></span> <span data-ttu-id="a6995-141">Dla typów złożonych schematu ważności element jest zależny od schematu ważność jej elementy podrzędne i atrybutów.</span><span class="sxs-lookup"><span data-stu-id="a6995-141">For complex types, the schema-validity of the element is dependent on the schema-validity of its child elements and attributes.</span></span> <span data-ttu-id="a6995-142">W związku z tym jeśli element jest prawidłowy przed jego definicję typu złożonego, wszystkie jego elementy podrzędne i atrybuty są prawidłowe przed ich definicji typu.</span><span class="sxs-lookup"><span data-stu-id="a6995-142">Thus if an element is valid against its complex type definition, all its child elements and attributes are valid against their type definitions.</span></span> <span data-ttu-id="a6995-143">Podobnie jeśli nawet jednego z elementów podrzędnych atrybuty elementu jest nieprawidłowa w przypadku jego definicji typu lub ma nieznany ważności, element jest również nieprawidłowe lub ważności nieznany.</span><span class="sxs-lookup"><span data-stu-id="a6995-143">Similarly, if even one of the child elements or attributes of an element is invalid against its type definition, or has an unknown validity, the element is also either invalid or of unknown validity.</span></span>  
  
 <span data-ttu-id="a6995-144">Biorąc pod uwagę, że ważności element jest zależny od ważności jego elementy podrzędne i atrybuty, albo modyfikacje spowodować zmiany ważności elementu, jeśli został wcześniej prawidłowy.</span><span class="sxs-lookup"><span data-stu-id="a6995-144">Given that the validity of an element is dependent on the validity of its child elements and attributes, modifications to either result in altering the validity of the element if it was previously valid.</span></span> <span data-ttu-id="a6995-145">W szczególności jeśli elementy podrzędne lub atrybuty elementu są wstawiane, zaktualizowane lub usunięte, ważność element staje się nieznany.</span><span class="sxs-lookup"><span data-stu-id="a6995-145">Specifically, if the child elements or attributes of an element are inserted, updated, or deleted, then the validity of the element becomes unknown.</span></span> <span data-ttu-id="a6995-146">To jest reprezentowana przez <xref:System.Xml.Schema.IXmlSchemaInfo.Validity%2A> właściwości elementu <xref:System.Xml.XPath.XPathNavigator.SchemaInfo%2A> właściwości ustawiany <xref:System.Xml.Schema.XmlSchemaValidity.NotKnown>.</span><span class="sxs-lookup"><span data-stu-id="a6995-146">This is represented by the <xref:System.Xml.Schema.IXmlSchemaInfo.Validity%2A> property of the element's <xref:System.Xml.XPath.XPathNavigator.SchemaInfo%2A> property being set to <xref:System.Xml.Schema.XmlSchemaValidity.NotKnown>.</span></span> <span data-ttu-id="a6995-147">Ponadto w tym celu dokonuje kaskadowych do góry rekursywnie w dokumencie XML, ponieważ ważność elementu nadrzędnego elementu (element nadrzędny, i tak dalej) staje się również nieznany.</span><span class="sxs-lookup"><span data-stu-id="a6995-147">Furthermore, this effect cascades upwards recursively across the XML document, because the validity of the element's parent element (and its parent element, and so on) also becomes unknown.</span></span>  
  
 <span data-ttu-id="a6995-148">Aby uzyskać więcej informacji na temat sprawdzania poprawności schematu i <xref:System.Xml.XPath.XPathNavigator> , zobacz [sprawdzanie poprawności schematu użyciu klasy XPathNavigator](../../../../docs/standard/data/xml/schema-validation-using-xpathnavigator.md).</span><span class="sxs-lookup"><span data-stu-id="a6995-148">For more information about schema validation and the <xref:System.Xml.XPath.XPathNavigator> class, see [Schema Validation using XPathNavigator](../../../../docs/standard/data/xml/schema-validation-using-xpathnavigator.md).</span></span>  
  
### <a name="modifying-attributes"></a><span data-ttu-id="a6995-149">Modyfikowanie atrybutów</span><span class="sxs-lookup"><span data-stu-id="a6995-149">Modifying Attributes</span></span>  
 <span data-ttu-id="a6995-150"><xref:System.Xml.XPath.XPathNavigator.SetValue%2A> i <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> metody może służyć do modyfikowania węzłów bez typu i typu atrybutu, a także inne typy węzłów wymienionych w sekcji "Modyfikowanie węzłów".</span><span class="sxs-lookup"><span data-stu-id="a6995-150">The <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> and <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> methods can be used to modify untyped and typed attribute nodes as well as the other node types listed in the "Modifying Nodes" section.</span></span>  
  
 <span data-ttu-id="a6995-151">Poniższy przykład umożliwia zmianę wartości `genre` atrybutu pierwszego `book` element `books.xml` pliku.</span><span class="sxs-lookup"><span data-stu-id="a6995-151">The following example changes the value of the `genre` attribute of the first `book` element in the `books.xml` file.</span></span>  
  
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
  
 <span data-ttu-id="a6995-152">Aby uzyskać więcej informacji na temat <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> i <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> metody, zobacz sekcje "Modyfikowanie nieuwzględniające typów wartości" i "Modyfikowanie wpisane wartości".</span><span class="sxs-lookup"><span data-stu-id="a6995-152">For more information about the <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> and <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> methods, see the "Modifying Untyped Values" and "Modifying Typed Values" sections.</span></span>  
  
## <a name="innerxml-and-outerxml-properties"></a><span data-ttu-id="a6995-153">Właściwości OuterXml i InnerXml</span><span class="sxs-lookup"><span data-stu-id="a6995-153">InnerXml and OuterXml Properties</span></span>  
 <span data-ttu-id="a6995-154"><xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> i <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> właściwości <xref:System.Xml.XPath.XPathNavigator> klasy Zmień adiustację XML węzłów <xref:System.Xml.XPath.XPathNavigator> obiekt znajduje się obecnie na.</span><span class="sxs-lookup"><span data-stu-id="a6995-154">The <xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> and <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> properties of the <xref:System.Xml.XPath.XPathNavigator> class change the XML markup of the nodes an <xref:System.Xml.XPath.XPathNavigator> object is currently positioned on.</span></span>  
  
 <span data-ttu-id="a6995-155"><xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> Znaczników XML węzłów podrzędnych zmiany właściwości <xref:System.Xml.XPath.XPathNavigator> obiekt aktualnie znajduje się na przy użyciu analizowanej zawartości danego XML `string`.</span><span class="sxs-lookup"><span data-stu-id="a6995-155">The <xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> property changes the XML markup of the child nodes an <xref:System.Xml.XPath.XPathNavigator> object is currently positioned on with the parsed contents of the given XML `string`.</span></span> <span data-ttu-id="a6995-156">Podobnie <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> znaczników XML węzłów podrzędnych zmiany właściwości <xref:System.Xml.XPath.XPathNavigator> obiekt aktualnie znajduje się na oraz bieżącego węzła.</span><span class="sxs-lookup"><span data-stu-id="a6995-156">Similarly, the <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> property changes the XML markup of the child nodes an <xref:System.Xml.XPath.XPathNavigator> object is currently positioned on as well as the current node itself.</span></span>  
  
 <span data-ttu-id="a6995-157">W poniższym przykładzie użyto <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> właściwość, aby zmodyfikować wartość `price` elementu i Wstaw nowy `discount` atrybutu pierwszego `book` element `contosoBooks.xml` pliku.</span><span class="sxs-lookup"><span data-stu-id="a6995-157">The following example uses the <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> property to modify the value of the `price` element and insert a new `discount` attribute on the first `book` element in the `contosoBooks.xml` file.</span></span>  
  
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
  
 <span data-ttu-id="a6995-158">Przykład przyjmuje `contosoBooks.xml` pliku jako danych wejściowych.</span><span class="sxs-lookup"><span data-stu-id="a6995-158">The example takes the `contosoBooks.xml` file as an input.</span></span>  
  
 [!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]  
  
## <a name="modifying-namespace-nodes"></a><span data-ttu-id="a6995-159">Modyfikowanie Namespace węzłów</span><span class="sxs-lookup"><span data-stu-id="a6995-159">Modifying Namespace Nodes</span></span>  
 <span data-ttu-id="a6995-160">W modelu DOM (Document Object), deklaracje przestrzeni nazw są traktowane jak, jeśli są one prawidłowe atrybuty, które można wstawiać, aktualizowane i usuwane.</span><span class="sxs-lookup"><span data-stu-id="a6995-160">In the Document Object Model (DOM), namespace declarations are treated as if they are regular attributes that can be inserted, updated and deleted.</span></span> <span data-ttu-id="a6995-161"><xref:System.Xml.XPath.XPathNavigator> Klasa nie zezwala na takich operacji w węzłach przestrzeni nazw nie zmieniając wartość węzła przestrzeni nazw można zmienić tożsamości elementów i atrybutów w zakresie przestrzeń nazw, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="a6995-161">The <xref:System.Xml.XPath.XPathNavigator> class does not allow such operations on namespace nodes because altering the value of a namespace node can change the identity of the elements and attributes within the scope of the namespace node as illustrated in the following example.</span></span>  
  
```xml  
<root xmlns="http://www.contoso.com">  
    <child />  
</root>  
```  
  
 <span data-ttu-id="a6995-162">Jeśli w powyższym przykładzie XML została zmieniona w następujący sposób, to skutecznie zmienia nazwę każdego elementu w dokumencie ponieważ wartość każdego elementu identyfikator URI przestrzeni nazw zostanie zmieniona.</span><span class="sxs-lookup"><span data-stu-id="a6995-162">If the XML example above is changed in the following way, this effectively renames every element in the document because the value of each element's namespace URI is changed.</span></span>  
  
```xml  
<root xmlns="urn:contoso.com">  
    <child />  
</root>  
```  
  
 <span data-ttu-id="a6995-163">Wstawianie węzłów przestrzeni nazw, które nie są w konflikcie z deklaracji przestrzeni nazw w zakresie, które zostały wstawione jest dozwolona przez <xref:System.Xml.XPath.XPathNavigator> klasy.</span><span class="sxs-lookup"><span data-stu-id="a6995-163">Inserting namespace nodes that do not conflict with namespace declarations at the scope that they are inserted in is allowed by the <xref:System.Xml.XPath.XPathNavigator> class.</span></span> <span data-ttu-id="a6995-164">W takim przypadku deklaracje przestrzeni nazw nie są zadeklarowane w dolnym zakresów w dokumencie XML i nie powoduje zmiany nazwy, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="a6995-164">In this case, the namespace declarations are not declared at lower scopes in the XML document and does not result in renaming as illustrated in the following example.</span></span>  
  
```xml  
<root xmlns:a="http://www.contoso.com">  
    <parent>  
        <a:child />  
    </parent>  
</root>  
```  
  
 <span data-ttu-id="a6995-165">Jeśli w powyższym przykładzie XML została zmieniona w następujący sposób, deklaracje przestrzeni nazw są poprawnie propagowane przez dokumentu XML poniżej zakresu deklaracji przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="a6995-165">If the XML example above is changed in the following way, the namespace declarations are correctly propagated across the XML document below the scope of the other namespace declaration.</span></span>  
  
```xml  
<root xmlns:a="http://www.contoso.com">  
    <parent a:parent-id="1234" xmlns:a="http://www.contoso.com/parent-id">  
        <a:child xmlns:a="http://www.contoso.com/">  
    </parent>  
</root>  
```  
  
 <span data-ttu-id="a6995-166">W przykładzie XML powyżej atrybut `a:parent-id` jest wstawiane na `parent` element `http://www.contoso.com/parent-id` przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="a6995-166">In the XML example above, the attribute `a:parent-id` is inserted on the `parent` element in the `http://www.contoso.com/parent-id` namespace.</span></span> <span data-ttu-id="a6995-167"><xref:System.Xml.XPath.XPathNavigator.CreateAttribute%2A> Metoda służy do wstawiania atrybutu, gdy znajduje się na `parent` elementu.</span><span class="sxs-lookup"><span data-stu-id="a6995-167">The <xref:System.Xml.XPath.XPathNavigator.CreateAttribute%2A> method is used to insert the attribute while positioned on the `parent` element.</span></span> <span data-ttu-id="a6995-168">`http://www.contoso.com` Deklaracji przestrzeni nazw jest automatycznie wstawiane przez <xref:System.Xml.XPath.XPathNavigator> klasy w celu zachowania spójności pozostałej części dokumentu XML.</span><span class="sxs-lookup"><span data-stu-id="a6995-168">The `http://www.contoso.com` namespace declaration is automatically inserted by the <xref:System.Xml.XPath.XPathNavigator> class to preserve the consistency of the rest of the XML document.</span></span>  
  
## <a name="modifying-entity-reference-nodes"></a><span data-ttu-id="a6995-169">Modyfikowanie węzłów odwołanie do jednostki</span><span class="sxs-lookup"><span data-stu-id="a6995-169">Modifying Entity Reference Nodes</span></span>  
 <span data-ttu-id="a6995-170">Węzły odwołanie do jednostki w <xref:System.Xml.XmlDocument> obiektu są tylko do odczytu i nie można edytować za pomocą <xref:System.Xml.XPath.XPathNavigator> lub <xref:System.Xml.XmlNode> klasy.</span><span class="sxs-lookup"><span data-stu-id="a6995-170">Entity reference nodes in an <xref:System.Xml.XmlDocument> object are read-only and cannot be edited using either the <xref:System.Xml.XPath.XPathNavigator> or <xref:System.Xml.XmlNode> classes.</span></span> <span data-ttu-id="a6995-171">Wszelkie próby zmodyfikowania jednostki węzeł odniesienia powoduje <xref:System.InvalidOperationException>.</span><span class="sxs-lookup"><span data-stu-id="a6995-171">Any attempt to modify an entity reference node results in an <xref:System.InvalidOperationException>.</span></span>  
  
## <a name="modifying-xsinil-nodes"></a><span data-ttu-id="a6995-172">Modyfikowanie xsi: nil węzłów</span><span class="sxs-lookup"><span data-stu-id="a6995-172">Modifying xsi:nil Nodes</span></span>  
 <span data-ttu-id="a6995-173">Zalecenie schematu W3C XML pojęcia związane z elementu trwa może być zerowy.</span><span class="sxs-lookup"><span data-stu-id="a6995-173">The W3C XML Schema recommendation introduces the concept of an element being nillable.</span></span> <span data-ttu-id="a6995-174">Gdy element jest nillable, istnieje możliwość dla elementu, aby nie ma zawartości i nadal ważne.</span><span class="sxs-lookup"><span data-stu-id="a6995-174">When an element is nillable, it is possible for the element to have no content and still be valid.</span></span> <span data-ttu-id="a6995-175">Koncepcja jest nillable elementu jest podobny do koncepcji jest obiekt `null`.</span><span class="sxs-lookup"><span data-stu-id="a6995-175">The concept of an element being nillable is similar to the concept of an object being `null`.</span></span> <span data-ttu-id="a6995-176">Główną różnicą jest to, że `null` obiekt nie może być dostępne w dowolny sposób, podczas gdy `xsi:nil` element nadal ma właściwości, takie jak atrybuty, które są dostępne, ale nie ma zawartości (elementy podrzędne lub tekst).</span><span class="sxs-lookup"><span data-stu-id="a6995-176">The main difference is that a `null` object cannot be accessed in any way, while an `xsi:nil` element still has properties such as attributes that can be accessed, but has no content (child elements or text).</span></span> <span data-ttu-id="a6995-177">Istnienie `xsi:nil` atrybutu o wartości `true` elementu w pliku XML dokumentu służy do wskazywania, że element nie ma zawartości.</span><span class="sxs-lookup"><span data-stu-id="a6995-177">The existence of the `xsi:nil` attribute with a value of `true` on an element in an XML document is used to indicate that an element has no content.</span></span>  
  
 <span data-ttu-id="a6995-178">Jeśli <xref:System.Xml.XPath.XPathNavigator> obiekt jest używany w celu dodania zawartości do prawidłowego elementu z `xsi:nil` atrybutu o wartości `true`, wartość jego `xsi:nil` atrybut ma ustawioną `false`.</span><span class="sxs-lookup"><span data-stu-id="a6995-178">If an <xref:System.Xml.XPath.XPathNavigator> object is used to add content to a valid element with an `xsi:nil` attribute with a value of `true`, the value of its `xsi:nil` attribute is set to `false`.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a6995-179">Jeśli zawartość elementu z `xsi:nil` ustawić atrybutu `false` jest usunięte, wartość atrybutu nie jest zmieniana na `true`.</span><span class="sxs-lookup"><span data-stu-id="a6995-179">If the content of an element with an `xsi:nil` attribute set to `false` is deleted, the value of the attribute is not changed to `true`.</span></span>  
  
## <a name="saving-an-xml-document"></a><span data-ttu-id="a6995-180">Zapisywanie dokumentu XML</span><span class="sxs-lookup"><span data-stu-id="a6995-180">Saving an XML Document</span></span>  
 <span data-ttu-id="a6995-181">Zapisywanie zmian <xref:System.Xml.XmlDocument> obiekt jako wynik edycji metod opisanych w tym temacie odbywa się przy użyciu metody <xref:System.Xml.XmlDocument> klasy.</span><span class="sxs-lookup"><span data-stu-id="a6995-181">Saving changes made to an <xref:System.Xml.XmlDocument> object as the result of the editing methods described in this topic is performed using the methods of the <xref:System.Xml.XmlDocument> class.</span></span> <span data-ttu-id="a6995-182">Aby uzyskać więcej informacji na temat zapisywania zmian w <xref:System.Xml.XmlDocument> obiektów, zobacz [zapisywania i zapisywanie dokumentu](../../../../docs/standard/data/xml/saving-and-writing-a-document.md).</span><span class="sxs-lookup"><span data-stu-id="a6995-182">For more information about saving changes made to an <xref:System.Xml.XmlDocument> object, see [Saving and Writing a Document](../../../../docs/standard/data/xml/saving-and-writing-a-document.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a6995-183">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a6995-183">See Also</span></span>  
 <xref:System.Xml.XmlDocument>  
 <xref:System.Xml.XPath.XPathDocument>  
 <xref:System.Xml.XPath.XPathNavigator>  
 [<span data-ttu-id="a6995-184">Przetwarzanie danych XML przy użyciu modelu danych XPath</span><span class="sxs-lookup"><span data-stu-id="a6995-184">Process XML Data Using the XPath Data Model</span></span>](../../../../docs/standard/data/xml/process-xml-data-using-the-xpath-data-model.md)  
 [<span data-ttu-id="a6995-185">Wstawianie danych XML przy użyciu klasy XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="a6995-185">Insert XML Data using XPathNavigator</span></span>](../../../../docs/standard/data/xml/insert-xml-data-using-xpathnavigator.md)  
 [<span data-ttu-id="a6995-186">Usuwanie danych XML przy użyciu klasy XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="a6995-186">Remove XML Data using XPathNavigator</span></span>](../../../../docs/standard/data/xml/remove-xml-data-using-xpathnavigator.md)
