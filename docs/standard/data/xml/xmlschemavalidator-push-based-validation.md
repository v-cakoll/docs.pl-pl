---
title: XmlSchemaValidator weryfikacja oparta na wypychaniu
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 911d4460-dd91-4958-85b2-2ca3299f9ec6
author: mairaw
ms.author: mairaw
ms.openlocfilehash: a420a134eda6c62758b0d218e3c0a4a4922b048c
ms.sourcegitcommit: d7c298f6c2e3aab0c7498bfafc0a0a94ea1fe23e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/10/2019
ms.locfileid: "72250042"
---
# <a name="xmlschemavalidator-push-based-validation"></a><span data-ttu-id="715d1-102">XmlSchemaValidator weryfikacja oparta na wypychaniu</span><span class="sxs-lookup"><span data-stu-id="715d1-102">XmlSchemaValidator Push-Based Validation</span></span>

<span data-ttu-id="715d1-103">Klasa <xref:System.Xml.Schema.XmlSchemaValidator> zapewnia wydajny mechanizm o wysokiej wydajności służący do sprawdzania poprawności danych XML w schematach XML w sposób oparty na wypychaniu.</span><span class="sxs-lookup"><span data-stu-id="715d1-103">The <xref:System.Xml.Schema.XmlSchemaValidator> class provides an efficient, high-performance mechanism to validate XML data against XML schemas in a push-based manner.</span></span> <span data-ttu-id="715d1-104">Na przykład Klasa <xref:System.Xml.Schema.XmlSchemaValidator> umożliwia sprawdzenie poprawności sprawdzonych XML, bez konieczności serializacji go jako dokumentu XML, a następnie ponowne przeanalizowanie dokumentu przy użyciu walidacji czytnika XML.</span><span class="sxs-lookup"><span data-stu-id="715d1-104">For example, the <xref:System.Xml.Schema.XmlSchemaValidator> class allows you to validate an XML infoset in-place without having to serialize it as an XML document and then reparse the document using a validating XML reader.</span></span>

<span data-ttu-id="715d1-105">Klasy <xref:System.Xml.Schema.XmlSchemaValidator> można używać w zaawansowanych scenariuszach, takich jak tworzenie aparatów walidacji w niestandardowych źródłach danych XML lub sposób tworzenia walidacji składnika zapisywania XML.</span><span class="sxs-lookup"><span data-stu-id="715d1-105">The <xref:System.Xml.Schema.XmlSchemaValidator> class can be used in advanced scenarios such as building validation engines over custom XML data sources or as a way to build a validating XML writer.</span></span>

<span data-ttu-id="715d1-106">Poniżej przedstawiono przykład użycia klasy <xref:System.Xml.Schema.XmlSchemaValidator> do walidacji pliku `contosoBooks.xml` względem schematu `contosoBooks.xsd`.</span><span class="sxs-lookup"><span data-stu-id="715d1-106">The following is an example of using the <xref:System.Xml.Schema.XmlSchemaValidator> class to validate the `contosoBooks.xml` file against the `contosoBooks.xsd` schema.</span></span> <span data-ttu-id="715d1-107">W przykładzie zastosowano klasę <xref:System.Xml.Serialization.XmlSerializer> w celu deserializacji pliku `contosoBooks.xml` i przekazania wartości węzłów do metod klasy <xref:System.Xml.Schema.XmlSchemaValidator>.</span><span class="sxs-lookup"><span data-stu-id="715d1-107">The example uses the <xref:System.Xml.Serialization.XmlSerializer> class to deserialize the `contosoBooks.xml` file and pass the value of the nodes to the methods of the <xref:System.Xml.Schema.XmlSchemaValidator> class.</span></span>

> [!NOTE]
> <span data-ttu-id="715d1-108">Ten przykład jest używany w części tego tematu.</span><span class="sxs-lookup"><span data-stu-id="715d1-108">This example is used throughout the sections of this topic.</span></span>

[!code-csharp[XmlSchemaValidatorExamples#1](../../../../samples/snippets/csharp/VS_Snippets_Data/XmlSchemaValidatorExamples/CS/XmlSchemaValidatorExamples.cs#1)]
[!code-vb[XmlSchemaValidatorExamples#1](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XmlSchemaValidatorExamples/VB/XmlSchemaValidatorExamples.vb#1)]

<span data-ttu-id="715d1-109">Przykład pobiera plik `contosoBooks.xml` jako dane wejściowe.</span><span class="sxs-lookup"><span data-stu-id="715d1-109">The example takes the `contosoBooks.xml` file as input.</span></span>

[!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]

<span data-ttu-id="715d1-110">Przykład pobiera również `contosoBooks.xsd` jako dane wejściowe.</span><span class="sxs-lookup"><span data-stu-id="715d1-110">The example also takes the `contosoBooks.xsd` as an input.</span></span>

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

## <a name="validating-xml-data-using-xmlschemavalidator"></a><span data-ttu-id="715d1-111">Walidacja danych XML przy użyciu XmlSchemaValidator</span><span class="sxs-lookup"><span data-stu-id="715d1-111">Validating XML Data using XmlSchemaValidator</span></span>

<span data-ttu-id="715d1-112">Aby rozpocząć walidację sprawdzonych XML, należy najpierw zainicjować nowe wystąpienie klasy <xref:System.Xml.Schema.XmlSchemaValidator> przy użyciu konstruktora <xref:System.Xml.Schema.XmlSchemaValidator.%23ctor%2A>.</span><span class="sxs-lookup"><span data-stu-id="715d1-112">To begin validating an XML infoset, you must first initialize a new instance of the <xref:System.Xml.Schema.XmlSchemaValidator> class using the <xref:System.Xml.Schema.XmlSchemaValidator.%23ctor%2A> constructor.</span></span>

<span data-ttu-id="715d1-113">Konstruktor <xref:System.Xml.Schema.XmlSchemaValidator.%23ctor%2A> przyjmuje <xref:System.Xml.XmlNameTable>, <xref:System.Xml.Schema.XmlSchemaSet> i <xref:System.Xml.XmlNamespaceManager> obiektów jako parametry, a także wartość <xref:System.Xml.Schema.XmlSchemaValidationFlags> jako parametr.</span><span class="sxs-lookup"><span data-stu-id="715d1-113">The <xref:System.Xml.Schema.XmlSchemaValidator.%23ctor%2A> constructor takes <xref:System.Xml.XmlNameTable>, <xref:System.Xml.Schema.XmlSchemaSet>, and <xref:System.Xml.XmlNamespaceManager> objects as parameters as well as a <xref:System.Xml.Schema.XmlSchemaValidationFlags> value as a parameter.</span></span> <span data-ttu-id="715d1-114">Obiekt <xref:System.Xml.XmlNameTable> służy do wyodrębnić dobrze znanych ciągów przestrzeni nazw, takich jak przestrzeń nazw schematu, przestrzeń nazw XML i tak dalej, i jest przenoszona do metody <xref:System.Xml.Schema.XmlSchemaDatatype.ParseValue%2A> podczas weryfikacji prostej zawartości.</span><span class="sxs-lookup"><span data-stu-id="715d1-114">The <xref:System.Xml.XmlNameTable> object is used to atomize well-known namespace strings like the schema namespace, the XML namespace, and so on, and is passed to the <xref:System.Xml.Schema.XmlSchemaDatatype.ParseValue%2A> method while validating simple content.</span></span> <span data-ttu-id="715d1-115">Obiekt <xref:System.Xml.Schema.XmlSchemaSet> zawiera schematy XML używane do sprawdzania poprawności sprawdzonych XML.</span><span class="sxs-lookup"><span data-stu-id="715d1-115">The <xref:System.Xml.Schema.XmlSchemaSet> object contains the XML schemas used to validate the XML infoset.</span></span> <span data-ttu-id="715d1-116">Obiekt <xref:System.Xml.XmlNamespaceManager> służy do rozpoznawania przestrzeni nazw napotkanych podczas walidacji.</span><span class="sxs-lookup"><span data-stu-id="715d1-116">The <xref:System.Xml.XmlNamespaceManager> object is used to resolve namespaces encountered during validation.</span></span> <span data-ttu-id="715d1-117">Wartość <xref:System.Xml.Schema.XmlSchemaValidationFlags> służy do wyłączania niektórych funkcji walidacji.</span><span class="sxs-lookup"><span data-stu-id="715d1-117">The <xref:System.Xml.Schema.XmlSchemaValidationFlags> value is used to disable certain features of validation.</span></span>

<span data-ttu-id="715d1-118">Więcej informacji na temat konstruktora <xref:System.Xml.Schema.XmlSchemaValidator.%23ctor%2A> można znaleźć w dokumentacji dotyczącej klasy <xref:System.Xml.Schema.XmlSchemaValidator>.</span><span class="sxs-lookup"><span data-stu-id="715d1-118">For more information about the <xref:System.Xml.Schema.XmlSchemaValidator.%23ctor%2A> constructor, see the <xref:System.Xml.Schema.XmlSchemaValidator> class reference documentation.</span></span>

### <a name="initializing-validation"></a><span data-ttu-id="715d1-119">Inicjowanie walidacji</span><span class="sxs-lookup"><span data-stu-id="715d1-119">Initializing Validation</span></span>

<span data-ttu-id="715d1-120">Po skonstruowaniu obiektu <xref:System.Xml.Schema.XmlSchemaValidator> istnieją dwie przeciążone metody <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> służące do zainicjowania stanu obiektu <xref:System.Xml.Schema.XmlSchemaValidator>.</span><span class="sxs-lookup"><span data-stu-id="715d1-120">After an <xref:System.Xml.Schema.XmlSchemaValidator> object has been constructed, there are two overloaded <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> methods used to initialize the state of the <xref:System.Xml.Schema.XmlSchemaValidator> object.</span></span> <span data-ttu-id="715d1-121">Poniżej przedstawiono dwie metody <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A>.</span><span class="sxs-lookup"><span data-stu-id="715d1-121">The following are the two <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> methods.</span></span>

- <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A?displayProperty=nameWithType>

- <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A?displayProperty=nameWithType>

<span data-ttu-id="715d1-122">Domyślna metoda <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A?displayProperty=nameWithType> inicjuje obiekt <xref:System.Xml.Schema.XmlSchemaValidator> do jego stanu początkowego i przeciążonej metody <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A?displayProperty=nameWithType>, która przyjmuje <xref:System.Xml.Schema.XmlSchemaObject> jako parametr inicjuje obiekt <xref:System.Xml.Schema.XmlSchemaValidator> do stanu początkowego dla częściowej walidacji.</span><span class="sxs-lookup"><span data-stu-id="715d1-122">The default <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A?displayProperty=nameWithType> method initializes an <xref:System.Xml.Schema.XmlSchemaValidator> object to its starting state, and the overloaded <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A?displayProperty=nameWithType> method that takes an <xref:System.Xml.Schema.XmlSchemaObject> as a parameter initializes an <xref:System.Xml.Schema.XmlSchemaValidator> object to its starting state for partial validation.</span></span>

<span data-ttu-id="715d1-123">Metody <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> można wywołać tylko natychmiast po skonstruowaniu obiektu <xref:System.Xml.Schema.XmlSchemaValidator> lub po wywołaniu <xref:System.Xml.Schema.XmlSchemaValidator.EndValidation%2A>.</span><span class="sxs-lookup"><span data-stu-id="715d1-123">Both <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> methods can only be called immediately after an <xref:System.Xml.Schema.XmlSchemaValidator> object has been constructed or after a call to <xref:System.Xml.Schema.XmlSchemaValidator.EndValidation%2A>.</span></span>

<span data-ttu-id="715d1-124">Przykład metody <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A?displayProperty=nameWithType> zawiera przykład we wprowadzeniu.</span><span class="sxs-lookup"><span data-stu-id="715d1-124">For an example of the <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A?displayProperty=nameWithType> method, see the example in the introduction.</span></span> <span data-ttu-id="715d1-125">Więcej informacji o metodzie <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> znajduje się w dokumentacji dotyczącej klasy <xref:System.Xml.Schema.XmlSchemaValidator>.</span><span class="sxs-lookup"><span data-stu-id="715d1-125">For more information about the <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> method, see the <xref:System.Xml.Schema.XmlSchemaValidator> class reference documentation.</span></span>

#### <a name="partial-validation"></a><span data-ttu-id="715d1-126">Częściowe sprawdzanie poprawności</span><span class="sxs-lookup"><span data-stu-id="715d1-126">Partial Validation</span></span>

<span data-ttu-id="715d1-127">Metoda <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A?displayProperty=nameWithType>, która przyjmuje <xref:System.Xml.Schema.XmlSchemaObject> jako parametr inicjuje obiekt <xref:System.Xml.Schema.XmlSchemaValidator> do stanu początkowego dla częściowej walidacji.</span><span class="sxs-lookup"><span data-stu-id="715d1-127">The <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A?displayProperty=nameWithType> method that takes an <xref:System.Xml.Schema.XmlSchemaObject> as a parameter initializes an <xref:System.Xml.Schema.XmlSchemaValidator> object to its starting state for partial validation.</span></span>

<span data-ttu-id="715d1-128">W poniższym przykładzie zainicjowano <xref:System.Xml.Schema.XmlSchemaObject> do walidacji częściowej przy użyciu metody <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="715d1-128">In the following example, an <xref:System.Xml.Schema.XmlSchemaObject> is initialized for partial validation using the <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="715d1-129">Element schematu `orderNumber` jest przenoszona przez wybranie elementu schematu o <xref:System.Xml.XmlQualifiedName> w kolekcji <xref:System.Xml.Schema.XmlSchemaObjectTable> zwróconej przez właściwość <xref:System.Xml.Schema.XmlSchemaSet.GlobalElements%2A> obiektu <xref:System.Xml.Schema.XmlSchemaSet>.</span><span class="sxs-lookup"><span data-stu-id="715d1-129">The `orderNumber` schema element is passed by selecting the schema element by <xref:System.Xml.XmlQualifiedName> in the <xref:System.Xml.Schema.XmlSchemaObjectTable> collection returned by the <xref:System.Xml.Schema.XmlSchemaSet.GlobalElements%2A> property of the <xref:System.Xml.Schema.XmlSchemaSet> object.</span></span> <span data-ttu-id="715d1-130">Obiekt <xref:System.Xml.Schema.XmlSchemaValidator> sprawdza poprawność tego określonego elementu.</span><span class="sxs-lookup"><span data-stu-id="715d1-130">The <xref:System.Xml.Schema.XmlSchemaValidator> object then validates this specific element.</span></span>

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

<span data-ttu-id="715d1-131">Przykład pobiera Poniższy schemat XML jako dane wejściowe.</span><span class="sxs-lookup"><span data-stu-id="715d1-131">The example takes the following XML schema as input.</span></span>

```xml
<xs:schema xmlns:xs="http://www.w3.org/2001/XMLSchema">
  <xs:element name="orderNumber" type="xs:int" />
</xs:schema>
```

<span data-ttu-id="715d1-132">Więcej informacji o metodzie <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> znajduje się w dokumentacji dotyczącej klasy <xref:System.Xml.Schema.XmlSchemaValidator>.</span><span class="sxs-lookup"><span data-stu-id="715d1-132">For more information about the <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> method, see the <xref:System.Xml.Schema.XmlSchemaValidator> class reference documentation.</span></span>

### <a name="adding-additional-schemas"></a><span data-ttu-id="715d1-133">Dodawanie dodatkowych schematów</span><span class="sxs-lookup"><span data-stu-id="715d1-133">Adding Additional Schemas</span></span>

<span data-ttu-id="715d1-134">Metoda <xref:System.Xml.Schema.XmlSchemaValidator.AddSchema%2A> klasy <xref:System.Xml.Schema.XmlSchemaValidator> służy do dodawania schematu XML do zestawu schematów używanych podczas walidacji.</span><span class="sxs-lookup"><span data-stu-id="715d1-134">The <xref:System.Xml.Schema.XmlSchemaValidator.AddSchema%2A> method of the <xref:System.Xml.Schema.XmlSchemaValidator> class is used to add an XML schema to the set of schemas used during validation.</span></span> <span data-ttu-id="715d1-135">Metoda <xref:System.Xml.Schema.XmlSchemaValidator.AddSchema%2A> może służyć do symulowania efektu napotkania wbudowanego schematu XML w kodzie XML sprawdzonych.</span><span class="sxs-lookup"><span data-stu-id="715d1-135">The <xref:System.Xml.Schema.XmlSchemaValidator.AddSchema%2A> method can be used to simulate the effect of encountering an inline XML schema in the XML infoset being validated.</span></span>

> [!NOTE]
> <span data-ttu-id="715d1-136">Docelowa przestrzeń nazw parametru <xref:System.Xml.Schema.XmlSchema> nie może być zgodna z elementem lub atrybutem już napotkanym przez obiekt <xref:System.Xml.Schema.XmlSchemaValidator>.</span><span class="sxs-lookup"><span data-stu-id="715d1-136">The target namespace of the <xref:System.Xml.Schema.XmlSchema> parameter cannot match that of any element or attribute already encountered by the <xref:System.Xml.Schema.XmlSchemaValidator> object.</span></span>
>
> <span data-ttu-id="715d1-137">Jeśli wartość <xref:System.Xml.Schema.XmlSchemaValidationFlags.ProcessInlineSchema?displayProperty=nameWithType> nie została przekazano jako parametr do konstruktora <xref:System.Xml.Schema.XmlSchemaValidator.%23ctor%2A>, Metoda <xref:System.Xml.Schema.XmlSchemaValidator.AddSchema%2A> nie wykonuje żadnych operacji.</span><span class="sxs-lookup"><span data-stu-id="715d1-137">If the <xref:System.Xml.Schema.XmlSchemaValidationFlags.ProcessInlineSchema?displayProperty=nameWithType> value was not passed as a parameter to the <xref:System.Xml.Schema.XmlSchemaValidator.%23ctor%2A> constructor, the <xref:System.Xml.Schema.XmlSchemaValidator.AddSchema%2A> method does nothing.</span></span>

<span data-ttu-id="715d1-138">Wynik metody <xref:System.Xml.Schema.XmlSchemaValidator.AddSchema%2A> zależy od bieżącego kontekstu węzła XML, który jest sprawdzany.</span><span class="sxs-lookup"><span data-stu-id="715d1-138">The result of the <xref:System.Xml.Schema.XmlSchemaValidator.AddSchema%2A> method is dependant on the current XML node context being validated.</span></span> <span data-ttu-id="715d1-139">Aby uzyskać więcej informacji na temat kontekstów walidacji, zobacz sekcję "kontekst walidacji" w tym temacie.</span><span class="sxs-lookup"><span data-stu-id="715d1-139">For more information about validation contexts, see the "Validation Context" section of this topic.</span></span>

<span data-ttu-id="715d1-140">Więcej informacji o metodzie <xref:System.Xml.Schema.XmlSchemaValidator.AddSchema%2A> znajduje się w dokumentacji dotyczącej klasy <xref:System.Xml.Schema.XmlSchemaValidator>.</span><span class="sxs-lookup"><span data-stu-id="715d1-140">For more information about the <xref:System.Xml.Schema.XmlSchemaValidator.AddSchema%2A> method, see the <xref:System.Xml.Schema.XmlSchemaValidator> class reference documentation.</span></span>

### <a name="validating-elements-attributes-and-content"></a><span data-ttu-id="715d1-141">Walidacja elementów, atrybutów i zawartości</span><span class="sxs-lookup"><span data-stu-id="715d1-141">Validating Elements, Attributes, and Content</span></span>

<span data-ttu-id="715d1-142">Klasa <xref:System.Xml.Schema.XmlSchemaValidator> udostępnia kilka metod służących do sprawdzania poprawności elementów, atrybutów i zawartości w sprawdzonych XML w schematach XML.</span><span class="sxs-lookup"><span data-stu-id="715d1-142">The <xref:System.Xml.Schema.XmlSchemaValidator> class provides several methods used to validate elements, attributes, and content in an XML infoset against XML schemas.</span></span> <span data-ttu-id="715d1-143">W poniższej tabeli opisano każdą z tych metod.</span><span class="sxs-lookup"><span data-stu-id="715d1-143">The following table describes each of these methods.</span></span>

|<span data-ttu-id="715d1-144">Metoda</span><span class="sxs-lookup"><span data-stu-id="715d1-144">Method</span></span>|<span data-ttu-id="715d1-145">Opis</span><span class="sxs-lookup"><span data-stu-id="715d1-145">Description</span></span>|
|------------|-----------------|
|<xref:System.Xml.Schema.XmlSchemaValidator.ValidateElement%2A>|<span data-ttu-id="715d1-146">Sprawdza poprawność nazwy elementu w bieżącym kontekście.</span><span class="sxs-lookup"><span data-stu-id="715d1-146">Validates the element name in the current context.</span></span>|
|<xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A>|<span data-ttu-id="715d1-147">Sprawdza poprawność atrybutu w kontekście bieżącego elementu lub względem obiektu <xref:System.Xml.Schema.XmlSchemaAttribute> przekazaną jako parametr do metody <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A>.</span><span class="sxs-lookup"><span data-stu-id="715d1-147">Validates the attribute in the current element context or against the <xref:System.Xml.Schema.XmlSchemaAttribute> object passed as a parameter to the <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> method.</span></span>|
|<xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndOfAttributes%2A>|<span data-ttu-id="715d1-148">Sprawdza, czy wszystkie wymagane atrybuty w kontekście elementu są obecne i przygotowuje obiekt <xref:System.Xml.Schema.XmlSchemaValidator> do walidacji zawartości podrzędnej elementu.</span><span class="sxs-lookup"><span data-stu-id="715d1-148">Verifies whether all the required attributes in the element context are present and prepares the <xref:System.Xml.Schema.XmlSchemaValidator> object to validate the child content of the element.</span></span>|
|<xref:System.Xml.Schema.XmlSchemaValidator.ValidateText%2A>|<span data-ttu-id="715d1-149">Sprawdza, czy tekst jest dozwolony w kontekście bieżącego elementu i gromadzi tekst do walidacji, jeśli bieżący element ma prostą zawartość.</span><span class="sxs-lookup"><span data-stu-id="715d1-149">Validates whether text is allowed in the current element context, and accumulates the text for validation if the current element has simple content.</span></span>|
|<xref:System.Xml.Schema.XmlSchemaValidator.ValidateWhitespace%2A>|<span data-ttu-id="715d1-150">Sprawdza, czy w bieżącym kontekście elementu jest dozwolone białe miejsce, i gromadzi białe miejsce do walidacji, czy bieżący element ma prostą zawartość.</span><span class="sxs-lookup"><span data-stu-id="715d1-150">Validates whether white-space is allowed in the current element context, and accumulates the white-space for validation whether the current element has simple content.</span></span>|
|<xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndElement%2A>|<span data-ttu-id="715d1-151">Sprawdza, czy zawartość tekstowa elementu jest prawidłowa przy uwzględnieniu jego typu danych dla elementów z prostą zawartością i sprawdza, czy zawartość bieżącego elementu jest kompletna dla elementów z zawartością złożoną.</span><span class="sxs-lookup"><span data-stu-id="715d1-151">Verifies whether the text content of the element is valid according to its data type for elements with simple content, and verifies whether the content of the current element is complete for elements with complex content.</span></span>|
|<xref:System.Xml.Schema.XmlSchemaValidator.SkipToEndElement%2A>|<span data-ttu-id="715d1-152">Pomija sprawdzanie poprawności zawartości bieżącego elementu i przygotowuje obiekt <xref:System.Xml.Schema.XmlSchemaValidator> do walidacji zawartości w kontekście elementu nadrzędnego.</span><span class="sxs-lookup"><span data-stu-id="715d1-152">Skips validation of the current element content and prepares the <xref:System.Xml.Schema.XmlSchemaValidator> object to validate content in the parent element's context.</span></span>|
|<xref:System.Xml.Schema.XmlSchemaValidator.EndValidation%2A>|<span data-ttu-id="715d1-153">Zakończenie walidacji i sprawdza ograniczenia tożsamości dla całego dokumentu XML, jeśli ustawiono opcję walidacji <xref:System.Xml.Schema.XmlSchemaValidationFlags.ProcessIdentityConstraints>.</span><span class="sxs-lookup"><span data-stu-id="715d1-153">Ends validation and checks identity constraints for the entire XML document if the <xref:System.Xml.Schema.XmlSchemaValidationFlags.ProcessIdentityConstraints> validation option is set.</span></span>|

> [!NOTE]
> <span data-ttu-id="715d1-154">Klasa <xref:System.Xml.Schema.XmlSchemaValidator> ma zdefiniowane przejście stanu, które wymusza sekwencję i wystąpienie wywołań wykonanych dla każdej z metod opisanych w poprzedniej tabeli.</span><span class="sxs-lookup"><span data-stu-id="715d1-154">The <xref:System.Xml.Schema.XmlSchemaValidator> class has a defined state transition that enforces the sequence and occurrence of calls made to each of the methods described in the previous table.</span></span> <span data-ttu-id="715d1-155">Przejście określonego stanu klasy <xref:System.Xml.Schema.XmlSchemaValidator> zostało opisane w sekcji "przechodzenie stanu XmlSchemaValidator" w tym temacie.</span><span class="sxs-lookup"><span data-stu-id="715d1-155">The specific state transition of the <xref:System.Xml.Schema.XmlSchemaValidator> class is described in the "XmlSchemaValidator State Transition" section of this topic.</span></span>

<span data-ttu-id="715d1-156">Przykład metod używanych do sprawdzania poprawności elementów, atrybutów i zawartości w sprawdzonych XML zawiera przykład w poprzedniej sekcji.</span><span class="sxs-lookup"><span data-stu-id="715d1-156">For an example of the methods used to validate elements, attributes, and content in an XML infoset, see the example in the previous section.</span></span> <span data-ttu-id="715d1-157">Więcej informacji o tych metodach znajduje się w dokumentacji dotyczącej klasy <xref:System.Xml.Schema.XmlSchemaValidator>.</span><span class="sxs-lookup"><span data-stu-id="715d1-157">For more information about these methods, see the <xref:System.Xml.Schema.XmlSchemaValidator> class reference documentation.</span></span>

#### <a name="validating-content-using-an-xmlvaluegetter"></a><span data-ttu-id="715d1-158">Sprawdzanie poprawności zawartości przy użyciu XmlValueGetter</span><span class="sxs-lookup"><span data-stu-id="715d1-158">Validating Content Using an XmlValueGetter</span></span>

<span data-ttu-id="715d1-159">@No__t-0 @ no__t-1 może służyć do przekazywania wartości węzłów atrybutów, tekstu lub białych miejsc jako typów środowiska uruchomieniowego języka wspólnego (CLR) zgodnych z typem języka definicji schematu XML (XSD) atrybutu, tekstu lub odstępu.</span><span class="sxs-lookup"><span data-stu-id="715d1-159">The <xref:System.Xml.Schema.XmlValueGetter>`delegate` can be used to pass the value of attribute, text, or white-space nodes as a Common Language Runtime (CLR) types compatible with the XML Schema Definition Language (XSD) type of the attribute, text, or white-space node.</span></span> <span data-ttu-id="715d1-160">@No__t-0 @ no__t-1 jest przydatna, jeśli wartość CLR atrybutu, tekstu lub węzła białego miejsca jest już dostępna, i unika kosztu konwersji na `string`, a następnie ponowne przeanalizowanie go w celu weryfikacji.</span><span class="sxs-lookup"><span data-stu-id="715d1-160">An <xref:System.Xml.Schema.XmlValueGetter>`delegate` is useful if the CLR value of an attribute, text, or white-space node is already available, and avoids the cost of converting it to a `string` and then reparsing it again for validation.</span></span>

<span data-ttu-id="715d1-161">Metody <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A>, <xref:System.Xml.Schema.XmlSchemaValidator.ValidateText%2A> i <xref:System.Xml.Schema.XmlSchemaValidator.ValidateWhitespace%2A> są przeciążone i akceptują wartości węzłów atrybutów, tekstu lub białych miejsc jako `string` lub <xref:System.Xml.Schema.XmlValueGetter> @ no__t-5.</span><span class="sxs-lookup"><span data-stu-id="715d1-161">The <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A>, <xref:System.Xml.Schema.XmlSchemaValidator.ValidateText%2A>, and <xref:System.Xml.Schema.XmlSchemaValidator.ValidateWhitespace%2A> methods are overloaded and accept the value of attribute, text, or white-space nodes as a `string` or <xref:System.Xml.Schema.XmlValueGetter>`delegate`.</span></span>

<span data-ttu-id="715d1-162">Następujące metody klasy <xref:System.Xml.Schema.XmlSchemaValidator> akceptują <xref:System.Xml.Schema.XmlValueGetter> @ no__t-2 jako parametr.</span><span class="sxs-lookup"><span data-stu-id="715d1-162">The following methods of the <xref:System.Xml.Schema.XmlSchemaValidator> class accept an <xref:System.Xml.Schema.XmlValueGetter>`delegate` as a parameter.</span></span>

- <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A>

- <xref:System.Xml.Schema.XmlSchemaValidator.ValidateText%2A>

- <xref:System.Xml.Schema.XmlSchemaValidator.ValidateWhitespace%2A>

<span data-ttu-id="715d1-163">Poniżej przedstawiono przykład <xref:System.Xml.Schema.XmlValueGetter> @ no__t-1 pobrane z przykładu klasy <xref:System.Xml.Schema.XmlSchemaValidator> we wprowadzeniu.</span><span class="sxs-lookup"><span data-stu-id="715d1-163">The following is an example <xref:System.Xml.Schema.XmlValueGetter>`delegate` taken from the <xref:System.Xml.Schema.XmlSchemaValidator> class example in the introduction.</span></span> <span data-ttu-id="715d1-164">@No__t-0 @ no__t-1 zwraca wartość atrybutu jako obiekt <xref:System.DateTime>.</span><span class="sxs-lookup"><span data-stu-id="715d1-164">The <xref:System.Xml.Schema.XmlValueGetter>`delegate` returns the value of an attribute as a <xref:System.DateTime> object.</span></span> <span data-ttu-id="715d1-165">Aby sprawdzić poprawność tego obiektu <xref:System.DateTime> zwróconego przez <xref:System.Xml.Schema.XmlValueGetter>, obiekt <xref:System.Xml.Schema.XmlSchemaValidator> najpierw konwertuje go na element ValueType (ValueType jest domyślnym mapowaniem CLR dla typu XSD) dla typu danych atrybutu, a następnie sprawdza aspekty w skonwertowanej wartości.</span><span class="sxs-lookup"><span data-stu-id="715d1-165">To validate this <xref:System.DateTime> object returned by the <xref:System.Xml.Schema.XmlValueGetter>, the <xref:System.Xml.Schema.XmlSchemaValidator> object first converts it to the ValueType (ValueType is the default CLR mapping for the XSD type) for the data type of the attribute and then checks facets on the converted value.</span></span>

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

<span data-ttu-id="715d1-166">Aby zapoznać się z kompletnym przykładem <xref:System.Xml.Schema.XmlValueGetter> @ no__t-1, zobacz przykład we wprowadzeniu.</span><span class="sxs-lookup"><span data-stu-id="715d1-166">For a complete example of the <xref:System.Xml.Schema.XmlValueGetter>`delegate`, see the example in the introduction.</span></span> <span data-ttu-id="715d1-167">Więcej informacji na temat <xref:System.Xml.Schema.XmlValueGetter> @ no__t-1 można znaleźć w dokumentacji dotyczącej klasy <xref:System.Xml.Schema.XmlValueGetter> i <xref:System.Xml.Schema.XmlSchemaValidator>.</span><span class="sxs-lookup"><span data-stu-id="715d1-167">For more information about the <xref:System.Xml.Schema.XmlValueGetter>`delegate`, see the <xref:System.Xml.Schema.XmlValueGetter>, and <xref:System.Xml.Schema.XmlSchemaValidator> class reference documentation.</span></span>

#### <a name="post-schema-validation-information"></a><span data-ttu-id="715d1-168">Po zaweryfikacji schematu — informacje</span><span class="sxs-lookup"><span data-stu-id="715d1-168">Post-Schema-Validation-Information</span></span>

<span data-ttu-id="715d1-169">Klasa <xref:System.Xml.Schema.XmlSchemaInfo> reprezentuje niektóre z podanych po schemacie walidacji węzła XML zweryfikowanego przez klasę <xref:System.Xml.Schema.XmlSchemaValidator>.</span><span class="sxs-lookup"><span data-stu-id="715d1-169">The <xref:System.Xml.Schema.XmlSchemaInfo> class represents some of the Post-Schema-Validation-Information of an XML node validated by the <xref:System.Xml.Schema.XmlSchemaValidator> class.</span></span> <span data-ttu-id="715d1-170">Różne metody klasy <xref:System.Xml.Schema.XmlSchemaValidator> akceptują obiekt <xref:System.Xml.Schema.XmlSchemaInfo> jako opcjonalny parametr (`null`) `out`.</span><span class="sxs-lookup"><span data-stu-id="715d1-170">Various methods of the <xref:System.Xml.Schema.XmlSchemaValidator> class accept an <xref:System.Xml.Schema.XmlSchemaInfo> object as an optional, (`null`) `out` parameter.</span></span>

<span data-ttu-id="715d1-171">Po pomyślnej weryfikacji właściwości obiektu <xref:System.Xml.Schema.XmlSchemaInfo> są ustawiane z wynikami walidacji.</span><span class="sxs-lookup"><span data-stu-id="715d1-171">Upon successful validation, properties of the <xref:System.Xml.Schema.XmlSchemaInfo> object are set with the results of the validation.</span></span> <span data-ttu-id="715d1-172">Na przykład po pomyślnej weryfikacji atrybutu przy użyciu metody <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A> obiekt <xref:System.Xml.Schema.XmlSchemaInfo> (jeśli jest określony) <xref:System.Xml.Schema.XmlSchemaInfo.SchemaAttribute%2A>, <xref:System.Xml.Schema.XmlSchemaInfo.SchemaType%2A>, <xref:System.Xml.Schema.XmlSchemaInfo.MemberType%2A> i <xref:System.Xml.Schema.XmlSchemaInfo.Validity%2A> właściwości są ustawiane z wynikami walidacji.</span><span class="sxs-lookup"><span data-stu-id="715d1-172">For example, upon successful validation of an attribute using the <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A> method, the <xref:System.Xml.Schema.XmlSchemaInfo> object's (if specified) <xref:System.Xml.Schema.XmlSchemaInfo.SchemaAttribute%2A>, <xref:System.Xml.Schema.XmlSchemaInfo.SchemaType%2A>, <xref:System.Xml.Schema.XmlSchemaInfo.MemberType%2A>, and <xref:System.Xml.Schema.XmlSchemaInfo.Validity%2A> properties are set with the results of the validation.</span></span>

<span data-ttu-id="715d1-173">Następujące metody klasy <xref:System.Xml.Schema.XmlSchemaValidator> akceptują obiekt <xref:System.Xml.Schema.XmlSchemaInfo> jako parametr out.</span><span class="sxs-lookup"><span data-stu-id="715d1-173">The following <xref:System.Xml.Schema.XmlSchemaValidator> class methods accept an <xref:System.Xml.Schema.XmlSchemaInfo> object as an out parameter.</span></span>

- <xref:System.Xml.Schema.XmlSchemaValidator.SkipToEndElement%2A>

- <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A>

- <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A>

- <xref:System.Xml.Schema.XmlSchemaValidator.ValidateElement%2A>

- <xref:System.Xml.Schema.XmlSchemaValidator.ValidateElement%2A>

- <xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndElement%2A>

- <xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndElement%2A>

- <xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndOfAttributes%2A>

<span data-ttu-id="715d1-174">Pełny przykład klasy <xref:System.Xml.Schema.XmlSchemaInfo> zawiera przykład we wprowadzeniu.</span><span class="sxs-lookup"><span data-stu-id="715d1-174">For a complete example of the <xref:System.Xml.Schema.XmlSchemaInfo> class, see the example in the introduction.</span></span> <span data-ttu-id="715d1-175">Aby uzyskać więcej informacji na temat klasy <xref:System.Xml.Schema.XmlSchemaInfo>, zapoznaj się z dokumentacją dotyczącą klasy <xref:System.Xml.Schema.XmlSchemaInfo>.</span><span class="sxs-lookup"><span data-stu-id="715d1-175">For more information about the <xref:System.Xml.Schema.XmlSchemaInfo> class, see the <xref:System.Xml.Schema.XmlSchemaInfo> class reference documentation.</span></span>

### <a name="retrieving-expected-particles-attributes-and-unspecified-default-attributes"></a><span data-ttu-id="715d1-176">Pobieranie oczekiwanych cząsteczek, atrybutów i nieokreślonych atrybutów domyślnych</span><span class="sxs-lookup"><span data-stu-id="715d1-176">Retrieving Expected Particles, Attributes, and Unspecified Default Attributes</span></span>

<span data-ttu-id="715d1-177">Klasa <xref:System.Xml.Schema.XmlSchemaValidator> udostępnia metody <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A>, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> i <xref:System.Xml.Schema.XmlSchemaValidator.GetUnspecifiedDefaultAttributes%2A>, aby pobrać oczekiwane cząstki, atrybuty i nieokreślone atrybuty domyślne w bieżącym kontekście walidacji.</span><span class="sxs-lookup"><span data-stu-id="715d1-177">The <xref:System.Xml.Schema.XmlSchemaValidator> class provides the <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A>, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A>, and <xref:System.Xml.Schema.XmlSchemaValidator.GetUnspecifiedDefaultAttributes%2A> methods to retrieve the expected particles, attributes, and unspecified default attributes in the current validation context.</span></span>

#### <a name="retrieving-expected-particles"></a><span data-ttu-id="715d1-178">Pobieranie oczekiwanych cząsteczek</span><span class="sxs-lookup"><span data-stu-id="715d1-178">Retrieving Expected Particles</span></span>

<span data-ttu-id="715d1-179">Metoda <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> zwraca tablicę obiektów <xref:System.Xml.Schema.XmlSchemaParticle> zawierających oczekiwane cząstki w bieżącym kontekście elementu.</span><span class="sxs-lookup"><span data-stu-id="715d1-179">The <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> method returns an array of <xref:System.Xml.Schema.XmlSchemaParticle> objects containing the expected particles in the current element context.</span></span> <span data-ttu-id="715d1-180">Prawidłowe cząstki, które mogą być zwracane przez metodę <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A>, są wystąpieniami <xref:System.Xml.Schema.XmlSchemaElement> i <xref:System.Xml.Schema.XmlSchemaAny> klas.</span><span class="sxs-lookup"><span data-stu-id="715d1-180">The valid particles that can be returned by the <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> method are instances of the <xref:System.Xml.Schema.XmlSchemaElement> and <xref:System.Xml.Schema.XmlSchemaAny> classes.</span></span>

<span data-ttu-id="715d1-181">Gdy compositor dla modelu zawartości jest `xs:sequence`, zwracana jest tylko Następna cząstka w sekwencji.</span><span class="sxs-lookup"><span data-stu-id="715d1-181">When the compositor for the content model is an `xs:sequence`, only the next particle in the sequence is returned.</span></span> <span data-ttu-id="715d1-182">Jeśli compositor dla modelu zawartości to `xs:all` lub `xs:choice`, zwracane są wszystkie prawidłowe cząstki, które mogą się pojawić w kontekście bieżącego elementu.</span><span class="sxs-lookup"><span data-stu-id="715d1-182">If the compositor for the content model is an `xs:all` or an `xs:choice`, then all valid particles that could follow in the current element context are returned.</span></span>

> [!NOTE]
> <span data-ttu-id="715d1-183">Jeśli metoda <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> jest wywoływana natychmiast po wywołaniu metody <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A>, Metoda <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> zwróci wszystkie elementy globalne.</span><span class="sxs-lookup"><span data-stu-id="715d1-183">If the <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> method is called immediately after calling the <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> method, the <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> method returns all global elements.</span></span>

<span data-ttu-id="715d1-184">Na przykład, w schemacie języka definicji schematu XML (XSD) i w poniższym dokumencie XML po walidacji elementu `book` element `book` jest bieżącym kontekstem elementu.</span><span class="sxs-lookup"><span data-stu-id="715d1-184">For example, in the XML Schema Definition Language (XSD) schema and XML document that follow, after validating the `book` element, the `book` element is the current element context.</span></span> <span data-ttu-id="715d1-185">Metoda <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> zwraca tablicę zawierającą jeden obiekt <xref:System.Xml.Schema.XmlSchemaElement> reprezentujący element `title`.</span><span class="sxs-lookup"><span data-stu-id="715d1-185">The <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> method returns an array containing a single <xref:System.Xml.Schema.XmlSchemaElement> object representing the `title` element.</span></span> <span data-ttu-id="715d1-186">Gdy kontekst walidacji jest elementem `title`, Metoda <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> zwraca pustą tablicę.</span><span class="sxs-lookup"><span data-stu-id="715d1-186">When the validation context is the `title` element, the <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> method returns an empty array.</span></span> <span data-ttu-id="715d1-187">Jeśli metoda <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> jest wywoływana po sprawdzeniu poprawności elementu `title`, ale przed zweryfikowaniem elementu `description` zwraca tablicę zawierającą pojedynczy obiekt <xref:System.Xml.Schema.XmlSchemaElement> reprezentujący element `description`.</span><span class="sxs-lookup"><span data-stu-id="715d1-187">If the <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> method is called after the `title` element has been validated but before the `description` element has been validated, it returns an array containing a single <xref:System.Xml.Schema.XmlSchemaElement> object representing the `description` element.</span></span> <span data-ttu-id="715d1-188">Jeśli metoda <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> jest wywoływana po sprawdzeniu poprawności elementu `description`, zwraca tablicę zawierającą pojedynczy obiekt <xref:System.Xml.Schema.XmlSchemaAny> reprezentujący symbol wieloznaczny.</span><span class="sxs-lookup"><span data-stu-id="715d1-188">If the <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> method is called after the `description` element has been validated then it returns an array containing a single <xref:System.Xml.Schema.XmlSchemaAny> object representing the wildcard.</span></span>

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

 <span data-ttu-id="715d1-189">Przykład pobiera następujący kod XML jako dane wejściowe:</span><span class="sxs-lookup"><span data-stu-id="715d1-189">The example takes the following XML as input:</span></span>

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

<span data-ttu-id="715d1-190">Przykład pobiera następujący schemat XSD jako dane wejściowe:</span><span class="sxs-lookup"><span data-stu-id="715d1-190">The example takes the following XSD schema as input:</span></span>

```xml
<book>
  <title>My Book</title>
  <description>My Book's Description</description>
  <namespace>System.Xml.Schema</namespace>
</book>
```

> [!NOTE]
> <span data-ttu-id="715d1-191">Wyniki <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A>, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> i <xref:System.Xml.Schema.XmlSchemaValidator.AddSchema%2A> klasy <xref:System.Xml.Schema.XmlSchemaValidator> są zależne od bieżącego kontekstu, który jest sprawdzany.</span><span class="sxs-lookup"><span data-stu-id="715d1-191">The results of the <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A>, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A>, and <xref:System.Xml.Schema.XmlSchemaValidator.AddSchema%2A> methods of the <xref:System.Xml.Schema.XmlSchemaValidator> class are dependent on the current context being validated.</span></span> <span data-ttu-id="715d1-192">Aby uzyskać więcej informacji, zobacz sekcję "kontekst walidacji" w tym temacie.</span><span class="sxs-lookup"><span data-stu-id="715d1-192">For more information, see the "Validation Context" section of this topic.</span></span>

<span data-ttu-id="715d1-193">Przykład metody <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> zawiera przykład we wprowadzeniu.</span><span class="sxs-lookup"><span data-stu-id="715d1-193">For an example of the <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> method, see the example in the introduction.</span></span> <span data-ttu-id="715d1-194">Więcej informacji o metodzie <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> znajduje się w dokumentacji dotyczącej klasy <xref:System.Xml.Schema.XmlSchemaValidator>.</span><span class="sxs-lookup"><span data-stu-id="715d1-194">For more information about the <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> method, see the <xref:System.Xml.Schema.XmlSchemaValidator> class reference documentation.</span></span>

#### <a name="retrieving-expected-attributes"></a><span data-ttu-id="715d1-195">Pobieranie oczekiwanych atrybutów</span><span class="sxs-lookup"><span data-stu-id="715d1-195">Retrieving Expected Attributes</span></span>

<span data-ttu-id="715d1-196">Metoda <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> zwraca tablicę obiektów <xref:System.Xml.Schema.XmlSchemaAttribute> zawierających oczekiwane atrybuty w kontekście bieżącego elementu.</span><span class="sxs-lookup"><span data-stu-id="715d1-196">The <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> method returns an array of <xref:System.Xml.Schema.XmlSchemaAttribute> objects containing the expected attributes in the current element context.</span></span>

<span data-ttu-id="715d1-197">Na przykład w przykładzie we wprowadzeniu Metoda <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> służy do pobierania wszystkich atrybutów elementu `book`.</span><span class="sxs-lookup"><span data-stu-id="715d1-197">For example, in the example in the introduction, the <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> method is used to retrieve all the attributes of the `book` element.</span></span>

<span data-ttu-id="715d1-198">Jeśli wywołasz metodę <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> bezpośrednio po metodzie <xref:System.Xml.Schema.XmlSchemaValidator.ValidateElement%2A>, zwracane są wszystkie atrybuty, które mogą pojawić się w dokumencie XML.</span><span class="sxs-lookup"><span data-stu-id="715d1-198">If you call the <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> method immediately after the <xref:System.Xml.Schema.XmlSchemaValidator.ValidateElement%2A> method, all the attributes that could appear in the XML document are returned.</span></span> <span data-ttu-id="715d1-199">Jeśli jednak wywołasz metodę <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> po jednym lub większej liczbie wywołań metody <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A>, zwracane są atrybuty, które nie zostały jeszcze zweryfikowane dla bieżącego elementu.</span><span class="sxs-lookup"><span data-stu-id="715d1-199">However, if you call the <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> method after one or more calls to the <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A> method, the attributes that have not yet been validated for the current element are returned.</span></span>

> [!NOTE]
> <span data-ttu-id="715d1-200">Wyniki <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A>, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> i <xref:System.Xml.Schema.XmlSchemaValidator.AddSchema%2A> klasy <xref:System.Xml.Schema.XmlSchemaValidator> są zależne od bieżącego kontekstu, który jest sprawdzany.</span><span class="sxs-lookup"><span data-stu-id="715d1-200">The results of the <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A>, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A>, and <xref:System.Xml.Schema.XmlSchemaValidator.AddSchema%2A> methods of the <xref:System.Xml.Schema.XmlSchemaValidator> class are dependent on the current context being validated.</span></span> <span data-ttu-id="715d1-201">Aby uzyskać więcej informacji, zobacz sekcję "kontekst walidacji" w tym temacie.</span><span class="sxs-lookup"><span data-stu-id="715d1-201">For more information, see the "Validation Context" section of this topic.</span></span>

<span data-ttu-id="715d1-202">Przykład metody <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> zawiera przykład we wprowadzeniu.</span><span class="sxs-lookup"><span data-stu-id="715d1-202">For an example of the <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> method, see the example in the introduction.</span></span> <span data-ttu-id="715d1-203">Więcej informacji o metodzie <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> znajduje się w dokumentacji dotyczącej klasy <xref:System.Xml.Schema.XmlSchemaValidator>.</span><span class="sxs-lookup"><span data-stu-id="715d1-203">For more information about the <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> method, see the <xref:System.Xml.Schema.XmlSchemaValidator> class reference documentation.</span></span>

#### <a name="retrieving-unspecified-default-attributes"></a><span data-ttu-id="715d1-204">Pobieranie nieokreślonych atrybutów domyślnych</span><span class="sxs-lookup"><span data-stu-id="715d1-204">Retrieving Unspecified Default Attributes</span></span>

<span data-ttu-id="715d1-205">Metoda <xref:System.Xml.Schema.XmlSchemaValidator.GetUnspecifiedDefaultAttributes%2A> wypełnia <xref:System.Collections.ArrayList> określone za pomocą obiektów <xref:System.Xml.Schema.XmlSchemaAttribute> dla wszystkich atrybutów z wartościami domyślnymi, które nie zostały wcześniej zweryfikowane przy użyciu metody <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A> w kontekście elementu.</span><span class="sxs-lookup"><span data-stu-id="715d1-205">The <xref:System.Xml.Schema.XmlSchemaValidator.GetUnspecifiedDefaultAttributes%2A> method populates the <xref:System.Collections.ArrayList> specified with <xref:System.Xml.Schema.XmlSchemaAttribute> objects for any attributes with default values that have not been previously validated using the <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A> method in the element context.</span></span> <span data-ttu-id="715d1-206">Metoda <xref:System.Xml.Schema.XmlSchemaValidator.GetUnspecifiedDefaultAttributes%2A> powinna być wywoływana po wywołaniu metody <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A> dla każdego atrybutu w kontekście elementu.</span><span class="sxs-lookup"><span data-stu-id="715d1-206">The <xref:System.Xml.Schema.XmlSchemaValidator.GetUnspecifiedDefaultAttributes%2A> method should be called after calling the <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A> method on each attribute in the element context.</span></span> <span data-ttu-id="715d1-207">Metoda <xref:System.Xml.Schema.XmlSchemaValidator.GetUnspecifiedDefaultAttributes%2A> powinna zostać użyta do określenia, jakie atrybuty domyślne mają zostać wstawione do zweryfikowanego dokumentu XML.</span><span class="sxs-lookup"><span data-stu-id="715d1-207">The <xref:System.Xml.Schema.XmlSchemaValidator.GetUnspecifiedDefaultAttributes%2A> method should be used to determine what default attributes are to be inserted into the XML document being validated.</span></span>

<span data-ttu-id="715d1-208">Więcej informacji o metodzie <xref:System.Xml.Schema.XmlSchemaValidator.GetUnspecifiedDefaultAttributes%2A> znajduje się w dokumentacji dotyczącej klasy <xref:System.Xml.Schema.XmlSchemaValidator>.</span><span class="sxs-lookup"><span data-stu-id="715d1-208">For more information about the <xref:System.Xml.Schema.XmlSchemaValidator.GetUnspecifiedDefaultAttributes%2A> method, see the <xref:System.Xml.Schema.XmlSchemaValidator> class reference documentation.</span></span>

### <a name="handling-schema-validation-events"></a><span data-ttu-id="715d1-209">Obsługa zdarzeń walidacji schematu</span><span class="sxs-lookup"><span data-stu-id="715d1-209">Handling Schema Validation Events</span></span>

<span data-ttu-id="715d1-210">Ostrzeżenia i błędy walidacji schematu napotkane podczas walidacji są obsługiwane przez zdarzenie <xref:System.Xml.Schema.XmlSchemaValidator.ValidationEventHandler> klasy <xref:System.Xml.Schema.XmlSchemaValidator>.</span><span class="sxs-lookup"><span data-stu-id="715d1-210">Schema validation warnings and errors encountered during validation are handled by the <xref:System.Xml.Schema.XmlSchemaValidator.ValidationEventHandler> event of the <xref:System.Xml.Schema.XmlSchemaValidator> class.</span></span>

<span data-ttu-id="715d1-211">Ostrzeżenia @no__t dotyczące walidacji schematu mają wartość <xref:System.Xml.Schema.XmlSeverityType> i błędy walidacji schematu mają wartość <xref:System.Xml.Schema.XmlSeverityType> <xref:System.Xml.Schema.XmlSeverityType.Error>.</span><span class="sxs-lookup"><span data-stu-id="715d1-211">Schema validation warnings have an <xref:System.Xml.Schema.XmlSeverityType> value of <xref:System.Xml.Schema.XmlSeverityType.Warning> and schema validation errors have an <xref:System.Xml.Schema.XmlSeverityType> value of <xref:System.Xml.Schema.XmlSeverityType.Error>.</span></span> <span data-ttu-id="715d1-212">Jeśli nie przypisano <xref:System.Xml.Schema.XmlSchemaValidator.ValidationEventHandler>, zostanie zgłoszony <xref:System.Xml.Schema.XmlSchemaValidationException> dla wszystkich błędów walidacji schematu z wartością <xref:System.Xml.Schema.XmlSeverityType> <xref:System.Xml.Schema.XmlSeverityType.Error>.</span><span class="sxs-lookup"><span data-stu-id="715d1-212">If no <xref:System.Xml.Schema.XmlSchemaValidator.ValidationEventHandler> has been assigned, an <xref:System.Xml.Schema.XmlSchemaValidationException> is thrown for all schema validation errors with an <xref:System.Xml.Schema.XmlSeverityType> value of <xref:System.Xml.Schema.XmlSeverityType.Error>.</span></span> <span data-ttu-id="715d1-213">Jednak <xref:System.Xml.Schema.XmlSchemaValidationException> nie jest generowany w przypadku ostrzeżeń dotyczących sprawdzania poprawności schematu z wartością <xref:System.Xml.Schema.XmlSeverityType> <xref:System.Xml.Schema.XmlSeverityType.Warning>.</span><span class="sxs-lookup"><span data-stu-id="715d1-213">However, an <xref:System.Xml.Schema.XmlSchemaValidationException> is not thrown for schema validation warnings with an <xref:System.Xml.Schema.XmlSeverityType> value of <xref:System.Xml.Schema.XmlSeverityType.Warning>.</span></span>

<span data-ttu-id="715d1-214">Poniżej znajduje się przykład <xref:System.Xml.Schema.ValidationEventHandler>, który odbiera ostrzeżenia i błędy walidacji schematu, które zostały wykryte podczas walidacji schematu z przykładu we wprowadzeniu.</span><span class="sxs-lookup"><span data-stu-id="715d1-214">The following is an example of a <xref:System.Xml.Schema.ValidationEventHandler> that receives schema validation warnings and errors encountered during schema validation taken from the example in the introduction.</span></span>

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

<span data-ttu-id="715d1-215">Pełny przykład <xref:System.Xml.Schema.ValidationEventHandler> zawiera przykład we wprowadzeniu.</span><span class="sxs-lookup"><span data-stu-id="715d1-215">For a complete example of the <xref:System.Xml.Schema.ValidationEventHandler>, see the example in the introduction.</span></span> <span data-ttu-id="715d1-216">Więcej informacji można znaleźć w dokumentacji dotyczącej klasy <xref:System.Xml.Schema.XmlSchemaInfo>.</span><span class="sxs-lookup"><span data-stu-id="715d1-216">For more information, see the <xref:System.Xml.Schema.XmlSchemaInfo> class reference documentation.</span></span>

## <a name="xmlschemavalidator-state-transition"></a><span data-ttu-id="715d1-217">XmlSchemaValidator stanu przejścia</span><span class="sxs-lookup"><span data-stu-id="715d1-217">XmlSchemaValidator State Transition</span></span>

<span data-ttu-id="715d1-218">Klasa <xref:System.Xml.Schema.XmlSchemaValidator> ma zdefiniowane przejście stanu, które wymusza sekwencję i wystąpienia wywołań wykonanych dla każdej metody używanej do sprawdzania poprawności elementów, atrybutów i zawartości w sprawdzonych XML.</span><span class="sxs-lookup"><span data-stu-id="715d1-218">The <xref:System.Xml.Schema.XmlSchemaValidator> class has a defined state transition that enforces the sequence and occurrence of calls made to each of the methods used to validate elements, attributes, and content in an XML infoset.</span></span>

<span data-ttu-id="715d1-219">W poniższej tabeli opisano przechodzenie stanu klasy <xref:System.Xml.Schema.XmlSchemaValidator> oraz sekwencję i wystąpienia wywołań metod, które można wykonać w każdym stanie.</span><span class="sxs-lookup"><span data-stu-id="715d1-219">The following table describes the state transition of the <xref:System.Xml.Schema.XmlSchemaValidator> class, and the sequence and occurrence of method calls that can be made in each state.</span></span>

|<span data-ttu-id="715d1-220">Stan</span><span class="sxs-lookup"><span data-stu-id="715d1-220">State</span></span>|<span data-ttu-id="715d1-221">Przejście</span><span class="sxs-lookup"><span data-stu-id="715d1-221">Transition</span></span>|
|-----------|----------------|
|<span data-ttu-id="715d1-222">Walidacja</span><span class="sxs-lookup"><span data-stu-id="715d1-222">Validate</span></span>|<span data-ttu-id="715d1-223"><xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> (<xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A> &#124; TopLevel \*) <xref:System.Xml.Schema.XmlSchemaValidator.EndValidation%2A></span><span class="sxs-lookup"><span data-stu-id="715d1-223"><xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> (<xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A> &#124; TopLevel\*) <xref:System.Xml.Schema.XmlSchemaValidator.EndValidation%2A></span></span>|
|<span data-ttu-id="715d1-224">TopLevel</span><span class="sxs-lookup"><span data-stu-id="715d1-224">TopLevel</span></span>|<span data-ttu-id="715d1-225"><xref:System.Xml.Schema.XmlSchemaValidator.ValidateWhitespace%2A> &#124; <xref:System.Xml.Schema.XmlSchemaValidator.ValidateText%2A> &#124; elementu</span><span class="sxs-lookup"><span data-stu-id="715d1-225"><xref:System.Xml.Schema.XmlSchemaValidator.ValidateWhitespace%2A> &#124; <xref:System.Xml.Schema.XmlSchemaValidator.ValidateText%2A> &#124; Element</span></span>|
|<span data-ttu-id="715d1-226">Element</span><span class="sxs-lookup"><span data-stu-id="715d1-226">Element</span></span>|<span data-ttu-id="715d1-227"><xref:System.Xml.Schema.XmlSchemaValidator.ValidateElement%2A> <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A> \* (w <xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndOfAttributes%2A> zawartość @ no__t-3)?</span><span class="sxs-lookup"><span data-stu-id="715d1-227"><xref:System.Xml.Schema.XmlSchemaValidator.ValidateElement%2A> <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A>\* (<xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndOfAttributes%2A> Content\*)?</span></span> <span data-ttu-id="715d1-228"><xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndElement%2A>&#124;</span><span class="sxs-lookup"><span data-stu-id="715d1-228"><xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndElement%2A> &#124;</span></span><br /><br /> <span data-ttu-id="715d1-229"><xref:System.Xml.Schema.XmlSchemaValidator.ValidateElement%2A> <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A> @ no__t-2 <xref:System.Xml.Schema.XmlSchemaValidator.SkipToEndElement%2A>&#124;</span><span class="sxs-lookup"><span data-stu-id="715d1-229"><xref:System.Xml.Schema.XmlSchemaValidator.ValidateElement%2A> <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A>\* <xref:System.Xml.Schema.XmlSchemaValidator.SkipToEndElement%2A> &#124;</span></span><br /><br /> <span data-ttu-id="715d1-230"><xref:System.Xml.Schema.XmlSchemaValidator.ValidateElement%2A> <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A> @ no__t-2 <xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndOfAttributes%2A> zawartość @ no__t-4 <xref:System.Xml.Schema.XmlSchemaValidator.SkipToEndElement%2A>&#124;</span><span class="sxs-lookup"><span data-stu-id="715d1-230"><xref:System.Xml.Schema.XmlSchemaValidator.ValidateElement%2A> <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A>\* <xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndOfAttributes%2A> Content\* <xref:System.Xml.Schema.XmlSchemaValidator.SkipToEndElement%2A> &#124;</span></span>|
|<span data-ttu-id="715d1-231">Zawartość</span><span class="sxs-lookup"><span data-stu-id="715d1-231">Content</span></span>|<span data-ttu-id="715d1-232"><xref:System.Xml.Schema.XmlSchemaValidator.ValidateWhitespace%2A> &#124; <xref:System.Xml.Schema.XmlSchemaValidator.ValidateText%2A> &#124; elementu</span><span class="sxs-lookup"><span data-stu-id="715d1-232"><xref:System.Xml.Schema.XmlSchemaValidator.ValidateWhitespace%2A> &#124; <xref:System.Xml.Schema.XmlSchemaValidator.ValidateText%2A> &#124; Element</span></span>|

> [!NOTE]
> <span data-ttu-id="715d1-233">@No__t-0 jest generowany przez każdą metodę w powyższej tabeli, gdy wywołanie metody jest wykonywane w niepoprawnej sekwencji zgodnie z bieżącym stanem obiektu <xref:System.Xml.Schema.XmlSchemaValidator>.</span><span class="sxs-lookup"><span data-stu-id="715d1-233">An <xref:System.InvalidOperationException> is thrown by each of the methods in the table above when the call to the method is made in the incorrect sequence according to the current state of an <xref:System.Xml.Schema.XmlSchemaValidator> object.</span></span>

<span data-ttu-id="715d1-234">W powyższej tabeli przechodzenia stanu są używane symbole interpunkcyjne do opisywania metod i innych stanów, które mogą być wywoływane dla każdego stanu przejścia stanu dla klasy <xref:System.Xml.Schema.XmlSchemaValidator>.</span><span class="sxs-lookup"><span data-stu-id="715d1-234">The state transition table above uses punctuation symbols to describe the methods and other states that can be called for each state of the state transition of the <xref:System.Xml.Schema.XmlSchemaValidator> class.</span></span> <span data-ttu-id="715d1-235">Używane symbole są tymi samymi symbolami, które znajdują się w dokumentacji XML Standards dla definicji typu dokumentu (DTD).</span><span class="sxs-lookup"><span data-stu-id="715d1-235">The symbols used are the same symbols found in the XML Standards reference for Document Type Definition (DTD).</span></span>

<span data-ttu-id="715d1-236">W poniższej tabeli opisano, jak symbole interpunkcji Znalezione w powyższej tabeli przejścia stanu mają wpływ na metody i inne Stany, które mogą być wywoływane dla każdego stanu w fazie przejścia stanu klasy <xref:System.Xml.Schema.XmlSchemaValidator>.</span><span class="sxs-lookup"><span data-stu-id="715d1-236">The following table describes how the punctuation symbols found in the state transition table above affect the methods and other states that can be called for each state in the state transition of the <xref:System.Xml.Schema.XmlSchemaValidator> class.</span></span>

|<span data-ttu-id="715d1-237">Symboliczn</span><span class="sxs-lookup"><span data-stu-id="715d1-237">Symbol</span></span>|<span data-ttu-id="715d1-238">Opis</span><span class="sxs-lookup"><span data-stu-id="715d1-238">Description</span></span>|
|------------|-----------------|
|<span data-ttu-id="715d1-239">&#124;</span><span class="sxs-lookup"><span data-stu-id="715d1-239">&#124;</span></span>|<span data-ttu-id="715d1-240">Można wywołać metodę lub stan (jeden przed paskiem lub po nim).</span><span class="sxs-lookup"><span data-stu-id="715d1-240">Either method or state (the one before the bar or the one after it) can be called.</span></span>|
|<span data-ttu-id="715d1-241">?</span><span class="sxs-lookup"><span data-stu-id="715d1-241">?</span></span>|<span data-ttu-id="715d1-242">Metoda lub stan, który poprzedza znak zapytania, jest opcjonalne, ale jeśli jest wywoływana, może być wywoływana tylko raz.</span><span class="sxs-lookup"><span data-stu-id="715d1-242">The method or state that precedes the question mark is optional but if it is called it can only be called once.</span></span>|
|*|<span data-ttu-id="715d1-243">Metoda lub stan poprzedzający symbol \* jest opcjonalny i może być wywoływana więcej niż raz.</span><span class="sxs-lookup"><span data-stu-id="715d1-243">The method or state that precedes the \* symbol is optional, and can be called more than once.</span></span>|

## <a name="validation-context"></a><span data-ttu-id="715d1-244">Kontekst walidacji</span><span class="sxs-lookup"><span data-stu-id="715d1-244">Validation Context</span></span>

<span data-ttu-id="715d1-245">Metody klasy <xref:System.Xml.Schema.XmlSchemaValidator> używane do walidacji elementów, atrybutów i zawartości w sprawdzonych XML, zmiana kontekstu walidacji obiektu <xref:System.Xml.Schema.XmlSchemaValidator>.</span><span class="sxs-lookup"><span data-stu-id="715d1-245">The methods of the <xref:System.Xml.Schema.XmlSchemaValidator> class used to validate elements, attributes, and content in an XML infoset, change the validation context of an <xref:System.Xml.Schema.XmlSchemaValidator> object.</span></span> <span data-ttu-id="715d1-246">Na przykład Metoda <xref:System.Xml.Schema.XmlSchemaValidator.SkipToEndElement%2A> pomija walidację zawartości bieżącego elementu i przygotowuje obiekt <xref:System.Xml.Schema.XmlSchemaValidator> do walidacji zawartości w kontekście elementu nadrzędnego. jest równoważne pominięciu weryfikacji dla wszystkich elementów podrzędnych bieżącego elementu, a następnie wywołania metody <xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndElement%2A>.</span><span class="sxs-lookup"><span data-stu-id="715d1-246">For example, the <xref:System.Xml.Schema.XmlSchemaValidator.SkipToEndElement%2A> method skips validation of the current element content and prepares the <xref:System.Xml.Schema.XmlSchemaValidator> object to validate content in the parent element's context; it is equivalent to skipping validation for all the children of the current element and then calling the <xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndElement%2A> method.</span></span>

<span data-ttu-id="715d1-247">Wyniki <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A>, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> i <xref:System.Xml.Schema.XmlSchemaValidator.AddSchema%2A> klasy <xref:System.Xml.Schema.XmlSchemaValidator> są zależne od bieżącego kontekstu, który jest sprawdzany.</span><span class="sxs-lookup"><span data-stu-id="715d1-247">The results of the <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A>, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A>, and <xref:System.Xml.Schema.XmlSchemaValidator.AddSchema%2A> methods of the <xref:System.Xml.Schema.XmlSchemaValidator> class are dependent on the current context being validated.</span></span>

<span data-ttu-id="715d1-248">W poniższej tabeli opisano wyniki wywołania tych metod po wywołaniu jednej z metod klasy <xref:System.Xml.Schema.XmlSchemaValidator> używanej do sprawdzania poprawności elementów, atrybutów i zawartości w sprawdzonych XML.</span><span class="sxs-lookup"><span data-stu-id="715d1-248">The following table describes the results of calling these methods after calling one of the methods of the <xref:System.Xml.Schema.XmlSchemaValidator> class used to validate elements, attributes, and content in an XML infoset.</span></span>

|<span data-ttu-id="715d1-249">Metoda</span><span class="sxs-lookup"><span data-stu-id="715d1-249">Method</span></span>|<span data-ttu-id="715d1-250">GetExpectedParticles</span><span class="sxs-lookup"><span data-stu-id="715d1-250">GetExpectedParticles</span></span>|<span data-ttu-id="715d1-251">GetExpectedAttributes</span><span class="sxs-lookup"><span data-stu-id="715d1-251">GetExpectedAttributes</span></span>|<span data-ttu-id="715d1-252">AddSchema</span><span class="sxs-lookup"><span data-stu-id="715d1-252">AddSchema</span></span>|
|------------|--------------------------|---------------------------|---------------|
|<xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A>|<span data-ttu-id="715d1-253">Jeśli domyślna metoda <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> jest wywoływana, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> zwraca tablicę zawierającą wszystkie elementy globalne.</span><span class="sxs-lookup"><span data-stu-id="715d1-253">If the default <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> method is called, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> returns an array containing all global elements.</span></span><br /><br /> <span data-ttu-id="715d1-254">Jeśli przeciążona metoda <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> pobierająca <xref:System.Xml.Schema.XmlSchemaObject> jako parametr jest wywoływana w celu zainicjowania częściowej walidacji elementu, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> zwraca tylko element, do którego zainicjowano obiekt <xref:System.Xml.Schema.XmlSchemaValidator>.</span><span class="sxs-lookup"><span data-stu-id="715d1-254">If the overloaded <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> method that takes an <xref:System.Xml.Schema.XmlSchemaObject> as a parameter is called to initialize partial validation of an element, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> returns only the element to which the <xref:System.Xml.Schema.XmlSchemaValidator> object was initialized.</span></span>|<span data-ttu-id="715d1-255">Jeśli zostanie wywołana domyślna metoda <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A>, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> zwróci pustą tablicę.</span><span class="sxs-lookup"><span data-stu-id="715d1-255">If the default <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> method is called, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> returns an empty array.</span></span><br /><br /> <span data-ttu-id="715d1-256">W przypadku przeciążenia metody <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> pobierającej <xref:System.Xml.Schema.XmlSchemaObject> jako parametr w celu zainicjowania częściowej walidacji atrybutu, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> zwraca tylko atrybut, do którego zainicjowano obiekt <xref:System.Xml.Schema.XmlSchemaValidator>.</span><span class="sxs-lookup"><span data-stu-id="715d1-256">If the overload of the <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> method that takes an <xref:System.Xml.Schema.XmlSchemaObject> as a parameter is called to initialize partial validation of an attribute, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> returns only the attribute to which the <xref:System.Xml.Schema.XmlSchemaValidator> object was initialized.</span></span>|<span data-ttu-id="715d1-257">Dodaje schemat do <xref:System.Xml.Schema.XmlSchemaSet> obiektu <xref:System.Xml.Schema.XmlSchemaValidator>, jeśli nie ma żadnych błędów przetwarzania wstępnego.</span><span class="sxs-lookup"><span data-stu-id="715d1-257">Adds the schema to the <xref:System.Xml.Schema.XmlSchemaSet> of the <xref:System.Xml.Schema.XmlSchemaValidator> object if it has no preprocessing errors.</span></span>|
|<xref:System.Xml.Schema.XmlSchemaValidator.ValidateElement%2A>|<span data-ttu-id="715d1-258">Jeśli element kontekstu jest prawidłowy, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> zwraca sekwencję elementów oczekiwanych jako elementy podrzędne elementu kontekstu.</span><span class="sxs-lookup"><span data-stu-id="715d1-258">If the context element is valid, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> returns the sequence of elements expected as children of the context element.</span></span><br /><br /> <span data-ttu-id="715d1-259">Jeśli element context jest nieprawidłowy, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> zwraca pustą tablicę.</span><span class="sxs-lookup"><span data-stu-id="715d1-259">If the context element is invalid, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> returns an empty array.</span></span>|<span data-ttu-id="715d1-260">Jeśli element context jest prawidłowy i jeśli żadne wywołanie do <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A> nie zostało wcześniej wykonane, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> zwraca listę wszystkich atrybutów zdefiniowanych w elemencie Context.</span><span class="sxs-lookup"><span data-stu-id="715d1-260">If the context element is valid, and if no call to <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A> has been previously made, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> returns a list of all the attributes defined on the context element.</span></span><br /><br /> <span data-ttu-id="715d1-261">Jeśli niektóre atrybuty zostały już sprawdzone, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> zwraca listę pozostałych atrybutów do zweryfikowania.</span><span class="sxs-lookup"><span data-stu-id="715d1-261">If some attributes have already been validated, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> returns a list of the remaining attributes to be validated.</span></span><br /><br /> <span data-ttu-id="715d1-262">Jeśli element context jest nieprawidłowy, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> zwraca pustą tablicę.</span><span class="sxs-lookup"><span data-stu-id="715d1-262">If the context element is invalid, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> returns an empty array.</span></span>|<span data-ttu-id="715d1-263">Tak samo jak powyżej.</span><span class="sxs-lookup"><span data-stu-id="715d1-263">Same as above.</span></span>|
|<xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A>|<span data-ttu-id="715d1-264">Jeśli atrybut kontekstu jest atrybutem najwyższego poziomu, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> zwraca pustą tablicę.</span><span class="sxs-lookup"><span data-stu-id="715d1-264">If the context attribute is a top-level attribute, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> returns an empty array.</span></span><br /><br /> <span data-ttu-id="715d1-265">W przeciwnym razie <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> zwraca sekwencję elementów oczekiwanych jako pierwszy element podrzędny elementu kontekstu.</span><span class="sxs-lookup"><span data-stu-id="715d1-265">Otherwise <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> returns the sequence of elements expected as the first child of the context element.</span></span>|<span data-ttu-id="715d1-266">Jeśli atrybut kontekstu jest atrybutem najwyższego poziomu, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> zwraca pustą tablicę.</span><span class="sxs-lookup"><span data-stu-id="715d1-266">If the context attribute is a top-level attribute, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> returns an empty array.</span></span><br /><br /> <span data-ttu-id="715d1-267">W przeciwnym razie <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> zwraca listę pozostałych atrybutów do zweryfikowania.</span><span class="sxs-lookup"><span data-stu-id="715d1-267">Otherwise <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> returns the list of remaining attributes to be validated.</span></span>|<span data-ttu-id="715d1-268">Tak samo jak powyżej.</span><span class="sxs-lookup"><span data-stu-id="715d1-268">Same as above.</span></span>|
|<xref:System.Xml.Schema.XmlSchemaValidator.GetUnspecifiedDefaultAttributes%2A>|<span data-ttu-id="715d1-269"><xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> zwraca sekwencję elementów oczekiwaną jako pierwszy element podrzędny elementu kontekstu.</span><span class="sxs-lookup"><span data-stu-id="715d1-269"><xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> returns the sequence of elements expected as the first child of the context element.</span></span>|<span data-ttu-id="715d1-270"><xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> zwraca listę wymaganych i opcjonalnych atrybutów, które nie zostały jeszcze zweryfikowane dla elementu kontekstu.</span><span class="sxs-lookup"><span data-stu-id="715d1-270"><xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> returns a list of the required and optional attributes that are yet to be validated for the context element.</span></span>|<span data-ttu-id="715d1-271">Tak samo jak powyżej.</span><span class="sxs-lookup"><span data-stu-id="715d1-271">Same as above.</span></span>|
|<xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndOfAttributes%2A>|<span data-ttu-id="715d1-272"><xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> zwraca sekwencję elementów oczekiwaną jako pierwszy element podrzędny elementu kontekstu.</span><span class="sxs-lookup"><span data-stu-id="715d1-272"><xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> returns the sequence of elements expected as the first child of the context element.</span></span>|<span data-ttu-id="715d1-273"><xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> zwraca pustą tablicę.</span><span class="sxs-lookup"><span data-stu-id="715d1-273"><xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> returns an empty array.</span></span>|<span data-ttu-id="715d1-274">Tak samo jak powyżej.</span><span class="sxs-lookup"><span data-stu-id="715d1-274">Same as above.</span></span>|
|<xref:System.Xml.Schema.XmlSchemaValidator.ValidateText%2A>|<span data-ttu-id="715d1-275">Jeśli element ContentType elementu context jest mieszany, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> zwraca sekwencję elementów oczekiwanych w następnym położeniu.</span><span class="sxs-lookup"><span data-stu-id="715d1-275">If the context element's contentType is Mixed, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> returns the sequence of elements expected in the next position.</span></span><br /><br /> <span data-ttu-id="715d1-276">Jeśli element ContentType elementu ContextType ma wartość textOnly lub Empty, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> zwraca pustą tablicę.</span><span class="sxs-lookup"><span data-stu-id="715d1-276">If the context element's contentType is TextOnly or Empty, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> returns an empty array.</span></span><br /><br /> <span data-ttu-id="715d1-277">Jeśli element ContentType elementu ContextType to ElementOnly, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> zwraca sekwencję elementów oczekiwanych w następnej pozycji, ale wystąpił błąd sprawdzania poprawności.</span><span class="sxs-lookup"><span data-stu-id="715d1-277">If the context element's contentType is ElementOnly, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> returns the sequence of elements expected in the next position but a validation error has already occurred.</span></span>|<span data-ttu-id="715d1-278"><xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> zwraca listę niezweryfikowanych elementów kontekstu.</span><span class="sxs-lookup"><span data-stu-id="715d1-278"><xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> returns the context element's list of attributes not validated.</span></span>|<span data-ttu-id="715d1-279">Tak samo jak powyżej.</span><span class="sxs-lookup"><span data-stu-id="715d1-279">Same as above.</span></span>|
|<xref:System.Xml.Schema.XmlSchemaValidator.ValidateWhitespace%2A>|<span data-ttu-id="715d1-280">Jeśli odstępy między kontekstami jest odstępem najwyższego poziomu, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> zwraca pustą tablicę.</span><span class="sxs-lookup"><span data-stu-id="715d1-280">If the context white-space is top-level white-space, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> returns an empty array.</span></span><br /><br /> <span data-ttu-id="715d1-281">W przeciwnym razie zachowanie metody <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> jest takie samo jak w <xref:System.Xml.Schema.XmlSchemaValidator.ValidateText%2A>.</span><span class="sxs-lookup"><span data-stu-id="715d1-281">Otherwise the <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> method's behavior is the same as in <xref:System.Xml.Schema.XmlSchemaValidator.ValidateText%2A>.</span></span>|<span data-ttu-id="715d1-282">Jeśli odstępy między kontekstami jest odstępem najwyższego poziomu, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> zwraca pustą tablicę.</span><span class="sxs-lookup"><span data-stu-id="715d1-282">If the context white-space is top-level white-space, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> returns an empty array.</span></span><br /><br /> <span data-ttu-id="715d1-283">W przeciwnym razie zachowanie metody <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> jest takie samo jak w <xref:System.Xml.Schema.XmlSchemaValidator.ValidateText%2A>.</span><span class="sxs-lookup"><span data-stu-id="715d1-283">Otherwise the <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> method's behavior is the same as in <xref:System.Xml.Schema.XmlSchemaValidator.ValidateText%2A>.</span></span>|<span data-ttu-id="715d1-284">Tak samo jak powyżej.</span><span class="sxs-lookup"><span data-stu-id="715d1-284">Same as above.</span></span>|
|<xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndElement%2A>|<span data-ttu-id="715d1-285"><xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> zwraca sekwencję elementów oczekiwanych po elemencie kontekstu (możliwe elementy równorzędne).</span><span class="sxs-lookup"><span data-stu-id="715d1-285"><xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> returns the sequence of elements expected after the context element (possible siblings).</span></span>|<span data-ttu-id="715d1-286"><xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> zwraca listę niezweryfikowanych elementów kontekstu.</span><span class="sxs-lookup"><span data-stu-id="715d1-286"><xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> returns the context element's list of attributes not validated.</span></span><br /><br /> <span data-ttu-id="715d1-287">Jeśli element kontekstu nie ma elementu nadrzędnego, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> zwraca listę pustą (element context jest obiektem nadrzędnym bieżącego elementu, w którym wywołano <xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndElement%2A>).</span><span class="sxs-lookup"><span data-stu-id="715d1-287">If the context element has no parent then <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> returns an empty list (the context element is the parent of the current element on which <xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndElement%2A> was called).</span></span>|<span data-ttu-id="715d1-288">Tak samo jak powyżej.</span><span class="sxs-lookup"><span data-stu-id="715d1-288">Same as above.</span></span>|
|<xref:System.Xml.Schema.XmlSchemaValidator.SkipToEndElement%2A>|<span data-ttu-id="715d1-289">Wartość taka sama jak <xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndElement%2A>.</span><span class="sxs-lookup"><span data-stu-id="715d1-289">Same as <xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndElement%2A>.</span></span>|<span data-ttu-id="715d1-290">Wartość taka sama jak <xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndElement%2A>.</span><span class="sxs-lookup"><span data-stu-id="715d1-290">Same as <xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndElement%2A>.</span></span>|<span data-ttu-id="715d1-291">Tak samo jak powyżej.</span><span class="sxs-lookup"><span data-stu-id="715d1-291">Same as above.</span></span>|
|<xref:System.Xml.Schema.XmlSchemaValidator.EndValidation%2A>|<span data-ttu-id="715d1-292">Zwraca pustą tablicę.</span><span class="sxs-lookup"><span data-stu-id="715d1-292">Returns an empty array.</span></span>|<span data-ttu-id="715d1-293">Zwraca pustą tablicę.</span><span class="sxs-lookup"><span data-stu-id="715d1-293">Returns an empty array.</span></span>|<span data-ttu-id="715d1-294">Tak samo jak powyżej.</span><span class="sxs-lookup"><span data-stu-id="715d1-294">Same as above.</span></span>|

> [!NOTE]
> <span data-ttu-id="715d1-295">Wartości zwracane przez różne właściwości klasy <xref:System.Xml.Schema.XmlSchemaValidator> nie są zmieniane przez wywołanie dowolnej metody z powyższej tabeli.</span><span class="sxs-lookup"><span data-stu-id="715d1-295">The values returned by the various properties of the <xref:System.Xml.Schema.XmlSchemaValidator> class are not altered by calling any of the methods in the above table.</span></span>

## <a name="see-also"></a><span data-ttu-id="715d1-296">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="715d1-296">See also</span></span>

- <xref:System.Xml.Schema.XmlSchemaValidator>
