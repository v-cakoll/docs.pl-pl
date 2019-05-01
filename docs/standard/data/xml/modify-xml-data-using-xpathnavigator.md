---
title: Modyfikowanie danych XML przy użyciu klasy XPathNavigator
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
ms.assetid: 03a7c5a1-b296-4af4-b209-043c958dc0a5
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 72cbcf1294f3d13f406d8db177f66fdc367c0758
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62027124"
---
# <a name="modify-xml-data-using-xpathnavigator"></a><span data-ttu-id="99131-102">Modyfikowanie danych XML przy użyciu klasy XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="99131-102">Modify XML Data using XPathNavigator</span></span>
<span data-ttu-id="99131-103"><xref:System.Xml.XPath.XPathNavigator> Klasa udostępnia zestaw metod, które służy do modyfikowania węzłów i wartości w dokumencie XML.</span><span class="sxs-lookup"><span data-stu-id="99131-103">The <xref:System.Xml.XPath.XPathNavigator> class provides a set of methods used to modify nodes and values in an XML document.</span></span> <span data-ttu-id="99131-104">Aby można było używać tych metod <xref:System.Xml.XPath.XPathNavigator> obiekt musi być niemożliwa, czyli jego <xref:System.Xml.XPath.XPathNavigator.CanEdit%2A> właściwość musi być `true`.</span><span class="sxs-lookup"><span data-stu-id="99131-104">In order to use these methods, the <xref:System.Xml.XPath.XPathNavigator> object must be editable, that is, its <xref:System.Xml.XPath.XPathNavigator.CanEdit%2A> property must be `true`.</span></span>  
  
 <span data-ttu-id="99131-105"><xref:System.Xml.XPath.XPathNavigator> obiekty, które można edytować dokumentu XML są tworzone przez <xref:System.Xml.XmlDocument.CreateNavigator%2A> metody <xref:System.Xml.XmlDocument> klasy.</span><span class="sxs-lookup"><span data-stu-id="99131-105"><xref:System.Xml.XPath.XPathNavigator> objects that can edit an XML document are created by the <xref:System.Xml.XmlDocument.CreateNavigator%2A> method of the <xref:System.Xml.XmlDocument> class.</span></span> <span data-ttu-id="99131-106"><xref:System.Xml.XPath.XPathNavigator> obiekty utworzone przez <xref:System.Xml.XPath.XPathDocument> klasy są przeznaczone tylko do odczytu i dowolne próba należy użyć metod edycji <xref:System.Xml.XPath.XPathNavigator> obiekt utworzony przez <xref:System.Xml.XPath.XPathDocument> wynik w obiekcie <xref:System.NotSupportedException>.</span><span class="sxs-lookup"><span data-stu-id="99131-106"><xref:System.Xml.XPath.XPathNavigator> objects created by the <xref:System.Xml.XPath.XPathDocument> class are read-only and any attempt to use the editing methods of an <xref:System.Xml.XPath.XPathNavigator> object created by an <xref:System.Xml.XPath.XPathDocument> object result in a <xref:System.NotSupportedException>.</span></span>  
  
 <span data-ttu-id="99131-107">Aby uzyskać więcej informacji o tworzeniu edytowalne <xref:System.Xml.XPath.XPathNavigator> obiekty, zobacz [odczytywania danych XML przy użyciu klas XPathDocument i XmlDocument](../../../../docs/standard/data/xml/reading-xml-data-using-xpathdocument-and-xmldocument.md).</span><span class="sxs-lookup"><span data-stu-id="99131-107">For more information about creating editable <xref:System.Xml.XPath.XPathNavigator> objects, see [Reading XML Data using XPathDocument and XmlDocument](../../../../docs/standard/data/xml/reading-xml-data-using-xpathdocument-and-xmldocument.md).</span></span>  
  
## <a name="modifying-nodes"></a><span data-ttu-id="99131-108">Modyfikowanie węzłów</span><span class="sxs-lookup"><span data-stu-id="99131-108">Modifying Nodes</span></span>  
 <span data-ttu-id="99131-109">Proste techniki, w przypadku zmiany wartości węzła jest użycie <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> i <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> metody <xref:System.Xml.XPath.XPathNavigator> klasy.</span><span class="sxs-lookup"><span data-stu-id="99131-109">A simple technique for changing the value of a node is to use the <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> and <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> methods of the <xref:System.Xml.XPath.XPathNavigator> class.</span></span>  
  
 <span data-ttu-id="99131-110">W poniższej tabeli wymieniono wpływu tych metod na różnych typów węzłów.</span><span class="sxs-lookup"><span data-stu-id="99131-110">The following table lists the effects of these methods on different node types.</span></span>  
  
|<xref:System.Xml.XPath.XPathNodeType>|<span data-ttu-id="99131-111">Zmiany danych</span><span class="sxs-lookup"><span data-stu-id="99131-111">Data Changed</span></span>|  
|---------------------------------------------------------------------------------------------------------------------------------------------|------------------|  
|<xref:System.Xml.XPath.XPathNodeType.Root>|<span data-ttu-id="99131-112">Nieobsługiwane.</span><span class="sxs-lookup"><span data-stu-id="99131-112">Not supported.</span></span>|  
|<xref:System.Xml.XPath.XPathNodeType.Element>|<span data-ttu-id="99131-113">Zawartość elementu.</span><span class="sxs-lookup"><span data-stu-id="99131-113">The content of the element.</span></span>|  
|<xref:System.Xml.XPath.XPathNodeType.Attribute>|<span data-ttu-id="99131-114">Wartość atrybutu.</span><span class="sxs-lookup"><span data-stu-id="99131-114">The value of the attribute.</span></span>|  
|<xref:System.Xml.XPath.XPathNodeType.Text>|<span data-ttu-id="99131-115">Zawartość tekstowa.</span><span class="sxs-lookup"><span data-stu-id="99131-115">The text content.</span></span>|  
|<xref:System.Xml.XPath.XPathNodeType.ProcessingInstruction>|<span data-ttu-id="99131-116">Zawartość, z wyłączeniem element docelowy.</span><span class="sxs-lookup"><span data-stu-id="99131-116">The content, excluding the target.</span></span>|  
|<xref:System.Xml.XPath.XPathNodeType.Comment>|<span data-ttu-id="99131-117">Treść komentarza.</span><span class="sxs-lookup"><span data-stu-id="99131-117">The content of the comment.</span></span>|  
|<xref:System.Xml.XPath.XPathNodeType.Namespace>|<span data-ttu-id="99131-118">Nie jest obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="99131-118">Not Supported.</span></span>|  
  
> [!NOTE]
>  <span data-ttu-id="99131-119">Edytowanie <xref:System.Xml.XPath.XPathNodeType.Namespace> węzłów lub <xref:System.Xml.XPath.XPathNodeType.Root> węzeł nie jest obsługiwany.</span><span class="sxs-lookup"><span data-stu-id="99131-119">Editing <xref:System.Xml.XPath.XPathNodeType.Namespace> nodes or the <xref:System.Xml.XPath.XPathNodeType.Root> node is not supported.</span></span>  
  
 <span data-ttu-id="99131-120"><xref:System.Xml.XPath.XPathNavigator> Klasa udostępnia także zestaw metod używanych do wstawiania i usuwania węzłów.</span><span class="sxs-lookup"><span data-stu-id="99131-120">The <xref:System.Xml.XPath.XPathNavigator> class also provides a set of methods used to insert and remove nodes.</span></span> <span data-ttu-id="99131-121">Aby uzyskać więcej informacji dotyczących wstawiania i usuwania węzłów z dokumentu XML, zobacz [Wstawianie danych XML przy użyciu klasy XPathNavigator](../../../../docs/standard/data/xml/insert-xml-data-using-xpathnavigator.md) i [usuwanie danych XML przy użyciu klasy XPathNavigator](../../../../docs/standard/data/xml/remove-xml-data-using-xpathnavigator.md) tematów.</span><span class="sxs-lookup"><span data-stu-id="99131-121">For more information about inserting and removing nodes from an XML document, see the [Insert XML Data using XPathNavigator](../../../../docs/standard/data/xml/insert-xml-data-using-xpathnavigator.md) and [Remove XML Data using XPathNavigator](../../../../docs/standard/data/xml/remove-xml-data-using-xpathnavigator.md) topics.</span></span>  
  
### <a name="modifying-untyped-values"></a><span data-ttu-id="99131-122">Modyfikowanie wartości bez typu</span><span class="sxs-lookup"><span data-stu-id="99131-122">Modifying Untyped Values</span></span>  
 <span data-ttu-id="99131-123"><xref:System.Xml.XPath.XPathNavigator.SetValue%2A> Metoda po prostu wstawia nietypizowane `string` wartość przekazywana jako parametr jako wartość węzła <xref:System.Xml.XPath.XPathNavigator> obiektu jest obecnie ustawiony na.</span><span class="sxs-lookup"><span data-stu-id="99131-123">The <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> method simply inserts the untyped `string` value passed as a parameter as the value of the node the <xref:System.Xml.XPath.XPathNavigator> object is currently positioned on.</span></span> <span data-ttu-id="99131-124">Wartość jest wstawiany bez dowolnego typu lub bez weryfikacji, nowa wartość jest nieprawidłowa według typu węzła, jeśli informacje schematu są dostępne.</span><span class="sxs-lookup"><span data-stu-id="99131-124">The value is inserted without any type or without verifying that the new value is valid according to the type of the node if schema information is available.</span></span>  
  
 <span data-ttu-id="99131-125">W poniższym przykładzie <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> metody używane do aktualizowania wszystkich `price` elementów w `contosoBooks.xml` pliku.</span><span class="sxs-lookup"><span data-stu-id="99131-125">In the following example, the <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> method is used to update all `price` elements in the `contosoBooks.xml` file.</span></span>  
  
 [!code-cpp[XPathNavigatorMethods#47](../../../../samples/snippets/cpp/VS_Snippets_Data/XPathNavigatorMethods/CPP/xpathnavigatormethods.cpp#47)]
 [!code-csharp[XPathNavigatorMethods#47](../../../../samples/snippets/csharp/VS_Snippets_Data/XPathNavigatorMethods/CS/xpathnavigatormethods.cs#47)]
 [!code-vb[XPathNavigatorMethods#47](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XPathNavigatorMethods/VB/xpathnavigatormethods.vb#47)]  
  
 <span data-ttu-id="99131-126">Przykład przyjmuje `contosoBooks.xml` pliku jako dane wejściowe.</span><span class="sxs-lookup"><span data-stu-id="99131-126">The example takes the `contosoBooks.xml` file as an input.</span></span>  
  
 [!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]  
  
### <a name="modifying-typed-values"></a><span data-ttu-id="99131-127">Modyfikowanie wartości Typizowane</span><span class="sxs-lookup"><span data-stu-id="99131-127">Modifying Typed Values</span></span>  
 <span data-ttu-id="99131-128">Gdy typ węzła jest schematu XML W3C prosty typ, nowej wartości, które są wstawiane przez <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> metody jest sprawdzana względem aspekty typu prostego, zanim ma wartość.</span><span class="sxs-lookup"><span data-stu-id="99131-128">When the type of a node is a W3C XML Schema simple type, the new value inserted by the <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> method is checked against the facets of the simple type before the value is set.</span></span> <span data-ttu-id="99131-129">Jeśli nowa wartość nie jest nieprawidłowa według typu węzła (na przykład ustawienie wartości `-1` w elemencie o typie `xs:positiveInteger`), powoduje wyjątek.</span><span class="sxs-lookup"><span data-stu-id="99131-129">If the new value is not valid according to the type of the node (for example, setting a value of `-1` on an element whose type is `xs:positiveInteger`), it results in an exception.</span></span>  
  
 <span data-ttu-id="99131-130">Poniższy przykład podejmie próbę Zmień wartość właściwości `price` element pierwszego `book` element `contosoBooks.xml` plik <xref:System.DateTime> wartość.</span><span class="sxs-lookup"><span data-stu-id="99131-130">The following example attempts to change the value of the `price` element of the first `book` element in the `contosoBooks.xml` file to a <xref:System.DateTime> value.</span></span> <span data-ttu-id="99131-131">Ponieważ typ schematu XML `price` element jest zdefiniowany jako `xs:decimal` w `contosoBooks.xsd` pliki, powoduje to wyjątek.</span><span class="sxs-lookup"><span data-stu-id="99131-131">Because the XML Schema type of the `price` element is defined as `xs:decimal` in the `contosoBooks.xsd` files, this results in an exception.</span></span>  
  
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
  
 <span data-ttu-id="99131-132">Przykład przyjmuje `contosoBooks.xml` pliku jako dane wejściowe.</span><span class="sxs-lookup"><span data-stu-id="99131-132">The example takes the `contosoBooks.xml` file as an input.</span></span>  
  
 [!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]  
  
 <span data-ttu-id="99131-133">Przykład pobiera również `contosoBooks.xsd` jako dane wejściowe.</span><span class="sxs-lookup"><span data-stu-id="99131-133">The example also takes the `contosoBooks.xsd` as an input.</span></span>  
  
 [!code-xml[XPathXMLExamples#3](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xsd#3)]  
  
#### <a name="the-effects-of-editing-strongly-typed-xml-data"></a><span data-ttu-id="99131-134">Edytowanie danych XML w silnie Typizowany efektów</span><span class="sxs-lookup"><span data-stu-id="99131-134">The Effects of Editing Strongly Typed XML Data</span></span>  
 <span data-ttu-id="99131-135"><xref:System.Xml.XPath.XPathNavigator> Klasa używa schematu XML W3C jako podstawy do opisywania silnie typizowane XML.</span><span class="sxs-lookup"><span data-stu-id="99131-135">The <xref:System.Xml.XPath.XPathNavigator> class uses the W3C XML Schema as a basis for describing strongly-typed XML.</span></span> <span data-ttu-id="99131-136">Atrybuty i elementy mogą być adnotowane przy użyciu informacji o typie oparte na weryfikacji względem dokumentów schematu XML W3C.</span><span class="sxs-lookup"><span data-stu-id="99131-136">Elements and attributes can be annotated with type information based on validation against a W3C XML Schema document.</span></span> <span data-ttu-id="99131-137">Elementy, które mogą zawierać innych elementów lub atrybutów są nazywane typów złożonych, gdy te, które mogą zawierać tylko zawartości tekstowej są nazywane typów prostych.</span><span class="sxs-lookup"><span data-stu-id="99131-137">Elements that can contain other elements or attributes are called complex types, while those that can only contain textual content are called simple types.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="99131-138">Atrybuty może mieć tylko proste typy.</span><span class="sxs-lookup"><span data-stu-id="99131-138">Attributes can only have simple types.</span></span>  
  
 <span data-ttu-id="99131-139">Element lub atrybut jest uznawana za schematu-ważności, jeśli odpowiada wszystkie reguły specyficzne dla swojej definicji typu.</span><span class="sxs-lookup"><span data-stu-id="99131-139">An element or attribute can be considered to be schema-valid if it conforms to all the rules specific to its type definition.</span></span> <span data-ttu-id="99131-140">Element, który ma typ prosty `xs:int` musi zawierać wartość liczbową od -2147483648 do 2147483647 był prawidłowy schemat.</span><span class="sxs-lookup"><span data-stu-id="99131-140">An element that has the simple type `xs:int` has to contain a numeric value between -2147483648 and 2147483647 to be schema-valid.</span></span> <span data-ttu-id="99131-141">W przypadku typów złożonych poprawność schematu elementu jest zależna od schematu ważność jego elementów podrzędnych i atrybutów.</span><span class="sxs-lookup"><span data-stu-id="99131-141">For complex types, the schema-validity of the element is dependent on the schema-validity of its child elements and attributes.</span></span> <span data-ttu-id="99131-142">Dlatego jeśli element jest nieprawidłowa względem jego definicji typu złożonego, wszystkie jego elementy podrzędne i atrybuty są prawidłowe przed ich definicje typów.</span><span class="sxs-lookup"><span data-stu-id="99131-142">Thus if an element is valid against its complex type definition, all its child elements and attributes are valid against their type definitions.</span></span> <span data-ttu-id="99131-143">Podobnie, jeśli jeszcze jeden z elementów podrzędnych atrybuty elementu jest nieprawidłowa w przypadku jej definicja typu lub ma nieznany ważności, element jest również niepoprawna lub nieznana ważność.</span><span class="sxs-lookup"><span data-stu-id="99131-143">Similarly, if even one of the child elements or attributes of an element is invalid against its type definition, or has an unknown validity, the element is also either invalid or of unknown validity.</span></span>  
  
 <span data-ttu-id="99131-144">Biorąc pod uwagę, że ważność elementu jest zależny od ważności jego elementów podrzędnych i atrybutów, albo modyfikacje spowodować zmianę ważności elementu, jeśli została poprzednio prawidłowe.</span><span class="sxs-lookup"><span data-stu-id="99131-144">Given that the validity of an element is dependent on the validity of its child elements and attributes, modifications to either result in altering the validity of the element if it was previously valid.</span></span> <span data-ttu-id="99131-145">W szczególności jeśli elementy podrzędne i atrybuty elementu są wstawione, zaktualizowane lub usunięto, ważność element staje się nieznane.</span><span class="sxs-lookup"><span data-stu-id="99131-145">Specifically, if the child elements or attributes of an element are inserted, updated, or deleted, then the validity of the element becomes unknown.</span></span> <span data-ttu-id="99131-146">To jest reprezentowany przez <xref:System.Xml.Schema.IXmlSchemaInfo.Validity%2A> właściwość elementu <xref:System.Xml.XPath.XPathNavigator.SchemaInfo%2A> właściwość zostanie ustawiona <xref:System.Xml.Schema.XmlSchemaValidity.NotKnown>.</span><span class="sxs-lookup"><span data-stu-id="99131-146">This is represented by the <xref:System.Xml.Schema.IXmlSchemaInfo.Validity%2A> property of the element's <xref:System.Xml.XPath.XPathNavigator.SchemaInfo%2A> property being set to <xref:System.Xml.Schema.XmlSchemaValidity.NotKnown>.</span></span> <span data-ttu-id="99131-147">Ponadto w tym celu dokonuje kaskadowych do góry cyklicznie w dokumencie XML, ponieważ ważność elementu nadrzędnego elementu (i jego element nadrzędny i tak dalej) staje się również nieznany.</span><span class="sxs-lookup"><span data-stu-id="99131-147">Furthermore, this effect cascades upwards recursively across the XML document, because the validity of the element's parent element (and its parent element, and so on) also becomes unknown.</span></span>  
  
 <span data-ttu-id="99131-148">Aby uzyskać więcej informacji na temat sprawdzania poprawności schematu i <xref:System.Xml.XPath.XPathNavigator> klasy, zobacz [sprawdzanie poprawności schematu przy użyciu klasy XPathNavigator](../../../../docs/standard/data/xml/schema-validation-using-xpathnavigator.md).</span><span class="sxs-lookup"><span data-stu-id="99131-148">For more information about schema validation and the <xref:System.Xml.XPath.XPathNavigator> class, see [Schema Validation using XPathNavigator](../../../../docs/standard/data/xml/schema-validation-using-xpathnavigator.md).</span></span>  
  
### <a name="modifying-attributes"></a><span data-ttu-id="99131-149">Modyfikowanie atrybutów</span><span class="sxs-lookup"><span data-stu-id="99131-149">Modifying Attributes</span></span>  
 <span data-ttu-id="99131-150"><xref:System.Xml.XPath.XPathNavigator.SetValue%2A> i <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> metody może służyć do modyfikowania węzłów atrybutu bez typu i kontrolą typów, a także inne typy węzłów wymienionych w sekcji "Modyfikowanie węzły".</span><span class="sxs-lookup"><span data-stu-id="99131-150">The <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> and <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> methods can be used to modify untyped and typed attribute nodes as well as the other node types listed in the "Modifying Nodes" section.</span></span>  
  
 <span data-ttu-id="99131-151">Poniższy przykład zmienia wartość `genre` atrybut pierwszego `book` element `books.xml` pliku.</span><span class="sxs-lookup"><span data-stu-id="99131-151">The following example changes the value of the `genre` attribute of the first `book` element in the `books.xml` file.</span></span>  
  
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
  
 <span data-ttu-id="99131-152">Aby uzyskać więcej informacji na temat <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> i <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> metody, zapoznaj się z sekcjami "Modyfikowanie bez typu" oraz "Modyfikowanie wpisane wartości".</span><span class="sxs-lookup"><span data-stu-id="99131-152">For more information about the <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> and <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> methods, see the "Modifying Untyped Values" and "Modifying Typed Values" sections.</span></span>  
  
## <a name="innerxml-and-outerxml-properties"></a><span data-ttu-id="99131-153">Właściwości OuterXml i elementu</span><span class="sxs-lookup"><span data-stu-id="99131-153">InnerXml and OuterXml Properties</span></span>  
 <span data-ttu-id="99131-154"><xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> i <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> właściwości <xref:System.Xml.XPath.XPathNavigator> klasy zmienić węzłów znaczniki XML <xref:System.Xml.XPath.XPathNavigator> obiektu jest obecnie ustawiony na.</span><span class="sxs-lookup"><span data-stu-id="99131-154">The <xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> and <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> properties of the <xref:System.Xml.XPath.XPathNavigator> class change the XML markup of the nodes an <xref:System.Xml.XPath.XPathNavigator> object is currently positioned on.</span></span>  
  
 <span data-ttu-id="99131-155"><xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> Zmienia właściwość znaczników XML węzłów podrzędnych <xref:System.Xml.XPath.XPathNavigator> przeanalizowany zawartość XML danego obiektu aktualnie jest ustawiony na `string`.</span><span class="sxs-lookup"><span data-stu-id="99131-155">The <xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> property changes the XML markup of the child nodes an <xref:System.Xml.XPath.XPathNavigator> object is currently positioned on with the parsed contents of the given XML `string`.</span></span> <span data-ttu-id="99131-156">Podobnie <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> zmienia właściwość znaczników XML węzłów podrzędnych <xref:System.Xml.XPath.XPathNavigator> obiektu aktualnie jest ustawiony na oraz bieżącego węzła.</span><span class="sxs-lookup"><span data-stu-id="99131-156">Similarly, the <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> property changes the XML markup of the child nodes an <xref:System.Xml.XPath.XPathNavigator> object is currently positioned on as well as the current node itself.</span></span>  
  
 <span data-ttu-id="99131-157">W poniższym przykładzie użyto <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> właściwość, aby zmodyfikować wartość `price` elementu i Wstaw nowy `discount` atrybut pierwszego `book` element `contosoBooks.xml` pliku.</span><span class="sxs-lookup"><span data-stu-id="99131-157">The following example uses the <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> property to modify the value of the `price` element and insert a new `discount` attribute on the first `book` element in the `contosoBooks.xml` file.</span></span>  
  
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
  
 <span data-ttu-id="99131-158">Przykład przyjmuje `contosoBooks.xml` pliku jako dane wejściowe.</span><span class="sxs-lookup"><span data-stu-id="99131-158">The example takes the `contosoBooks.xml` file as an input.</span></span>  
  
 [!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]  
  
## <a name="modifying-namespace-nodes"></a><span data-ttu-id="99131-159">Modyfikowanie węzłów Namespace</span><span class="sxs-lookup"><span data-stu-id="99131-159">Modifying Namespace Nodes</span></span>  
 <span data-ttu-id="99131-160">W modelu DOM (Document Object), deklaracje przestrzeni nazw są traktowane tak, jakby są regularnie atrybutów, które można wstawić, aktualizowane oraz usuwane.</span><span class="sxs-lookup"><span data-stu-id="99131-160">In the Document Object Model (DOM), namespace declarations are treated as if they are regular attributes that can be inserted, updated and deleted.</span></span> <span data-ttu-id="99131-161"><xref:System.Xml.XPath.XPathNavigator> Klasy nie zezwala na takie operacje na węzły przestrzeni nazw, ponieważ zmiany wartości węzła obszaru nazw można zmienić tożsamości elementów i atrybutów w zakresie węzła obszaru nazw, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="99131-161">The <xref:System.Xml.XPath.XPathNavigator> class does not allow such operations on namespace nodes because altering the value of a namespace node can change the identity of the elements and attributes within the scope of the namespace node as illustrated in the following example.</span></span>  
  
```xml  
<root xmlns="http://www.contoso.com">  
    <child />  
</root>  
```  
  
 <span data-ttu-id="99131-162">Jeśli w powyższym przykładzie XML zostanie zmieniony w następujący sposób, to skutecznie zmienia nazwę każdego elementu w dokumencie, ponieważ wartość identyfikatora URI obszaru nazw każdego elementu zostanie zmieniona.</span><span class="sxs-lookup"><span data-stu-id="99131-162">If the XML example above is changed in the following way, this effectively renames every element in the document because the value of each element's namespace URI is changed.</span></span>  
  
```xml  
<root xmlns="urn:contoso.com">  
    <child />  
</root>  
```  
  
 <span data-ttu-id="99131-163">Wstawianie węzły przestrzeni nazw, które nie wchodzą w konflikt z nazw deklaracji w zakresie, które zostały wstawione jest dozwolona przez <xref:System.Xml.XPath.XPathNavigator> klasy.</span><span class="sxs-lookup"><span data-stu-id="99131-163">Inserting namespace nodes that do not conflict with namespace declarations at the scope that they are inserted in is allowed by the <xref:System.Xml.XPath.XPathNavigator> class.</span></span> <span data-ttu-id="99131-164">W takim przypadku deklaracje przestrzeni nazw nie są zadeklarowane na niższe zakresy w dokumencie XML i nie powoduje zmiany nazwy, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="99131-164">In this case, the namespace declarations are not declared at lower scopes in the XML document and does not result in renaming as illustrated in the following example.</span></span>  
  
```xml  
<root xmlns:a="http://www.contoso.com">  
    <parent>  
        <a:child />  
    </parent>  
</root>  
```  
  
 <span data-ttu-id="99131-165">Jeśli w powyższym przykładzie XML zostanie zmieniony w następujący sposób, deklaracje przestrzeni nazw są poprawnie propagowane w dokumencie XML poniżej zakresu deklaracji przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="99131-165">If the XML example above is changed in the following way, the namespace declarations are correctly propagated across the XML document below the scope of the other namespace declaration.</span></span>  
  
```xml  
<root xmlns:a="http://www.contoso.com">  
    <parent a:parent-id="1234" xmlns:a="http://www.contoso.com/parent-id">  
        <a:child xmlns:a="http://www.contoso.com/">  
    </parent>  
</root>  
```  
  
 <span data-ttu-id="99131-166">W przykładzie XML powyżej atrybut `a:parent-id` jest wstawiany na `parent` element `http://www.contoso.com/parent-id` przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="99131-166">In the XML example above, the attribute `a:parent-id` is inserted on the `parent` element in the `http://www.contoso.com/parent-id` namespace.</span></span> <span data-ttu-id="99131-167"><xref:System.Xml.XPath.XPathNavigator.CreateAttribute%2A> Metoda służy do wstawiania atrybutu, gdy ustawiony na `parent` elementu.</span><span class="sxs-lookup"><span data-stu-id="99131-167">The <xref:System.Xml.XPath.XPathNavigator.CreateAttribute%2A> method is used to insert the attribute while positioned on the `parent` element.</span></span> <span data-ttu-id="99131-168">`http://www.contoso.com` Deklarację przestrzeni nazw jest automatycznie wstawiany przez <xref:System.Xml.XPath.XPathNavigator> klasy w celu zachowania spójności w pozostałej części dokumentu XML.</span><span class="sxs-lookup"><span data-stu-id="99131-168">The `http://www.contoso.com` namespace declaration is automatically inserted by the <xref:System.Xml.XPath.XPathNavigator> class to preserve the consistency of the rest of the XML document.</span></span>  
  
## <a name="modifying-entity-reference-nodes"></a><span data-ttu-id="99131-169">Modyfikowanie węzłów odwołanie do jednostki</span><span class="sxs-lookup"><span data-stu-id="99131-169">Modifying Entity Reference Nodes</span></span>  
 <span data-ttu-id="99131-170">Węzły odwołanie do jednostki w <xref:System.Xml.XmlDocument> obiektu są przeznaczone tylko do odczytu i nie można edytować za pomocą <xref:System.Xml.XPath.XPathNavigator> lub <xref:System.Xml.XmlNode> klasy.</span><span class="sxs-lookup"><span data-stu-id="99131-170">Entity reference nodes in an <xref:System.Xml.XmlDocument> object are read-only and cannot be edited using either the <xref:System.Xml.XPath.XPathNavigator> or <xref:System.Xml.XmlNode> classes.</span></span> <span data-ttu-id="99131-171">Każda próba zmodyfikowania węzła odwołanie do obiektu skutkuje <xref:System.InvalidOperationException>.</span><span class="sxs-lookup"><span data-stu-id="99131-171">Any attempt to modify an entity reference node results in an <xref:System.InvalidOperationException>.</span></span>  
  
## <a name="modifying-xsinil-nodes"></a><span data-ttu-id="99131-172">Modyfikowanie xsi: nil węzłów</span><span class="sxs-lookup"><span data-stu-id="99131-172">Modifying xsi:nil Nodes</span></span>  
 <span data-ttu-id="99131-173">Zaleceniem schematu XML W3C pojęcia związane z elementu trwa może być zerowy.</span><span class="sxs-lookup"><span data-stu-id="99131-173">The W3C XML Schema recommendation introduces the concept of an element being nillable.</span></span> <span data-ttu-id="99131-174">Gdy element jest może być zerowy, jest możliwe dla elementu nie ma zawartości i nadal ważne.</span><span class="sxs-lookup"><span data-stu-id="99131-174">When an element is nillable, it is possible for the element to have no content and still be valid.</span></span> <span data-ttu-id="99131-175">Pojęcia są może być zerowy element jest podobny do koncepcji jest obiekt `null`.</span><span class="sxs-lookup"><span data-stu-id="99131-175">The concept of an element being nillable is similar to the concept of an object being `null`.</span></span> <span data-ttu-id="99131-176">Główną różnicą jest to, że `null` obiekt nie może być używane w jakikolwiek sposób, podczas gdy `xsi:nil` element nadal ma właściwości, takie jak atrybuty, które są dostępne, ale nie ma zawartości (elementy podrzędne lub tekst).</span><span class="sxs-lookup"><span data-stu-id="99131-176">The main difference is that a `null` object cannot be accessed in any way, while an `xsi:nil` element still has properties such as attributes that can be accessed, but has no content (child elements or text).</span></span> <span data-ttu-id="99131-177">Istnienie `xsi:nil` atrybutu o wartości `true` elementu w pliku XML dokumentu jest używany do wskazania, że element nie ma zawartości.</span><span class="sxs-lookup"><span data-stu-id="99131-177">The existence of the `xsi:nil` attribute with a value of `true` on an element in an XML document is used to indicate that an element has no content.</span></span>  
  
 <span data-ttu-id="99131-178">Jeśli <xref:System.Xml.XPath.XPathNavigator> obiekt jest używany do dodawania zawartości do prawidłowego elementu z `xsi:nil` atrybutu o wartości `true`, wartość jego `xsi:nil` ma ustawioną wartość atrybutu `false`.</span><span class="sxs-lookup"><span data-stu-id="99131-178">If an <xref:System.Xml.XPath.XPathNavigator> object is used to add content to a valid element with an `xsi:nil` attribute with a value of `true`, the value of its `xsi:nil` attribute is set to `false`.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="99131-179">Jeśli zawartość elementu za pomocą `xsi:nil` ustawioną wartość atrybutu `false` jest usunięte, wartość atrybutu nie jest zmieniana na `true`.</span><span class="sxs-lookup"><span data-stu-id="99131-179">If the content of an element with an `xsi:nil` attribute set to `false` is deleted, the value of the attribute is not changed to `true`.</span></span>  
  
## <a name="saving-an-xml-document"></a><span data-ttu-id="99131-180">Zapisywanie dokumentu XML</span><span class="sxs-lookup"><span data-stu-id="99131-180">Saving an XML Document</span></span>  
 <span data-ttu-id="99131-181">Zapisywanie zmian <xref:System.Xml.XmlDocument> obiektu jako wynik edycji metod opisanych w tym temacie odbywa się przy użyciu metody <xref:System.Xml.XmlDocument> klasy.</span><span class="sxs-lookup"><span data-stu-id="99131-181">Saving changes made to an <xref:System.Xml.XmlDocument> object as the result of the editing methods described in this topic is performed using the methods of the <xref:System.Xml.XmlDocument> class.</span></span> <span data-ttu-id="99131-182">Aby uzyskać więcej informacji na temat zapisywania zmian <xref:System.Xml.XmlDocument> obiektu, zobacz [zapisywania i zapisywania dokumentu](../../../../docs/standard/data/xml/saving-and-writing-a-document.md).</span><span class="sxs-lookup"><span data-stu-id="99131-182">For more information about saving changes made to an <xref:System.Xml.XmlDocument> object, see [Saving and Writing a Document](../../../../docs/standard/data/xml/saving-and-writing-a-document.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="99131-183">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="99131-183">See also</span></span>

- <xref:System.Xml.XmlDocument>
- <xref:System.Xml.XPath.XPathDocument>
- <xref:System.Xml.XPath.XPathNavigator>
- [<span data-ttu-id="99131-184">Przetwarzanie danych XML przy użyciu modelu danych XPath</span><span class="sxs-lookup"><span data-stu-id="99131-184">Process XML Data Using the XPath Data Model</span></span>](../../../../docs/standard/data/xml/process-xml-data-using-the-xpath-data-model.md)
- [<span data-ttu-id="99131-185">Wstawianie danych XML przy użyciu klasy XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="99131-185">Insert XML Data using XPathNavigator</span></span>](../../../../docs/standard/data/xml/insert-xml-data-using-xpathnavigator.md)
- [<span data-ttu-id="99131-186">Usuwanie danych XML przy użyciu klasy XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="99131-186">Remove XML Data using XPathNavigator</span></span>](../../../../docs/standard/data/xml/remove-xml-data-using-xpathnavigator.md)
