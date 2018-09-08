---
title: Walidacja oparta XmlSchemaValidator
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 911d4460-dd91-4958-85b2-2ca3299f9ec6
author: mairaw
ms.author: mairaw
ms.openlocfilehash: c4d1d5602ff224c1c8f3e0948fc93c9200b9661e
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/08/2018
ms.locfileid: "44189079"
---
# <a name="xmlschemavalidator-push-based-validation"></a><span data-ttu-id="839a8-102">Walidacja oparta XmlSchemaValidator</span><span class="sxs-lookup"><span data-stu-id="839a8-102">XmlSchemaValidator Push-Based Validation</span></span>
<span data-ttu-id="839a8-103"><xref:System.Xml.Schema.XmlSchemaValidator> Klasa udostępnia efektywny, wydajny mechanizm weryfikacji danych XML względem schematów XML w sposób, na podstawie wypychania.</span><span class="sxs-lookup"><span data-stu-id="839a8-103">The <xref:System.Xml.Schema.XmlSchemaValidator> class provides an efficient, high-performance mechanism to validate XML data against XML schemas in a push-based manner.</span></span> <span data-ttu-id="839a8-104">Na przykład <xref:System.Xml.Schema.XmlSchemaValidator> klasy umożliwia sprawdzenie poprawności XML zestaw informacji w miejscu, bez konieczności serializować go jako dokument XML, a następnie ponownej analizy dokumentu przy użyciu sprawdzania poprawności odczytującego XML.</span><span class="sxs-lookup"><span data-stu-id="839a8-104">For example, the <xref:System.Xml.Schema.XmlSchemaValidator> class allows you to validate an XML infoset in-place without having to serialize it as an XML document and then reparse the document using a validating XML reader.</span></span>  
  
 <span data-ttu-id="839a8-105"><xref:System.Xml.Schema.XmlSchemaValidator> Klasy mogą być używane w zaawansowanych scenariuszach, takich jak tworzenie aparatów sprawdzania poprawności dla niestandardowych źródeł danych XML lub umożliwia tworzenie sprawdzania poprawności edytora XML.</span><span class="sxs-lookup"><span data-stu-id="839a8-105">The <xref:System.Xml.Schema.XmlSchemaValidator> class can be used in advanced scenarios such as building validation engines over custom XML data sources or as a way to build a validating XML writer.</span></span>  
  
 <span data-ttu-id="839a8-106">Oto przykład użycia <xref:System.Xml.Schema.XmlSchemaValidator> klasy, aby sprawdzić poprawność `contosoBooks.xml` pliku względem `contosoBooks.xsd` schematu.</span><span class="sxs-lookup"><span data-stu-id="839a8-106">The following is an example of using the <xref:System.Xml.Schema.XmlSchemaValidator> class to validate the `contosoBooks.xml` file against the `contosoBooks.xsd` schema.</span></span> <span data-ttu-id="839a8-107">W przykładzie użyto <xref:System.Xml.Serialization.XmlSerializer> klasy do deserializacji `contosoBooks.xml` pliku i przekazać wartość węzłów do metody <xref:System.Xml.Schema.XmlSchemaValidator> klasy.</span><span class="sxs-lookup"><span data-stu-id="839a8-107">The example uses the <xref:System.Xml.Serialization.XmlSerializer> class to deserialize the `contosoBooks.xml` file and pass the value of the nodes to the methods of the <xref:System.Xml.Schema.XmlSchemaValidator> class.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="839a8-108">W tym przykładzie jest używane w sekcjach tego tematu.</span><span class="sxs-lookup"><span data-stu-id="839a8-108">This example is used throughout the sections of this topic.</span></span>  
  
 [!code-csharp[XmlSchemaValidatorExamples#1](../../../../samples/snippets/csharp/VS_Snippets_Data/XmlSchemaValidatorExamples/CS/XmlSchemaValidatorExamples.cs#1)]
 [!code-vb[XmlSchemaValidatorExamples#1](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XmlSchemaValidatorExamples/VB/XmlSchemaValidatorExamples.vb#1)]  
  
 <span data-ttu-id="839a8-109">Przykład przyjmuje `contosoBooks.xml` pliku jako dane wejściowe.</span><span class="sxs-lookup"><span data-stu-id="839a8-109">The example takes the `contosoBooks.xml` file as input.</span></span>  
  
 [!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]  
  
 <span data-ttu-id="839a8-110">Przykład pobiera również `contosoBooks.xsd` jako dane wejściowe.</span><span class="sxs-lookup"><span data-stu-id="839a8-110">The example also takes the `contosoBooks.xsd` as an input.</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<xs:schema attributeFormDefault="unqualified" elementFormDefault="qualified" targetNamespace="http://www.contoso.com/books" xmlns:xs="http://www.w3.org/2001/XMLSchema">  
    <xs:element name="bookstore">  
        <xs:complexType>  
            <xs:sequence>  
                <xs:element maxOccurs="unbounded" name="book">  
                    <xs:complexType>  
                        <xs:sequence>  
                            <xs:element name="title" type="xs:string" />  
                            <xs:element name="author">  
                                <xs:complexType>  
                                    <xs:sequence>  
                                        <xs:element minOccurs="0" name="name" type="xs:string" />  
                                        <xs:element minOccurs="0" name="first-name" type="xs:string" />  
                                        <xs:element minOccurs="0" name="last-name" type="xs:string" />  
                                    </xs:sequence>  
                                </xs:complexType>  
                            </xs:element>  
                            <xs:element name="price" type="xs:decimal" />  
                        </xs:sequence>  
                        <xs:attribute name="genre" type="xs:string" use="required" />  
                        <xs:attribute name="publicationdate" type="xs:date" use="required" />  
                        <xs:attribute name="ISBN" type="xs:string" use="required" />  
                    </xs:complexType>  
                </xs:element>  
            </xs:sequence>  
        </xs:complexType>  
    </xs:element>  
</xs:schema>  
```  
  
## <a name="validating-xml-data-using-xmlschemavalidator"></a><span data-ttu-id="839a8-111">Walidacja danych XML przy użyciu XmlSchemaValidator</span><span class="sxs-lookup"><span data-stu-id="839a8-111">Validating XML Data using XmlSchemaValidator</span></span>  
 <span data-ttu-id="839a8-112">Aby rozpocząć sprawdzanie poprawności zestaw informacji XML, najpierw należy zainicjować nowe wystąpienie klasy <xref:System.Xml.Schema.XmlSchemaValidator> przy użyciu <xref:System.Xml.Schema.XmlSchemaValidator.%23ctor%2A> konstruktora.</span><span class="sxs-lookup"><span data-stu-id="839a8-112">To begin validating an XML infoset, you must first initialize a new instance of the <xref:System.Xml.Schema.XmlSchemaValidator> class using the <xref:System.Xml.Schema.XmlSchemaValidator.%23ctor%2A> constructor.</span></span>  
  
 <span data-ttu-id="839a8-113"><xref:System.Xml.Schema.XmlSchemaValidator.%23ctor%2A> Konstruktor przyjmuje <xref:System.Xml.XmlNameTable>, <xref:System.Xml.Schema.XmlSchemaSet>, i <xref:System.Xml.XmlNamespaceManager> obiektów jako parametrów, a także <xref:System.Xml.Schema.XmlSchemaValidationFlags> wartość jako parametr.</span><span class="sxs-lookup"><span data-stu-id="839a8-113">The <xref:System.Xml.Schema.XmlSchemaValidator.%23ctor%2A> constructor takes <xref:System.Xml.XmlNameTable>, <xref:System.Xml.Schema.XmlSchemaSet>, and <xref:System.Xml.XmlNamespaceManager> objects as parameters as well as a <xref:System.Xml.Schema.XmlSchemaValidationFlags> value as a parameter.</span></span> <span data-ttu-id="839a8-114"><xref:System.Xml.XmlNameTable> Obiekt jest używany do wyodrębnić dobrze znanych nazw ciągi, takie jak przestrzeń nazw schematu, przestrzeń nazw XML i tak dalej i jest przekazywany do <xref:System.Xml.Schema.XmlSchemaDatatype.ParseValue%2A> metody podczas sprawdzania poprawności prostej zawartości.</span><span class="sxs-lookup"><span data-stu-id="839a8-114">The <xref:System.Xml.XmlNameTable> object is used to atomize well-known namespace strings like the schema namespace, the XML namespace, and so on, and is passed to the <xref:System.Xml.Schema.XmlSchemaDatatype.ParseValue%2A> method while validating simple content.</span></span> <span data-ttu-id="839a8-115"><xref:System.Xml.Schema.XmlSchemaSet> Obiekt zawiera schematów XML, używany do sprawdzania poprawności zestaw informacji XML.</span><span class="sxs-lookup"><span data-stu-id="839a8-115">The <xref:System.Xml.Schema.XmlSchemaSet> object contains the XML schemas used to validate the XML infoset.</span></span> <span data-ttu-id="839a8-116"><xref:System.Xml.XmlNamespaceManager> Obiekt jest używany do rozpoznawania nazw podczas sprawdzania poprawności.</span><span class="sxs-lookup"><span data-stu-id="839a8-116">The <xref:System.Xml.XmlNamespaceManager> object is used to resolve namespaces encountered during validation.</span></span> <span data-ttu-id="839a8-117"><xref:System.Xml.Schema.XmlSchemaValidationFlags> Wartość jest używana do wyłączenia niektórych funkcji sprawdzania poprawności.</span><span class="sxs-lookup"><span data-stu-id="839a8-117">The <xref:System.Xml.Schema.XmlSchemaValidationFlags> value is used to disable certain features of validation.</span></span>  
  
 <span data-ttu-id="839a8-118">Aby uzyskać więcej informacji na temat <xref:System.Xml.Schema.XmlSchemaValidator.%23ctor%2A> konstruktora, zobacz <xref:System.Xml.Schema.XmlSchemaValidator> klasy dokumentację referencyjną.</span><span class="sxs-lookup"><span data-stu-id="839a8-118">For more information about the <xref:System.Xml.Schema.XmlSchemaValidator.%23ctor%2A> constructor, see the <xref:System.Xml.Schema.XmlSchemaValidator> class reference documentation.</span></span>  
  
### <a name="initializing-validation"></a><span data-ttu-id="839a8-119">Inicjowanie weryfikacji</span><span class="sxs-lookup"><span data-stu-id="839a8-119">Initializing Validation</span></span>  
 <span data-ttu-id="839a8-120">Po <xref:System.Xml.Schema.XmlSchemaValidator> obiekt został skonstruowany, istnieją dwie przeciążone <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> metody używane do zainicjowania stan <xref:System.Xml.Schema.XmlSchemaValidator> obiektu.</span><span class="sxs-lookup"><span data-stu-id="839a8-120">After an <xref:System.Xml.Schema.XmlSchemaValidator> object has been constructed, there are two overloaded <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> methods used to initialize the state of the <xref:System.Xml.Schema.XmlSchemaValidator> object.</span></span> <span data-ttu-id="839a8-121">Poniżej przedstawiono dwa <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="839a8-121">The following are the two <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> methods.</span></span>  
  
-   <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A?displayProperty=nameWithType>  
  
-   <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A?displayProperty=nameWithType>  
  
 <span data-ttu-id="839a8-122">Wartość domyślna <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A?displayProperty=nameWithType> inicjuje metodę <xref:System.Xml.Schema.XmlSchemaValidator> obiekt do stanu początkowego i przeciążone <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A?displayProperty=nameWithType> metody, która przyjmuje <xref:System.Xml.Schema.XmlSchemaObject> jako parametr inicjuje <xref:System.Xml.Schema.XmlSchemaValidator> obiekt początkowy stan dla częściowego Sprawdzanie poprawności.</span><span class="sxs-lookup"><span data-stu-id="839a8-122">The default <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A?displayProperty=nameWithType> method initializes an <xref:System.Xml.Schema.XmlSchemaValidator> object to its starting state, and the overloaded <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A?displayProperty=nameWithType> method that takes an <xref:System.Xml.Schema.XmlSchemaObject> as a parameter initializes an <xref:System.Xml.Schema.XmlSchemaValidator> object to its starting state for partial validation.</span></span>  
  
 <span data-ttu-id="839a8-123">Zarówno <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> metody można wywołać tylko natychmiast po <xref:System.Xml.Schema.XmlSchemaValidator> został skonstruowany obiekt lub po wywołaniu <xref:System.Xml.Schema.XmlSchemaValidator.EndValidation%2A>.</span><span class="sxs-lookup"><span data-stu-id="839a8-123">Both <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> methods can only be called immediately after an <xref:System.Xml.Schema.XmlSchemaValidator> object has been constructed or after a call to <xref:System.Xml.Schema.XmlSchemaValidator.EndValidation%2A>.</span></span>  
  
 <span data-ttu-id="839a8-124">Na przykład <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A?displayProperty=nameWithType> metody, zobacz przykład we wstępie.</span><span class="sxs-lookup"><span data-stu-id="839a8-124">For an example of the <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A?displayProperty=nameWithType> method, see the example in the introduction.</span></span> <span data-ttu-id="839a8-125">Aby uzyskać więcej informacji na temat <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> metody, zobacz <xref:System.Xml.Schema.XmlSchemaValidator> klasy dokumentację referencyjną.</span><span class="sxs-lookup"><span data-stu-id="839a8-125">For more information about the <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> method, see the <xref:System.Xml.Schema.XmlSchemaValidator> class reference documentation.</span></span>  
  
#### <a name="partial-validation"></a><span data-ttu-id="839a8-126">Częściowej weryfikacji</span><span class="sxs-lookup"><span data-stu-id="839a8-126">Partial Validation</span></span>  
 <span data-ttu-id="839a8-127"><xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A?displayProperty=nameWithType> Metody, która przyjmuje <xref:System.Xml.Schema.XmlSchemaObject> jako parametr inicjuje <xref:System.Xml.Schema.XmlSchemaValidator> obiekt początkowy stan dla częściowej weryfikacji.</span><span class="sxs-lookup"><span data-stu-id="839a8-127">The <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A?displayProperty=nameWithType> method that takes an <xref:System.Xml.Schema.XmlSchemaObject> as a parameter initializes an <xref:System.Xml.Schema.XmlSchemaValidator> object to its starting state for partial validation.</span></span>  
  
 <span data-ttu-id="839a8-128">W poniższym przykładzie <xref:System.Xml.Schema.XmlSchemaObject> inicjowane dla częściowej weryfikacji za pomocą <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="839a8-128">In the following example, an <xref:System.Xml.Schema.XmlSchemaObject> is initialized for partial validation using the <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="839a8-129">`orderNumber` Elementu schematu jest przekazywany przez wybranie elementu schematu za <xref:System.Xml.XmlQualifiedName> w <xref:System.Xml.Schema.XmlSchemaObjectTable> kolekcji zwróconej przez <xref:System.Xml.Schema.XmlSchemaSet.GlobalElements%2A> właściwość <xref:System.Xml.Schema.XmlSchemaSet> obiektu.</span><span class="sxs-lookup"><span data-stu-id="839a8-129">The `orderNumber` schema element is passed by selecting the schema element by <xref:System.Xml.XmlQualifiedName> in the <xref:System.Xml.Schema.XmlSchemaObjectTable> collection returned by the <xref:System.Xml.Schema.XmlSchemaSet.GlobalElements%2A> property of the <xref:System.Xml.Schema.XmlSchemaSet> object.</span></span> <span data-ttu-id="839a8-130"><xref:System.Xml.Schema.XmlSchemaValidator> Obiektu następnie weryfikuje ten określony element.</span><span class="sxs-lookup"><span data-stu-id="839a8-130">The <xref:System.Xml.Schema.XmlSchemaValidator> object then validates this specific element.</span></span>  
  
```vb  
Dim schemaSet As XmlSchemaSet = New XmlSchemaSet()  
schemaSet.Add(Nothing, "schema.xsd")  
schemaSet.Compile()  
Dim nameTable As NameTable = New NameTable()  
Dim manager As XmlNamespaceManager = New XmlNamespaceManager(nameTable)  
  
Dim validator As XmlSchemaValidator = New XmlSchemaValidator(nameTable, schemaSet, manager, XmlSchemaValidationFlags.None)  
validator.Initialize(schemaSet.GlobalElements.Item(New XmlQualifiedName("orderNumber")))  
  
validator.ValidateElement("orderNumber", "", Nothing)  
validator.ValidateEndOfAttributes(Nothing)  
validator.ValidateText("123")  
validator.ValidateEndElement(Nothing)  
```  
  
```csharp  
XmlSchemaSet schemaSet = new XmlSchemaSet();  
schemaSet.Add(null, "schema.xsd");  
schemaSet.Compile();  
NameTable nameTable = new NameTable();  
XmlNamespaceManager manager = new XmlNamespaceManager(nameTable);  
  
XmlSchemaValidator validator = new XmlSchemaValidator(nameTable, schemaSet, manager, XmlSchemaValidationFlags.None);  
validator.Initialize(schemaSet.GlobalElements[new XmlQualifiedName("orderNumber")]);  
  
validator.ValidateElement("orderNumber", "", null);  
validator.ValidateEndOfAttributes(null);  
validator.ValidateText("123");  
validator.ValidateEndElement(null);  
```  
  
 <span data-ttu-id="839a8-131">Przykład przyjmuje następujące schematu XML jako dane wejściowe.</span><span class="sxs-lookup"><span data-stu-id="839a8-131">The example takes the following XML schema as input.</span></span>  
  
 `<xs:schema xmlns:xs="http://www.w3.org/2001/XMLSchema">`  
  
 `<xs:element name="orderNumber" type="xs:int" />`  
  
 `</xs:schema>`  
  
 <span data-ttu-id="839a8-132">Aby uzyskać więcej informacji na temat <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> metody, zobacz <xref:System.Xml.Schema.XmlSchemaValidator> klasy dokumentację referencyjną.</span><span class="sxs-lookup"><span data-stu-id="839a8-132">For more information about the <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> method, see the <xref:System.Xml.Schema.XmlSchemaValidator> class reference documentation.</span></span>  
  
### <a name="adding-additional-schemas"></a><span data-ttu-id="839a8-133">Dodawanie schematów dodatkowych</span><span class="sxs-lookup"><span data-stu-id="839a8-133">Adding Additional Schemas</span></span>  
 <span data-ttu-id="839a8-134"><xref:System.Xml.Schema.XmlSchemaValidator.AddSchema%2A> Metody <xref:System.Xml.Schema.XmlSchemaValidator> klasa jest używana do dodawania schematu XML do zestawu schematów używany podczas sprawdzania poprawności.</span><span class="sxs-lookup"><span data-stu-id="839a8-134">The <xref:System.Xml.Schema.XmlSchemaValidator.AddSchema%2A> method of the <xref:System.Xml.Schema.XmlSchemaValidator> class is used to add an XML schema to the set of schemas used during validation.</span></span> <span data-ttu-id="839a8-135"><xref:System.Xml.Schema.XmlSchemaValidator.AddSchema%2A> Metoda można symulować efekt napotkania wbudowanego schematu XML w zestaw informacji XML, sprawdzania poprawności.</span><span class="sxs-lookup"><span data-stu-id="839a8-135">The <xref:System.Xml.Schema.XmlSchemaValidator.AddSchema%2A> method can be used to simulate the effect of encountering an inline XML schema in the XML infoset being validated.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="839a8-136">Docelowy obszar nazw <xref:System.Xml.Schema.XmlSchema> parametru nie może być zgodna z nazwą dowolny element lub atrybut już napotykanych przez <xref:System.Xml.Schema.XmlSchemaValidator> obiektu.</span><span class="sxs-lookup"><span data-stu-id="839a8-136">The target namespace of the <xref:System.Xml.Schema.XmlSchema> parameter cannot match that of any element or attribute already encountered by the <xref:System.Xml.Schema.XmlSchemaValidator> object.</span></span>  
>   
>  <span data-ttu-id="839a8-137">Jeśli <xref:System.Xml.Schema.XmlSchemaValidationFlags.ProcessInlineSchema?displayProperty=nameWithType> wartość nie została przekazana jako parametr do <xref:System.Xml.Schema.XmlSchemaValidator.%23ctor%2A> konstruktora, <xref:System.Xml.Schema.XmlSchemaValidator.AddSchema%2A> metoda nic nie robi.</span><span class="sxs-lookup"><span data-stu-id="839a8-137">If the <xref:System.Xml.Schema.XmlSchemaValidationFlags.ProcessInlineSchema?displayProperty=nameWithType> value was not passed as a parameter to the <xref:System.Xml.Schema.XmlSchemaValidator.%23ctor%2A> constructor, the <xref:System.Xml.Schema.XmlSchemaValidator.AddSchema%2A> method does nothing.</span></span>  
  
 <span data-ttu-id="839a8-138">Wynik <xref:System.Xml.Schema.XmlSchemaValidator.AddSchema%2A> metoda zależy od bieżącego kontekstu węzła XML weryfikowana.</span><span class="sxs-lookup"><span data-stu-id="839a8-138">The result of the <xref:System.Xml.Schema.XmlSchemaValidator.AddSchema%2A> method is dependant on the current XML node context being validated.</span></span> <span data-ttu-id="839a8-139">Aby uzyskać więcej informacji o kontekstach sprawdzania poprawności zobacz sekcję "Kontekst weryfikacji" w tym temacie.</span><span class="sxs-lookup"><span data-stu-id="839a8-139">For more information about validation contexts, see the "Validation Context" section of this topic.</span></span>  
  
 <span data-ttu-id="839a8-140">Aby uzyskać więcej informacji na temat <xref:System.Xml.Schema.XmlSchemaValidator.AddSchema%2A> metody, zobacz <xref:System.Xml.Schema.XmlSchemaValidator> klasy dokumentację referencyjną.</span><span class="sxs-lookup"><span data-stu-id="839a8-140">For more information about the <xref:System.Xml.Schema.XmlSchemaValidator.AddSchema%2A> method, see the <xref:System.Xml.Schema.XmlSchemaValidator> class reference documentation.</span></span>  
  
### <a name="validating-elements-attributes-and-content"></a><span data-ttu-id="839a8-141">Sprawdzanie poprawności, elementy, atrybuty i zawartości</span><span class="sxs-lookup"><span data-stu-id="839a8-141">Validating Elements, Attributes, and Content</span></span>  
 <span data-ttu-id="839a8-142"><xref:System.Xml.Schema.XmlSchemaValidator> Klasa udostępnia kilka metod sprawdzania poprawności, elementy, atrybuty i zawartości w zestaw informacji XML, względem schematów XML.</span><span class="sxs-lookup"><span data-stu-id="839a8-142">The <xref:System.Xml.Schema.XmlSchemaValidator> class provides several methods used to validate elements, attributes, and content in an XML infoset against XML schemas.</span></span> <span data-ttu-id="839a8-143">W poniższej tabeli opisano każdy z tych metod.</span><span class="sxs-lookup"><span data-stu-id="839a8-143">The following table describes each of these methods.</span></span>  
  
|<span data-ttu-id="839a8-144">Metoda</span><span class="sxs-lookup"><span data-stu-id="839a8-144">Method</span></span>|<span data-ttu-id="839a8-145">Opis</span><span class="sxs-lookup"><span data-stu-id="839a8-145">Description</span></span>|  
|------------|-----------------|  
|<xref:System.Xml.Schema.XmlSchemaValidator.ValidateElement%2A>|<span data-ttu-id="839a8-146">Sprawdza poprawność nazwy elementu w bieżącym kontekście.</span><span class="sxs-lookup"><span data-stu-id="839a8-146">Validates the element name in the current context.</span></span>|  
|<xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A>|<span data-ttu-id="839a8-147">Sprawdza poprawność atrybutu kontekst bieżącego elementu lub względem <xref:System.Xml.Schema.XmlSchemaAttribute> przekazano obiekt jako parametr do <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="839a8-147">Validates the attribute in the current element context or against the <xref:System.Xml.Schema.XmlSchemaAttribute> object passed as a parameter to the <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> method.</span></span>|  
|<xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndOfAttributes%2A>|<span data-ttu-id="839a8-148">Sprawdza, czy wszystkie wymagane atrybuty w kontekście elementu są obecne i przygotowuje <xref:System.Xml.Schema.XmlSchemaValidator> obiektu do weryfikacji zawartość elementu podrzędnego elementu.</span><span class="sxs-lookup"><span data-stu-id="839a8-148">Verifies whether all the required attributes in the element context are present and prepares the <xref:System.Xml.Schema.XmlSchemaValidator> object to validate the child content of the element.</span></span>|  
|<xref:System.Xml.Schema.XmlSchemaValidator.ValidateText%2A>|<span data-ttu-id="839a8-149">Sprawdza, czy tekst jest dozwolona w bieżącym kontekście elementu i gromadzi tekstu do sprawdzania poprawności, jeśli bieżący element ma zawartość, proste.</span><span class="sxs-lookup"><span data-stu-id="839a8-149">Validates whether text is allowed in the current element context, and accumulates the text for validation if the current element has simple content.</span></span>|  
|<xref:System.Xml.Schema.XmlSchemaValidator.ValidateWhitespace%2A>|<span data-ttu-id="839a8-150">Sprawdza, czy odstępu, jest dozwolona w bieżącym kontekście elementu i gromadzi biały do weryfikacji, czy bieżący element posiada prostej zawartości.</span><span class="sxs-lookup"><span data-stu-id="839a8-150">Validates whether white-space is allowed in the current element context, and accumulates the white-space for validation whether the current element has simple content.</span></span>|  
|<xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndElement%2A>|<span data-ttu-id="839a8-151">Sprawdza, czy zawartości tekstowej elementu jest nieprawidłowa w kontekście jego typu danych dla elementów z zawartością prostą i sprawdza, czy zawartość bieżącego elementu jest ukończony dla elementów z zawartością złożoną.</span><span class="sxs-lookup"><span data-stu-id="839a8-151">Verifies whether the text content of the element is valid according to its data type for elements with simple content, and verifies whether the content of the current element is complete for elements with complex content.</span></span>|  
|<xref:System.Xml.Schema.XmlSchemaValidator.SkipToEndElement%2A>|<span data-ttu-id="839a8-152">Pomija weryfikację bieżącej zawartości elementu i przygotowuje <xref:System.Xml.Schema.XmlSchemaValidator> obiektu, aby walidować zawartość w kontekście elementu nadrzędnego.</span><span class="sxs-lookup"><span data-stu-id="839a8-152">Skips validation of the current element content and prepares the <xref:System.Xml.Schema.XmlSchemaValidator> object to validate content in the parent element's context.</span></span>|  
|<xref:System.Xml.Schema.XmlSchemaValidator.EndValidation%2A>|<span data-ttu-id="839a8-153">Kończy się sprawdzanie poprawności i sprawdza ograniczenia tożsamości na całego dokumentu XML, czy <xref:System.Xml.Schema.XmlSchemaValidationFlags.ProcessIdentityConstraints> ustawiono opcję sprawdzania poprawności.</span><span class="sxs-lookup"><span data-stu-id="839a8-153">Ends validation and checks identity constraints for the entire XML document if the <xref:System.Xml.Schema.XmlSchemaValidationFlags.ProcessIdentityConstraints> validation option is set.</span></span>|  
  
> [!NOTE]
>  <span data-ttu-id="839a8-154"><xref:System.Xml.Schema.XmlSchemaValidator> Klasa ma zmianę stanu zdefiniowany, który wymusza kolejność i wystąpienie wywołania do każdej z metod opisanych w poprzedniej tabeli.</span><span class="sxs-lookup"><span data-stu-id="839a8-154">The <xref:System.Xml.Schema.XmlSchemaValidator> class has a defined state transition that enforces the sequence and occurrence of calls made to each of the methods described in the previous table.</span></span> <span data-ttu-id="839a8-155">Przejście stanu z określonego <xref:System.Xml.Schema.XmlSchemaValidator> klasy jest opisane w sekcji "XmlSchemaValidator przejście stanu" w tym temacie.</span><span class="sxs-lookup"><span data-stu-id="839a8-155">The specific state transition of the <xref:System.Xml.Schema.XmlSchemaValidator> class is described in the "XmlSchemaValidator State Transition" section of this topic.</span></span>  
  
 <span data-ttu-id="839a8-156">Na przykład metody używane do sprawdzania poprawności, elementy, atrybuty i zawartości w zestaw informacji XML Zobacz przykład w poprzedniej sekcji.</span><span class="sxs-lookup"><span data-stu-id="839a8-156">For an example of the methods used to validate elements, attributes, and content in an XML infoset, see the example in the previous section.</span></span> <span data-ttu-id="839a8-157">Aby uzyskać więcej informacji o tych metodach, zobacz <xref:System.Xml.Schema.XmlSchemaValidator> klasy dokumentację referencyjną.</span><span class="sxs-lookup"><span data-stu-id="839a8-157">For more information about these methods, see the <xref:System.Xml.Schema.XmlSchemaValidator> class reference documentation.</span></span>  
  
#### <a name="validating-content-using-an-xmlvaluegetter"></a><span data-ttu-id="839a8-158">Sprawdzanie poprawności zawartości przy użyciu XmlValueGetter</span><span class="sxs-lookup"><span data-stu-id="839a8-158">Validating Content Using an XmlValueGetter</span></span>  
 <span data-ttu-id="839a8-159"><xref:System.Xml.Schema.XmlValueGetter> `delegate` Może służyć do przekazywania wartości atrybutu, tekst lub węzły odstępu jako typy środowiska uruchomieniowego języka wspólnego (CLR) zgodny z typem języka definicji schematu XML (XSD) atrybutu, tekst lub węzeł odstępu.</span><span class="sxs-lookup"><span data-stu-id="839a8-159">The <xref:System.Xml.Schema.XmlValueGetter>`delegate` can be used to pass the value of attribute, text, or white-space nodes as a Common Language Runtime (CLR) types compatible with the XML Schema Definition Language (XSD) type of the attribute, text, or white-space node.</span></span> <span data-ttu-id="839a8-160"><xref:System.Xml.Schema.XmlValueGetter> `delegate` Jest przydatne, jeśli wartość CLR atrybut, tekst lub odstępu węzeł jest już dostępny i pozwala uniknąć kosztów podczas konwertowania go do `string` i następnie ponownej analizy go ponownie do sprawdzania poprawności.</span><span class="sxs-lookup"><span data-stu-id="839a8-160">An <xref:System.Xml.Schema.XmlValueGetter>`delegate` is useful if the CLR value of an attribute, text, or white-space node is already available, and avoids the cost of converting it to a `string` and then reparsing it again for validation.</span></span>  
  
 <span data-ttu-id="839a8-161"><xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A>, <xref:System.Xml.Schema.XmlSchemaValidator.ValidateText%2A>, I <xref:System.Xml.Schema.XmlSchemaValidator.ValidateWhitespace%2A> metody są przeciążone i zaakceptuj wartość atrybutu, tekst lub węzły odstępu jako `string` lub <xref:System.Xml.Schema.XmlValueGetter> `delegate`.</span><span class="sxs-lookup"><span data-stu-id="839a8-161">The <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A>, <xref:System.Xml.Schema.XmlSchemaValidator.ValidateText%2A>, and <xref:System.Xml.Schema.XmlSchemaValidator.ValidateWhitespace%2A> methods are overloaded and accept the value of attribute, text, or white-space nodes as a `string` or <xref:System.Xml.Schema.XmlValueGetter>`delegate`.</span></span>  
  
 <span data-ttu-id="839a8-162">Następujące metody <xref:System.Xml.Schema.XmlSchemaValidator> zaakceptować klasy <xref:System.Xml.Schema.XmlValueGetter> `delegate` jako parametr.</span><span class="sxs-lookup"><span data-stu-id="839a8-162">The following methods of the <xref:System.Xml.Schema.XmlSchemaValidator> class accept an <xref:System.Xml.Schema.XmlValueGetter>`delegate` as a parameter.</span></span>  
  
-   <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A>  
  
-   <xref:System.Xml.Schema.XmlSchemaValidator.ValidateText%2A>  
  
-   <xref:System.Xml.Schema.XmlSchemaValidator.ValidateWhitespace%2A>  
  
 <span data-ttu-id="839a8-163">Poniżej przedstawiono przykład <xref:System.Xml.Schema.XmlValueGetter> `delegate` pobranych z <xref:System.Xml.Schema.XmlSchemaValidator> klasy przykładu we wprowadzeniu.</span><span class="sxs-lookup"><span data-stu-id="839a8-163">The following is an example <xref:System.Xml.Schema.XmlValueGetter>`delegate` taken from the <xref:System.Xml.Schema.XmlSchemaValidator> class example in the introduction.</span></span> <span data-ttu-id="839a8-164"><xref:System.Xml.Schema.XmlValueGetter> `delegate` Zwraca wartość atrybutu jako <xref:System.DateTime> obiektu.</span><span class="sxs-lookup"><span data-stu-id="839a8-164">The <xref:System.Xml.Schema.XmlValueGetter>`delegate` returns the value of an attribute as a <xref:System.DateTime> object.</span></span> <span data-ttu-id="839a8-165">Aby to sprawdzić <xref:System.DateTime> obiektu zwróconego przez <xref:System.Xml.Schema.XmlValueGetter>, <xref:System.Xml.Schema.XmlSchemaValidator> obiektu najpierw konwertuje ją na właściwość ValueType (ValueType jest domyślne mapowanie środowiska CLR dla typu XSD) dla typu danych atrybutu, a następnie aspektami kontroli na przekonwertowany wartość.</span><span class="sxs-lookup"><span data-stu-id="839a8-165">To validate this <xref:System.DateTime> object returned by the <xref:System.Xml.Schema.XmlValueGetter>, the <xref:System.Xml.Schema.XmlSchemaValidator> object first converts it to the ValueType (ValueType is the default CLR mapping for the XSD type) for the data type of the attribute and then checks facets on the converted value.</span></span>  
  
```vb  
Shared dateTimeGetterContent As Object  
  
Shared Function dateTimeGetterHandle() As Object  
    Return dateTimeGetterContent  
End Function  
  
Shared Function dateTimeGetter(ByVal dateTime As DateTime) As XmlValueGetter  
    dateTimeGetterContent = dateTime  
    Return New XmlValueGetter(AddressOf dateTimeGetterHandle)  
End Function  
```  
  
```csharp  
static object dateTimeGetterContent;  
  
static object dateTimeGetterHandle()  
{  
    return dateTimeGetterContent;  
}  
  
static XmlValueGetter dateTimeGetter(DateTime dateTime)  
{  
    dateTimeGetterContent = dateTime;  
    return new XmlValueGetter(dateTimeGetterHandle);  
}  
```  
  
 <span data-ttu-id="839a8-166">Aby uzyskać pełny przykład <xref:System.Xml.Schema.XmlValueGetter> `delegate`, zobacz przykład we wstępie.</span><span class="sxs-lookup"><span data-stu-id="839a8-166">For a complete example of the <xref:System.Xml.Schema.XmlValueGetter>`delegate`, see the example in the introduction.</span></span> <span data-ttu-id="839a8-167">Aby uzyskać więcej informacji na temat <xref:System.Xml.Schema.XmlValueGetter> `delegate`, zobacz <xref:System.Xml.Schema.XmlValueGetter>, i <xref:System.Xml.Schema.XmlSchemaValidator> klasy dokumentację referencyjną.</span><span class="sxs-lookup"><span data-stu-id="839a8-167">For more information about the <xref:System.Xml.Schema.XmlValueGetter>`delegate`, see the <xref:System.Xml.Schema.XmlValueGetter>, and <xref:System.Xml.Schema.XmlSchemaValidator> class reference documentation.</span></span>  
  
#### <a name="post-schema-validation-information"></a><span data-ttu-id="839a8-168">Post-Schema-Validation-Information</span><span class="sxs-lookup"><span data-stu-id="839a8-168">Post-Schema-Validation-Information</span></span>  
 <span data-ttu-id="839a8-169"><xref:System.Xml.Schema.XmlSchemaInfo> Klasa reprezentuje niektóre odniesienie-Schema-weryfikacji — informacje o węzła XML zweryfikowany przez <xref:System.Xml.Schema.XmlSchemaValidator> klasy.</span><span class="sxs-lookup"><span data-stu-id="839a8-169">The <xref:System.Xml.Schema.XmlSchemaInfo> class represents some of the Post-Schema-Validation-Information of an XML node validated by the <xref:System.Xml.Schema.XmlSchemaValidator> class.</span></span> <span data-ttu-id="839a8-170">Różnych metod <xref:System.Xml.Schema.XmlSchemaValidator> zaakceptować klasy <xref:System.Xml.Schema.XmlSchemaInfo> obiektu jako opcjonalny (`null`) `out` parametru.</span><span class="sxs-lookup"><span data-stu-id="839a8-170">Various methods of the <xref:System.Xml.Schema.XmlSchemaValidator> class accept an <xref:System.Xml.Schema.XmlSchemaInfo> object as an optional, (`null`) `out` parameter.</span></span>  
  
 <span data-ttu-id="839a8-171">Po pomyślnej weryfikacji, właściwości <xref:System.Xml.Schema.XmlSchemaInfo> obiektu są konfigurowane przy użyciu wyników weryfikacji.</span><span class="sxs-lookup"><span data-stu-id="839a8-171">Upon successful validation, properties of the <xref:System.Xml.Schema.XmlSchemaInfo> object are set with the results of the validation.</span></span> <span data-ttu-id="839a8-172">Na przykład po pomyślnej weryfikacji przy użyciu atrybutu <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A> metody <xref:System.Xml.Schema.XmlSchemaInfo> obiekt użytkownika (Jeśli określono) <xref:System.Xml.Schema.XmlSchemaInfo.SchemaAttribute%2A>, <xref:System.Xml.Schema.XmlSchemaInfo.SchemaType%2A>, <xref:System.Xml.Schema.XmlSchemaInfo.MemberType%2A>, i <xref:System.Xml.Schema.XmlSchemaInfo.Validity%2A> właściwości są ustawiane przy użyciu wyników weryfikacji .</span><span class="sxs-lookup"><span data-stu-id="839a8-172">For example, upon successful validation of an attribute using the <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A> method, the <xref:System.Xml.Schema.XmlSchemaInfo> object's (if specified) <xref:System.Xml.Schema.XmlSchemaInfo.SchemaAttribute%2A>, <xref:System.Xml.Schema.XmlSchemaInfo.SchemaType%2A>, <xref:System.Xml.Schema.XmlSchemaInfo.MemberType%2A>, and <xref:System.Xml.Schema.XmlSchemaInfo.Validity%2A> properties are set with the results of the validation.</span></span>  
  
 <span data-ttu-id="839a8-173">Następujące <xref:System.Xml.Schema.XmlSchemaValidator> akceptować metod klasy <xref:System.Xml.Schema.XmlSchemaInfo> obiektu jako parametru wyjściowego.</span><span class="sxs-lookup"><span data-stu-id="839a8-173">The following <xref:System.Xml.Schema.XmlSchemaValidator> class methods accept an <xref:System.Xml.Schema.XmlSchemaInfo> object as an out parameter.</span></span>  
  
-   <xref:System.Xml.Schema.XmlSchemaValidator.SkipToEndElement%2A>  
  
-   <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A>  
  
-   <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A>  
  
-   <xref:System.Xml.Schema.XmlSchemaValidator.ValidateElement%2A>  
  
-   <xref:System.Xml.Schema.XmlSchemaValidator.ValidateElement%2A>  
  
-   <xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndElement%2A>  
  
-   <xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndElement%2A>  
  
-   <xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndOfAttributes%2A>  
  
 <span data-ttu-id="839a8-174">Aby uzyskać pełny przykład <xref:System.Xml.Schema.XmlSchemaInfo> klasy, zobacz przykładu we wprowadzeniu.</span><span class="sxs-lookup"><span data-stu-id="839a8-174">For a complete example of the <xref:System.Xml.Schema.XmlSchemaInfo> class, see the example in the introduction.</span></span> <span data-ttu-id="839a8-175">Aby uzyskać więcej informacji na temat <xref:System.Xml.Schema.XmlSchemaInfo> klasy, zobacz <xref:System.Xml.Schema.XmlSchemaInfo> klasy dokumentację referencyjną.</span><span class="sxs-lookup"><span data-stu-id="839a8-175">For more information about the <xref:System.Xml.Schema.XmlSchemaInfo> class, see the <xref:System.Xml.Schema.XmlSchemaInfo> class reference documentation.</span></span>  
  
### <a name="retrieving-expected-particles-attributes-and-unspecified-default-attributes"></a><span data-ttu-id="839a8-176">Trwa pobieranie oczekiwanego cząstek, atrybuty i atrybuty domyślne nieokreślony</span><span class="sxs-lookup"><span data-stu-id="839a8-176">Retrieving Expected Particles, Attributes, and Unspecified Default Attributes</span></span>  
 <span data-ttu-id="839a8-177"><xref:System.Xml.Schema.XmlSchemaValidator> Klasa udostępnia <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A>, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A>, i <xref:System.Xml.Schema.XmlSchemaValidator.GetUnspecifiedDefaultAttributes%2A> metod, które można pobrać oczekiwanego cząstek, atrybuty i atrybuty domyślne nieokreślony w bieżącym kontekście sprawdzania poprawności.</span><span class="sxs-lookup"><span data-stu-id="839a8-177">The <xref:System.Xml.Schema.XmlSchemaValidator> class provides the <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A>, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A>, and <xref:System.Xml.Schema.XmlSchemaValidator.GetUnspecifiedDefaultAttributes%2A> methods to retrieve the expected particles, attributes, and unspecified default attributes in the current validation context.</span></span>  
  
#### <a name="retrieving-expected-particles"></a><span data-ttu-id="839a8-178">Trwa pobieranie cząstki oczekiwane</span><span class="sxs-lookup"><span data-stu-id="839a8-178">Retrieving Expected Particles</span></span>  
 <span data-ttu-id="839a8-179"><xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> Metoda zwraca tablicę <xref:System.Xml.Schema.XmlSchemaParticle> obiektów zawierających oczekiwanego cząstek w kontekst bieżącego elementu.</span><span class="sxs-lookup"><span data-stu-id="839a8-179">The <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> method returns an array of <xref:System.Xml.Schema.XmlSchemaParticle> objects containing the expected particles in the current element context.</span></span> <span data-ttu-id="839a8-180">Nieprawidłowa cząstek, które mogą być zwrócone przez <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> metody są wystąpieniami <xref:System.Xml.Schema.XmlSchemaElement> i <xref:System.Xml.Schema.XmlSchemaAny> klasy.</span><span class="sxs-lookup"><span data-stu-id="839a8-180">The valid particles that can be returned by the <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> method are instances of the <xref:System.Xml.Schema.XmlSchemaElement> and <xref:System.Xml.Schema.XmlSchemaAny> classes.</span></span>  
  
 <span data-ttu-id="839a8-181">Gdy compositor dla modelu zawartości jest `xs:sequence`, zwracany jest tylko dalej cząstka w sekwencji.</span><span class="sxs-lookup"><span data-stu-id="839a8-181">When the compositor for the content model is an `xs:sequence`, only the next particle in the sequence is returned.</span></span> <span data-ttu-id="839a8-182">Jeśli compositor dla modelu zawartości jest `xs:all` lub `xs:choice`, a następnie zwracane są wszystkie cząstki prawidłowe, które można wykonać w bieżącym kontekście elementu.</span><span class="sxs-lookup"><span data-stu-id="839a8-182">If the compositor for the content model is an `xs:all` or an `xs:choice`, then all valid particles that could follow in the current element context are returned.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="839a8-183">Jeśli <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> metoda jest wywoływana natychmiast po wywołaniu <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> metody <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> metoda zwraca wszystkie elementy globalne.</span><span class="sxs-lookup"><span data-stu-id="839a8-183">If the <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> method is called immediately after calling the <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> method, the <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> method returns all global elements.</span></span>  
  
 <span data-ttu-id="839a8-184">Na przykład w języku definicji schematu XML (XSD) schematu i XML dokumentu poniżej, po upewnieniu się, `book` elementu `book` element jest kontekst bieżącego elementu.</span><span class="sxs-lookup"><span data-stu-id="839a8-184">For example, in the XML Schema Definition Language (XSD) schema and XML document that follow, after validating the `book` element, the `book` element is the current element context.</span></span> <span data-ttu-id="839a8-185"><xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> Metoda zwraca tablicę zawierającą jeden <xref:System.Xml.Schema.XmlSchemaElement> obiekt reprezentujący `title` elementu.</span><span class="sxs-lookup"><span data-stu-id="839a8-185">The <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> method returns an array containing a single <xref:System.Xml.Schema.XmlSchemaElement> object representing the `title` element.</span></span> <span data-ttu-id="839a8-186">Gdy jest kontekst weryfikacji `title` elementu <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> metoda zwraca pustą tablicę.</span><span class="sxs-lookup"><span data-stu-id="839a8-186">When the validation context is the `title` element, the <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> method returns an empty array.</span></span> <span data-ttu-id="839a8-187">Jeśli <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> metoda jest wywoływana po `title` element został zweryfikowany, lecz przed `description` zweryfikowany element, zwraca tablicę zawierającą jeden <xref:System.Xml.Schema.XmlSchemaElement> obiekt reprezentujący `description` elementu.</span><span class="sxs-lookup"><span data-stu-id="839a8-187">If the <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> method is called after the `title` element has been validated but before the `description` element has been validated, it returns an array containing a single <xref:System.Xml.Schema.XmlSchemaElement> object representing the `description` element.</span></span> <span data-ttu-id="839a8-188">Jeśli <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> metoda jest wywoływana po `description` element został zweryfikowany, a następnie zwraca tablicę zawierającą pojedynczy <xref:System.Xml.Schema.XmlSchemaAny> obiekt reprezentujący symbol wieloznaczny.</span><span class="sxs-lookup"><span data-stu-id="839a8-188">If the <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> method is called after the `description` element has been validated then it returns an array containing a single <xref:System.Xml.Schema.XmlSchemaAny> object representing the wildcard.</span></span>  
  
```vb  
Dim reader As XmlReader =  XmlReader.Create("input.xml")   
  
Dim schemaSet As XmlSchemaSet =  New XmlSchemaSet()   
schemaSet.Add(Nothing, "schema.xsd")  
Dim manager As XmlNamespaceManager =  New XmlNamespaceManager(reader.NameTable)   
  
Dim validator As XmlSchemaValidator =  New XmlSchemaValidator(reader.NameTable,schemaSet,manager,XmlSchemaValidationFlags.None)  
validator.Initialize()  
  
validator.ValidateElement("book", "", Nothing)  
  
validator.ValidateEndOfAttributes(Nothing)  
For Each element As XmlSchemaElement In validator.GetExpectedParticles()  
    Console.WriteLine(element.Name)  
Next  
  
validator.ValidateElement("title", "", Nothing)  
validator.ValidateEndOfAttributes(Nothing)  
For Each element As XmlSchemaElement In validator.GetExpectedParticles()  
    Console.WriteLine(element.Name)  
Next  
validator.ValidateEndElement(Nothing)  
  
For Each element As XmlSchemaElement In validator.GetExpectedParticles()  
    Console.WriteLine(element.Name)  
Next  
  
validator.ValidateElement("description", "", Nothing)  
validator.ValidateEndOfAttributes(Nothing)  
validator.ValidateEndElement(Nothing)  
  
For Each particle As XmlSchemaParticle In validator.GetExpectedParticles()  
    Console.WriteLine(particle.GetType())  
Next  
  
validator.ValidateElement("namespace", "", Nothing)  
validator.ValidateEndOfAttributes(Nothing)  
validator.ValidateEndElement(Nothing)  
  
validator.ValidateEndElement(Nothing)  
```  
  
```csharp  
XmlReader reader = XmlReader.Create("input.xml");  
  
XmlSchemaSet schemaSet = new XmlSchemaSet();  
schemaSet.Add(null, "schema.xsd");  
XmlNamespaceManager manager = new XmlNamespaceManager(reader.NameTable);  
  
XmlSchemaValidator validator = new XmlSchemaValidator(reader.NameTable, schemaSet, manager, XmlSchemaValidationFlags.None);  
validator.Initialize();  
  
validator.ValidateElement("book", "", null);  
  
validator.ValidateEndOfAttributes(null);  
foreach (XmlSchemaElement element in validator.GetExpectedParticles())  
{  
    Console.WriteLine(element.Name);  
}  
  
validator.ValidateElement("title", "", null);  
validator.ValidateEndOfAttributes(null);  
foreach (XmlSchemaElement element in validator.GetExpectedParticles())  
{  
    Console.WriteLine(element.Name);  
}  
validator.ValidateEndElement(null);  
  
foreach (XmlSchemaElement element in validator.GetExpectedParticles())  
{  
    Console.WriteLine(element.Name);  
}  
  
validator.ValidateElement("description", "", null);  
validator.ValidateEndOfAttributes(null);  
validator.ValidateEndElement(null);  
  
foreach (XmlSchemaParticle particle in validator.GetExpectedParticles())  
{  
    Console.WriteLine(particle.GetType());  
}  
  
validator.ValidateElement("namespace", "", null);  
validator.ValidateEndOfAttributes(null);  
validator.ValidateEndElement(null);  
  
validator.ValidateEndElement(null);  
```  
  
 <span data-ttu-id="839a8-189">Przykład przyjmuje następujący kod XML jako dane wejściowe.</span><span class="sxs-lookup"><span data-stu-id="839a8-189">The example takes the following XML as input.</span></span>  
  
 `<xs:schema xmlns:xs="http://www.w3c.org/2001/XMLSchema">`  
  
 `<xs:element name="book">`  
  
 `<xs:sequence>`  
  
 `<xs:element name="title" type="xs:string" />`  
  
 `<xs:element name="description" type="xs:string" />`  
  
 `<xs:any processContent="lax" maxOccurs="unbounded" />`  
  
 `</xs:sequence>`  
  
 `</xs:element>`  
  
 `</xs:schema>`  
  
 <span data-ttu-id="839a8-190">Przykład przyjmuje następujące schematu XSD jako dane wejściowe.</span><span class="sxs-lookup"><span data-stu-id="839a8-190">The example takes the following XSD schema as input.</span></span>  
  
 `<book>`  
  
 `<title>My Book</title>`  
  
 `<description>My Book's Description</description>`  
  
 `<namespace>System.Xml.Schema</namespace>`  
  
 `</book>`  
  
> [!NOTE]
>  <span data-ttu-id="839a8-191">Wyniki <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A>, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A>, i <xref:System.Xml.Schema.XmlSchemaValidator.AddSchema%2A> metody <xref:System.Xml.Schema.XmlSchemaValidator> klasy są uzależnione od bieżącego kontekstu sprawdzania poprawności.</span><span class="sxs-lookup"><span data-stu-id="839a8-191">The results of the <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A>, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A>, and <xref:System.Xml.Schema.XmlSchemaValidator.AddSchema%2A> methods of the <xref:System.Xml.Schema.XmlSchemaValidator> class are dependent on the current context being validated.</span></span> <span data-ttu-id="839a8-192">Aby uzyskać więcej informacji zobacz sekcję "Kontekst weryfikacji" tego tematu.</span><span class="sxs-lookup"><span data-stu-id="839a8-192">For more information, see the "Validation Context" section of this topic.</span></span>  
  
 <span data-ttu-id="839a8-193">Na przykład <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> metody, zobacz przykład we wstępie.</span><span class="sxs-lookup"><span data-stu-id="839a8-193">For an example of the <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> method, see the example in the introduction.</span></span> <span data-ttu-id="839a8-194">Aby uzyskać więcej informacji na temat <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> metody, zobacz <xref:System.Xml.Schema.XmlSchemaValidator> klasy dokumentację referencyjną.</span><span class="sxs-lookup"><span data-stu-id="839a8-194">For more information about the <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> method, see the <xref:System.Xml.Schema.XmlSchemaValidator> class reference documentation.</span></span>  
  
#### <a name="retrieving-expected-attributes"></a><span data-ttu-id="839a8-195">Pobieranie atrybutów oczekiwane</span><span class="sxs-lookup"><span data-stu-id="839a8-195">Retrieving Expected Attributes</span></span>  
 <span data-ttu-id="839a8-196"><xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> Metoda zwraca tablicę <xref:System.Xml.Schema.XmlSchemaAttribute> obiektów zawierających oczekiwanego atrybuty kontekst bieżącego elementu.</span><span class="sxs-lookup"><span data-stu-id="839a8-196">The <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> method returns an array of <xref:System.Xml.Schema.XmlSchemaAttribute> objects containing the expected attributes in the current element context.</span></span>  
  
 <span data-ttu-id="839a8-197">Na przykład w przypadku przykładu we wprowadzeniu <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> metoda służy do pobierania wszystkich atrybutów `book` elementu.</span><span class="sxs-lookup"><span data-stu-id="839a8-197">For example, in the example in the introduction, the <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> method is used to retrieve all the attributes of the `book` element.</span></span>  
  
 <span data-ttu-id="839a8-198">Jeśli wywołasz <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> metoda natychmiast po <xref:System.Xml.Schema.XmlSchemaValidator.ValidateElement%2A> metody, zwracane są wszystkie atrybuty, które może się pojawić w dokumencie XML.</span><span class="sxs-lookup"><span data-stu-id="839a8-198">If you call the <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> method immediately after the <xref:System.Xml.Schema.XmlSchemaValidator.ValidateElement%2A> method, all the attributes that could appear in the XML document are returned.</span></span> <span data-ttu-id="839a8-199">Jednak jeśli wywołasz <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> metody jedno lub więcej wywołań <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A> metody, zwracane są atrybuty, które nie zostały jeszcze zweryfikowane dla bieżącego elementu.</span><span class="sxs-lookup"><span data-stu-id="839a8-199">However, if you call the <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> method after one or more calls to the <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A> method, the attributes that have not yet been validated for the current element are returned.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="839a8-200">Wyniki <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A>, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A>, i <xref:System.Xml.Schema.XmlSchemaValidator.AddSchema%2A> metody <xref:System.Xml.Schema.XmlSchemaValidator> klasy są uzależnione od bieżącego kontekstu sprawdzania poprawności.</span><span class="sxs-lookup"><span data-stu-id="839a8-200">The results of the <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A>, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A>, and <xref:System.Xml.Schema.XmlSchemaValidator.AddSchema%2A> methods of the <xref:System.Xml.Schema.XmlSchemaValidator> class are dependent on the current context being validated.</span></span> <span data-ttu-id="839a8-201">Aby uzyskać więcej informacji zobacz sekcję "Kontekst weryfikacji" tego tematu.</span><span class="sxs-lookup"><span data-stu-id="839a8-201">For more information, see the "Validation Context" section of this topic.</span></span>  
  
 <span data-ttu-id="839a8-202">Na przykład <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> metody, zobacz przykład we wstępie.</span><span class="sxs-lookup"><span data-stu-id="839a8-202">For an example of the <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> method, see the example in the introduction.</span></span> <span data-ttu-id="839a8-203">Aby uzyskać więcej informacji na temat <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> metody, zobacz <xref:System.Xml.Schema.XmlSchemaValidator> klasy dokumentację referencyjną.</span><span class="sxs-lookup"><span data-stu-id="839a8-203">For more information about the <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> method, see the <xref:System.Xml.Schema.XmlSchemaValidator> class reference documentation.</span></span>  
  
#### <a name="retrieving-unspecified-default-attributes"></a><span data-ttu-id="839a8-204">Podczas pobierania atrybutów nieokreślonych domyślnych</span><span class="sxs-lookup"><span data-stu-id="839a8-204">Retrieving Unspecified Default Attributes</span></span>  
 <span data-ttu-id="839a8-205"><xref:System.Xml.Schema.XmlSchemaValidator.GetUnspecifiedDefaultAttributes%2A> Metoda wypełni <xref:System.Collections.ArrayList> określenia <xref:System.Xml.Schema.XmlSchemaAttribute> obiektów wszystkich atrybutów z wartościami domyślnymi, które mają nie zostało wcześniej poddane walidacji za pomocą <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A> metodę w kontekście elementu.</span><span class="sxs-lookup"><span data-stu-id="839a8-205">The <xref:System.Xml.Schema.XmlSchemaValidator.GetUnspecifiedDefaultAttributes%2A> method populates the <xref:System.Collections.ArrayList> specified with <xref:System.Xml.Schema.XmlSchemaAttribute> objects for any attributes with default values that have not been previously validated using the <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A> method in the element context.</span></span> <span data-ttu-id="839a8-206"><xref:System.Xml.Schema.XmlSchemaValidator.GetUnspecifiedDefaultAttributes%2A> Metoda powinna być wywoływana po wywołaniu <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A> metody dla każdego atrybutu w kontekście elementu.</span><span class="sxs-lookup"><span data-stu-id="839a8-206">The <xref:System.Xml.Schema.XmlSchemaValidator.GetUnspecifiedDefaultAttributes%2A> method should be called after calling the <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A> method on each attribute in the element context.</span></span> <span data-ttu-id="839a8-207"><xref:System.Xml.Schema.XmlSchemaValidator.GetUnspecifiedDefaultAttributes%2A> Metoda powinna służyć, aby określić atrybuty domyślnych ma zostać wstawiony w dokumencie XML, w trakcie sprawdzania poprawności.</span><span class="sxs-lookup"><span data-stu-id="839a8-207">The <xref:System.Xml.Schema.XmlSchemaValidator.GetUnspecifiedDefaultAttributes%2A> method should be used to determine what default attributes are to be inserted into the XML document being validated.</span></span>  
  
 <span data-ttu-id="839a8-208">Aby uzyskać więcej informacji na temat <xref:System.Xml.Schema.XmlSchemaValidator.GetUnspecifiedDefaultAttributes%2A> metody, zobacz <xref:System.Xml.Schema.XmlSchemaValidator> klasy dokumentację referencyjną.</span><span class="sxs-lookup"><span data-stu-id="839a8-208">For more information about the <xref:System.Xml.Schema.XmlSchemaValidator.GetUnspecifiedDefaultAttributes%2A> method, see the <xref:System.Xml.Schema.XmlSchemaValidator> class reference documentation.</span></span>  
  
### <a name="handling-schema-validation-events"></a><span data-ttu-id="839a8-209">Obsługa zdarzeń sprawdzania poprawności schematu</span><span class="sxs-lookup"><span data-stu-id="839a8-209">Handling Schema Validation Events</span></span>  
 <span data-ttu-id="839a8-210">Schemat Walidacja ostrzeżeń i błędów napotkanych podczas sprawdzania poprawności, które są obsługiwane przez <xref:System.Xml.Schema.XmlSchemaValidator.ValidationEventHandler> zdarzenia <xref:System.Xml.Schema.XmlSchemaValidator> klasy.</span><span class="sxs-lookup"><span data-stu-id="839a8-210">Schema validation warnings and errors encountered during validation are handled by the <xref:System.Xml.Schema.XmlSchemaValidator.ValidationEventHandler> event of the <xref:System.Xml.Schema.XmlSchemaValidator> class.</span></span>  
  
 <span data-ttu-id="839a8-211">Ostrzeżenia sprawdzania poprawności schematu mają <xref:System.Xml.Schema.XmlSeverityType> wartość <xref:System.Xml.Schema.XmlSeverityType.Warning> i błędy sprawdzania poprawności schematu <xref:System.Xml.Schema.XmlSeverityType> wartość <xref:System.Xml.Schema.XmlSeverityType.Error>.</span><span class="sxs-lookup"><span data-stu-id="839a8-211">Schema validation warnings have an <xref:System.Xml.Schema.XmlSeverityType> value of <xref:System.Xml.Schema.XmlSeverityType.Warning> and schema validation errors have an <xref:System.Xml.Schema.XmlSeverityType> value of <xref:System.Xml.Schema.XmlSeverityType.Error>.</span></span> <span data-ttu-id="839a8-212">Jeśli nie <xref:System.Xml.Schema.XmlSchemaValidator.ValidationEventHandler> został przypisany, <xref:System.Xml.Schema.XmlSchemaValidationException> jest generowany dla wszystkich błędów sprawdzania poprawności schematu za pomocą <xref:System.Xml.Schema.XmlSeverityType> wartość <xref:System.Xml.Schema.XmlSeverityType.Error>.</span><span class="sxs-lookup"><span data-stu-id="839a8-212">If no <xref:System.Xml.Schema.XmlSchemaValidator.ValidationEventHandler> has been assigned, an <xref:System.Xml.Schema.XmlSchemaValidationException> is thrown for all schema validation errors with an <xref:System.Xml.Schema.XmlSeverityType> value of <xref:System.Xml.Schema.XmlSeverityType.Error>.</span></span> <span data-ttu-id="839a8-213">Jednak <xref:System.Xml.Schema.XmlSchemaValidationException> nie jest generowany dla ostrzeżenia sprawdzania poprawności schematu za pomocą <xref:System.Xml.Schema.XmlSeverityType> wartość <xref:System.Xml.Schema.XmlSeverityType.Warning>.</span><span class="sxs-lookup"><span data-stu-id="839a8-213">However, an <xref:System.Xml.Schema.XmlSchemaValidationException> is not thrown for schema validation warnings with an <xref:System.Xml.Schema.XmlSeverityType> value of <xref:System.Xml.Schema.XmlSeverityType.Warning>.</span></span>  
  
 <span data-ttu-id="839a8-214">Oto przykład <xref:System.Xml.Schema.ValidationEventHandler> odbierająca schematu Walidacja ostrzeżeń i błędów napotkanych podczas sprawdzania poprawności schematu z przykładu we wprowadzeniu.</span><span class="sxs-lookup"><span data-stu-id="839a8-214">The following is an example of a <xref:System.Xml.Schema.ValidationEventHandler> that receives schema validation warnings and errors encountered during schema validation taken from the example in the introduction.</span></span>  
  
```vb  
Shared Sub SchemaValidationEventHandler(ByVal sender As Object, ByVal e As ValidationEventArgs)  
  
    Select Case e.Severity  
        Case XmlSeverityType.Error  
            Console.WriteLine(vbCrLf & "Error: {0}", e.Message)  
            Exit Sub  
        Case XmlSeverityType.Warning  
            Console.WriteLine(vbCrLf & "Warning: {0}", e.Message)  
            Exit Sub  
    End Select  
End Sub  
```  
  
```csharp  
static void SchemaValidationEventHandler(object sender, ValidationEventArgs e)  
{  
    switch (e.Severity)  
    {  
        case XmlSeverityType.Error:  
            Console.WriteLine("\nError: {0}", e.Message);  
            break;  
        case XmlSeverityType.Warning:  
            Console.WriteLine("\nWarning: {0}", e.Message);  
            break;  
    }  
}  
```  
  
 <span data-ttu-id="839a8-215">Aby uzyskać pełny przykład <xref:System.Xml.Schema.ValidationEventHandler>, zobacz przykład we wstępie.</span><span class="sxs-lookup"><span data-stu-id="839a8-215">For a complete example of the <xref:System.Xml.Schema.ValidationEventHandler>, see the example in the introduction.</span></span> <span data-ttu-id="839a8-216">Aby uzyskać więcej informacji, zobacz <xref:System.Xml.Schema.XmlSchemaInfo> klasy dokumentację referencyjną.</span><span class="sxs-lookup"><span data-stu-id="839a8-216">For more information, see the <xref:System.Xml.Schema.XmlSchemaInfo> class reference documentation.</span></span>  
  
## <a name="xmlschemavalidator-state-transition"></a><span data-ttu-id="839a8-217">Przejście stanu XmlSchemaValidator</span><span class="sxs-lookup"><span data-stu-id="839a8-217">XmlSchemaValidator State Transition</span></span>  
 <span data-ttu-id="839a8-218"><xref:System.Xml.Schema.XmlSchemaValidator> Klasa ma zmianę stanu zdefiniowany, który wymusza kolejność i wystąpienie wywołania do każdej metody sprawdzania poprawności, elementy, atrybuty i zawartości w zestaw informacji XML.</span><span class="sxs-lookup"><span data-stu-id="839a8-218">The <xref:System.Xml.Schema.XmlSchemaValidator> class has a defined state transition that enforces the sequence and occurrence of calls made to each of the methods used to validate elements, attributes, and content in an XML infoset.</span></span>  
  
 <span data-ttu-id="839a8-219">W poniższej tabeli opisano przejście stanu z <xref:System.Xml.Schema.XmlSchemaValidator> klasy, a sekwencji i wystąpienie wywołania metody, które mogą być wykonane w każdym stanie.</span><span class="sxs-lookup"><span data-stu-id="839a8-219">The following table describes the state transition of the <xref:System.Xml.Schema.XmlSchemaValidator> class, and the sequence and occurrence of method calls that can be made in each state.</span></span>  
  
|<span data-ttu-id="839a8-220">Stan</span><span class="sxs-lookup"><span data-stu-id="839a8-220">State</span></span>|<span data-ttu-id="839a8-221">przejścia</span><span class="sxs-lookup"><span data-stu-id="839a8-221">Transition</span></span>|  
|-----------|----------------|  
|<span data-ttu-id="839a8-222">Sprawdzanie poprawności</span><span class="sxs-lookup"><span data-stu-id="839a8-222">Validate</span></span>|<span data-ttu-id="839a8-223"><xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> (<xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A> &#124; TopLevel \*) <xref:System.Xml.Schema.XmlSchemaValidator.EndValidation%2A></span><span class="sxs-lookup"><span data-stu-id="839a8-223"><xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> (<xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A> &#124; TopLevel\*) <xref:System.Xml.Schema.XmlSchemaValidator.EndValidation%2A></span></span>|  
|<span data-ttu-id="839a8-224">TopLevel</span><span class="sxs-lookup"><span data-stu-id="839a8-224">TopLevel</span></span>|<span data-ttu-id="839a8-225"><xref:System.Xml.Schema.XmlSchemaValidator.ValidateWhitespace%2A> &#124;<xref:System.Xml.Schema.XmlSchemaValidator.ValidateText%2A> &#124; — Element</span><span class="sxs-lookup"><span data-stu-id="839a8-225"><xref:System.Xml.Schema.XmlSchemaValidator.ValidateWhitespace%2A> &#124; <xref:System.Xml.Schema.XmlSchemaValidator.ValidateText%2A> &#124; Element</span></span>|  
|<span data-ttu-id="839a8-226">Element</span><span class="sxs-lookup"><span data-stu-id="839a8-226">Element</span></span>|<span data-ttu-id="839a8-227"><xref:System.Xml.Schema.XmlSchemaValidator.ValidateElement%2A> <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A>\* (<xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndOfAttributes%2A> Zawartości\*)?</span><span class="sxs-lookup"><span data-stu-id="839a8-227"><xref:System.Xml.Schema.XmlSchemaValidator.ValidateElement%2A> <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A>\* (<xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndOfAttributes%2A> Content\*)?</span></span> <span data-ttu-id="839a8-228"><xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndElement%2A> &#124;</span><span class="sxs-lookup"><span data-stu-id="839a8-228"><xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndElement%2A> &#124;</span></span><br /><br /> <span data-ttu-id="839a8-229"><xref:System.Xml.Schema.XmlSchemaValidator.ValidateElement%2A> <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A>\* <xref:System.Xml.Schema.XmlSchemaValidator.SkipToEndElement%2A> &#124;</span><span class="sxs-lookup"><span data-stu-id="839a8-229"><xref:System.Xml.Schema.XmlSchemaValidator.ValidateElement%2A> <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A>\* <xref:System.Xml.Schema.XmlSchemaValidator.SkipToEndElement%2A> &#124;</span></span><br /><br /> <span data-ttu-id="839a8-230"><xref:System.Xml.Schema.XmlSchemaValidator.ValidateElement%2A> <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A>\* <xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndOfAttributes%2A> Zawartość\* <xref:System.Xml.Schema.XmlSchemaValidator.SkipToEndElement%2A>&#124;</span><span class="sxs-lookup"><span data-stu-id="839a8-230"><xref:System.Xml.Schema.XmlSchemaValidator.ValidateElement%2A> <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A>\* <xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndOfAttributes%2A> Content\* <xref:System.Xml.Schema.XmlSchemaValidator.SkipToEndElement%2A> &#124;</span></span>|  
|<span data-ttu-id="839a8-231">Zawartość</span><span class="sxs-lookup"><span data-stu-id="839a8-231">Content</span></span>|<span data-ttu-id="839a8-232"><xref:System.Xml.Schema.XmlSchemaValidator.ValidateWhitespace%2A> &#124;<xref:System.Xml.Schema.XmlSchemaValidator.ValidateText%2A> &#124; — Element</span><span class="sxs-lookup"><span data-stu-id="839a8-232"><xref:System.Xml.Schema.XmlSchemaValidator.ValidateWhitespace%2A> &#124; <xref:System.Xml.Schema.XmlSchemaValidator.ValidateText%2A> &#124; Element</span></span>|  
  
> [!NOTE]
>  <span data-ttu-id="839a8-233"><xref:System.InvalidOperationException> Jest zgłaszany przez każdą z metod w powyższej tabeli, gdy wywołanie metody składa się nieprawidłowe sekwencji zgodnie z bieżącym stanem <xref:System.Xml.Schema.XmlSchemaValidator> obiektu.</span><span class="sxs-lookup"><span data-stu-id="839a8-233">An <xref:System.InvalidOperationException> is thrown by each of the methods in the table above when the call to the method is made in the incorrect sequence according to the current state of an <xref:System.Xml.Schema.XmlSchemaValidator> object.</span></span>  
  
 <span data-ttu-id="839a8-234">Powyższej tabeli przejścia stanu używa symbole znaków interpunkcyjnych, aby opisać metody i innych stanów, którą można wywołać dla każdego stanu przejście stanu <xref:System.Xml.Schema.XmlSchemaValidator> klasy.</span><span class="sxs-lookup"><span data-stu-id="839a8-234">The state transition table above uses punctuation symbols to describe the methods and other states that can be called for each state of the state transition of the <xref:System.Xml.Schema.XmlSchemaValidator> class.</span></span> <span data-ttu-id="839a8-235">Symbole używane są te same symbole w odwołanie do standardów XML znaleziono dokumentu Type Definition (DTD).</span><span class="sxs-lookup"><span data-stu-id="839a8-235">The symbols used are the same symbols found in the XML Standards reference for Document Type Definition (DTD).</span></span>  
  
 <span data-ttu-id="839a8-236">W poniższej tabeli opisano wpływ symbole znaków interpunkcyjnych, znaleziono w powyższej tabeli przejścia stanu na metody i innych państw, może być wywoływana dla każdego stanu w okresie przejściowym stanu z <xref:System.Xml.Schema.XmlSchemaValidator> klasy.</span><span class="sxs-lookup"><span data-stu-id="839a8-236">The following table describes how the punctuation symbols found in the state transition table above affect the methods and other states that can be called for each state in the state transition of the <xref:System.Xml.Schema.XmlSchemaValidator> class.</span></span>  
  
|<span data-ttu-id="839a8-237">Symbol</span><span class="sxs-lookup"><span data-stu-id="839a8-237">Symbol</span></span>|<span data-ttu-id="839a8-238">Opis</span><span class="sxs-lookup"><span data-stu-id="839a8-238">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="839a8-239">&#124;</span><span class="sxs-lookup"><span data-stu-id="839a8-239">&#124;</span></span>|<span data-ttu-id="839a8-240">Można wywołać metody lub stan (jeden przed pasku) lub obiektowi po nim.</span><span class="sxs-lookup"><span data-stu-id="839a8-240">Either method or state (the one before the bar or the one after it) can be called.</span></span>|  
|<span data-ttu-id="839a8-241">?</span><span class="sxs-lookup"><span data-stu-id="839a8-241">?</span></span>|<span data-ttu-id="839a8-242">Ta metoda lub stan, który poprzedza znak zapytania jest opcjonalne, ale jeśli jest on nazywany go może lze volat pouze jednou.</span><span class="sxs-lookup"><span data-stu-id="839a8-242">The method or state that precedes the question mark is optional but if it is called it can only be called once.</span></span>|  
|*|<span data-ttu-id="839a8-243">Ta metoda lub stan, który poprzedza \* symboli jest opcjonalna i może być wywoływana więcej niż jeden raz.</span><span class="sxs-lookup"><span data-stu-id="839a8-243">The method or state that precedes the \* symbol is optional, and can be called more than once.</span></span>|  
  
## <a name="validation-context"></a><span data-ttu-id="839a8-244">Kontekst weryfikacji</span><span class="sxs-lookup"><span data-stu-id="839a8-244">Validation Context</span></span>  
 <span data-ttu-id="839a8-245">Metody <xref:System.Xml.Schema.XmlSchemaValidator> klasa służy do sprawdzania poprawności, elementy, atrybuty i zawartości w zestaw informacji XML, Zmień kontekst weryfikacji <xref:System.Xml.Schema.XmlSchemaValidator> obiektu.</span><span class="sxs-lookup"><span data-stu-id="839a8-245">The methods of the <xref:System.Xml.Schema.XmlSchemaValidator> class used to validate elements, attributes, and content in an XML infoset, change the validation context of an <xref:System.Xml.Schema.XmlSchemaValidator> object.</span></span> <span data-ttu-id="839a8-246">Na przykład <xref:System.Xml.Schema.XmlSchemaValidator.SkipToEndElement%2A> metoda Pomija weryfikację bieżącej zawartości elementu i przygotowuje <xref:System.Xml.Schema.XmlSchemaValidator> obiektu aby walidować zawartość w kontekście elementu nadrzędnego; jest to równoważne do pomijania sprawdzania poprawności na wszystkie obiekty podrzędne bieżącego elementu a następnie wywołując <xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndElement%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="839a8-246">For example, the <xref:System.Xml.Schema.XmlSchemaValidator.SkipToEndElement%2A> method skips validation of the current element content and prepares the <xref:System.Xml.Schema.XmlSchemaValidator> object to validate content in the parent element's context; it is equivalent to skipping validation for all the children of the current element and then calling the <xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndElement%2A> method.</span></span>  
  
 <span data-ttu-id="839a8-247">Wyniki <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A>, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A>, i <xref:System.Xml.Schema.XmlSchemaValidator.AddSchema%2A> metody <xref:System.Xml.Schema.XmlSchemaValidator> klasy są uzależnione od bieżącego kontekstu sprawdzania poprawności.</span><span class="sxs-lookup"><span data-stu-id="839a8-247">The results of the <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A>, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A>, and <xref:System.Xml.Schema.XmlSchemaValidator.AddSchema%2A> methods of the <xref:System.Xml.Schema.XmlSchemaValidator> class are dependent on the current context being validated.</span></span>  
  
 <span data-ttu-id="839a8-248">W poniższej tabeli opisano wyniki wywoływanie tych metod po wywołaniu jednej z metod <xref:System.Xml.Schema.XmlSchemaValidator> klasa służy do sprawdzania poprawności, elementy, atrybuty i zawartości w zestaw informacji XML.</span><span class="sxs-lookup"><span data-stu-id="839a8-248">The following table describes the results of calling these methods after calling one of the methods of the <xref:System.Xml.Schema.XmlSchemaValidator> class used to validate elements, attributes, and content in an XML infoset.</span></span>  
  
|<span data-ttu-id="839a8-249">Metoda</span><span class="sxs-lookup"><span data-stu-id="839a8-249">Method</span></span>|<span data-ttu-id="839a8-250">GetExpectedParticles</span><span class="sxs-lookup"><span data-stu-id="839a8-250">GetExpectedParticles</span></span>|<span data-ttu-id="839a8-251">GetExpectedAttributes</span><span class="sxs-lookup"><span data-stu-id="839a8-251">GetExpectedAttributes</span></span>|<span data-ttu-id="839a8-252">AddSchema</span><span class="sxs-lookup"><span data-stu-id="839a8-252">AddSchema</span></span>|  
|------------|--------------------------|---------------------------|---------------|  
|<xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A>|<span data-ttu-id="839a8-253">Jeśli wartość domyślna <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> metoda jest wywoływana, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> zwraca tablicę zawierającą wszystkie elementy globalne.</span><span class="sxs-lookup"><span data-stu-id="839a8-253">If the default <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> method is called, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> returns an array containing all global elements.</span></span><br /><br /> <span data-ttu-id="839a8-254">Jeśli przeciążone <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> metody, która przyjmuje <xref:System.Xml.Schema.XmlSchemaObject> jako parametru jest wywoływana, aby zainicjować częściowej weryfikacji elementu <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> zwraca tylko element, do którego <xref:System.Xml.Schema.XmlSchemaValidator> obiekt został zainicjowany.</span><span class="sxs-lookup"><span data-stu-id="839a8-254">If the overloaded <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> method that takes an <xref:System.Xml.Schema.XmlSchemaObject> as a parameter is called to initialize partial validation of an element, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> returns only the element to which the <xref:System.Xml.Schema.XmlSchemaValidator> object was initialized.</span></span>|<span data-ttu-id="839a8-255">Jeśli wartość domyślna <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> metoda jest wywoływana, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> zwraca pustą tablicę.</span><span class="sxs-lookup"><span data-stu-id="839a8-255">If the default <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> method is called, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> returns an empty array.</span></span><br /><br /> <span data-ttu-id="839a8-256">Jeśli przeciążenia <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> metody, która przyjmuje <xref:System.Xml.Schema.XmlSchemaObject> jako parametru jest wywoływana, aby zainicjować częściowej weryfikacji atrybutu <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> zwraca tylko atrybut, do którego <xref:System.Xml.Schema.XmlSchemaValidator> obiekt został zainicjowany.</span><span class="sxs-lookup"><span data-stu-id="839a8-256">If the overload of the <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> method that takes an <xref:System.Xml.Schema.XmlSchemaObject> as a parameter is called to initialize partial validation of an attribute, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> returns only the attribute to which the <xref:System.Xml.Schema.XmlSchemaValidator> object was initialized.</span></span>|<span data-ttu-id="839a8-257">Dodaje schematu do <xref:System.Xml.Schema.XmlSchemaSet> z <xref:System.Xml.Schema.XmlSchemaValidator> obiektu, jeśli nie ma żadnych błędów przetwarzania wstępnego.</span><span class="sxs-lookup"><span data-stu-id="839a8-257">Adds the schema to the <xref:System.Xml.Schema.XmlSchemaSet> of the <xref:System.Xml.Schema.XmlSchemaValidator> object if it has no preprocessing errors.</span></span>|  
|<xref:System.Xml.Schema.XmlSchemaValidator.ValidateElement%2A>|<span data-ttu-id="839a8-258">Jeśli element kontekstu jest prawidłowy, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> zwraca sekwencję elementów oczekiwanych jako elementy podrzędne elementu kontekstu.</span><span class="sxs-lookup"><span data-stu-id="839a8-258">If the context element is valid, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> returns the sequence of elements expected as children of the context element.</span></span><br /><br /> <span data-ttu-id="839a8-259">Jeśli element kontekstu jest nieprawidłowy, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> zwraca pustą tablicę.</span><span class="sxs-lookup"><span data-stu-id="839a8-259">If the context element is invalid, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> returns an empty array.</span></span>|<span data-ttu-id="839a8-260">Jeśli element kontekstu jest prawidłowy, a nie wywołanie <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A> zostało wcześniej ustanowione, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> zwraca listę wszystkich atrybutów, które są zdefiniowane w elemencie kontekstu.</span><span class="sxs-lookup"><span data-stu-id="839a8-260">If the context element is valid, and if no call to <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A> has been previously made, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> returns a list of all the attributes defined on the context element.</span></span><br /><br /> <span data-ttu-id="839a8-261">Jeśli niektóre atrybuty zostały już zweryfikowane, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> zwraca listę pozostałe atrybuty, które ma zostać zweryfikowana.</span><span class="sxs-lookup"><span data-stu-id="839a8-261">If some attributes have already been validated, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> returns a list of the remaining attributes to be validated.</span></span><br /><br /> <span data-ttu-id="839a8-262">Jeśli element kontekstu jest nieprawidłowy, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> zwraca pustą tablicę.</span><span class="sxs-lookup"><span data-stu-id="839a8-262">If the context element is invalid, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> returns an empty array.</span></span>|<span data-ttu-id="839a8-263">Wartość taka sama jak powyżej.</span><span class="sxs-lookup"><span data-stu-id="839a8-263">Same as above.</span></span>|  
|<xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A>|<span data-ttu-id="839a8-264">Jeśli atrybut kontekstu jest atrybutem najwyższego poziomu <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> zwraca pustą tablicę.</span><span class="sxs-lookup"><span data-stu-id="839a8-264">If the context attribute is a top-level attribute, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> returns an empty array.</span></span><br /><br /> <span data-ttu-id="839a8-265">W przeciwnym razie <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> zwraca sekwencję elementów oczekiwano jako pierwszy element podrzędny elementu kontekstu.</span><span class="sxs-lookup"><span data-stu-id="839a8-265">Otherwise <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> returns the sequence of elements expected as the first child of the context element.</span></span>|<span data-ttu-id="839a8-266">Jeśli atrybut kontekstu jest atrybutem najwyższego poziomu <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> zwraca pustą tablicę.</span><span class="sxs-lookup"><span data-stu-id="839a8-266">If the context attribute is a top-level attribute, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> returns an empty array.</span></span><br /><br /> <span data-ttu-id="839a8-267">W przeciwnym razie <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> zwraca listę wszystkich pozostałych atrybutów, które mają być weryfikowane.</span><span class="sxs-lookup"><span data-stu-id="839a8-267">Otherwise <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> returns the list of remaining attributes to be validated.</span></span>|<span data-ttu-id="839a8-268">Wartość taka sama jak powyżej.</span><span class="sxs-lookup"><span data-stu-id="839a8-268">Same as above.</span></span>|  
|<xref:System.Xml.Schema.XmlSchemaValidator.GetUnspecifiedDefaultAttributes%2A>|<span data-ttu-id="839a8-269"><xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> Zwraca sekwencję elementów oczekiwano jako pierwszy element podrzędny elementu kontekstu.</span><span class="sxs-lookup"><span data-stu-id="839a8-269"><xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> returns the sequence of elements expected as the first child of the context element.</span></span>|<span data-ttu-id="839a8-270"><xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> Zwraca listę wymaganych i opcjonalnych atrybutów, które są jeszcze zostanie wykonane sprawdzanie poprawności elementu kontekstu.</span><span class="sxs-lookup"><span data-stu-id="839a8-270"><xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> returns a list of the required and optional attributes that are yet to be validated for the context element.</span></span>|<span data-ttu-id="839a8-271">Wartość taka sama jak powyżej.</span><span class="sxs-lookup"><span data-stu-id="839a8-271">Same as above.</span></span>|  
|<xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndOfAttributes%2A>|<span data-ttu-id="839a8-272"><xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> Zwraca sekwencję elementów oczekiwano jako pierwszy element podrzędny elementu kontekstu.</span><span class="sxs-lookup"><span data-stu-id="839a8-272"><xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> returns the sequence of elements expected as the first child of the context element.</span></span>|<span data-ttu-id="839a8-273"><xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> Zwraca pustą tablicę.</span><span class="sxs-lookup"><span data-stu-id="839a8-273"><xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> returns an empty array.</span></span>|<span data-ttu-id="839a8-274">Wartość taka sama jak powyżej.</span><span class="sxs-lookup"><span data-stu-id="839a8-274">Same as above.</span></span>|  
|<xref:System.Xml.Schema.XmlSchemaValidator.ValidateText%2A>|<span data-ttu-id="839a8-275">Jeśli typ zawartości elementu kontekstu jest mieszany, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> zwraca sekwencję elementów oczekiwanych pozycji dalej.</span><span class="sxs-lookup"><span data-stu-id="839a8-275">If the context element's contentType is Mixed, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> returns the sequence of elements expected in the next position.</span></span><br /><br /> <span data-ttu-id="839a8-276">Jeśli typ zawartości elementu kontekstu jest TextOnly lub jest pusta, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> zwraca pustą tablicę.</span><span class="sxs-lookup"><span data-stu-id="839a8-276">If the context element's contentType is TextOnly or Empty, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> returns an empty array.</span></span><br /><br /> <span data-ttu-id="839a8-277">Jeśli typ zawartości elementu kontekstu jest ElementOnly, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> zwraca sekwencję elementów w pozycji dalej, ale błąd sprawdzania poprawności już wystąpił.</span><span class="sxs-lookup"><span data-stu-id="839a8-277">If the context element's contentType is ElementOnly, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> returns the sequence of elements expected in the next position but a validation error has already occurred.</span></span>|<span data-ttu-id="839a8-278"><xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> Zwraca listę atrybutów, które nie są weryfikowane elementu kontekstu.</span><span class="sxs-lookup"><span data-stu-id="839a8-278"><xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> returns the context element's list of attributes not validated.</span></span>|<span data-ttu-id="839a8-279">Wartość taka sama jak powyżej.</span><span class="sxs-lookup"><span data-stu-id="839a8-279">Same as above.</span></span>|  
|<xref:System.Xml.Schema.XmlSchemaValidator.ValidateWhitespace%2A>|<span data-ttu-id="839a8-280">Jeśli kontekst-biały znak jest najwyższego poziomu odstępu <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> zwraca pustą tablicę.</span><span class="sxs-lookup"><span data-stu-id="839a8-280">If the context white-space is top-level white-space, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> returns an empty array.</span></span><br /><br /> <span data-ttu-id="839a8-281">W przeciwnym razie <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> zachowanie metody jest taka sama, jak w <xref:System.Xml.Schema.XmlSchemaValidator.ValidateText%2A>.</span><span class="sxs-lookup"><span data-stu-id="839a8-281">Otherwise the <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> method's behavior is the same as in <xref:System.Xml.Schema.XmlSchemaValidator.ValidateText%2A>.</span></span>|<span data-ttu-id="839a8-282">Jeśli kontekst-biały znak jest najwyższego poziomu odstępu <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> zwraca pustą tablicę.</span><span class="sxs-lookup"><span data-stu-id="839a8-282">If the context white-space is top-level white-space, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> returns an empty array.</span></span><br /><br /> <span data-ttu-id="839a8-283">W przeciwnym razie <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> zachowanie metody jest taka sama, jak w <xref:System.Xml.Schema.XmlSchemaValidator.ValidateText%2A>.</span><span class="sxs-lookup"><span data-stu-id="839a8-283">Otherwise the <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> method's behavior is the same as in <xref:System.Xml.Schema.XmlSchemaValidator.ValidateText%2A>.</span></span>|<span data-ttu-id="839a8-284">Wartość taka sama jak powyżej.</span><span class="sxs-lookup"><span data-stu-id="839a8-284">Same as above.</span></span>|  
|<xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndElement%2A>|<span data-ttu-id="839a8-285"><xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> Zwraca sekwencję elementów oczekiwanych po elemencie kontekstu (możliwe elementów równorzędnych).</span><span class="sxs-lookup"><span data-stu-id="839a8-285"><xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> returns the sequence of elements expected after the context element (possible siblings).</span></span>|<span data-ttu-id="839a8-286"><xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> Zwraca listę atrybutów, które nie są weryfikowane elementu kontekstu.</span><span class="sxs-lookup"><span data-stu-id="839a8-286"><xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> returns the context element's list of attributes not validated.</span></span><br /><br /> <span data-ttu-id="839a8-287">Jeśli element kontekstu nie ma elementu nadrzędnego następnie <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> zwraca pustą listę (element kontekstu jest elementem nadrzędnym bieżącego elementu, na którym <xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndElement%2A> wywołano).</span><span class="sxs-lookup"><span data-stu-id="839a8-287">If the context element has no parent then <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> returns an empty list (the context element is the parent of the current element on which <xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndElement%2A> was called).</span></span>|<span data-ttu-id="839a8-288">Wartość taka sama jak powyżej.</span><span class="sxs-lookup"><span data-stu-id="839a8-288">Same as above.</span></span>|  
|<xref:System.Xml.Schema.XmlSchemaValidator.SkipToEndElement%2A>|<span data-ttu-id="839a8-289">Taki sam jak <xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndElement%2A>.</span><span class="sxs-lookup"><span data-stu-id="839a8-289">Same as <xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndElement%2A>.</span></span>|<span data-ttu-id="839a8-290">Taki sam jak <xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndElement%2A>.</span><span class="sxs-lookup"><span data-stu-id="839a8-290">Same as <xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndElement%2A>.</span></span>|<span data-ttu-id="839a8-291">Wartość taka sama jak powyżej.</span><span class="sxs-lookup"><span data-stu-id="839a8-291">Same as above.</span></span>|  
|<xref:System.Xml.Schema.XmlSchemaValidator.EndValidation%2A>|<span data-ttu-id="839a8-292">Zwraca pustą tablicę.</span><span class="sxs-lookup"><span data-stu-id="839a8-292">Returns an empty array.</span></span>|<span data-ttu-id="839a8-293">Zwraca pustą tablicę.</span><span class="sxs-lookup"><span data-stu-id="839a8-293">Returns an empty array.</span></span>|<span data-ttu-id="839a8-294">Wartość taka sama jak powyżej.</span><span class="sxs-lookup"><span data-stu-id="839a8-294">Same as above.</span></span>|  
  
> [!NOTE]
>  <span data-ttu-id="839a8-295">Wartości zwracane przez różne właściwości <xref:System.Xml.Schema.XmlSchemaValidator> klasy nie są modyfikowane przez wywołanie jednej z metod w powyższej tabeli.</span><span class="sxs-lookup"><span data-stu-id="839a8-295">The values returned by the various properties of the <xref:System.Xml.Schema.XmlSchemaValidator> class are not altered by calling any of the methods in the above table.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="839a8-296">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="839a8-296">See also</span></span>

- <xref:System.Xml.Schema.XmlSchemaValidator>
