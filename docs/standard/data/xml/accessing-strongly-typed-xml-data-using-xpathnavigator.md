---
title: "Uzyskiwanie dostępu do silnie typu danych XML przy użyciu parametrem XPathNavigator"
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
ms.assetid: 898e0f52-8a7c-4d1f-afcd-6ffb28b050b4
caps.latest.revision: "2"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 651a8e11b5782227cdf5ffcc3d53cf2c75def031
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/23/2017
---
# <a name="accessing-strongly-typed-xml-data-using-xpathnavigator"></a><span data-ttu-id="d57a9-102">Uzyskiwanie dostępu do silnie typu danych XML przy użyciu parametrem XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="d57a9-102">Accessing Strongly Typed XML Data Using XPathNavigator</span></span>
<span data-ttu-id="d57a9-103">Jako wystąpienie modelu danych XPath 2.0 <xref:System.Xml.XPath.XPathNavigator> klasy może zawierać jednoznacznie danych, który jest mapowany na typowych języka wspólnego (CLR).</span><span class="sxs-lookup"><span data-stu-id="d57a9-103">As an instance of the XPath 2.0 data model, the <xref:System.Xml.XPath.XPathNavigator> class can contain strongly-typed data that maps to common language runtime (CLR) types.</span></span> <span data-ttu-id="d57a9-104">Zgodnie z modelem danych XPath 2.0 tylko elementy i atrybuty mogą zawierać silnie typizowane dane.</span><span class="sxs-lookup"><span data-stu-id="d57a9-104">According to the XPath 2.0 data model, only elements and attributes can contain strongly-typed data.</span></span> <span data-ttu-id="d57a9-105"><xref:System.Xml.XPath.XPathNavigator> Klasy zawiera mechanizmy do uzyskiwania dostępu do danych w ramach <xref:System.Xml.XPath.XPathDocument> lub <xref:System.Xml.XmlDocument> obiektu jako silnie typizowane dane, a także mechanizmy do konwertowania z jednego typu danych.</span><span class="sxs-lookup"><span data-stu-id="d57a9-105">The <xref:System.Xml.XPath.XPathNavigator> class provides mechanisms for accessing data within an <xref:System.Xml.XPath.XPathDocument> or <xref:System.Xml.XmlDocument> object as strongly-typed data as well as mechanisms for converting from one data type to another.</span></span>  
  
## <a name="type-information-exposed-by-xpathnavigator"></a><span data-ttu-id="d57a9-106">Informacje o typie udostępnione przez element XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="d57a9-106">Type Information Exposed by XPathNavigator</span></span>  
 <span data-ttu-id="d57a9-107">Dane XML 1.0 jest technicznie bez typu, chyba że przetworzyć DTD XML schematu (XSD) języka definicji schematu lub inny mechanizm.</span><span class="sxs-lookup"><span data-stu-id="d57a9-107">XML 1.0 data is technically without type, unless processed with a DTD, XML schema definition language (XSD) schema, or other mechanism.</span></span> <span data-ttu-id="d57a9-108">Istnieje wiele kategorii informacji o typie, który może być skojarzony z elementu lub atrybutu XML.</span><span class="sxs-lookup"><span data-stu-id="d57a9-108">There are a number of categories of type information that can be associated with an XML element or attribute.</span></span>  
  
-   <span data-ttu-id="d57a9-109">Proste typy CLR: Brak schematu XML języków obsługuje typy środowiska uruchomieniowego języka wspólnego (CLR) bezpośrednio.</span><span class="sxs-lookup"><span data-stu-id="d57a9-109">Simple CLR Types: None of the XML Schema languages support Common Language Runtime (CLR) types directly.</span></span> <span data-ttu-id="d57a9-110">Ponieważ warto mieć możliwość wyświetlania elementu proste i zawartość atrybutów jako najbardziej odpowiedni typ CLR, wszystkie prostej zawartości można wpisać jako <xref:System.String> w przypadku braku informacji o schemacie ze wszystkimi dodać informacji o schemacie potencjalnie uściślenie tę zawartość więcej odpowiedniego typu.</span><span class="sxs-lookup"><span data-stu-id="d57a9-110">Because it is useful to be able to view simple element and attribute content as the most appropriate CLR type, all simple content can be typed as <xref:System.String> in the absence of schema information with any added schema information potentially refining this content to a more appropriate type.</span></span> <span data-ttu-id="d57a9-111">Można znaleźć najlepiej dopasowaną CLR typu prostego elementów i atrybutów zawartości przy użyciu <xref:System.Xml.XPath.XPathNavigator.ValueType%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="d57a9-111">You can find the best matching CLR type of simple element and attribute content by using the <xref:System.Xml.XPath.XPathNavigator.ValueType%2A> property.</span></span> <span data-ttu-id="d57a9-112">Aby uzyskać więcej informacji na temat mapowanie schematu typy wbudowane typy CLR, zobacz [typu obsługi w klasach System.Xml](../../../../docs/standard/data/xml/type-support-in-the-system-xml-classes.md).</span><span class="sxs-lookup"><span data-stu-id="d57a9-112">For more information about the mapping from schema built-in types to CLR types, see [Type Support in the System.Xml Classes](../../../../docs/standard/data/xml/type-support-in-the-system-xml-classes.md).</span></span>  
  
-   <span data-ttu-id="d57a9-113">Lista typów prostych (CLR): element lub atrybut o zawartości prostej mogą zawierać listę wartości oddzielonych biały znak.</span><span class="sxs-lookup"><span data-stu-id="d57a9-113">Lists of Simple (CLR) Types: An element or attribute with simple content can contain a list of values separated by white space.</span></span> <span data-ttu-id="d57a9-114">Wartości są określone przez schemat XML na "typ listy".</span><span class="sxs-lookup"><span data-stu-id="d57a9-114">The values are specified by an XML Schema to be a "list type."</span></span> <span data-ttu-id="d57a9-115">W przypadku braku schematu XML takie prostej zawartości będzie traktowane jako jeden tekst węzła.</span><span class="sxs-lookup"><span data-stu-id="d57a9-115">In the absence of an XML Schema, such simple content would be treated as a single text node.</span></span> <span data-ttu-id="d57a9-116">Po udostępnieniu schematu XML to prosta zawartość można udostępnić jak szereg atomic wartości każde posiada typu prostego, który jest mapowany na kolekcję obiektów CLR.</span><span class="sxs-lookup"><span data-stu-id="d57a9-116">When an XML Schema is available, this simple content can be exposed as a series of atomic values each having a simple type that maps to a collection of CLR objects.</span></span> <span data-ttu-id="d57a9-117">Aby uzyskać więcej informacji na temat mapowanie schematu typy wbudowane typy CLR, zobacz [typu obsługi w klasach System.Xml](../../../../docs/standard/data/xml/type-support-in-the-system-xml-classes.md).</span><span class="sxs-lookup"><span data-stu-id="d57a9-117">For more information about the mapping from schema built-in types to CLR types, see [Type Support in the System.Xml Classes](../../../../docs/standard/data/xml/type-support-in-the-system-xml-classes.md).</span></span>  
  
-   <span data-ttu-id="d57a9-118">Wartość: Sprawdzania poprawności schematu atrybutu lub elementu z typu prostego ma wartość typu.</span><span class="sxs-lookup"><span data-stu-id="d57a9-118">Typed Value: A schema-validated attribute or element with a simple type has a typed value.</span></span> <span data-ttu-id="d57a9-119">Ta wartość jest typu pierwotnego, takie jak liczbowe, ciągu lub typu date.</span><span class="sxs-lookup"><span data-stu-id="d57a9-119">This value is a primitive type such as a numeric, string, or date type.</span></span> <span data-ttu-id="d57a9-120">Wszystkie typy proste wbudowane w XSD mogą być mapowane na typy CLR, które zapewniają dostęp do wartości węzła jako typu bardziej odpowiednie, a nie tylko jako <xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="d57a9-120">All the built-in simple types in XSD can be mapped to CLR types that provide access to the value of a node as a more appropriate type instead of just as a <xref:System.String>.</span></span> <span data-ttu-id="d57a9-121">Element z atrybutów lub elementów podrzędnych jest uważany za typ złożony.</span><span class="sxs-lookup"><span data-stu-id="d57a9-121">An element with attributes or element children is considered to be a complex type.</span></span> <span data-ttu-id="d57a9-122">Typu wartości typu złożonego o zawartości prostej (tylko węzły tekstowe jako elementy podrzędne) jest taka sama jak typu prostego jego zawartości.</span><span class="sxs-lookup"><span data-stu-id="d57a9-122">The typed value of a complex type with simple content (only text nodes as children) is the same as that of the simple type of its content.</span></span> <span data-ttu-id="d57a9-123">Wartość typu Typ złożony z zawartością złożoną (jeden lub więcej elementów podrzędnych) to wartość ciągu łączenia wszystkich tekst węzły podrzędne zwracane jako <xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="d57a9-123">The typed value of a complex type with complex content (one or more child elements) is the string value of the concatenation of all its child text nodes returned as a <xref:System.String>.</span></span> <span data-ttu-id="d57a9-124">Aby uzyskać więcej informacji na temat mapowanie schematu typy wbudowane typy CLR, zobacz [typu obsługi w klasach System.Xml](../../../../docs/standard/data/xml/type-support-in-the-system-xml-classes.md).</span><span class="sxs-lookup"><span data-stu-id="d57a9-124">For more information about the mapping from schema built-in types to CLR types, see [Type Support in the System.Xml Classes](../../../../docs/standard/data/xml/type-support-in-the-system-xml-classes.md).</span></span>  
  
-   <span data-ttu-id="d57a9-125">Nazwa typu z określonego języka schematu: W większości przypadków typy CLR, które są skonfigurowane jako efekt uboczny stosowania zewnętrzny schemat, są używane do zapewniają dostęp do wartości węzła.</span><span class="sxs-lookup"><span data-stu-id="d57a9-125">Schema-Language Specific Type Name: In most cases, the CLR types, which are set as a side-effect of applying an external schema, are used to provide access to the value of a node.</span></span> <span data-ttu-id="d57a9-126">Jednak może być sytuacje, w którym można zbadać typ skojarzony z określonym schematem zastosowane do dokumentu XML.</span><span class="sxs-lookup"><span data-stu-id="d57a9-126">However, there may be situations where you may want to examine the type associated with a particular schema applied to an XML document.</span></span> <span data-ttu-id="d57a9-127">Na przykład możesz przeszukiwać dokument XML wyodrębniania wszystkie elementy, które są określane mieć zawartości typu "PurchaseOrder" w zależności od schematu.</span><span class="sxs-lookup"><span data-stu-id="d57a9-127">For example, you may wish to search through an XML document, extracting all elements that are determined to have content of type "PurchaseOrder" according to an attached schema.</span></span> <span data-ttu-id="d57a9-128">Takie informacje o typie można ustawić tylko w wyniku sprawdzania poprawności schematu i te informacje jest dostępny za pośrednictwem <xref:System.Xml.XPath.XPathNavigator.XmlType%2A> i <xref:System.Xml.XPath.XPathNavigator.SchemaInfo%2A> właściwości <xref:System.Xml.XPath.XPathNavigator> klasy.</span><span class="sxs-lookup"><span data-stu-id="d57a9-128">Such type information can be set only as a result of schema validation and this information is accessed through the <xref:System.Xml.XPath.XPathNavigator.XmlType%2A> and <xref:System.Xml.XPath.XPathNavigator.SchemaInfo%2A> properties of the <xref:System.Xml.XPath.XPathNavigator> class.</span></span> <span data-ttu-id="d57a9-129">Aby uzyskać więcej informacji zobacz sekcję Post schemat sprawdzania poprawności typu infoset sprawdzonych (PSVI) poniżej.</span><span class="sxs-lookup"><span data-stu-id="d57a9-129">For more information, see The Post Schema Validation Infoset (PSVI) section below.</span></span>  
  
-   <span data-ttu-id="d57a9-130">Odbicie typu określonego języka schematu: W innych przypadkach można uzyskać dodatkowe szczegóły typu określonego schematu zastosowane do dokumentu XML.</span><span class="sxs-lookup"><span data-stu-id="d57a9-130">Schema-Language Specific Type Reflection: In other cases, you may want to obtain further details of the schema-specific type applied to an XML document.</span></span> <span data-ttu-id="d57a9-131">Na przykład podczas odczytywania pliku XML, można wyodrębnić `maxOccurs` atrybutu dla każdego węzła nieprawidłowy dokument XML w celu wykonywania pewnych obliczeń niestandardowych.</span><span class="sxs-lookup"><span data-stu-id="d57a9-131">For example, when reading an XML file, you may want to extract the `maxOccurs` attribute for each valid node in the XML document in order to perform some custom calculation.</span></span> <span data-ttu-id="d57a9-132">Ponieważ te informacje jest ustawiona tylko przez schemat weryfikacji, jest dostępny za pośrednictwem <xref:System.Xml.XPath.XPathNavigator.SchemaInfo%2A> właściwość <xref:System.Xml.XPath.XPathNavigator> klasy.</span><span class="sxs-lookup"><span data-stu-id="d57a9-132">Because this information is set only through schema validation, it is accessed through the <xref:System.Xml.XPath.XPathNavigator.SchemaInfo%2A> property of the <xref:System.Xml.XPath.XPathNavigator> class.</span></span> <span data-ttu-id="d57a9-133">Aby uzyskać więcej informacji zobacz sekcję Post schemat sprawdzania poprawności typu infoset sprawdzonych (PSVI) poniżej.</span><span class="sxs-lookup"><span data-stu-id="d57a9-133">For more information, see The Post Schema Validation Infoset (PSVI) section below.</span></span>  
  
## <a name="xpathnavigator-typed-accessors"></a><span data-ttu-id="d57a9-134">Element XPathNavigator typu metody dostępu</span><span class="sxs-lookup"><span data-stu-id="d57a9-134">XPathNavigator Typed Accessors</span></span>  
 <span data-ttu-id="d57a9-135">W poniższej tabeli przedstawiono różne właściwości i metody <xref:System.Xml.XPath.XPathNavigator> klasy, która umożliwia dostęp do informacji o typie o węzła.</span><span class="sxs-lookup"><span data-stu-id="d57a9-135">The following table shows the various properties and methods of the <xref:System.Xml.XPath.XPathNavigator> class that can be used to access the type information about a node.</span></span>  
  
|<span data-ttu-id="d57a9-136">Właściwość</span><span class="sxs-lookup"><span data-stu-id="d57a9-136">Property</span></span>|<span data-ttu-id="d57a9-137">Opis</span><span class="sxs-lookup"><span data-stu-id="d57a9-137">Description</span></span>|  
|--------------|-----------------|  
|<xref:System.Xml.XPath.XPathNavigator.XmlType%2A>|<span data-ttu-id="d57a9-138">Zawiera informacje o typie schematu XML dla węzła, jeśli jest ona prawidłowa.</span><span class="sxs-lookup"><span data-stu-id="d57a9-138">This contains the XML schema type information for the node if it is valid.</span></span>|  
|<xref:System.Xml.XPath.XPathNavigator.SchemaInfo%2A>|<span data-ttu-id="d57a9-139">Zawiera Infoset sprawdzania poprawności schematu Post węzła, który jest dodawany po weryfikacji.</span><span class="sxs-lookup"><span data-stu-id="d57a9-139">This contains the Post Schema Validation Infoset of the node that is added after validation.</span></span> <span data-ttu-id="d57a9-140">W tym informacje o typie schematu XML, a także informacje o ważności.</span><span class="sxs-lookup"><span data-stu-id="d57a9-140">This includes the XML schema type information, as well as validity information.</span></span>|  
|<xref:System.Xml.XPath.XPathNavigator.ValueType%2A>|<span data-ttu-id="d57a9-141">Typ CLR typu wartość węzła.</span><span class="sxs-lookup"><span data-stu-id="d57a9-141">The CLR type of the typed value of the node.</span></span>|  
|<xref:System.Xml.XPath.XPathNavigator.TypedValue%2A>|<span data-ttu-id="d57a9-142">Zawartość węzła CLR jeden lub więcej wartości o typie jest najlepiej pasuje do typu schematu XML węzła.</span><span class="sxs-lookup"><span data-stu-id="d57a9-142">The content of the node as one or more CLR values whose type is the closest match to the XML schema type of the node.</span></span>|  
|<xref:System.Xml.XPath.XPathNavigator.ValueAsBoolean%2A>|<span data-ttu-id="d57a9-143"><xref:System.String> Rzutować wartości z bieżącego węzła <xref:System.Boolean> wartości zgodnie z regułami rzutowanie XPath 2.0 dla `xs:boolean`.</span><span class="sxs-lookup"><span data-stu-id="d57a9-143">The <xref:System.String> value of the current node cast to a <xref:System.Boolean> value, according to the XPath 2.0 casting rules for `xs:boolean`.</span></span>|  
|<xref:System.Xml.XPath.XPathNavigator.ValueAsDateTime%2A>|<span data-ttu-id="d57a9-144"><xref:System.String> Rzutować wartości z bieżącego węzła <xref:System.DateTime> wartości zgodnie z regułami rzutowanie XPath 2.0 dla `xs:datetime`.</span><span class="sxs-lookup"><span data-stu-id="d57a9-144">The <xref:System.String> value of the current node cast to a <xref:System.DateTime> value, according to the XPath 2.0 casting rules for `xs:datetime`.</span></span>|  
|<xref:System.Xml.XPath.XPathNavigator.ValueAsDouble%2A>|<span data-ttu-id="d57a9-145"><xref:System.String> Rzutować wartości z bieżącego węzła <xref:System.Double> wartości zgodnie z regułami rzutowanie XPath 2.0 dla `xsd:double`.</span><span class="sxs-lookup"><span data-stu-id="d57a9-145">The <xref:System.String> value of the current node cast to a <xref:System.Double> value, according to the XPath 2.0 casting rules for `xsd:double`.</span></span>|  
|<xref:System.Xml.XPath.XPathNavigator.ValueAsInt%2A>|<span data-ttu-id="d57a9-146"><xref:System.String> Rzutować wartości z bieżącego węzła <xref:System.Int32> wartości zgodnie z regułami rzutowanie XPath 2.0 dla `xs:integer`.</span><span class="sxs-lookup"><span data-stu-id="d57a9-146">The <xref:System.String> value of the current node cast to a <xref:System.Int32> value, according to the XPath 2.0 casting rules for `xs:integer`.</span></span>|  
|<xref:System.Xml.XPath.XPathNavigator.ValueAsLong%2A>|<span data-ttu-id="d57a9-147"><xref:System.String> Rzutować wartości z bieżącego węzła <xref:System.Int64> wartości zgodnie z regułami rzutowanie XPath 2.0 dla `xs:integer`.</span><span class="sxs-lookup"><span data-stu-id="d57a9-147">The <xref:System.String> value of the current node cast to a <xref:System.Int64> value, according to the XPath 2.0 casting rules for `xs:integer`.</span></span>|  
|<xref:System.Xml.XPath.XPathNavigator.ValueAs%2A>|<span data-ttu-id="d57a9-148">Zawartość węzła Rzutowanie na typ docelowy zgodnie z regułami rzutowanie XPath 2.0.</span><span class="sxs-lookup"><span data-stu-id="d57a9-148">The contents of the node cast to the target type according to the XPath 2.0 casting rules.</span></span>|  
  
 <span data-ttu-id="d57a9-149">Aby uzyskać więcej informacji na temat mapowanie schematu typy wbudowane typy CLR, zobacz [typu obsługi w klasach System.Xml](../../../../docs/standard/data/xml/type-support-in-the-system-xml-classes.md).</span><span class="sxs-lookup"><span data-stu-id="d57a9-149">For more information about the mapping from schema built-in types to CLR types, see [Type Support in the System.Xml Classes](../../../../docs/standard/data/xml/type-support-in-the-system-xml-classes.md).</span></span>  
  
## <a name="the-post-schema-validation-infoset-psvi"></a><span data-ttu-id="d57a9-150">Post schemat sprawdzania poprawności typu infoset sprawdzonych (PSVI)</span><span class="sxs-lookup"><span data-stu-id="d57a9-150">The Post Schema Validation Infoset (PSVI)</span></span>  
 <span data-ttu-id="d57a9-151">Procesor schematu XML akceptuje obiektu XML typu Infoset jako dane wejściowe i konwertuje ją na Post schemat sprawdzania poprawności typu Infoset (PSVI).</span><span class="sxs-lookup"><span data-stu-id="d57a9-151">An XML Schema processor accepts an XML Infoset as input and converts it into a Post Schema Validation Infoset (PSVI).</span></span> <span data-ttu-id="d57a9-152">PSVI jest oryginalny wejściowego XML typu infoset nowych elementów informacji dodany i nowych właściwości dodane do istniejących elementów informacji.</span><span class="sxs-lookup"><span data-stu-id="d57a9-152">A PSVI is the original input XML infoset with new information items added and new properties added to existing information items.</span></span> <span data-ttu-id="d57a9-153">Istnieją trzy klasy szerokie informacji dodawanych do typu Infoset XML w PSVI, które są udostępniane przez <xref:System.Xml.XPath.XPathNavigator>.</span><span class="sxs-lookup"><span data-stu-id="d57a9-153">There are three broad classes of information added to the XML Infoset in the PSVI that are exposed by the <xref:System.Xml.XPath.XPathNavigator>.</span></span>  
  
1.  <span data-ttu-id="d57a9-154">Wyniki sprawdzania poprawności: Informacje dotyczące tego, czy element lub atrybut pomyślnie zweryfikowano lub nie.</span><span class="sxs-lookup"><span data-stu-id="d57a9-154">Validation Outcomes: Information as to whether an element or attribute was successfully validated or not.</span></span> <span data-ttu-id="d57a9-155">To jest udostępniany przez <xref:System.Xml.Schema.IXmlSchemaInfo.Validity%2A> właściwość <xref:System.Xml.XPath.XPathNavigator.SchemaInfo%2A> właściwość <xref:System.Xml.XPath.XPathNavigator> klasy.</span><span class="sxs-lookup"><span data-stu-id="d57a9-155">This is exposed by the <xref:System.Xml.Schema.IXmlSchemaInfo.Validity%2A> property of the <xref:System.Xml.XPath.XPathNavigator.SchemaInfo%2A> property of the <xref:System.Xml.XPath.XPathNavigator> class.</span></span>  
  
2.  <span data-ttu-id="d57a9-156">Domyślne informacje: Wskazać, czy wartość elementu lub atrybutu uzyskano przy użyciu wartości domyślnych określonej w schemacie, czy nie.</span><span class="sxs-lookup"><span data-stu-id="d57a9-156">Default Information: Indications as to whether the value of the element or attribute was obtained via default values specified in the schema or not.</span></span> <span data-ttu-id="d57a9-157">To jest udostępniany przez <xref:System.Xml.Schema.IXmlSchemaInfo.IsDefault%2A> właściwość <xref:System.Xml.XPath.XPathNavigator.SchemaInfo%2A> właściwość <xref:System.Xml.XPath.XPathNavigator> klasy.</span><span class="sxs-lookup"><span data-stu-id="d57a9-157">This is exposed by the <xref:System.Xml.Schema.IXmlSchemaInfo.IsDefault%2A> property of the <xref:System.Xml.XPath.XPathNavigator.SchemaInfo%2A> property of the <xref:System.Xml.XPath.XPathNavigator> class.</span></span>  
  
3.  <span data-ttu-id="d57a9-158">Adnotacje typu: Odwołania do składników schematu, które mogą być definicji typu lub deklaracje elementów i atrybutów.</span><span class="sxs-lookup"><span data-stu-id="d57a9-158">Type Annotations: References to schema components that may be type definitions or element and attribute declarations.</span></span> <span data-ttu-id="d57a9-159"><xref:System.Xml.XPath.XPathNavigator.XmlType%2A> Właściwość <xref:System.Xml.XPath.XPathNavigator> zawiera informacje określonego typu węzła, jeśli jest ona prawidłowa.</span><span class="sxs-lookup"><span data-stu-id="d57a9-159">The <xref:System.Xml.XPath.XPathNavigator.XmlType%2A> property of the <xref:System.Xml.XPath.XPathNavigator> contains the specific type information of the node if it is valid.</span></span> <span data-ttu-id="d57a9-160">Jeśli ważność węzeł jest nieznany, takie jak kiedy został zweryfikowany następnie później edytować.</span><span class="sxs-lookup"><span data-stu-id="d57a9-160">If the validity of a node is unknown, such as when it was validated then subsequently edited.</span></span> <span data-ttu-id="d57a9-161">następnie przy użyciu <xref:System.Xml.XPath.XPathNavigator.XmlType%2A> właściwość jest ustawiona na `null` , ale jest nadal dostępne z różne właściwości informacji o typie <xref:System.Xml.XPath.XPathNavigator.SchemaInfo%2A> właściwość <xref:System.Xml.XPath.XPathNavigator> klasy.</span><span class="sxs-lookup"><span data-stu-id="d57a9-161">then the <xref:System.Xml.XPath.XPathNavigator.XmlType%2A> property is set to `null` but type information is still available from the various properties of the <xref:System.Xml.XPath.XPathNavigator.SchemaInfo%2A> property of the <xref:System.Xml.XPath.XPathNavigator> class.</span></span>  
  
 <span data-ttu-id="d57a9-162">Poniższy przykład przedstawia, korzystając z informacji Infoset sprawdzania poprawności schematu Post udostępnianych przez <xref:System.Xml.XPath.XPathNavigator>.</span><span class="sxs-lookup"><span data-stu-id="d57a9-162">The following example illustrates using information in the Post Schema Validation Infoset exposed by the <xref:System.Xml.XPath.XPathNavigator>.</span></span>  
  
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
  
 <span data-ttu-id="d57a9-163">Przykład przyjmuje `books.xml` pliku jako dane wejściowe.</span><span class="sxs-lookup"><span data-stu-id="d57a9-163">The example takes the `books.xml` file as input.</span></span>  
  
```xml  
<books xmlns="http://www.contoso.com/books">  
    <book>  
        <title>Title</title>  
        <price>10.00</price>  
        <published>2003-12-31</published>  
    </book>  
</books>  
```  
  
 <span data-ttu-id="d57a9-164">Przykład również przyjmuje `books.xsd` schematu jako dane wejściowe.</span><span class="sxs-lookup"><span data-stu-id="d57a9-164">The example also takes the `books.xsd` schema as input.</span></span>  
  
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
  
## <a name="obtain-typed-values-using-valueas-properties"></a><span data-ttu-id="d57a9-165">Uzyskanie typu wartości za pomocą właściwości ValueAs</span><span class="sxs-lookup"><span data-stu-id="d57a9-165">Obtain Typed Values Using ValueAs Properties</span></span>  
 <span data-ttu-id="d57a9-166">Można pobrać typu wartości węzła po zalogowaniu się do <xref:System.Xml.XPath.XPathNavigator.TypedValue%2A> właściwość <xref:System.Xml.XPath.XPathNavigator>.</span><span class="sxs-lookup"><span data-stu-id="d57a9-166">The typed value of a node can be retrieved by accessing the <xref:System.Xml.XPath.XPathNavigator.TypedValue%2A> property of the <xref:System.Xml.XPath.XPathNavigator>.</span></span> <span data-ttu-id="d57a9-167">W niektórych przypadkach można przekonwertować wartości typu węzła do innego typu.</span><span class="sxs-lookup"><span data-stu-id="d57a9-167">In certain cases you may want to convert the typed value of a node to a different type.</span></span> <span data-ttu-id="d57a9-168">Typowym przykładem jest uzyskanie wartość liczbową z węzła XML.</span><span class="sxs-lookup"><span data-stu-id="d57a9-168">A common example is to get a numeric value from an XML node.</span></span> <span data-ttu-id="d57a9-169">Rozważmy na przykład następujący dokument XML niezweryfikowanych i bez typu.</span><span class="sxs-lookup"><span data-stu-id="d57a9-169">For example, consider the following unvalidated and untyped XML document.</span></span>  
  
```xml  
<books>  
    <book>  
        <title>Title</title>  
        <price>10.00</price>  
        <published>2003-12-31</published>  
    </book>  
</books>  
```  
  
 <span data-ttu-id="d57a9-170">Jeśli <xref:System.Xml.XPath.XPathNavigator> jest ustawiony na `price` elementu <xref:System.Xml.XPath.XPathNavigator.XmlType%2A> byłoby właściwości `null`, <xref:System.Xml.XPath.XPathNavigator.ValueType%2A> byłoby właściwości <xref:System.String>i <xref:System.Xml.XPath.XPathNavigator.TypedValue%2A> właściwość może być ciągiem `10.00`.</span><span class="sxs-lookup"><span data-stu-id="d57a9-170">If the <xref:System.Xml.XPath.XPathNavigator> is positioned on the `price` element the <xref:System.Xml.XPath.XPathNavigator.XmlType%2A> property would be `null`, the <xref:System.Xml.XPath.XPathNavigator.ValueType%2A> property would be <xref:System.String>, and the <xref:System.Xml.XPath.XPathNavigator.TypedValue%2A> property would be the string `10.00`.</span></span>  
  
 <span data-ttu-id="d57a9-171">Jednak jest nadal możliwe wyodrębnić wartość jako wartość liczbowa przy użyciu <xref:System.Xml.XPath.XPathItem.ValueAs%2A>, <xref:System.Xml.XPath.XPathNavigator.ValueAsDouble%2A>, <xref:System.Xml.XPath.XPathNavigator.ValueAsInt%2A>, lub <xref:System.Xml.XPath.XPathNavigator.ValueAsLong%2A> metody i właściwości.</span><span class="sxs-lookup"><span data-stu-id="d57a9-171">However, it is still possible to extract the value as a numeric value using the <xref:System.Xml.XPath.XPathItem.ValueAs%2A>, <xref:System.Xml.XPath.XPathNavigator.ValueAsDouble%2A>, <xref:System.Xml.XPath.XPathNavigator.ValueAsInt%2A>, or <xref:System.Xml.XPath.XPathNavigator.ValueAsLong%2A> method and properties.</span></span> <span data-ttu-id="d57a9-172">Poniższy przykład przedstawia wykonywania takich rzutowania using <xref:System.Xml.XPath.XPathItem.ValueAs%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="d57a9-172">The following example illustrates performing such a cast using the <xref:System.Xml.XPath.XPathItem.ValueAs%2A> method.</span></span>  
  
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
  
 <span data-ttu-id="d57a9-173">Aby uzyskać więcej informacji na temat mapowanie schematu typy wbudowane typy CLR, zobacz [typu obsługi w klasach System.Xml](../../../../docs/standard/data/xml/type-support-in-the-system-xml-classes.md).</span><span class="sxs-lookup"><span data-stu-id="d57a9-173">For more information about the mapping from schema built-in types to CLR types, see [Type Support in the System.Xml Classes](../../../../docs/standard/data/xml/type-support-in-the-system-xml-classes.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d57a9-174">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d57a9-174">See Also</span></span>  
 <xref:System.Xml.XmlDocument>  
 <xref:System.Xml.XPath.XPathDocument>  
 <xref:System.Xml.XPath.XPathNavigator>  
 [<span data-ttu-id="d57a9-175">Obsługa typu w ramach klas zestawu System.Xml</span><span class="sxs-lookup"><span data-stu-id="d57a9-175">Type Support in the System.Xml Classes</span></span>](../../../../docs/standard/data/xml/type-support-in-the-system-xml-classes.md)  
 [<span data-ttu-id="d57a9-176">Przetwarzanie danych XML przy użyciu modelu danych XPath</span><span class="sxs-lookup"><span data-stu-id="d57a9-176">Process XML Data Using the XPath Data Model</span></span>](../../../../docs/standard/data/xml/process-xml-data-using-the-xpath-data-model.md)  
 [<span data-ttu-id="d57a9-177">Nawigacja po zestawie węzłów przy użyciu klasy XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="d57a9-177">Node Set Navigation Using XPathNavigator</span></span>](../../../../docs/standard/data/xml/node-set-navigation-using-xpathnavigator.md)  
 [<span data-ttu-id="d57a9-178">Nawigacja po atrybutach i przestrzeni nazw węzła przy użyciu klasy XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="d57a9-178">Attribute and Namespace Node Navigation Using XPathNavigator</span></span>](../../../../docs/standard/data/xml/attribute-and-namespace-node-navigation-using-xpathnavigator.md)  
 [<span data-ttu-id="d57a9-179">Wyodrębnianie danych XML przy użyciu klasy XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="d57a9-179">Extract XML Data Using XPathNavigator</span></span>](../../../../docs/standard/data/xml/extract-xml-data-using-xpathnavigator.md)
