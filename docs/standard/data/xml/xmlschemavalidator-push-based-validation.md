---
title: Weryfikacja oparta na wypchnięciach przy użyciu klasy XmlSchemaValidator
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 911d4460-dd91-4958-85b2-2ca3299f9ec6
ms.openlocfilehash: 6a0cc110c2b8bcd97b9f5c16a344db5a63046353
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75709806"
---
# <a name="xmlschemavalidator-push-based-validation"></a><span data-ttu-id="674f3-102">Weryfikacja oparta na wypchnięciach przy użyciu klasy XmlSchemaValidator</span><span class="sxs-lookup"><span data-stu-id="674f3-102">XmlSchemaValidator Push-Based Validation</span></span>

<span data-ttu-id="674f3-103"><xref:System.Xml.Schema.XmlSchemaValidator> Klasa zapewnia wydajny mechanizm o wysokiej wydajności służący do sprawdzania poprawności danych XML w schematach XML w sposób oparty na wypychaniu.</span><span class="sxs-lookup"><span data-stu-id="674f3-103">The <xref:System.Xml.Schema.XmlSchemaValidator> class provides an efficient, high-performance mechanism to validate XML data against XML schemas in a push-based manner.</span></span> <span data-ttu-id="674f3-104">Na przykład <xref:System.Xml.Schema.XmlSchemaValidator> Klasa pozwala na sprawdzenie poprawności sprawdzonych XML, bez konieczności serializacji go jako dokumentu XML, a następnie ponowne przeanalizowanie dokumentu przy użyciu walidacji kodu XML.</span><span class="sxs-lookup"><span data-stu-id="674f3-104">For example, the <xref:System.Xml.Schema.XmlSchemaValidator> class allows you to validate an XML infoset in-place without having to serialize it as an XML document and then reparse the document using a validating XML reader.</span></span>

<span data-ttu-id="674f3-105"><xref:System.Xml.Schema.XmlSchemaValidator> Klasa może być używana w zaawansowanych scenariuszach, takich jak tworzenie aparatów walidacji w niestandardowych źródłach danych XML lub sposób tworzenia walidacji składnika zapisywania XML.</span><span class="sxs-lookup"><span data-stu-id="674f3-105">The <xref:System.Xml.Schema.XmlSchemaValidator> class can be used in advanced scenarios such as building validation engines over custom XML data sources or as a way to build a validating XML writer.</span></span>

<span data-ttu-id="674f3-106">Poniżej przedstawiono przykład użycia <xref:System.Xml.Schema.XmlSchemaValidator> klasy do walidacji `contosoBooks.xml` pliku względem `contosoBooks.xsd` schematu.</span><span class="sxs-lookup"><span data-stu-id="674f3-106">The following is an example of using the <xref:System.Xml.Schema.XmlSchemaValidator> class to validate the `contosoBooks.xml` file against the `contosoBooks.xsd` schema.</span></span> <span data-ttu-id="674f3-107">W przykładzie używa <xref:System.Xml.Serialization.XmlSerializer> klasy do deserializacji `contosoBooks.xml` pliku i przekazywania wartości węzłów do metod <xref:System.Xml.Schema.XmlSchemaValidator> klasy.</span><span class="sxs-lookup"><span data-stu-id="674f3-107">The example uses the <xref:System.Xml.Serialization.XmlSerializer> class to deserialize the `contosoBooks.xml` file and pass the value of the nodes to the methods of the <xref:System.Xml.Schema.XmlSchemaValidator> class.</span></span>

> [!NOTE]
> <span data-ttu-id="674f3-108">Ten przykład jest używany w części tego tematu.</span><span class="sxs-lookup"><span data-stu-id="674f3-108">This example is used throughout the sections of this topic.</span></span>

[!code-csharp[XmlSchemaValidatorExamples#1](../../../../samples/snippets/csharp/VS_Snippets_Data/XmlSchemaValidatorExamples/CS/XmlSchemaValidatorExamples.cs#1)]
[!code-vb[XmlSchemaValidatorExamples#1](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XmlSchemaValidatorExamples/VB/XmlSchemaValidatorExamples.vb#1)]

<span data-ttu-id="674f3-109">Przykład pobiera `contosoBooks.xml` plik jako dane wejściowe.</span><span class="sxs-lookup"><span data-stu-id="674f3-109">The example takes the `contosoBooks.xml` file as input.</span></span>

[!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]

<span data-ttu-id="674f3-110">Przykład pobiera również `contosoBooks.xsd` jako dane wejściowe.</span><span class="sxs-lookup"><span data-stu-id="674f3-110">The example also takes the `contosoBooks.xsd` as an input.</span></span>

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

## <a name="validating-xml-data-using-xmlschemavalidator"></a><span data-ttu-id="674f3-111">Walidacja danych XML przy użyciu XmlSchemaValidator</span><span class="sxs-lookup"><span data-stu-id="674f3-111">Validating XML Data using XmlSchemaValidator</span></span>

<span data-ttu-id="674f3-112">Aby rozpocząć walidację sprawdzonych XML, należy najpierw zainicjować nowe wystąpienie <xref:System.Xml.Schema.XmlSchemaValidator> klasy przy użyciu <xref:System.Xml.Schema.XmlSchemaValidator.%23ctor%2A> konstruktora.</span><span class="sxs-lookup"><span data-stu-id="674f3-112">To begin validating an XML infoset, you must first initialize a new instance of the <xref:System.Xml.Schema.XmlSchemaValidator> class using the <xref:System.Xml.Schema.XmlSchemaValidator.%23ctor%2A> constructor.</span></span>

<span data-ttu-id="674f3-113"><xref:System.Xml.Schema.XmlSchemaValidator.%23ctor%2A> Konstruktor przyjmuje <xref:System.Xml.XmlNameTable>, <xref:System.Xml.Schema.XmlSchemaSet>, i obiekty <xref:System.Xml.XmlNamespaceManager> jako parametry, a także <xref:System.Xml.Schema.XmlSchemaValidationFlags> wartość jako parametr.</span><span class="sxs-lookup"><span data-stu-id="674f3-113">The <xref:System.Xml.Schema.XmlSchemaValidator.%23ctor%2A> constructor takes <xref:System.Xml.XmlNameTable>, <xref:System.Xml.Schema.XmlSchemaSet>, and <xref:System.Xml.XmlNamespaceManager> objects as parameters as well as a <xref:System.Xml.Schema.XmlSchemaValidationFlags> value as a parameter.</span></span> <span data-ttu-id="674f3-114"><xref:System.Xml.XmlNameTable> Obiekt jest używany do wyodrębnić dobrze znanych ciągów przestrzeni nazw, takich jak przestrzeń nazw schematu, przestrzeń nazw XML i tak dalej, i jest przenoszona do <xref:System.Xml.Schema.XmlSchemaDatatype.ParseValue%2A> metody podczas walidacji zawartości prostej.</span><span class="sxs-lookup"><span data-stu-id="674f3-114">The <xref:System.Xml.XmlNameTable> object is used to atomize well-known namespace strings like the schema namespace, the XML namespace, and so on, and is passed to the <xref:System.Xml.Schema.XmlSchemaDatatype.ParseValue%2A> method while validating simple content.</span></span> <span data-ttu-id="674f3-115"><xref:System.Xml.Schema.XmlSchemaSet> Obiekt zawiera schematy XML używane do sprawdzania poprawności sprawdzonych XML.</span><span class="sxs-lookup"><span data-stu-id="674f3-115">The <xref:System.Xml.Schema.XmlSchemaSet> object contains the XML schemas used to validate the XML infoset.</span></span> <span data-ttu-id="674f3-116"><xref:System.Xml.XmlNamespaceManager> Obiekt jest używany do rozpoznawania przestrzeni nazw napotkanych podczas walidacji.</span><span class="sxs-lookup"><span data-stu-id="674f3-116">The <xref:System.Xml.XmlNamespaceManager> object is used to resolve namespaces encountered during validation.</span></span> <span data-ttu-id="674f3-117">Ta <xref:System.Xml.Schema.XmlSchemaValidationFlags> wartość służy do wyłączania niektórych funkcji weryfikacji.</span><span class="sxs-lookup"><span data-stu-id="674f3-117">The <xref:System.Xml.Schema.XmlSchemaValidationFlags> value is used to disable certain features of validation.</span></span>

<span data-ttu-id="674f3-118">Aby uzyskać więcej informacji na <xref:System.Xml.Schema.XmlSchemaValidator.%23ctor%2A> temat konstruktora, zobacz <xref:System.Xml.Schema.XmlSchemaValidator> dokumentację referencyjną klasy.</span><span class="sxs-lookup"><span data-stu-id="674f3-118">For more information about the <xref:System.Xml.Schema.XmlSchemaValidator.%23ctor%2A> constructor, see the <xref:System.Xml.Schema.XmlSchemaValidator> class reference documentation.</span></span>

### <a name="initializing-validation"></a><span data-ttu-id="674f3-119">Inicjowanie walidacji</span><span class="sxs-lookup"><span data-stu-id="674f3-119">Initializing Validation</span></span>

<span data-ttu-id="674f3-120">Po skonstruowaniu <xref:System.Xml.Schema.XmlSchemaValidator> obiektu istnieją dwie przeciążone <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> metody służące do zainicjowania stanu <xref:System.Xml.Schema.XmlSchemaValidator> obiektu.</span><span class="sxs-lookup"><span data-stu-id="674f3-120">After an <xref:System.Xml.Schema.XmlSchemaValidator> object has been constructed, there are two overloaded <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> methods used to initialize the state of the <xref:System.Xml.Schema.XmlSchemaValidator> object.</span></span> <span data-ttu-id="674f3-121">Poniżej przedstawiono dwie <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="674f3-121">The following are the two <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> methods.</span></span>

- <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A?displayProperty=nameWithType>

- <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A?displayProperty=nameWithType>

<span data-ttu-id="674f3-122">Metoda Domyślna <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A?displayProperty=nameWithType> inicjuje <xref:System.Xml.Schema.XmlSchemaValidator> obiekt do jego stanu początkowego, a <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A?displayProperty=nameWithType> przeciążona metoda, która przyjmuje <xref:System.Xml.Schema.XmlSchemaObject> jako parametr inicjuje <xref:System.Xml.Schema.XmlSchemaValidator> obiekt do stanu początkowego dla częściowej walidacji.</span><span class="sxs-lookup"><span data-stu-id="674f3-122">The default <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A?displayProperty=nameWithType> method initializes an <xref:System.Xml.Schema.XmlSchemaValidator> object to its starting state, and the overloaded <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A?displayProperty=nameWithType> method that takes an <xref:System.Xml.Schema.XmlSchemaObject> as a parameter initializes an <xref:System.Xml.Schema.XmlSchemaValidator> object to its starting state for partial validation.</span></span>

<span data-ttu-id="674f3-123">Obie <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> metody można wywołać tylko natychmiast po skonstruowaniu <xref:System.Xml.Schema.XmlSchemaValidator> obiektu lub po wywołaniu metody <xref:System.Xml.Schema.XmlSchemaValidator.EndValidation%2A>.</span><span class="sxs-lookup"><span data-stu-id="674f3-123">Both <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> methods can only be called immediately after an <xref:System.Xml.Schema.XmlSchemaValidator> object has been constructed or after a call to <xref:System.Xml.Schema.XmlSchemaValidator.EndValidation%2A>.</span></span>

<span data-ttu-id="674f3-124">Aby zapoznać się z przykładem <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A?displayProperty=nameWithType> metody, zobacz przykład we wprowadzeniu.</span><span class="sxs-lookup"><span data-stu-id="674f3-124">For an example of the <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A?displayProperty=nameWithType> method, see the example in the introduction.</span></span> <span data-ttu-id="674f3-125">Aby uzyskać więcej informacji na <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> temat metody, zobacz <xref:System.Xml.Schema.XmlSchemaValidator> dokumentację dotyczącą klasy.</span><span class="sxs-lookup"><span data-stu-id="674f3-125">For more information about the <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> method, see the <xref:System.Xml.Schema.XmlSchemaValidator> class reference documentation.</span></span>

#### <a name="partial-validation"></a><span data-ttu-id="674f3-126">Częściowe sprawdzanie poprawności</span><span class="sxs-lookup"><span data-stu-id="674f3-126">Partial Validation</span></span>

<span data-ttu-id="674f3-127"><xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A?displayProperty=nameWithType> Metoda, która przyjmuje <xref:System.Xml.Schema.XmlSchemaObject> jako parametr inicjuje <xref:System.Xml.Schema.XmlSchemaValidator> obiekt do stanu początkowego dla częściowej walidacji.</span><span class="sxs-lookup"><span data-stu-id="674f3-127">The <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A?displayProperty=nameWithType> method that takes an <xref:System.Xml.Schema.XmlSchemaObject> as a parameter initializes an <xref:System.Xml.Schema.XmlSchemaValidator> object to its starting state for partial validation.</span></span>

<span data-ttu-id="674f3-128">W poniższym przykładzie <xref:System.Xml.Schema.XmlSchemaObject> jest inicjowane dla częściowej walidacji przy użyciu <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="674f3-128">In the following example, an <xref:System.Xml.Schema.XmlSchemaObject> is initialized for partial validation using the <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="674f3-129">Element `orderNumber` schematu jest przesyłany przez wybranie elementu <xref:System.Xml.XmlQualifiedName> schematu w <xref:System.Xml.Schema.XmlSchemaObjectTable> kolekcji zwróconej przez <xref:System.Xml.Schema.XmlSchemaSet.GlobalElements%2A> Właściwość <xref:System.Xml.Schema.XmlSchemaSet> obiektu.</span><span class="sxs-lookup"><span data-stu-id="674f3-129">The `orderNumber` schema element is passed by selecting the schema element by <xref:System.Xml.XmlQualifiedName> in the <xref:System.Xml.Schema.XmlSchemaObjectTable> collection returned by the <xref:System.Xml.Schema.XmlSchemaSet.GlobalElements%2A> property of the <xref:System.Xml.Schema.XmlSchemaSet> object.</span></span> <span data-ttu-id="674f3-130">Następnie <xref:System.Xml.Schema.XmlSchemaValidator> obiekt sprawdza poprawność tego określonego elementu.</span><span class="sxs-lookup"><span data-stu-id="674f3-130">The <xref:System.Xml.Schema.XmlSchemaValidator> object then validates this specific element.</span></span>

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

<span data-ttu-id="674f3-131">Przykład pobiera Poniższy schemat XML jako dane wejściowe.</span><span class="sxs-lookup"><span data-stu-id="674f3-131">The example takes the following XML schema as input.</span></span>

```xml
<xs:schema xmlns:xs="http://www.w3.org/2001/XMLSchema">
  <xs:element name="orderNumber" type="xs:int" />
</xs:schema>
```

<span data-ttu-id="674f3-132">Aby uzyskać więcej informacji na <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> temat metody, zobacz <xref:System.Xml.Schema.XmlSchemaValidator> dokumentację dotyczącą klasy.</span><span class="sxs-lookup"><span data-stu-id="674f3-132">For more information about the <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> method, see the <xref:System.Xml.Schema.XmlSchemaValidator> class reference documentation.</span></span>

### <a name="adding-additional-schemas"></a><span data-ttu-id="674f3-133">Dodawanie dodatkowych schematów</span><span class="sxs-lookup"><span data-stu-id="674f3-133">Adding Additional Schemas</span></span>

<span data-ttu-id="674f3-134"><xref:System.Xml.Schema.XmlSchemaValidator.AddSchema%2A> Metoda <xref:System.Xml.Schema.XmlSchemaValidator> klasy służy do dodawania schematu XML do zestawu schematów używanych podczas walidacji.</span><span class="sxs-lookup"><span data-stu-id="674f3-134">The <xref:System.Xml.Schema.XmlSchemaValidator.AddSchema%2A> method of the <xref:System.Xml.Schema.XmlSchemaValidator> class is used to add an XML schema to the set of schemas used during validation.</span></span> <span data-ttu-id="674f3-135"><xref:System.Xml.Schema.XmlSchemaValidator.AddSchema%2A> Metoda może służyć do symulowania efektu napotkania wbudowanego schematu XML w sprawdzonych XML.</span><span class="sxs-lookup"><span data-stu-id="674f3-135">The <xref:System.Xml.Schema.XmlSchemaValidator.AddSchema%2A> method can be used to simulate the effect of encountering an inline XML schema in the XML infoset being validated.</span></span>

> [!NOTE]
> <span data-ttu-id="674f3-136">Docelowa przestrzeń nazw <xref:System.Xml.Schema.XmlSchema> parametru nie może być zgodna z elementem lub atrybutem już napotkanym <xref:System.Xml.Schema.XmlSchemaValidator> przez obiekt.</span><span class="sxs-lookup"><span data-stu-id="674f3-136">The target namespace of the <xref:System.Xml.Schema.XmlSchema> parameter cannot match that of any element or attribute already encountered by the <xref:System.Xml.Schema.XmlSchemaValidator> object.</span></span>
>
> <span data-ttu-id="674f3-137">Jeśli <xref:System.Xml.Schema.XmlSchemaValidationFlags.ProcessInlineSchema?displayProperty=nameWithType> wartość nie została przeniesiona jako parametr do <xref:System.Xml.Schema.XmlSchemaValidator.%23ctor%2A> konstruktora, <xref:System.Xml.Schema.XmlSchemaValidator.AddSchema%2A> Metoda nie wykonuje żadnych operacji.</span><span class="sxs-lookup"><span data-stu-id="674f3-137">If the <xref:System.Xml.Schema.XmlSchemaValidationFlags.ProcessInlineSchema?displayProperty=nameWithType> value was not passed as a parameter to the <xref:System.Xml.Schema.XmlSchemaValidator.%23ctor%2A> constructor, the <xref:System.Xml.Schema.XmlSchemaValidator.AddSchema%2A> method does nothing.</span></span>

<span data-ttu-id="674f3-138">Wynik <xref:System.Xml.Schema.XmlSchemaValidator.AddSchema%2A> metody jest zależny od bieżącego kontekstu węzła XML, który jest sprawdzany.</span><span class="sxs-lookup"><span data-stu-id="674f3-138">The result of the <xref:System.Xml.Schema.XmlSchemaValidator.AddSchema%2A> method is dependant on the current XML node context being validated.</span></span> <span data-ttu-id="674f3-139">Aby uzyskać więcej informacji na temat kontekstów walidacji, zobacz sekcję "kontekst walidacji" w tym temacie.</span><span class="sxs-lookup"><span data-stu-id="674f3-139">For more information about validation contexts, see the "Validation Context" section of this topic.</span></span>

<span data-ttu-id="674f3-140">Aby uzyskać więcej informacji na <xref:System.Xml.Schema.XmlSchemaValidator.AddSchema%2A> temat metody, zobacz <xref:System.Xml.Schema.XmlSchemaValidator> dokumentację dotyczącą klasy.</span><span class="sxs-lookup"><span data-stu-id="674f3-140">For more information about the <xref:System.Xml.Schema.XmlSchemaValidator.AddSchema%2A> method, see the <xref:System.Xml.Schema.XmlSchemaValidator> class reference documentation.</span></span>

### <a name="validating-elements-attributes-and-content"></a><span data-ttu-id="674f3-141">Walidacja elementów, atrybutów i zawartości</span><span class="sxs-lookup"><span data-stu-id="674f3-141">Validating Elements, Attributes, and Content</span></span>

<span data-ttu-id="674f3-142"><xref:System.Xml.Schema.XmlSchemaValidator> Klasa zawiera kilka metod służących do sprawdzania poprawności elementów, atrybutów i zawartości w sprawdzonych XML w schematach XML.</span><span class="sxs-lookup"><span data-stu-id="674f3-142">The <xref:System.Xml.Schema.XmlSchemaValidator> class provides several methods used to validate elements, attributes, and content in an XML infoset against XML schemas.</span></span> <span data-ttu-id="674f3-143">W poniższej tabeli opisano każdą z tych metod.</span><span class="sxs-lookup"><span data-stu-id="674f3-143">The following table describes each of these methods.</span></span>

|<span data-ttu-id="674f3-144">Metoda</span><span class="sxs-lookup"><span data-stu-id="674f3-144">Method</span></span>|<span data-ttu-id="674f3-145">Opis</span><span class="sxs-lookup"><span data-stu-id="674f3-145">Description</span></span>|
|------------|-----------------|
|<xref:System.Xml.Schema.XmlSchemaValidator.ValidateElement%2A>|<span data-ttu-id="674f3-146">Sprawdza poprawność nazwy elementu w bieżącym kontekście.</span><span class="sxs-lookup"><span data-stu-id="674f3-146">Validates the element name in the current context.</span></span>|
|<xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A>|<span data-ttu-id="674f3-147">Sprawdza poprawność atrybutu w bieżącym kontekście elementu lub względem <xref:System.Xml.Schema.XmlSchemaAttribute> obiektu, który przeszedł jako parametr do <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="674f3-147">Validates the attribute in the current element context or against the <xref:System.Xml.Schema.XmlSchemaAttribute> object passed as a parameter to the <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> method.</span></span>|
|<xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndOfAttributes%2A>|<span data-ttu-id="674f3-148">Sprawdza, czy wszystkie wymagane atrybuty w kontekście elementu są obecne i przygotowuje <xref:System.Xml.Schema.XmlSchemaValidator> obiekt do zweryfikowania zawartości podrzędnej elementu.</span><span class="sxs-lookup"><span data-stu-id="674f3-148">Verifies whether all the required attributes in the element context are present and prepares the <xref:System.Xml.Schema.XmlSchemaValidator> object to validate the child content of the element.</span></span>|
|<xref:System.Xml.Schema.XmlSchemaValidator.ValidateText%2A>|<span data-ttu-id="674f3-149">Sprawdza, czy tekst jest dozwolony w kontekście bieżącego elementu i gromadzi tekst do walidacji, jeśli bieżący element ma prostą zawartość.</span><span class="sxs-lookup"><span data-stu-id="674f3-149">Validates whether text is allowed in the current element context, and accumulates the text for validation if the current element has simple content.</span></span>|
|<xref:System.Xml.Schema.XmlSchemaValidator.ValidateWhitespace%2A>|<span data-ttu-id="674f3-150">Sprawdza, czy w bieżącym kontekście elementu jest dozwolone białe miejsce, i gromadzi białe miejsce do walidacji, czy bieżący element ma prostą zawartość.</span><span class="sxs-lookup"><span data-stu-id="674f3-150">Validates whether white-space is allowed in the current element context, and accumulates the white-space for validation whether the current element has simple content.</span></span>|
|<xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndElement%2A>|<span data-ttu-id="674f3-151">Sprawdza, czy zawartość tekstowa elementu jest prawidłowa przy uwzględnieniu jego typu danych dla elementów z prostą zawartością i sprawdza, czy zawartość bieżącego elementu jest kompletna dla elementów z zawartością złożoną.</span><span class="sxs-lookup"><span data-stu-id="674f3-151">Verifies whether the text content of the element is valid according to its data type for elements with simple content, and verifies whether the content of the current element is complete for elements with complex content.</span></span>|
|<xref:System.Xml.Schema.XmlSchemaValidator.SkipToEndElement%2A>|<span data-ttu-id="674f3-152">Pomija sprawdzanie poprawności zawartości bieżącego elementu i przygotowuje <xref:System.Xml.Schema.XmlSchemaValidator> obiekt do walidacji zawartości w kontekście elementu nadrzędnego.</span><span class="sxs-lookup"><span data-stu-id="674f3-152">Skips validation of the current element content and prepares the <xref:System.Xml.Schema.XmlSchemaValidator> object to validate content in the parent element's context.</span></span>|
|<xref:System.Xml.Schema.XmlSchemaValidator.EndValidation%2A>|<span data-ttu-id="674f3-153">Zakończenie sprawdzania poprawności i sprawdza ograniczenia tożsamości dla całego dokumentu XML, jeśli <xref:System.Xml.Schema.XmlSchemaValidationFlags.ProcessIdentityConstraints> opcja walidacji jest ustawiona.</span><span class="sxs-lookup"><span data-stu-id="674f3-153">Ends validation and checks identity constraints for the entire XML document if the <xref:System.Xml.Schema.XmlSchemaValidationFlags.ProcessIdentityConstraints> validation option is set.</span></span>|

> [!NOTE]
> <span data-ttu-id="674f3-154"><xref:System.Xml.Schema.XmlSchemaValidator> Klasa ma zdefiniowane przejście stanu, które wymusza sekwencję i wystąpienia wywołań wykonanych dla każdej z metod opisanych w poprzedniej tabeli.</span><span class="sxs-lookup"><span data-stu-id="674f3-154">The <xref:System.Xml.Schema.XmlSchemaValidator> class has a defined state transition that enforces the sequence and occurrence of calls made to each of the methods described in the previous table.</span></span> <span data-ttu-id="674f3-155">Przejście określonego stanu <xref:System.Xml.Schema.XmlSchemaValidator> klasy jest opisane w sekcji "przechodzenie stanu XmlSchemaValidator" w tym temacie.</span><span class="sxs-lookup"><span data-stu-id="674f3-155">The specific state transition of the <xref:System.Xml.Schema.XmlSchemaValidator> class is described in the "XmlSchemaValidator State Transition" section of this topic.</span></span>

<span data-ttu-id="674f3-156">Przykład metod używanych do sprawdzania poprawności elementów, atrybutów i zawartości w sprawdzonych XML zawiera przykład w poprzedniej sekcji.</span><span class="sxs-lookup"><span data-stu-id="674f3-156">For an example of the methods used to validate elements, attributes, and content in an XML infoset, see the example in the previous section.</span></span> <span data-ttu-id="674f3-157">Więcej informacji o tych metodach znajduje się w <xref:System.Xml.Schema.XmlSchemaValidator> dokumentacji dotyczącej klas.</span><span class="sxs-lookup"><span data-stu-id="674f3-157">For more information about these methods, see the <xref:System.Xml.Schema.XmlSchemaValidator> class reference documentation.</span></span>

#### <a name="validating-content-using-an-xmlvaluegetter"></a><span data-ttu-id="674f3-158">Sprawdzanie poprawności zawartości przy użyciu XmlValueGetter</span><span class="sxs-lookup"><span data-stu-id="674f3-158">Validating Content Using an XmlValueGetter</span></span>

<span data-ttu-id="674f3-159"><xref:System.Xml.Schema.XmlValueGetter> Może służyć do przekazywania wartości węzłów atrybutów, tekstu lub białych miejsc jako typów środowiska uruchomieniowego języka wspólnego (CLR) zgodnych z typem języka definicji schematu XML (XSD) atrybutu, tekstu lub odstępu `delegate` .</span><span class="sxs-lookup"><span data-stu-id="674f3-159">The <xref:System.Xml.Schema.XmlValueGetter>`delegate` can be used to pass the value of attribute, text, or white-space nodes as a Common Language Runtime (CLR) types compatible with the XML Schema Definition Language (XSD) type of the attribute, text, or white-space node.</span></span> <span data-ttu-id="674f3-160"><xref:System.Xml.Schema.XmlValueGetter> Jest przydatny, jeśli wartość CLR atrybutu, tekstu lub pustego węzła jest już dostępna, i unika kosztu konwertowania go na `string` a następnie ponowne przeanalizowanie w celu `delegate` weryfikacji.</span><span class="sxs-lookup"><span data-stu-id="674f3-160">An <xref:System.Xml.Schema.XmlValueGetter>`delegate` is useful if the CLR value of an attribute, text, or white-space node is already available, and avoids the cost of converting it to a `string` and then reparsing it again for validation.</span></span>

<span data-ttu-id="674f3-161">Metody <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A>, <xref:System.Xml.Schema.XmlSchemaValidator.ValidateText%2A>, i <xref:System.Xml.Schema.XmlSchemaValidator.ValidateWhitespace%2A> są przeciążone i akceptują wartość atrybutu, tekst lub węzły białych miejsc jako `string` lub. <xref:System.Xml.Schema.XmlValueGetter> `delegate`</span><span class="sxs-lookup"><span data-stu-id="674f3-161">The <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A>, <xref:System.Xml.Schema.XmlSchemaValidator.ValidateText%2A>, and <xref:System.Xml.Schema.XmlSchemaValidator.ValidateWhitespace%2A> methods are overloaded and accept the value of attribute, text, or white-space nodes as a `string` or <xref:System.Xml.Schema.XmlValueGetter>`delegate`.</span></span>

<span data-ttu-id="674f3-162">Następujące metody <xref:System.Xml.Schema.XmlSchemaValidator> klasy akceptują <xref:System.Xml.Schema.XmlValueGetter> `delegate` jako parametr.</span><span class="sxs-lookup"><span data-stu-id="674f3-162">The following methods of the <xref:System.Xml.Schema.XmlSchemaValidator> class accept an <xref:System.Xml.Schema.XmlValueGetter>`delegate` as a parameter.</span></span>

- <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A>

- <xref:System.Xml.Schema.XmlSchemaValidator.ValidateText%2A>

- <xref:System.Xml.Schema.XmlSchemaValidator.ValidateWhitespace%2A>

<span data-ttu-id="674f3-163">Poniżej przedstawiono przykład <xref:System.Xml.Schema.XmlValueGetter> `delegate` pochodzący z przykładu <xref:System.Xml.Schema.XmlSchemaValidator> klasy we wprowadzeniu.</span><span class="sxs-lookup"><span data-stu-id="674f3-163">The following is an example <xref:System.Xml.Schema.XmlValueGetter>`delegate` taken from the <xref:System.Xml.Schema.XmlSchemaValidator> class example in the introduction.</span></span> <span data-ttu-id="674f3-164">Zwraca wartość atrybutu jako <xref:System.DateTime> obiekt. <xref:System.Xml.Schema.XmlValueGetter> `delegate`</span><span class="sxs-lookup"><span data-stu-id="674f3-164">The <xref:System.Xml.Schema.XmlValueGetter>`delegate` returns the value of an attribute as a <xref:System.DateTime> object.</span></span> <span data-ttu-id="674f3-165">Aby sprawdzić poprawność tego <xref:System.DateTime> obiektu <xref:System.Xml.Schema.XmlValueGetter>zwróconego <xref:System.Xml.Schema.XmlSchemaValidator> przez, obiekt najpierw konwertuje go na element ValueType (ValueType jest domyślnym mapowaniem CLR dla typu XSD) dla typu danych atrybutu, a następnie sprawdza aspekty w skonwertowanej wartości.</span><span class="sxs-lookup"><span data-stu-id="674f3-165">To validate this <xref:System.DateTime> object returned by the <xref:System.Xml.Schema.XmlValueGetter>, the <xref:System.Xml.Schema.XmlSchemaValidator> object first converts it to the ValueType (ValueType is the default CLR mapping for the XSD type) for the data type of the attribute and then checks facets on the converted value.</span></span>

```vb
Shared dateTimeGetterContent As Object

Shared Function DateTimeGetterHandle() As Object
    Return dateTimeGetterContent
End Function

Shared Function DateTimeGetter(dateTime As DateTime) As XmlValueGetter
    dateTimeGetterContent = dateTime
    Return New XmlValueGetter(AddressOf DateTimeGetterHandle)
End Function
```

```csharp
static object dateTimeGetterContent;

static object DateTimeGetterHandle()
{
    return dateTimeGetterContent;
}

static XmlValueGetter DateTimeGetter(DateTime dateTime)
{
    dateTimeGetterContent = dateTime;
    return new XmlValueGetter(dateTimeGetterHandle);
}
```

<span data-ttu-id="674f3-166">Pełny przykład <xref:System.Xml.Schema.XmlValueGetter> `delegate`można znaleźć w przykładowym wprowadzeniu.</span><span class="sxs-lookup"><span data-stu-id="674f3-166">For a complete example of the <xref:System.Xml.Schema.XmlValueGetter>`delegate`, see the example in the introduction.</span></span> <span data-ttu-id="674f3-167">Aby uzyskać więcej informacji na <xref:System.Xml.Schema.XmlValueGetter> `delegate`temat, zobacz <xref:System.Xml.Schema.XmlValueGetter>dokumentację dotyczącą i <xref:System.Xml.Schema.XmlSchemaValidator> dokumentacja klasy.</span><span class="sxs-lookup"><span data-stu-id="674f3-167">For more information about the <xref:System.Xml.Schema.XmlValueGetter>`delegate`, see the <xref:System.Xml.Schema.XmlValueGetter>, and <xref:System.Xml.Schema.XmlSchemaValidator> class reference documentation.</span></span>

#### <a name="post-schema-validation-information"></a><span data-ttu-id="674f3-168">Po zaweryfikacji schematu — informacje</span><span class="sxs-lookup"><span data-stu-id="674f3-168">Post-Schema-Validation-Information</span></span>

<span data-ttu-id="674f3-169"><xref:System.Xml.Schema.XmlSchemaInfo> Klasa reprezentuje niektóre z podanych po schemacie walidacji węzła XML zweryfikowanego przez <xref:System.Xml.Schema.XmlSchemaValidator> klasę.</span><span class="sxs-lookup"><span data-stu-id="674f3-169">The <xref:System.Xml.Schema.XmlSchemaInfo> class represents some of the Post-Schema-Validation-Information of an XML node validated by the <xref:System.Xml.Schema.XmlSchemaValidator> class.</span></span> <span data-ttu-id="674f3-170">Różne metody <xref:System.Xml.Schema.XmlSchemaValidator> klasy akceptują <xref:System.Xml.Schema.XmlSchemaInfo> obiekt jako opcjonalny parametr (`null`). `out`</span><span class="sxs-lookup"><span data-stu-id="674f3-170">Various methods of the <xref:System.Xml.Schema.XmlSchemaValidator> class accept an <xref:System.Xml.Schema.XmlSchemaInfo> object as an optional, (`null`) `out` parameter.</span></span>

<span data-ttu-id="674f3-171">Po pomyślnej weryfikacji właściwości <xref:System.Xml.Schema.XmlSchemaInfo> obiektu są ustawiane z wynikami walidacji.</span><span class="sxs-lookup"><span data-stu-id="674f3-171">Upon successful validation, properties of the <xref:System.Xml.Schema.XmlSchemaInfo> object are set with the results of the validation.</span></span> <span data-ttu-id="674f3-172">Na przykład po pomyślnej weryfikacji atrybutu przy <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A> użyciu metody <xref:System.Xml.Schema.XmlSchemaInfo> obiekt (jeśli określony) <xref:System.Xml.Schema.XmlSchemaInfo.SchemaAttribute%2A>, <xref:System.Xml.Schema.XmlSchemaInfo.SchemaType%2A>, <xref:System.Xml.Schema.XmlSchemaInfo.MemberType%2A>, i <xref:System.Xml.Schema.XmlSchemaInfo.Validity%2A> właściwości są ustawiane z wynikami walidacji.</span><span class="sxs-lookup"><span data-stu-id="674f3-172">For example, upon successful validation of an attribute using the <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A> method, the <xref:System.Xml.Schema.XmlSchemaInfo> object's (if specified) <xref:System.Xml.Schema.XmlSchemaInfo.SchemaAttribute%2A>, <xref:System.Xml.Schema.XmlSchemaInfo.SchemaType%2A>, <xref:System.Xml.Schema.XmlSchemaInfo.MemberType%2A>, and <xref:System.Xml.Schema.XmlSchemaInfo.Validity%2A> properties are set with the results of the validation.</span></span>

<span data-ttu-id="674f3-173">Poniższe <xref:System.Xml.Schema.XmlSchemaValidator> metody klasy akceptują <xref:System.Xml.Schema.XmlSchemaInfo> obiekt jako parametr out.</span><span class="sxs-lookup"><span data-stu-id="674f3-173">The following <xref:System.Xml.Schema.XmlSchemaValidator> class methods accept an <xref:System.Xml.Schema.XmlSchemaInfo> object as an out parameter.</span></span>

- <xref:System.Xml.Schema.XmlSchemaValidator.SkipToEndElement%2A>

- <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A>

- <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A>

- <xref:System.Xml.Schema.XmlSchemaValidator.ValidateElement%2A>

- <xref:System.Xml.Schema.XmlSchemaValidator.ValidateElement%2A>

- <xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndElement%2A>

- <xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndElement%2A>

- <xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndOfAttributes%2A>

<span data-ttu-id="674f3-174">Aby zapoznać się z kompletnym <xref:System.Xml.Schema.XmlSchemaInfo> przykładem klasy, zobacz przykład we wprowadzeniu.</span><span class="sxs-lookup"><span data-stu-id="674f3-174">For a complete example of the <xref:System.Xml.Schema.XmlSchemaInfo> class, see the example in the introduction.</span></span> <span data-ttu-id="674f3-175">Więcej informacji o <xref:System.Xml.Schema.XmlSchemaInfo> klasie można znaleźć w <xref:System.Xml.Schema.XmlSchemaInfo> dokumentacji dotyczącej klas.</span><span class="sxs-lookup"><span data-stu-id="674f3-175">For more information about the <xref:System.Xml.Schema.XmlSchemaInfo> class, see the <xref:System.Xml.Schema.XmlSchemaInfo> class reference documentation.</span></span>

### <a name="retrieving-expected-particles-attributes-and-unspecified-default-attributes"></a><span data-ttu-id="674f3-176">Pobieranie oczekiwanych cząsteczek, atrybutów i nieokreślonych atrybutów domyślnych</span><span class="sxs-lookup"><span data-stu-id="674f3-176">Retrieving Expected Particles, Attributes, and Unspecified Default Attributes</span></span>

<span data-ttu-id="674f3-177"><xref:System.Xml.Schema.XmlSchemaValidator> Klasa zawiera metody <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A>, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A>i <xref:System.Xml.Schema.XmlSchemaValidator.GetUnspecifiedDefaultAttributes%2A> , aby pobrać oczekiwane cząstki, atrybuty i nieokreślone atrybuty domyślne w bieżącym kontekście walidacji.</span><span class="sxs-lookup"><span data-stu-id="674f3-177">The <xref:System.Xml.Schema.XmlSchemaValidator> class provides the <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A>, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A>, and <xref:System.Xml.Schema.XmlSchemaValidator.GetUnspecifiedDefaultAttributes%2A> methods to retrieve the expected particles, attributes, and unspecified default attributes in the current validation context.</span></span>

#### <a name="retrieving-expected-particles"></a><span data-ttu-id="674f3-178">Pobieranie oczekiwanych cząsteczek</span><span class="sxs-lookup"><span data-stu-id="674f3-178">Retrieving Expected Particles</span></span>

<span data-ttu-id="674f3-179"><xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> Metoda zwraca tablicę <xref:System.Xml.Schema.XmlSchemaParticle> obiektów zawierających oczekiwane cząstki w bieżącym kontekście elementu.</span><span class="sxs-lookup"><span data-stu-id="674f3-179">The <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> method returns an array of <xref:System.Xml.Schema.XmlSchemaParticle> objects containing the expected particles in the current element context.</span></span> <span data-ttu-id="674f3-180">Prawidłowe cząstki, które mogą być zwracane przez <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> metodę, są wystąpieniami <xref:System.Xml.Schema.XmlSchemaElement> klas <xref:System.Xml.Schema.XmlSchemaAny> i.</span><span class="sxs-lookup"><span data-stu-id="674f3-180">The valid particles that can be returned by the <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> method are instances of the <xref:System.Xml.Schema.XmlSchemaElement> and <xref:System.Xml.Schema.XmlSchemaAny> classes.</span></span>

<span data-ttu-id="674f3-181">Gdy compositor dla modelu zawartości to `xs:sequence`, zwracana jest tylko Następna cząstka w sekwencji.</span><span class="sxs-lookup"><span data-stu-id="674f3-181">When the compositor for the content model is an `xs:sequence`, only the next particle in the sequence is returned.</span></span> <span data-ttu-id="674f3-182">Jeśli compositor dla modelu zawartości to `xs:all` lub a `xs:choice`, zwracane są wszystkie prawidłowe cząstki, które mogą się pojawić w kontekście bieżącego elementu.</span><span class="sxs-lookup"><span data-stu-id="674f3-182">If the compositor for the content model is an `xs:all` or an `xs:choice`, then all valid particles that could follow in the current element context are returned.</span></span>

> [!NOTE]
> <span data-ttu-id="674f3-183">Jeśli <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> Metoda jest wywoływana natychmiast po wywołaniu <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> metody, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> Metoda zwraca wszystkie elementy globalne.</span><span class="sxs-lookup"><span data-stu-id="674f3-183">If the <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> method is called immediately after calling the <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> method, the <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> method returns all global elements.</span></span>

<span data-ttu-id="674f3-184">Na przykład, w schemacie języka definicji schematu XML (XSD) i w poniższym dokumencie XML po walidacji `book` elementu `book` element jest bieżącym kontekstem elementu.</span><span class="sxs-lookup"><span data-stu-id="674f3-184">For example, in the XML Schema Definition Language (XSD) schema and XML document that follow, after validating the `book` element, the `book` element is the current element context.</span></span> <span data-ttu-id="674f3-185"><xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> Metoda zwraca tablicę zawierającą pojedynczy <xref:System.Xml.Schema.XmlSchemaElement> obiekt reprezentujący `title` element.</span><span class="sxs-lookup"><span data-stu-id="674f3-185">The <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> method returns an array containing a single <xref:System.Xml.Schema.XmlSchemaElement> object representing the `title` element.</span></span> <span data-ttu-id="674f3-186">Gdy kontekst walidacji jest `title` elementem, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> Metoda zwraca pustą tablicę.</span><span class="sxs-lookup"><span data-stu-id="674f3-186">When the validation context is the `title` element, the <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> method returns an empty array.</span></span> <span data-ttu-id="674f3-187">Jeśli <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> Metoda jest wywoływana po sprawdzeniu `title` elementu, ale przed `description` zweryfikowaniem elementu, zwraca tablicę zawierającą pojedynczy <xref:System.Xml.Schema.XmlSchemaElement> obiekt reprezentujący `description` element.</span><span class="sxs-lookup"><span data-stu-id="674f3-187">If the <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> method is called after the `title` element has been validated but before the `description` element has been validated, it returns an array containing a single <xref:System.Xml.Schema.XmlSchemaElement> object representing the `description` element.</span></span> <span data-ttu-id="674f3-188">Jeśli <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> Metoda jest wywoływana po sprawdzeniu `description` elementu, zwraca tablicę zawierającą pojedynczy <xref:System.Xml.Schema.XmlSchemaAny> obiekt reprezentujący symbol wieloznaczny.</span><span class="sxs-lookup"><span data-stu-id="674f3-188">If the <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> method is called after the `description` element has been validated then it returns an array containing a single <xref:System.Xml.Schema.XmlSchemaAny> object representing the wildcard.</span></span>

```vb
Dim reader As XmlReader =  XmlReader.Create("input.xml")

Dim schemaSet As New XmlSchemaSet()
schemaSet.Add(Nothing, "schema.xsd")
Dim manager As New XmlNamespaceManager(reader.NameTable)

Dim validator As New XmlSchemaValidator(reader.NameTable,schemaSet,manager,XmlSchemaValidationFlags.None)
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

var schemaSet = new XmlSchemaSet();
schemaSet.Add(null, "schema.xsd");
var manager = new XmlNamespaceManager(reader.NameTable);

var validator = new XmlSchemaValidator(reader.NameTable, schemaSet, manager, XmlSchemaValidationFlags.None);
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

 <span data-ttu-id="674f3-189">Przykład pobiera następujący kod XML jako dane wejściowe:</span><span class="sxs-lookup"><span data-stu-id="674f3-189">The example takes the following XML as input:</span></span>

```xml
<xs:schema xmlns:xs="http://www.w3c.org/2001/XMLSchema">
  <xs:element name="book">
    <xs:sequence>
      <xs:element name="title" type="xs:string" />
      <xs:element name="description" type="xs:string" />
      <xs:any processContent="lax" maxOccurs="unbounded" />
    </xs:sequence>
  </xs:element>
</xs:schema>
```

<span data-ttu-id="674f3-190">Przykład pobiera następujący schemat XSD jako dane wejściowe:</span><span class="sxs-lookup"><span data-stu-id="674f3-190">The example takes the following XSD schema as input:</span></span>

```xml
<book>
  <title>My Book</title>
  <description>My Book's Description</description>
  <namespace>System.Xml.Schema</namespace>
</book>
```

> [!NOTE]
> <span data-ttu-id="674f3-191">Wyniki metod <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A>, i <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> <xref:System.Xml.Schema.XmlSchemaValidator.AddSchema%2A> <xref:System.Xml.Schema.XmlSchemaValidator> klasy są zależne od bieżącego kontekstu, który jest sprawdzany.</span><span class="sxs-lookup"><span data-stu-id="674f3-191">The results of the <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A>, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A>, and <xref:System.Xml.Schema.XmlSchemaValidator.AddSchema%2A> methods of the <xref:System.Xml.Schema.XmlSchemaValidator> class are dependent on the current context being validated.</span></span> <span data-ttu-id="674f3-192">Aby uzyskać więcej informacji, zobacz sekcję "kontekst walidacji" w tym temacie.</span><span class="sxs-lookup"><span data-stu-id="674f3-192">For more information, see the "Validation Context" section of this topic.</span></span>

<span data-ttu-id="674f3-193">Aby zapoznać się z przykładem <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> metody, zobacz przykład we wprowadzeniu.</span><span class="sxs-lookup"><span data-stu-id="674f3-193">For an example of the <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> method, see the example in the introduction.</span></span> <span data-ttu-id="674f3-194">Aby uzyskać więcej informacji na <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> temat metody, zobacz <xref:System.Xml.Schema.XmlSchemaValidator> dokumentację dotyczącą klasy.</span><span class="sxs-lookup"><span data-stu-id="674f3-194">For more information about the <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> method, see the <xref:System.Xml.Schema.XmlSchemaValidator> class reference documentation.</span></span>

#### <a name="retrieving-expected-attributes"></a><span data-ttu-id="674f3-195">Pobieranie oczekiwanych atrybutów</span><span class="sxs-lookup"><span data-stu-id="674f3-195">Retrieving Expected Attributes</span></span>

<span data-ttu-id="674f3-196"><xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> Metoda zwraca tablicę <xref:System.Xml.Schema.XmlSchemaAttribute> obiektów zawierających oczekiwane atrybuty w bieżącym kontekście elementu.</span><span class="sxs-lookup"><span data-stu-id="674f3-196">The <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> method returns an array of <xref:System.Xml.Schema.XmlSchemaAttribute> objects containing the expected attributes in the current element context.</span></span>

<span data-ttu-id="674f3-197">Na przykład w przykładzie we wprowadzeniu <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> Metoda jest używana do pobierania wszystkich atrybutów `book` elementu.</span><span class="sxs-lookup"><span data-stu-id="674f3-197">For example, in the example in the introduction, the <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> method is used to retrieve all the attributes of the `book` element.</span></span>

<span data-ttu-id="674f3-198">Jeśli wywołasz <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> metodę natychmiast po <xref:System.Xml.Schema.XmlSchemaValidator.ValidateElement%2A> metodzie, zwracane są wszystkie atrybuty, które mogą pojawić się w dokumencie XML.</span><span class="sxs-lookup"><span data-stu-id="674f3-198">If you call the <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> method immediately after the <xref:System.Xml.Schema.XmlSchemaValidator.ValidateElement%2A> method, all the attributes that could appear in the XML document are returned.</span></span> <span data-ttu-id="674f3-199">Jednak w przypadku wywołania <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> metody po jednym lub większej liczbie wywołań do <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A> metody zwracane są atrybuty, które nie zostały jeszcze zweryfikowane dla bieżącego elementu.</span><span class="sxs-lookup"><span data-stu-id="674f3-199">However, if you call the <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> method after one or more calls to the <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A> method, the attributes that have not yet been validated for the current element are returned.</span></span>

> [!NOTE]
> <span data-ttu-id="674f3-200">Wyniki metod <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A>, i <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> <xref:System.Xml.Schema.XmlSchemaValidator.AddSchema%2A> <xref:System.Xml.Schema.XmlSchemaValidator> klasy są zależne od bieżącego kontekstu, który jest sprawdzany.</span><span class="sxs-lookup"><span data-stu-id="674f3-200">The results of the <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A>, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A>, and <xref:System.Xml.Schema.XmlSchemaValidator.AddSchema%2A> methods of the <xref:System.Xml.Schema.XmlSchemaValidator> class are dependent on the current context being validated.</span></span> <span data-ttu-id="674f3-201">Aby uzyskać więcej informacji, zobacz sekcję "kontekst walidacji" w tym temacie.</span><span class="sxs-lookup"><span data-stu-id="674f3-201">For more information, see the "Validation Context" section of this topic.</span></span>

<span data-ttu-id="674f3-202">Aby zapoznać się z przykładem <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> metody, zobacz przykład we wprowadzeniu.</span><span class="sxs-lookup"><span data-stu-id="674f3-202">For an example of the <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> method, see the example in the introduction.</span></span> <span data-ttu-id="674f3-203">Aby uzyskać więcej informacji na <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> temat metody, zobacz <xref:System.Xml.Schema.XmlSchemaValidator> dokumentację dotyczącą klasy.</span><span class="sxs-lookup"><span data-stu-id="674f3-203">For more information about the <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> method, see the <xref:System.Xml.Schema.XmlSchemaValidator> class reference documentation.</span></span>

#### <a name="retrieving-unspecified-default-attributes"></a><span data-ttu-id="674f3-204">Pobieranie nieokreślonych atrybutów domyślnych</span><span class="sxs-lookup"><span data-stu-id="674f3-204">Retrieving Unspecified Default Attributes</span></span>

<span data-ttu-id="674f3-205"><xref:System.Xml.Schema.XmlSchemaValidator.GetUnspecifiedDefaultAttributes%2A> Metoda <xref:System.Collections.ArrayList> wypełnia określone z <xref:System.Xml.Schema.XmlSchemaAttribute> obiektami dla wszystkich atrybutów wartościami domyślnymi, które nie zostały wcześniej zweryfikowane przy użyciu <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A> metody w kontekście elementu.</span><span class="sxs-lookup"><span data-stu-id="674f3-205">The <xref:System.Xml.Schema.XmlSchemaValidator.GetUnspecifiedDefaultAttributes%2A> method populates the <xref:System.Collections.ArrayList> specified with <xref:System.Xml.Schema.XmlSchemaAttribute> objects for any attributes with default values that have not been previously validated using the <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A> method in the element context.</span></span> <span data-ttu-id="674f3-206"><xref:System.Xml.Schema.XmlSchemaValidator.GetUnspecifiedDefaultAttributes%2A> Metoda powinna być wywoływana po wywołaniu <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A> metody dla każdego atrybutu w kontekście elementu.</span><span class="sxs-lookup"><span data-stu-id="674f3-206">The <xref:System.Xml.Schema.XmlSchemaValidator.GetUnspecifiedDefaultAttributes%2A> method should be called after calling the <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A> method on each attribute in the element context.</span></span> <span data-ttu-id="674f3-207"><xref:System.Xml.Schema.XmlSchemaValidator.GetUnspecifiedDefaultAttributes%2A> Metoda powinna służyć do określenia, jakie atrybuty domyślne mają zostać wstawione do zweryfikowanego dokumentu XML.</span><span class="sxs-lookup"><span data-stu-id="674f3-207">The <xref:System.Xml.Schema.XmlSchemaValidator.GetUnspecifiedDefaultAttributes%2A> method should be used to determine what default attributes are to be inserted into the XML document being validated.</span></span>

<span data-ttu-id="674f3-208">Aby uzyskać więcej informacji na <xref:System.Xml.Schema.XmlSchemaValidator.GetUnspecifiedDefaultAttributes%2A> temat metody, zobacz <xref:System.Xml.Schema.XmlSchemaValidator> dokumentację dotyczącą klasy.</span><span class="sxs-lookup"><span data-stu-id="674f3-208">For more information about the <xref:System.Xml.Schema.XmlSchemaValidator.GetUnspecifiedDefaultAttributes%2A> method, see the <xref:System.Xml.Schema.XmlSchemaValidator> class reference documentation.</span></span>

### <a name="handling-schema-validation-events"></a><span data-ttu-id="674f3-209">Obsługa zdarzeń walidacji schematu</span><span class="sxs-lookup"><span data-stu-id="674f3-209">Handling Schema Validation Events</span></span>

<span data-ttu-id="674f3-210">Ostrzeżenia i błędy walidacji schematu napotkane podczas walidacji są <xref:System.Xml.Schema.XmlSchemaValidator.ValidationEventHandler> obsługiwane przez zdarzenie <xref:System.Xml.Schema.XmlSchemaValidator> klasy.</span><span class="sxs-lookup"><span data-stu-id="674f3-210">Schema validation warnings and errors encountered during validation are handled by the <xref:System.Xml.Schema.XmlSchemaValidator.ValidationEventHandler> event of the <xref:System.Xml.Schema.XmlSchemaValidator> class.</span></span>

<span data-ttu-id="674f3-211"><xref:System.Xml.Schema.XmlSeverityType> Ostrzeżenia dotyczące <xref:System.Xml.Schema.XmlSeverityType.Warning> walidacji schematu mają wartość i błędy walidacji schematu mają <xref:System.Xml.Schema.XmlSeverityType> wartość <xref:System.Xml.Schema.XmlSeverityType.Error>.</span><span class="sxs-lookup"><span data-stu-id="674f3-211">Schema validation warnings have an <xref:System.Xml.Schema.XmlSeverityType> value of <xref:System.Xml.Schema.XmlSeverityType.Warning> and schema validation errors have an <xref:System.Xml.Schema.XmlSeverityType> value of <xref:System.Xml.Schema.XmlSeverityType.Error>.</span></span> <span data-ttu-id="674f3-212">Jeśli nie <xref:System.Xml.Schema.XmlSchemaValidator.ValidationEventHandler> został przypisany, <xref:System.Xml.Schema.XmlSchemaValidationException> jest zgłaszany dla wszystkich błędów walidacji schematu z <xref:System.Xml.Schema.XmlSeverityType> wartością. <xref:System.Xml.Schema.XmlSeverityType.Error></span><span class="sxs-lookup"><span data-stu-id="674f3-212">If no <xref:System.Xml.Schema.XmlSchemaValidator.ValidationEventHandler> has been assigned, an <xref:System.Xml.Schema.XmlSchemaValidationException> is thrown for all schema validation errors with an <xref:System.Xml.Schema.XmlSeverityType> value of <xref:System.Xml.Schema.XmlSeverityType.Error>.</span></span> <span data-ttu-id="674f3-213">Nie <xref:System.Xml.Schema.XmlSchemaValidationException> jest jednak zgłaszany dla ostrzeżeń dotyczących sprawdzania poprawności schematu z <xref:System.Xml.Schema.XmlSeverityType> wartością <xref:System.Xml.Schema.XmlSeverityType.Warning>.</span><span class="sxs-lookup"><span data-stu-id="674f3-213">However, an <xref:System.Xml.Schema.XmlSchemaValidationException> is not thrown for schema validation warnings with an <xref:System.Xml.Schema.XmlSeverityType> value of <xref:System.Xml.Schema.XmlSeverityType.Warning>.</span></span>

<span data-ttu-id="674f3-214">Poniżej znajduje się przykład <xref:System.Xml.Schema.ValidationEventHandler> , który odbiera ostrzeżenia i błędy walidacji schematu, które zostały wykryte podczas walidacji schematu z przykładu we wprowadzeniu.</span><span class="sxs-lookup"><span data-stu-id="674f3-214">The following is an example of a <xref:System.Xml.Schema.ValidationEventHandler> that receives schema validation warnings and errors encountered during schema validation taken from the example in the introduction.</span></span>

```vb
Shared Sub SchemaValidationEventHandler(sender As Object, e As ValidationEventArgs)

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

<span data-ttu-id="674f3-215">Pełny przykład <xref:System.Xml.Schema.ValidationEventHandler>można znaleźć w przykładowym wprowadzeniu.</span><span class="sxs-lookup"><span data-stu-id="674f3-215">For a complete example of the <xref:System.Xml.Schema.ValidationEventHandler>, see the example in the introduction.</span></span> <span data-ttu-id="674f3-216">Więcej informacji można znaleźć w <xref:System.Xml.Schema.XmlSchemaInfo> dokumentacji dotyczącej klas.</span><span class="sxs-lookup"><span data-stu-id="674f3-216">For more information, see the <xref:System.Xml.Schema.XmlSchemaInfo> class reference documentation.</span></span>

## <a name="xmlschemavalidator-state-transition"></a><span data-ttu-id="674f3-217">XmlSchemaValidator stanu przejścia</span><span class="sxs-lookup"><span data-stu-id="674f3-217">XmlSchemaValidator State Transition</span></span>

<span data-ttu-id="674f3-218"><xref:System.Xml.Schema.XmlSchemaValidator> Klasa ma zdefiniowane przejście stanu, które wymusza sekwencję i wystąpienia wywołań wykonanych do każdej metody używanej do sprawdzania poprawności elementów, atrybutów i zawartości w sprawdzonych XML.</span><span class="sxs-lookup"><span data-stu-id="674f3-218">The <xref:System.Xml.Schema.XmlSchemaValidator> class has a defined state transition that enforces the sequence and occurrence of calls made to each of the methods used to validate elements, attributes, and content in an XML infoset.</span></span>

<span data-ttu-id="674f3-219">W poniższej tabeli opisano przechodzenie stanu <xref:System.Xml.Schema.XmlSchemaValidator> klasy oraz sekwencję i wystąpienia wywołań metod, które można wykonać w każdym stanie.</span><span class="sxs-lookup"><span data-stu-id="674f3-219">The following table describes the state transition of the <xref:System.Xml.Schema.XmlSchemaValidator> class, and the sequence and occurrence of method calls that can be made in each state.</span></span>

|<span data-ttu-id="674f3-220">Stan</span><span class="sxs-lookup"><span data-stu-id="674f3-220">State</span></span>|<span data-ttu-id="674f3-221">Transition</span><span class="sxs-lookup"><span data-stu-id="674f3-221">Transition</span></span>|
|-----------|----------------|
|<span data-ttu-id="674f3-222">Walidacja</span><span class="sxs-lookup"><span data-stu-id="674f3-222">Validate</span></span>|<span data-ttu-id="674f3-223"><xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A>(<xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A> &#124; TopLevel \*)<xref:System.Xml.Schema.XmlSchemaValidator.EndValidation%2A></span><span class="sxs-lookup"><span data-stu-id="674f3-223"><xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> (<xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A> &#124; TopLevel\*) <xref:System.Xml.Schema.XmlSchemaValidator.EndValidation%2A></span></span>|
|<span data-ttu-id="674f3-224">TopLevel</span><span class="sxs-lookup"><span data-stu-id="674f3-224">TopLevel</span></span>|<span data-ttu-id="674f3-225"><xref:System.Xml.Schema.XmlSchemaValidator.ValidateWhitespace%2A>Element <xref:System.Xml.Schema.XmlSchemaValidator.ValidateText%2A> &#124; &#124;</span><span class="sxs-lookup"><span data-stu-id="674f3-225"><xref:System.Xml.Schema.XmlSchemaValidator.ValidateWhitespace%2A> &#124; <xref:System.Xml.Schema.XmlSchemaValidator.ValidateText%2A> &#124; Element</span></span>|
|<span data-ttu-id="674f3-226">Element</span><span class="sxs-lookup"><span data-stu-id="674f3-226">Element</span></span>|<span data-ttu-id="674f3-227"><xref:System.Xml.Schema.XmlSchemaValidator.ValidateElement%2A><xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A>\* (<xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndOfAttributes%2A> Zawartość\*)?</span><span class="sxs-lookup"><span data-stu-id="674f3-227"><xref:System.Xml.Schema.XmlSchemaValidator.ValidateElement%2A> <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A>\* (<xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndOfAttributes%2A> Content\*)?</span></span> <span data-ttu-id="674f3-228"><xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndElement%2A>&#124;</span><span class="sxs-lookup"><span data-stu-id="674f3-228"><xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndElement%2A> &#124;</span></span><br /><br /> <span data-ttu-id="674f3-229"><xref:System.Xml.Schema.XmlSchemaValidator.ValidateElement%2A><xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A> &#124; \* <xref:System.Xml.Schema.XmlSchemaValidator.SkipToEndElement%2A></span><span class="sxs-lookup"><span data-stu-id="674f3-229"><xref:System.Xml.Schema.XmlSchemaValidator.ValidateElement%2A> <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A>\* <xref:System.Xml.Schema.XmlSchemaValidator.SkipToEndElement%2A> &#124;</span></span><br /><br /> <span data-ttu-id="674f3-230"><xref:System.Xml.Schema.XmlSchemaValidator.ValidateElement%2A><xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A> \* <xref:System.Xml.Schema.XmlSchemaValidator.SkipToEndElement%2A> &#124; zawartości <xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndOfAttributes%2A> \*</span><span class="sxs-lookup"><span data-stu-id="674f3-230"><xref:System.Xml.Schema.XmlSchemaValidator.ValidateElement%2A> <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A>\* <xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndOfAttributes%2A> Content\* <xref:System.Xml.Schema.XmlSchemaValidator.SkipToEndElement%2A> &#124;</span></span>|
|<span data-ttu-id="674f3-231">Zawartość</span><span class="sxs-lookup"><span data-stu-id="674f3-231">Content</span></span>|<span data-ttu-id="674f3-232"><xref:System.Xml.Schema.XmlSchemaValidator.ValidateWhitespace%2A>Element <xref:System.Xml.Schema.XmlSchemaValidator.ValidateText%2A> &#124; &#124;</span><span class="sxs-lookup"><span data-stu-id="674f3-232"><xref:System.Xml.Schema.XmlSchemaValidator.ValidateWhitespace%2A> &#124; <xref:System.Xml.Schema.XmlSchemaValidator.ValidateText%2A> &#124; Element</span></span>|

> [!NOTE]
> <span data-ttu-id="674f3-233"><xref:System.InvalidOperationException> Jest generowany przez każdą z metod w powyższej tabeli, gdy wywołanie metody jest wykonywane w niepoprawnej sekwencji zgodnie z bieżącym stanem <xref:System.Xml.Schema.XmlSchemaValidator> obiektu.</span><span class="sxs-lookup"><span data-stu-id="674f3-233">An <xref:System.InvalidOperationException> is thrown by each of the methods in the table above when the call to the method is made in the incorrect sequence according to the current state of an <xref:System.Xml.Schema.XmlSchemaValidator> object.</span></span>

<span data-ttu-id="674f3-234">W powyższej tabeli przechodzenia stanu są używane symbole interpunkcyjne do opisywania metod i innych stanów, które mogą być wywoływane dla każdego stanu <xref:System.Xml.Schema.XmlSchemaValidator> przejścia stanu klasy.</span><span class="sxs-lookup"><span data-stu-id="674f3-234">The state transition table above uses punctuation symbols to describe the methods and other states that can be called for each state of the state transition of the <xref:System.Xml.Schema.XmlSchemaValidator> class.</span></span> <span data-ttu-id="674f3-235">Używane symbole są tymi samymi symbolami, które znajdują się w dokumentacji XML Standards dla definicji typu dokumentu (DTD).</span><span class="sxs-lookup"><span data-stu-id="674f3-235">The symbols used are the same symbols found in the XML Standards reference for Document Type Definition (DTD).</span></span>

<span data-ttu-id="674f3-236">W poniższej tabeli opisano, jak symbole interpunkcji Znalezione w powyższej tabeli przejścia stanu mają wpływ na metody i inne Stany, które mogą być wywoływane dla każdego stanu w fazie <xref:System.Xml.Schema.XmlSchemaValidator> przejścia stanu klasy.</span><span class="sxs-lookup"><span data-stu-id="674f3-236">The following table describes how the punctuation symbols found in the state transition table above affect the methods and other states that can be called for each state in the state transition of the <xref:System.Xml.Schema.XmlSchemaValidator> class.</span></span>

|<span data-ttu-id="674f3-237">Symbol</span><span class="sxs-lookup"><span data-stu-id="674f3-237">Symbol</span></span>|<span data-ttu-id="674f3-238">Opis</span><span class="sxs-lookup"><span data-stu-id="674f3-238">Description</span></span>|
|------------|-----------------|
|<span data-ttu-id="674f3-239">&#124;</span><span class="sxs-lookup"><span data-stu-id="674f3-239">&#124;</span></span>|<span data-ttu-id="674f3-240">Można wywołać metodę lub stan (jeden przed paskiem lub po nim).</span><span class="sxs-lookup"><span data-stu-id="674f3-240">Either method or state (the one before the bar or the one after it) can be called.</span></span>|
|<span data-ttu-id="674f3-241">?</span><span class="sxs-lookup"><span data-stu-id="674f3-241">?</span></span>|<span data-ttu-id="674f3-242">Metoda lub stan, który poprzedza znak zapytania, jest opcjonalne, ale jeśli jest wywoływana, może być wywoływana tylko raz.</span><span class="sxs-lookup"><span data-stu-id="674f3-242">The method or state that precedes the question mark is optional but if it is called it can only be called once.</span></span>|
|*|<span data-ttu-id="674f3-243">Metoda lub stan poprzedzający symbol \* jest opcjonalny i może być wywoływana więcej niż raz.</span><span class="sxs-lookup"><span data-stu-id="674f3-243">The method or state that precedes the \* symbol is optional, and can be called more than once.</span></span>|

## <a name="validation-context"></a><span data-ttu-id="674f3-244">Kontekst walidacji</span><span class="sxs-lookup"><span data-stu-id="674f3-244">Validation Context</span></span>

<span data-ttu-id="674f3-245">Metody <xref:System.Xml.Schema.XmlSchemaValidator> klasy używane do sprawdzania poprawności elementów, atrybutów i zawartości w sprawdzonych XML, zmiana kontekstu walidacji <xref:System.Xml.Schema.XmlSchemaValidator> obiektu.</span><span class="sxs-lookup"><span data-stu-id="674f3-245">The methods of the <xref:System.Xml.Schema.XmlSchemaValidator> class used to validate elements, attributes, and content in an XML infoset, change the validation context of an <xref:System.Xml.Schema.XmlSchemaValidator> object.</span></span> <span data-ttu-id="674f3-246">Na przykład <xref:System.Xml.Schema.XmlSchemaValidator.SkipToEndElement%2A> Metoda pomija sprawdzanie poprawności zawartości bieżącego elementu i przygotowuje <xref:System.Xml.Schema.XmlSchemaValidator> obiekt do zweryfikowania zawartości w kontekście elementu nadrzędnego; jest równoważne pominięciu weryfikacji dla wszystkich elementów podrzędnych bieżącego elementu, a następnie wywołania <xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndElement%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="674f3-246">For example, the <xref:System.Xml.Schema.XmlSchemaValidator.SkipToEndElement%2A> method skips validation of the current element content and prepares the <xref:System.Xml.Schema.XmlSchemaValidator> object to validate content in the parent element's context; it is equivalent to skipping validation for all the children of the current element and then calling the <xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndElement%2A> method.</span></span>

<span data-ttu-id="674f3-247">Wyniki metod <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A>, i <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> <xref:System.Xml.Schema.XmlSchemaValidator.AddSchema%2A> <xref:System.Xml.Schema.XmlSchemaValidator> klasy są zależne od bieżącego kontekstu, który jest sprawdzany.</span><span class="sxs-lookup"><span data-stu-id="674f3-247">The results of the <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A>, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A>, and <xref:System.Xml.Schema.XmlSchemaValidator.AddSchema%2A> methods of the <xref:System.Xml.Schema.XmlSchemaValidator> class are dependent on the current context being validated.</span></span>

<span data-ttu-id="674f3-248">W poniższej tabeli opisano wyniki wywołania tych metod po wywołaniu jednej z metod <xref:System.Xml.Schema.XmlSchemaValidator> klasy używanej do walidacji elementów, atrybutów i zawartości w sprawdzonych XML.</span><span class="sxs-lookup"><span data-stu-id="674f3-248">The following table describes the results of calling these methods after calling one of the methods of the <xref:System.Xml.Schema.XmlSchemaValidator> class used to validate elements, attributes, and content in an XML infoset.</span></span>

|<span data-ttu-id="674f3-249">Metoda</span><span class="sxs-lookup"><span data-stu-id="674f3-249">Method</span></span>|<span data-ttu-id="674f3-250">GetExpectedParticles</span><span class="sxs-lookup"><span data-stu-id="674f3-250">GetExpectedParticles</span></span>|<span data-ttu-id="674f3-251">GetExpectedAttributes</span><span class="sxs-lookup"><span data-stu-id="674f3-251">GetExpectedAttributes</span></span>|<span data-ttu-id="674f3-252">AddSchema</span><span class="sxs-lookup"><span data-stu-id="674f3-252">AddSchema</span></span>|
|------------|--------------------------|---------------------------|---------------|
|<xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A>|<span data-ttu-id="674f3-253">Jeśli wywoływana jest <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> metoda domyślna, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> zwraca tablicę zawierającą wszystkie elementy globalne.</span><span class="sxs-lookup"><span data-stu-id="674f3-253">If the default <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> method is called, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> returns an array containing all global elements.</span></span><br /><br /> <span data-ttu-id="674f3-254">Jeśli przeciążona <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> Metoda, która przyjmuje <xref:System.Xml.Schema.XmlSchemaObject> jako parametr, jest wywoływana w celu zainicjowania częściowej walidacji <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> elementu, zwraca tylko element, do <xref:System.Xml.Schema.XmlSchemaValidator> którego obiekt został zainicjowany.</span><span class="sxs-lookup"><span data-stu-id="674f3-254">If the overloaded <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> method that takes an <xref:System.Xml.Schema.XmlSchemaObject> as a parameter is called to initialize partial validation of an element, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> returns only the element to which the <xref:System.Xml.Schema.XmlSchemaValidator> object was initialized.</span></span>|<span data-ttu-id="674f3-255">Jeśli wywoływana jest <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> metoda domyślna, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> zwraca pustą tablicę.</span><span class="sxs-lookup"><span data-stu-id="674f3-255">If the default <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> method is called, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> returns an empty array.</span></span><br /><br /> <span data-ttu-id="674f3-256">Jeśli Przeciążenie <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> metody, która przyjmuje <xref:System.Xml.Schema.XmlSchemaObject> jako parametr jest wywoływana w celu zainicjowania częściowej walidacji atrybutu, zwraca tylko <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> atrybut, do którego <xref:System.Xml.Schema.XmlSchemaValidator> obiekt został zainicjowany.</span><span class="sxs-lookup"><span data-stu-id="674f3-256">If the overload of the <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> method that takes an <xref:System.Xml.Schema.XmlSchemaObject> as a parameter is called to initialize partial validation of an attribute, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> returns only the attribute to which the <xref:System.Xml.Schema.XmlSchemaValidator> object was initialized.</span></span>|<span data-ttu-id="674f3-257">Dodaje schemat do <xref:System.Xml.Schema.XmlSchemaSet> <xref:System.Xml.Schema.XmlSchemaValidator> obiektu, jeśli nie ma żadnych błędów przetwarzania wstępnego.</span><span class="sxs-lookup"><span data-stu-id="674f3-257">Adds the schema to the <xref:System.Xml.Schema.XmlSchemaSet> of the <xref:System.Xml.Schema.XmlSchemaValidator> object if it has no preprocessing errors.</span></span>|
|<xref:System.Xml.Schema.XmlSchemaValidator.ValidateElement%2A>|<span data-ttu-id="674f3-258">Jeśli element context jest prawidłowy, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> zwraca sekwencję elementów oczekiwaną jako elementy podrzędne elementu Context.</span><span class="sxs-lookup"><span data-stu-id="674f3-258">If the context element is valid, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> returns the sequence of elements expected as children of the context element.</span></span><br /><br /> <span data-ttu-id="674f3-259">Jeśli element context jest nieprawidłowy, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> zwraca pustą tablicę.</span><span class="sxs-lookup"><span data-stu-id="674f3-259">If the context element is invalid, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> returns an empty array.</span></span>|<span data-ttu-id="674f3-260">Jeśli element kontekstu jest prawidłowy i jeśli żadne wywołanie do <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A> nie zostało wcześniej wykonane, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> zwraca listę wszystkich atrybutów zdefiniowanych w elemencie kontekstu.</span><span class="sxs-lookup"><span data-stu-id="674f3-260">If the context element is valid, and if no call to <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A> has been previously made, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> returns a list of all the attributes defined on the context element.</span></span><br /><br /> <span data-ttu-id="674f3-261">Jeśli niektóre atrybuty zostały już zweryfikowane, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> zwraca listę pozostałych atrybutów do zweryfikowania.</span><span class="sxs-lookup"><span data-stu-id="674f3-261">If some attributes have already been validated, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> returns a list of the remaining attributes to be validated.</span></span><br /><br /> <span data-ttu-id="674f3-262">Jeśli element context jest nieprawidłowy, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> zwraca pustą tablicę.</span><span class="sxs-lookup"><span data-stu-id="674f3-262">If the context element is invalid, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> returns an empty array.</span></span>|<span data-ttu-id="674f3-263">Tak samo jak powyżej.</span><span class="sxs-lookup"><span data-stu-id="674f3-263">Same as above.</span></span>|
|<xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A>|<span data-ttu-id="674f3-264">Jeśli atrybut kontekstu jest atrybutem najwyższego poziomu, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> zwraca pustą tablicę.</span><span class="sxs-lookup"><span data-stu-id="674f3-264">If the context attribute is a top-level attribute, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> returns an empty array.</span></span><br /><br /> <span data-ttu-id="674f3-265">W <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> przeciwnym razie zwraca sekwencję elementów oczekiwaną jako pierwszy element podrzędny elementu kontekstu.</span><span class="sxs-lookup"><span data-stu-id="674f3-265">Otherwise <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> returns the sequence of elements expected as the first child of the context element.</span></span>|<span data-ttu-id="674f3-266">Jeśli atrybut kontekstu jest atrybutem najwyższego poziomu, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> zwraca pustą tablicę.</span><span class="sxs-lookup"><span data-stu-id="674f3-266">If the context attribute is a top-level attribute, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> returns an empty array.</span></span><br /><br /> <span data-ttu-id="674f3-267">W <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> przeciwnym razie zwraca listę pozostałych atrybutów do zweryfikowania.</span><span class="sxs-lookup"><span data-stu-id="674f3-267">Otherwise <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> returns the list of remaining attributes to be validated.</span></span>|<span data-ttu-id="674f3-268">Tak samo jak powyżej.</span><span class="sxs-lookup"><span data-stu-id="674f3-268">Same as above.</span></span>|
|<xref:System.Xml.Schema.XmlSchemaValidator.GetUnspecifiedDefaultAttributes%2A>|<span data-ttu-id="674f3-269"><xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A>zwraca sekwencję elementów oczekiwaną jako pierwszy element podrzędny elementu kontekstu.</span><span class="sxs-lookup"><span data-stu-id="674f3-269"><xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> returns the sequence of elements expected as the first child of the context element.</span></span>|<span data-ttu-id="674f3-270"><xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A>zwraca listę wymaganych i opcjonalnych atrybutów, które nie zostały jeszcze zweryfikowane dla elementu kontekstu.</span><span class="sxs-lookup"><span data-stu-id="674f3-270"><xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> returns a list of the required and optional attributes that are yet to be validated for the context element.</span></span>|<span data-ttu-id="674f3-271">Tak samo jak powyżej.</span><span class="sxs-lookup"><span data-stu-id="674f3-271">Same as above.</span></span>|
|<xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndOfAttributes%2A>|<span data-ttu-id="674f3-272"><xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A>zwraca sekwencję elementów oczekiwaną jako pierwszy element podrzędny elementu kontekstu.</span><span class="sxs-lookup"><span data-stu-id="674f3-272"><xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> returns the sequence of elements expected as the first child of the context element.</span></span>|<span data-ttu-id="674f3-273"><xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A>zwraca pustą tablicę.</span><span class="sxs-lookup"><span data-stu-id="674f3-273"><xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> returns an empty array.</span></span>|<span data-ttu-id="674f3-274">Tak samo jak powyżej.</span><span class="sxs-lookup"><span data-stu-id="674f3-274">Same as above.</span></span>|
|<xref:System.Xml.Schema.XmlSchemaValidator.ValidateText%2A>|<span data-ttu-id="674f3-275">Jeśli element ContentType elementu context jest mieszany, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> zwraca sekwencję elementów oczekiwaną w następnym położeniu.</span><span class="sxs-lookup"><span data-stu-id="674f3-275">If the context element's contentType is Mixed, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> returns the sequence of elements expected in the next position.</span></span><br /><br /> <span data-ttu-id="674f3-276">Jeśli element ContentType elementu ContextType ma wartość textOnly lub Empty <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> , zwraca pustą tablicę.</span><span class="sxs-lookup"><span data-stu-id="674f3-276">If the context element's contentType is TextOnly or Empty, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> returns an empty array.</span></span><br /><br /> <span data-ttu-id="674f3-277">Jeśli element ContentType elementu ContextType ma wartość ElementOnly <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> , zwraca sekwencję elementów oczekiwaną w następnym miejscu, ale wystąpił błąd sprawdzania poprawności.</span><span class="sxs-lookup"><span data-stu-id="674f3-277">If the context element's contentType is ElementOnly, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> returns the sequence of elements expected in the next position but a validation error has already occurred.</span></span>|<span data-ttu-id="674f3-278"><xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A>zwraca listę atrybutów elementu kontekstu, które nie zostały zweryfikowane.</span><span class="sxs-lookup"><span data-stu-id="674f3-278"><xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> returns the context element's list of attributes not validated.</span></span>|<span data-ttu-id="674f3-279">Tak samo jak powyżej.</span><span class="sxs-lookup"><span data-stu-id="674f3-279">Same as above.</span></span>|
|<xref:System.Xml.Schema.XmlSchemaValidator.ValidateWhitespace%2A>|<span data-ttu-id="674f3-280">Jeśli odstępy między kontekstami jest odstępem najwyższego poziomu, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> zwraca pustą tablicę.</span><span class="sxs-lookup"><span data-stu-id="674f3-280">If the context white-space is top-level white-space, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> returns an empty array.</span></span><br /><br /> <span data-ttu-id="674f3-281">W przeciwnym <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> razie zachowanie metody jest takie samo jak w <xref:System.Xml.Schema.XmlSchemaValidator.ValidateText%2A>.</span><span class="sxs-lookup"><span data-stu-id="674f3-281">Otherwise the <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> method's behavior is the same as in <xref:System.Xml.Schema.XmlSchemaValidator.ValidateText%2A>.</span></span>|<span data-ttu-id="674f3-282">Jeśli odstępy między kontekstami jest odstępem najwyższego poziomu, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> zwraca pustą tablicę.</span><span class="sxs-lookup"><span data-stu-id="674f3-282">If the context white-space is top-level white-space, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> returns an empty array.</span></span><br /><br /> <span data-ttu-id="674f3-283">W przeciwnym <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> razie zachowanie metody jest takie samo jak w <xref:System.Xml.Schema.XmlSchemaValidator.ValidateText%2A>.</span><span class="sxs-lookup"><span data-stu-id="674f3-283">Otherwise the <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> method's behavior is the same as in <xref:System.Xml.Schema.XmlSchemaValidator.ValidateText%2A>.</span></span>|<span data-ttu-id="674f3-284">Tak samo jak powyżej.</span><span class="sxs-lookup"><span data-stu-id="674f3-284">Same as above.</span></span>|
|<xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndElement%2A>|<span data-ttu-id="674f3-285"><xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A>zwraca sekwencję elementów oczekiwaną po elemencie kontekstu (możliwe elementy równorzędne).</span><span class="sxs-lookup"><span data-stu-id="674f3-285"><xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> returns the sequence of elements expected after the context element (possible siblings).</span></span>|<span data-ttu-id="674f3-286"><xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A>zwraca listę atrybutów elementu kontekstu, które nie zostały zweryfikowane.</span><span class="sxs-lookup"><span data-stu-id="674f3-286"><xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> returns the context element's list of attributes not validated.</span></span><br /><br /> <span data-ttu-id="674f3-287">Jeśli element kontekstu nie ma elementu nadrzędnego, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> funkcja zwróci pustą listę (element context jest obiektem nadrzędnym bieżącego elementu, w <xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndElement%2A> którym został wywołany).</span><span class="sxs-lookup"><span data-stu-id="674f3-287">If the context element has no parent then <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> returns an empty list (the context element is the parent of the current element on which <xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndElement%2A> was called).</span></span>|<span data-ttu-id="674f3-288">Tak samo jak powyżej.</span><span class="sxs-lookup"><span data-stu-id="674f3-288">Same as above.</span></span>|
|<xref:System.Xml.Schema.XmlSchemaValidator.SkipToEndElement%2A>|<span data-ttu-id="674f3-289">Analogicznie <xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndElement%2A>jak.</span><span class="sxs-lookup"><span data-stu-id="674f3-289">Same as <xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndElement%2A>.</span></span>|<span data-ttu-id="674f3-290">Analogicznie <xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndElement%2A>jak.</span><span class="sxs-lookup"><span data-stu-id="674f3-290">Same as <xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndElement%2A>.</span></span>|<span data-ttu-id="674f3-291">Tak samo jak powyżej.</span><span class="sxs-lookup"><span data-stu-id="674f3-291">Same as above.</span></span>|
|<xref:System.Xml.Schema.XmlSchemaValidator.EndValidation%2A>|<span data-ttu-id="674f3-292">Zwraca pustą tablicę.</span><span class="sxs-lookup"><span data-stu-id="674f3-292">Returns an empty array.</span></span>|<span data-ttu-id="674f3-293">Zwraca pustą tablicę.</span><span class="sxs-lookup"><span data-stu-id="674f3-293">Returns an empty array.</span></span>|<span data-ttu-id="674f3-294">Tak samo jak powyżej.</span><span class="sxs-lookup"><span data-stu-id="674f3-294">Same as above.</span></span>|

> [!NOTE]
> <span data-ttu-id="674f3-295">Wartości zwracane przez różne właściwości <xref:System.Xml.Schema.XmlSchemaValidator> klasy nie są zmieniane przez wywołanie dowolnej metody z powyższej tabeli.</span><span class="sxs-lookup"><span data-stu-id="674f3-295">The values returned by the various properties of the <xref:System.Xml.Schema.XmlSchemaValidator> class are not altered by calling any of the methods in the above table.</span></span>

## <a name="see-also"></a><span data-ttu-id="674f3-296">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="674f3-296">See also</span></span>

- <xref:System.Xml.Schema.XmlSchemaValidator>
