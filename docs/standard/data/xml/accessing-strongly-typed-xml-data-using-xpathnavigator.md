---
title: Uzyskiwanie dostępu do silnie typizowanych danych XML przy użyciu klasy XPathNavigator
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 898e0f52-8a7c-4d1f-afcd-6ffb28b050b4
ms.openlocfilehash: e6ec30e3c7c2318b199122cd63c7f56584707a98
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/28/2020
ms.locfileid: "78158054"
---
# <a name="accessing-strongly-typed-xml-data-using-xpathnavigator"></a><span data-ttu-id="a00d9-102">Uzyskiwanie dostępu do silnie typizowanych danych XML przy użyciu klasy XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="a00d9-102">Accessing Strongly Typed XML Data Using XPathNavigator</span></span>
<span data-ttu-id="a00d9-103">Jako wystąpienie modelu danych XPath 2,0, <xref:System.Xml.XPath.XPathNavigator> Klasa może zawierać dane z jednoznacznie określonym typem, które są mapowane na typy środowiska uruchomieniowego języka wspólnego (CLR).</span><span class="sxs-lookup"><span data-stu-id="a00d9-103">As an instance of the XPath 2.0 data model, the <xref:System.Xml.XPath.XPathNavigator> class can contain strongly-typed data that maps to common language runtime (CLR) types.</span></span> <span data-ttu-id="a00d9-104">Zgodnie z modelem danych XPath 2,0, tylko elementy i atrybuty mogą zawierać dane o jednoznacznie określonym typie.</span><span class="sxs-lookup"><span data-stu-id="a00d9-104">According to the XPath 2.0 data model, only elements and attributes can contain strongly-typed data.</span></span> <span data-ttu-id="a00d9-105"><xref:System.Xml.XPath.XPathNavigator> Klasa udostępnia mechanizmy do uzyskiwania dostępu do danych w <xref:System.Xml.XPath.XPathDocument> obiekcie <xref:System.Xml.XmlDocument> lub jako dane z jednoznacznie określonym typem, a także mechanizmy konwersji z jednego typu danych na inny.</span><span class="sxs-lookup"><span data-stu-id="a00d9-105">The <xref:System.Xml.XPath.XPathNavigator> class provides mechanisms for accessing data within an <xref:System.Xml.XPath.XPathDocument> or <xref:System.Xml.XmlDocument> object as strongly-typed data as well as mechanisms for converting from one data type to another.</span></span>  
  
## <a name="type-information-exposed-by-xpathnavigator"></a><span data-ttu-id="a00d9-106">Informacje o typie uwidocznione przez element XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="a00d9-106">Type Information Exposed by XPathNavigator</span></span>  
 <span data-ttu-id="a00d9-107">Dane XML 1,0 są technicznie bez typu, chyba że są przetwarzane ze schematem DTD, językiem definicji schematu XML (XSD) lub innym mechanizmem.</span><span class="sxs-lookup"><span data-stu-id="a00d9-107">XML 1.0 data is technically without type, unless processed with a DTD, XML schema definition language (XSD) schema, or other mechanism.</span></span> <span data-ttu-id="a00d9-108">Istnieje wiele kategorii informacji o typie, które mogą być skojarzone z elementem lub atrybutem XML.</span><span class="sxs-lookup"><span data-stu-id="a00d9-108">There are a number of categories of type information that can be associated with an XML element or attribute.</span></span>  
  
- <span data-ttu-id="a00d9-109">Proste typy CLR: żaden z języków schematu XML nie obsługuje bezpośrednio typów środowiska uruchomieniowego języka wspólnego (CLR).</span><span class="sxs-lookup"><span data-stu-id="a00d9-109">Simple CLR Types: None of the XML Schema languages support Common Language Runtime (CLR) types directly.</span></span> <span data-ttu-id="a00d9-110">Ponieważ warto mieć możliwość wyświetlania prostej zawartości elementu i atrybutu jako najbardziej odpowiedniego typu CLR, cała prosta zawartość może zostać wpisana jako <xref:System.String> nieobecność informacji o schemacie z dowolnymi dodatkowymi informacjami o schemacie, które mogłyby spowodować, że ta zawartość jest bardziej odpowiedni.</span><span class="sxs-lookup"><span data-stu-id="a00d9-110">Because it is useful to be able to view simple element and attribute content as the most appropriate CLR type, all simple content can be typed as <xref:System.String> in the absence of schema information with any added schema information potentially refining this content to a more appropriate type.</span></span> <span data-ttu-id="a00d9-111">Najlepiej pasujący typ CLR elementu prostego i zawartości atrybutu można znaleźć za pomocą <xref:System.Xml.XPath.XPathNavigator.ValueType%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="a00d9-111">You can find the best matching CLR type of simple element and attribute content by using the <xref:System.Xml.XPath.XPathNavigator.ValueType%2A> property.</span></span> <span data-ttu-id="a00d9-112">Aby uzyskać więcej informacji na temat mapowania ze schematów wbudowanych typów do typów CLR, zobacz [Obsługa typów w klasach system. XML](../../../../docs/standard/data/xml/type-support-in-the-system-xml-classes.md).</span><span class="sxs-lookup"><span data-stu-id="a00d9-112">For more information about the mapping from schema built-in types to CLR types, see [Type Support in the System.Xml Classes](../../../../docs/standard/data/xml/type-support-in-the-system-xml-classes.md).</span></span>  
  
- <span data-ttu-id="a00d9-113">Listy typów prostych (CLR): element lub atrybut o prostej zawartości może zawierać listę wartości rozdzielonych znakami odstępu.</span><span class="sxs-lookup"><span data-stu-id="a00d9-113">Lists of Simple (CLR) Types: An element or attribute with simple content can contain a list of values separated by white space.</span></span> <span data-ttu-id="a00d9-114">Wartości są określane przez schemat XML jako "typ listy".</span><span class="sxs-lookup"><span data-stu-id="a00d9-114">The values are specified by an XML Schema to be a "list type."</span></span> <span data-ttu-id="a00d9-115">W przypadku braku schematu XML taka zawartość prosta byłaby traktowana jak pojedynczy węzeł tekstowy.</span><span class="sxs-lookup"><span data-stu-id="a00d9-115">In the absence of an XML Schema, such simple content would be treated as a single text node.</span></span> <span data-ttu-id="a00d9-116">Gdy schemat XML jest dostępny, ta prosta zawartość może być ujawniona jako szereg wartości niepodzielnych, z których każdy ma typ prosty, który jest mapowany do kolekcji obiektów CLR.</span><span class="sxs-lookup"><span data-stu-id="a00d9-116">When an XML Schema is available, this simple content can be exposed as a series of atomic values each having a simple type that maps to a collection of CLR objects.</span></span> <span data-ttu-id="a00d9-117">Aby uzyskać więcej informacji na temat mapowania ze schematów wbudowanych typów do typów CLR, zobacz [Obsługa typów w klasach system. XML](../../../../docs/standard/data/xml/type-support-in-the-system-xml-classes.md).</span><span class="sxs-lookup"><span data-stu-id="a00d9-117">For more information about the mapping from schema built-in types to CLR types, see [Type Support in the System.Xml Classes](../../../../docs/standard/data/xml/type-support-in-the-system-xml-classes.md).</span></span>  
  
- <span data-ttu-id="a00d9-118">Wpisana wartość: atrybut lub element, który został sprawdzony przez schemat z typem prostym, ma wpisaną wartość.</span><span class="sxs-lookup"><span data-stu-id="a00d9-118">Typed Value: A schema-validated attribute or element with a simple type has a typed value.</span></span> <span data-ttu-id="a00d9-119">Ta wartość to typ pierwotny, taki jak liczbowy, ciąg lub typ daty.</span><span class="sxs-lookup"><span data-stu-id="a00d9-119">This value is a primitive type such as a numeric, string, or date type.</span></span> <span data-ttu-id="a00d9-120">Wszystkie wbudowane typy proste w XSD można zamapować na typy CLR, które zapewniają dostęp do wartości węzła jako bardziej odpowiedni typ, a nie tylko jako <xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="a00d9-120">All the built-in simple types in XSD can be mapped to CLR types that provide access to the value of a node as a more appropriate type instead of just as a <xref:System.String>.</span></span> <span data-ttu-id="a00d9-121">Element z atrybutami lub elementami podrzędnymi jest traktowany jako typ złożony.</span><span class="sxs-lookup"><span data-stu-id="a00d9-121">An element with attributes or element children is considered to be a complex type.</span></span> <span data-ttu-id="a00d9-122">Wpisana wartość typu złożonego z prostą zawartością (tylko węzły tekstowe jako elementy podrzędne) jest taka sama jak w przypadku typu prostego jego zawartości.</span><span class="sxs-lookup"><span data-stu-id="a00d9-122">The typed value of a complex type with simple content (only text nodes as children) is the same as that of the simple type of its content.</span></span> <span data-ttu-id="a00d9-123">Wpisana wartość typu złożonego z zawartością złożoną (co najmniej jeden element podrzędny) to wartość ciągu łącząca wszystkie podrzędne węzły tekstowe zwracane jako <xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="a00d9-123">The typed value of a complex type with complex content (one or more child elements) is the string value of the concatenation of all its child text nodes returned as a <xref:System.String>.</span></span> <span data-ttu-id="a00d9-124">Aby uzyskać więcej informacji na temat mapowania ze schematów wbudowanych typów do typów CLR, zobacz [Obsługa typów w klasach system. XML](../../../../docs/standard/data/xml/type-support-in-the-system-xml-classes.md).</span><span class="sxs-lookup"><span data-stu-id="a00d9-124">For more information about the mapping from schema built-in types to CLR types, see [Type Support in the System.Xml Classes](../../../../docs/standard/data/xml/type-support-in-the-system-xml-classes.md).</span></span>  
  
- <span data-ttu-id="a00d9-125">Nazwa typu określonego dla języka: w większości przypadków typy CLR, które są ustawiane jako efekt uboczny zastosowania schematu zewnętrznego, są używane w celu zapewnienia dostępu do wartości węzła.</span><span class="sxs-lookup"><span data-stu-id="a00d9-125">Schema-Language Specific Type Name: In most cases, the CLR types, which are set as a side-effect of applying an external schema, are used to provide access to the value of a node.</span></span> <span data-ttu-id="a00d9-126">Mogą jednak wystąpić sytuacje, w których można ocenić typ skojarzony z określonym schematem zastosowanym do dokumentu XML.</span><span class="sxs-lookup"><span data-stu-id="a00d9-126">However, there may be situations where you may want to examine the type associated with a particular schema applied to an XML document.</span></span> <span data-ttu-id="a00d9-127">Na przykład możesz chcieć przeszukać dokument XML, wyodrębniając wszystkie elementy, które są określone jako mają zawartość typu "PurchaseOrder" zgodnie z dołączonym schematem.</span><span class="sxs-lookup"><span data-stu-id="a00d9-127">For example, you may wish to search through an XML document, extracting all elements that are determined to have content of type "PurchaseOrder" according to an attached schema.</span></span> <span data-ttu-id="a00d9-128">Takie informacje o typie można ustawić tylko w wyniku walidacji schematu i dostęp do tych informacji za pomocą właściwości <xref:System.Xml.XPath.XPathNavigator.XmlType%2A> i <xref:System.Xml.XPath.XPathNavigator.SchemaInfo%2A> <xref:System.Xml.XPath.XPathNavigator> klasy.</span><span class="sxs-lookup"><span data-stu-id="a00d9-128">Such type information can be set only as a result of schema validation and this information is accessed through the <xref:System.Xml.XPath.XPathNavigator.XmlType%2A> and <xref:System.Xml.XPath.XPathNavigator.SchemaInfo%2A> properties of the <xref:System.Xml.XPath.XPathNavigator> class.</span></span> <span data-ttu-id="a00d9-129">Aby uzyskać więcej informacji, zobacz poniższą sekcję po sprawdzeniu poprawności schematu sprawdzonych (PSVI).</span><span class="sxs-lookup"><span data-stu-id="a00d9-129">For more information, see The Post Schema Validation Infoset (PSVI) section below.</span></span>  
  
- <span data-ttu-id="a00d9-130">Odbicie typu specyficznego dla języka schematu: w innych przypadkach może być konieczne uzyskanie dalszych szczegółowych informacji o typie specyficznym dla schematu zastosowanym w dokumencie XML.</span><span class="sxs-lookup"><span data-stu-id="a00d9-130">Schema-Language Specific Type Reflection: In other cases, you may want to obtain further details of the schema-specific type applied to an XML document.</span></span> <span data-ttu-id="a00d9-131">Na przykład podczas odczytywania pliku XML może być konieczne wyodrębnienie `maxOccurs` atrybutu dla każdego prawidłowego węzła w dokumencie XML w celu wykonania niektórych obliczeń niestandardowych.</span><span class="sxs-lookup"><span data-stu-id="a00d9-131">For example, when reading an XML file, you may want to extract the `maxOccurs` attribute for each valid node in the XML document in order to perform some custom calculation.</span></span> <span data-ttu-id="a00d9-132">Ponieważ te informacje są ustawiane tylko za pomocą walidacji schematu, są dostępne <xref:System.Xml.XPath.XPathNavigator.SchemaInfo%2A> za pomocą właściwości <xref:System.Xml.XPath.XPathNavigator> klasy.</span><span class="sxs-lookup"><span data-stu-id="a00d9-132">Because this information is set only through schema validation, it is accessed through the <xref:System.Xml.XPath.XPathNavigator.SchemaInfo%2A> property of the <xref:System.Xml.XPath.XPathNavigator> class.</span></span> <span data-ttu-id="a00d9-133">Aby uzyskać więcej informacji, zobacz poniższą sekcję po sprawdzeniu poprawności schematu sprawdzonych (PSVI).</span><span class="sxs-lookup"><span data-stu-id="a00d9-133">For more information, see The Post Schema Validation Infoset (PSVI) section below.</span></span>  
  
## <a name="xpathnavigator-typed-accessors"></a><span data-ttu-id="a00d9-134">Metody dostępu typu XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="a00d9-134">XPathNavigator Typed Accessors</span></span>  
 <span data-ttu-id="a00d9-135">W poniższej tabeli przedstawiono różne właściwości i metody <xref:System.Xml.XPath.XPathNavigator> klasy, których można użyć w celu uzyskania dostępu do informacji o typie węzła.</span><span class="sxs-lookup"><span data-stu-id="a00d9-135">The following table shows the various properties and methods of the <xref:System.Xml.XPath.XPathNavigator> class that can be used to access the type information about a node.</span></span>  
  
|<span data-ttu-id="a00d9-136">Właściwość</span><span class="sxs-lookup"><span data-stu-id="a00d9-136">Property</span></span>|<span data-ttu-id="a00d9-137">Opis</span><span class="sxs-lookup"><span data-stu-id="a00d9-137">Description</span></span>|  
|--------------|-----------------|  
|<xref:System.Xml.XPath.XPathNavigator.XmlType%2A>|<span data-ttu-id="a00d9-138">Zawiera informacje o typie schematu XML dla węzła, jeśli jest on prawidłowy.</span><span class="sxs-lookup"><span data-stu-id="a00d9-138">This contains the XML schema type information for the node if it is valid.</span></span>|  
|<xref:System.Xml.XPath.XPathNavigator.SchemaInfo%2A>|<span data-ttu-id="a00d9-139">Zawiera sprawdzonych walidacji schematu w węźle, który jest dodawany po walidacji.</span><span class="sxs-lookup"><span data-stu-id="a00d9-139">This contains the Post Schema Validation Infoset of the node that is added after validation.</span></span> <span data-ttu-id="a00d9-140">Obejmuje to informacje o typie schematu XML, a także informacje o ważności.</span><span class="sxs-lookup"><span data-stu-id="a00d9-140">This includes the XML schema type information, as well as validity information.</span></span>|  
|<xref:System.Xml.XPath.XPathNavigator.ValueType%2A>|<span data-ttu-id="a00d9-141">Typ CLR wartości w węźle.</span><span class="sxs-lookup"><span data-stu-id="a00d9-141">The CLR type of the typed value of the node.</span></span>|  
|<xref:System.Xml.XPath.XPathNavigator.TypedValue%2A>|<span data-ttu-id="a00d9-142">Zawartość węzła jako co najmniej jedna wartość CLR, której typem jest najbliższe dopasowanie do typu schematu XML węzła.</span><span class="sxs-lookup"><span data-stu-id="a00d9-142">The content of the node as one or more CLR values whose type is the closest match to the XML schema type of the node.</span></span>|  
|<xref:System.Xml.XPath.XPathNavigator.ValueAsBoolean%2A>|<span data-ttu-id="a00d9-143"><xref:System.String> Wartość bieżącego węzła rzutowana na <xref:System.Boolean> wartość, zgodnie z regułami rzutowania XPath 2,0 dla `xs:boolean`.</span><span class="sxs-lookup"><span data-stu-id="a00d9-143">The <xref:System.String> value of the current node cast to a <xref:System.Boolean> value, according to the XPath 2.0 casting rules for `xs:boolean`.</span></span>|  
|<xref:System.Xml.XPath.XPathNavigator.ValueAsDateTime%2A>|<span data-ttu-id="a00d9-144"><xref:System.String> Wartość bieżącego węzła rzutowana na <xref:System.DateTime> wartość, zgodnie z regułami rzutowania XPath 2,0 dla `xs:datetime`.</span><span class="sxs-lookup"><span data-stu-id="a00d9-144">The <xref:System.String> value of the current node cast to a <xref:System.DateTime> value, according to the XPath 2.0 casting rules for `xs:datetime`.</span></span>|  
|<xref:System.Xml.XPath.XPathNavigator.ValueAsDouble%2A>|<span data-ttu-id="a00d9-145"><xref:System.String> Wartość bieżącego węzła rzutowana na <xref:System.Double> wartość, zgodnie z regułami rzutowania XPath 2,0 dla `xsd:double`.</span><span class="sxs-lookup"><span data-stu-id="a00d9-145">The <xref:System.String> value of the current node cast to a <xref:System.Double> value, according to the XPath 2.0 casting rules for `xsd:double`.</span></span>|  
|<xref:System.Xml.XPath.XPathNavigator.ValueAsInt%2A>|<span data-ttu-id="a00d9-146"><xref:System.String> Wartość bieżącego węzła rzutowana na <xref:System.Int32> wartość, zgodnie z regułami rzutowania XPath 2,0 dla `xs:integer`.</span><span class="sxs-lookup"><span data-stu-id="a00d9-146">The <xref:System.String> value of the current node cast to a <xref:System.Int32> value, according to the XPath 2.0 casting rules for `xs:integer`.</span></span>|  
|<xref:System.Xml.XPath.XPathNavigator.ValueAsLong%2A>|<span data-ttu-id="a00d9-147"><xref:System.String> Wartość bieżącego węzła rzutowana na <xref:System.Int64> wartość, zgodnie z regułami rzutowania XPath 2,0 dla `xs:integer`.</span><span class="sxs-lookup"><span data-stu-id="a00d9-147">The <xref:System.String> value of the current node cast to a <xref:System.Int64> value, according to the XPath 2.0 casting rules for `xs:integer`.</span></span>|  
|<xref:System.Xml.XPath.XPathNavigator.ValueAs%2A>|<span data-ttu-id="a00d9-148">Zawartość węzła jest rzutowana na typ docelowy zgodnie z regułami rzutowania XPath 2,0.</span><span class="sxs-lookup"><span data-stu-id="a00d9-148">The contents of the node cast to the target type according to the XPath 2.0 casting rules.</span></span>|  
  
 <span data-ttu-id="a00d9-149">Aby uzyskać więcej informacji na temat mapowania ze schematów wbudowanych typów do typów CLR, zobacz [Obsługa typów w klasach system. XML](../../../../docs/standard/data/xml/type-support-in-the-system-xml-classes.md).</span><span class="sxs-lookup"><span data-stu-id="a00d9-149">For more information about the mapping from schema built-in types to CLR types, see [Type Support in the System.Xml Classes](../../../../docs/standard/data/xml/type-support-in-the-system-xml-classes.md).</span></span>  
  
## <a name="the-post-schema-validation-infoset-psvi"></a><span data-ttu-id="a00d9-150">Sprawdzanie poprawności po stronie sprawdzonych (PSVI)</span><span class="sxs-lookup"><span data-stu-id="a00d9-150">The Post Schema Validation Infoset (PSVI)</span></span>  
 <span data-ttu-id="a00d9-151">Procesor schematu XML akceptuje sprawdzonych XML jako dane wejściowe i konwertuje ją na wpis weryfikacji schematu sprawdzonych (PSVI).</span><span class="sxs-lookup"><span data-stu-id="a00d9-151">An XML Schema processor accepts an XML Infoset as input and converts it into a Post Schema Validation Infoset (PSVI).</span></span> <span data-ttu-id="a00d9-152">PSVI to oryginalny wejściowy kod XML sprawdzonych z nowymi dodawanymi elementami informacji i nowymi właściwościami dodawanymi do istniejących elementów informacji.</span><span class="sxs-lookup"><span data-stu-id="a00d9-152">A PSVI is the original input XML infoset with new information items added and new properties added to existing information items.</span></span> <span data-ttu-id="a00d9-153">Istnieją trzy szerokie klasy informacji dodanych do sprawdzonych XML w PSVI, które są udostępniane przez <xref:System.Xml.XPath.XPathNavigator>.</span><span class="sxs-lookup"><span data-stu-id="a00d9-153">There are three broad classes of information added to the XML Infoset in the PSVI that are exposed by the <xref:System.Xml.XPath.XPathNavigator>.</span></span>  
  
1. <span data-ttu-id="a00d9-154">Wyniki walidacji: informacje o tym, czy element lub atrybut został pomyślnie zweryfikowany.</span><span class="sxs-lookup"><span data-stu-id="a00d9-154">Validation Outcomes: Information as to whether an element or attribute was successfully validated or not.</span></span> <span data-ttu-id="a00d9-155">Jest to uwidaczniane przez <xref:System.Xml.Schema.IXmlSchemaInfo.Validity%2A> Właściwość <xref:System.Xml.XPath.XPathNavigator.SchemaInfo%2A> właściwości <xref:System.Xml.XPath.XPathNavigator> klasy.</span><span class="sxs-lookup"><span data-stu-id="a00d9-155">This is exposed by the <xref:System.Xml.Schema.IXmlSchemaInfo.Validity%2A> property of the <xref:System.Xml.XPath.XPathNavigator.SchemaInfo%2A> property of the <xref:System.Xml.XPath.XPathNavigator> class.</span></span>  
  
2. <span data-ttu-id="a00d9-156">Informacje domyślne: wskazanie, czy wartość elementu lub atrybutu została uzyskana za pośrednictwem wartości domyślnych określonych w schemacie, czy nie.</span><span class="sxs-lookup"><span data-stu-id="a00d9-156">Default Information: Indications as to whether the value of the element or attribute was obtained via default values specified in the schema or not.</span></span> <span data-ttu-id="a00d9-157">Jest to uwidaczniane przez <xref:System.Xml.Schema.IXmlSchemaInfo.IsDefault%2A> Właściwość <xref:System.Xml.XPath.XPathNavigator.SchemaInfo%2A> właściwości <xref:System.Xml.XPath.XPathNavigator> klasy.</span><span class="sxs-lookup"><span data-stu-id="a00d9-157">This is exposed by the <xref:System.Xml.Schema.IXmlSchemaInfo.IsDefault%2A> property of the <xref:System.Xml.XPath.XPathNavigator.SchemaInfo%2A> property of the <xref:System.Xml.XPath.XPathNavigator> class.</span></span>  
  
3. <span data-ttu-id="a00d9-158">Adnotacje typu: odwołania do składników schematu, które mogą być definicjami typów lub deklaracji elementów i atrybutów.</span><span class="sxs-lookup"><span data-stu-id="a00d9-158">Type Annotations: References to schema components that may be type definitions or element and attribute declarations.</span></span> <span data-ttu-id="a00d9-159"><xref:System.Xml.XPath.XPathNavigator.XmlType%2A> Właściwość <xref:System.Xml.XPath.XPathNavigator> zawiera informacje o określonym typie węzła, jeśli jest on prawidłowy.</span><span class="sxs-lookup"><span data-stu-id="a00d9-159">The <xref:System.Xml.XPath.XPathNavigator.XmlType%2A> property of the <xref:System.Xml.XPath.XPathNavigator> contains the specific type information of the node if it is valid.</span></span> <span data-ttu-id="a00d9-160">Jeśli ważność węzła jest nieznana, na przykład gdy została zweryfikowana, a następnie edytowana.</span><span class="sxs-lookup"><span data-stu-id="a00d9-160">If the validity of a node is unknown, such as when it was validated then subsequently edited.</span></span> <span data-ttu-id="a00d9-161">następnie <xref:System.Xml.XPath.XPathNavigator.XmlType%2A> właściwość jest ustawiona na `null` , ale informacje o typie są nadal dostępne z różnych właściwości <xref:System.Xml.XPath.XPathNavigator.SchemaInfo%2A> właściwości <xref:System.Xml.XPath.XPathNavigator> klasy.</span><span class="sxs-lookup"><span data-stu-id="a00d9-161">then the <xref:System.Xml.XPath.XPathNavigator.XmlType%2A> property is set to `null` but type information is still available from the various properties of the <xref:System.Xml.XPath.XPathNavigator.SchemaInfo%2A> property of the <xref:System.Xml.XPath.XPathNavigator> class.</span></span>  
  
 <span data-ttu-id="a00d9-162">Poniższy przykład ilustruje użycie informacji w sprawdzonych walidacji schematu uwidocznionych przez <xref:System.Xml.XPath.XPathNavigator>.</span><span class="sxs-lookup"><span data-stu-id="a00d9-162">The following example illustrates using information in the Post Schema Validation Infoset exposed by the <xref:System.Xml.XPath.XPathNavigator>.</span></span>  
  
```vb  
Dim settings As XmlReaderSettings = New XmlReaderSettings()  
settings.Schemas.Add("http://www.contoso.com/books", "books.xsd")  
settings.ValidationType = ValidationType.Schema  
  
Dim reader As XmlReader = XmlReader.Create("books.xml", settings)  
  
Dim document As XmlDocument = New XmlDocument()  
document.Load(reader)  
Dim navigator As XPathNavigator = document.CreateNavigator()  
navigator.MoveToChild("books", "http://www.contoso.com/books")  
navigator.MoveToChild("book", "http://www.contoso.com/books")  
navigator.MoveToChild("published", "http://www.contoso.com/books")  
  
Console.WriteLine(navigator.SchemaInfo.SchemaType.Name)  
Console.WriteLine(navigator.SchemaInfo.Validity)  
Console.WriteLine(navigator.SchemaInfo.SchemaElement.MinOccurs)  
```  
  
```csharp  
XmlReaderSettings settings = new XmlReaderSettings();  
settings.Schemas.Add("http://www.contoso.com/books", "books.xsd");  
settings.ValidationType = ValidationType.Schema;  
  
XmlReader reader = XmlReader.Create("books.xml", settings);  
  
XmlDocument document = new XmlDocument();  
document.Load(reader);  
XPathNavigator navigator = document.CreateNavigator();  
navigator.MoveToChild("books", "http://www.contoso.com/books");  
navigator.MoveToChild("book", "http://www.contoso.com/books");  
navigator.MoveToChild("published", "http://www.contoso.com/books");  
  
Console.WriteLine(navigator.SchemaInfo.SchemaType.Name);  
Console.WriteLine(navigator.SchemaInfo.Validity);  
Console.WriteLine(navigator.SchemaInfo.SchemaElement.MinOccurs);  
```  
  
 <span data-ttu-id="a00d9-163">Przykład pobiera `books.xml` plik jako dane wejściowe.</span><span class="sxs-lookup"><span data-stu-id="a00d9-163">The example takes the `books.xml` file as input.</span></span>  
  
```xml  
<books xmlns="http://www.contoso.com/books">  
    <book>  
        <title>Title</title>  
        <price>10.00</price>  
        <published>2003-12-31</published>  
    </book>  
</books>  
```  
  
 <span data-ttu-id="a00d9-164">Przykład pobiera również `books.xsd` schemat jako dane wejściowe.</span><span class="sxs-lookup"><span data-stu-id="a00d9-164">The example also takes the `books.xsd` schema as input.</span></span>  
  
```xml  
<xs:schema xmlns="http://www.contoso.com/books"
attributeFormDefault="unqualified" elementFormDefault="qualified"
targetNamespace="http://www.contoso.com/books"
xmlns:xs="http://www.w3.org/2001/XMLSchema">  
    <xs:simpleType name="publishedType">  
        <xs:restriction base="xs:date">  
            <xs:minInclusive value="2003-01-01" />  
            <xs:maxInclusive value="2003-12-31" />  
        </xs:restriction>  
    </xs:simpleType>  
    <xs:complexType name="bookType">  
        <xs:sequence>  
            <xs:element name="title" type="xs:string"/>  
            <xs:element name="price" type="xs:decimal"/>  
            <xs:element name="published" type="publishedType"/>  
        </xs:sequence>  
    </xs:complexType>  
    <xs:complexType name="booksType">  
        <xs:sequence>  
            <xs:element name="book" type="bookType" />  
        </xs:sequence>  
    </xs:complexType>  
    <xs:element name="books" type="booksType" />  
</xs:schema>  
```  
  
## <a name="obtain-typed-values-using-valueas-properties"></a><span data-ttu-id="a00d9-165">Uzyskiwanie wpisanych wartości przy użyciu właściwości ValueAs</span><span class="sxs-lookup"><span data-stu-id="a00d9-165">Obtain Typed Values Using ValueAs Properties</span></span>  
 <span data-ttu-id="a00d9-166">Wartość wpisana w węźle można pobrać, uzyskując dostęp do <xref:System.Xml.XPath.XPathNavigator.TypedValue%2A> właściwości. <xref:System.Xml.XPath.XPathNavigator></span><span class="sxs-lookup"><span data-stu-id="a00d9-166">The typed value of a node can be retrieved by accessing the <xref:System.Xml.XPath.XPathNavigator.TypedValue%2A> property of the <xref:System.Xml.XPath.XPathNavigator>.</span></span> <span data-ttu-id="a00d9-167">W niektórych przypadkach możesz chcieć przekonwertować wpisaną wartość węzła na inny typ.</span><span class="sxs-lookup"><span data-stu-id="a00d9-167">In certain cases you may want to convert the typed value of a node to a different type.</span></span> <span data-ttu-id="a00d9-168">Typowym przykładem jest uzyskanie wartości liczbowej z węzła XML.</span><span class="sxs-lookup"><span data-stu-id="a00d9-168">A common example is to get a numeric value from an XML node.</span></span> <span data-ttu-id="a00d9-169">Rozważmy na przykład następujący niesprawdzony i niewpisany dokument XML.</span><span class="sxs-lookup"><span data-stu-id="a00d9-169">For example, consider the following unvalidated and untyped XML document.</span></span>  
  
```xml  
<books>  
    <book>  
        <title>Title</title>  
        <price>10.00</price>  
        <published>2003-12-31</published>  
    </book>  
</books>  
```  
  
 <span data-ttu-id="a00d9-170">Jeśli pozycja <xref:System.Xml.XPath.XPathNavigator> jest ustawiona w `price` elemencie <xref:System.Xml.XPath.XPathNavigator.XmlType%2A> `null` <xref:System.Xml.XPath.XPathNavigator.ValueType%2A> <xref:System.String>, właściwość powinna być, a <xref:System.Xml.XPath.XPathNavigator.TypedValue%2A> Właściwość byłaby ciągiem. `10.00`</span><span class="sxs-lookup"><span data-stu-id="a00d9-170">If the <xref:System.Xml.XPath.XPathNavigator> is positioned on the `price` element the <xref:System.Xml.XPath.XPathNavigator.XmlType%2A> property would be `null`, the <xref:System.Xml.XPath.XPathNavigator.ValueType%2A> property would be <xref:System.String>, and the <xref:System.Xml.XPath.XPathNavigator.TypedValue%2A> property would be the string `10.00`.</span></span>  
  
 <span data-ttu-id="a00d9-171">Jednak nadal jest możliwe wyodrębnienie wartości jako wartości liczbowej przy użyciu <xref:System.Xml.XPath.XPathItem.ValueAs%2A>metody, <xref:System.Xml.XPath.XPathNavigator.ValueAsDouble%2A>, <xref:System.Xml.XPath.XPathNavigator.ValueAsInt%2A>lub <xref:System.Xml.XPath.XPathNavigator.ValueAsLong%2A> i właściwości.</span><span class="sxs-lookup"><span data-stu-id="a00d9-171">However, it is still possible to extract the value as a numeric value using the <xref:System.Xml.XPath.XPathItem.ValueAs%2A>, <xref:System.Xml.XPath.XPathNavigator.ValueAsDouble%2A>, <xref:System.Xml.XPath.XPathNavigator.ValueAsInt%2A>, or <xref:System.Xml.XPath.XPathNavigator.ValueAsLong%2A> method and properties.</span></span> <span data-ttu-id="a00d9-172">Poniższy przykład ilustruje wykonywanie takich rzutowania przy użyciu <xref:System.Xml.XPath.XPathItem.ValueAs%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="a00d9-172">The following example illustrates performing such a cast using the <xref:System.Xml.XPath.XPathItem.ValueAs%2A> method.</span></span>  
  
```vb  
Dim document As New XmlDocument()  
document.Load("books.xml")  
Dim navigator As XPathNavigator = document.CreateNavigator()  
navigator.MoveToChild("books", "")  
navigator.MoveToChild("book", "")  
navigator.MoveToChild("price", "")  
  
Dim price = navigator.ValueAs(GetType(Decimal))  
Dim discount As Decimal = 0.2  
  
Console.WriteLine("The price of the book has been dropped 20% from {0:C} to {1:C}", navigator.Value, (price - price * discount))  
```  
  
```csharp  
XmlDocument document = new XmlDocument();  
document.Load("books.xml");  
XPathNavigator navigator = document.CreateNavigator();  
navigator.MoveToChild("books", "");  
navigator.MoveToChild("book", "");  
navigator.MoveToChild("price", "");  
  
Decimal price = (decimal)navigator.ValueAs(typeof(decimal));  
  
Console.WriteLine("The price of the book has been dropped 20% from {0:C} to {1:C}", navigator.Value, (price - price * (decimal)0.20));  
```  
  
 <span data-ttu-id="a00d9-173">Aby uzyskać więcej informacji na temat mapowania ze schematów wbudowanych typów do typów CLR, zobacz [Obsługa typów w klasach system. XML](../../../../docs/standard/data/xml/type-support-in-the-system-xml-classes.md).</span><span class="sxs-lookup"><span data-stu-id="a00d9-173">For more information about the mapping from schema built-in types to CLR types, see [Type Support in the System.Xml Classes](../../../../docs/standard/data/xml/type-support-in-the-system-xml-classes.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a00d9-174">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a00d9-174">See also</span></span>

- <xref:System.Xml.XmlDocument>
- <xref:System.Xml.XPath.XPathDocument>
- <xref:System.Xml.XPath.XPathNavigator>
- [<span data-ttu-id="a00d9-175">Obsługa typu w ramach klas zestawu System.Xml</span><span class="sxs-lookup"><span data-stu-id="a00d9-175">Type Support in the System.Xml Classes</span></span>](../../../../docs/standard/data/xml/type-support-in-the-system-xml-classes.md)
- [<span data-ttu-id="a00d9-176">Przetwarzanie danych XML przy użyciu modelu danych XPath</span><span class="sxs-lookup"><span data-stu-id="a00d9-176">Process XML Data Using the XPath Data Model</span></span>](../../../../docs/standard/data/xml/process-xml-data-using-the-xpath-data-model.md)
- [<span data-ttu-id="a00d9-177">Nawigacja po zestawie węzłów przy użyciu klasy XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="a00d9-177">Node Set Navigation Using XPathNavigator</span></span>](../../../../docs/standard/data/xml/node-set-navigation-using-xpathnavigator.md)
- [<span data-ttu-id="a00d9-178">Nawigacja po atrybutach i przestrzeni nazw węzła przy użyciu klasy XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="a00d9-178">Attribute and Namespace Node Navigation Using XPathNavigator</span></span>](../../../../docs/standard/data/xml/attribute-and-namespace-node-navigation-using-xpathnavigator.md)
- [<span data-ttu-id="a00d9-179">Wyodrębnianie danych XML przy użyciu klasy XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="a00d9-179">Extract XML Data Using XPathNavigator</span></span>](../../../../docs/standard/data/xml/extract-xml-data-using-xpathnavigator.md)
