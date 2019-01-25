---
title: Uzyskiwanie dostępu do silnie Typizowanych danych XML, przy użyciu klasy XPathNavigator
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 898e0f52-8a7c-4d1f-afcd-6ffb28b050b4
author: mairaw
ms.author: mairaw
ms.openlocfilehash: cd0719fbc84159fdf751b136c2a65b0ce40b42ec
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54665191"
---
# <a name="accessing-strongly-typed-xml-data-using-xpathnavigator"></a><span data-ttu-id="73991-102">Uzyskiwanie dostępu do silnie Typizowanych danych XML, przy użyciu klasy XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="73991-102">Accessing Strongly Typed XML Data Using XPathNavigator</span></span>
<span data-ttu-id="73991-103">Jako wystąpienia w modelu danych XPath 2.0 <xref:System.Xml.XPath.XPathNavigator> klasy może zawierać silnie typizowane dane, który jest mapowany do typowych języka wspólnego (CLR).</span><span class="sxs-lookup"><span data-stu-id="73991-103">As an instance of the XPath 2.0 data model, the <xref:System.Xml.XPath.XPathNavigator> class can contain strongly-typed data that maps to common language runtime (CLR) types.</span></span> <span data-ttu-id="73991-104">Zgodnie z modelu danych XPath 2.0 tylko elementów i atrybutów może zawierać silnie typizowane dane.</span><span class="sxs-lookup"><span data-stu-id="73991-104">According to the XPath 2.0 data model, only elements and attributes can contain strongly-typed data.</span></span> <span data-ttu-id="73991-105"><xref:System.Xml.XPath.XPathNavigator> Klasa udostępnia mechanizmy do uzyskiwania dostępu do danych w ramach <xref:System.Xml.XPath.XPathDocument> lub <xref:System.Xml.XmlDocument> obiektu jako silnie typizowane dane, a także mechanizmów do konwertowania z jednego typu danych.</span><span class="sxs-lookup"><span data-stu-id="73991-105">The <xref:System.Xml.XPath.XPathNavigator> class provides mechanisms for accessing data within an <xref:System.Xml.XPath.XPathDocument> or <xref:System.Xml.XmlDocument> object as strongly-typed data as well as mechanisms for converting from one data type to another.</span></span>  
  
## <a name="type-information-exposed-by-xpathnavigator"></a><span data-ttu-id="73991-106">Informacje o typie udostępnianych przez klasy XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="73991-106">Type Information Exposed by XPathNavigator</span></span>  
 <span data-ttu-id="73991-107">Dane XML 1.0 jest technicznie bez typu, chyba że przetworzyć DTD, XML języka (XSD) definicji schematu lub inny mechanizm.</span><span class="sxs-lookup"><span data-stu-id="73991-107">XML 1.0 data is technically without type, unless processed with a DTD, XML schema definition language (XSD) schema, or other mechanism.</span></span> <span data-ttu-id="73991-108">Istnieje wiele kategorii informacji o typie, który może być skojarzony z elementu lub atrybutu XML.</span><span class="sxs-lookup"><span data-stu-id="73991-108">There are a number of categories of type information that can be associated with an XML element or attribute.</span></span>  
  
-   <span data-ttu-id="73991-109">Typy proste CLR: Brak języki schematu XML bezpośrednio obsługują typy środowiska uruchomieniowego języka wspólnego (CLR).</span><span class="sxs-lookup"><span data-stu-id="73991-109">Simple CLR Types: None of the XML Schema languages support Common Language Runtime (CLR) types directly.</span></span> <span data-ttu-id="73991-110">Ponieważ jest to przydatne można było wyświetlić prosty element i atrybut zawartość jako najbardziej odpowiednim typem CLR, cała zawartość prostą można wpisać jako <xref:System.String> w przypadku braku informacji o schemacie ze wszystkimi dodano potencjalnie rafinacja tę zawartość do informacji o schemacie Typ, bardziej odpowiednie.</span><span class="sxs-lookup"><span data-stu-id="73991-110">Because it is useful to be able to view simple element and attribute content as the most appropriate CLR type, all simple content can be typed as <xref:System.String> in the absence of schema information with any added schema information potentially refining this content to a more appropriate type.</span></span> <span data-ttu-id="73991-111">Możesz znaleźć najlepiej dopasowaną typ CLR prostej zawartości elementów i atrybutów przy użyciu <xref:System.Xml.XPath.XPathNavigator.ValueType%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="73991-111">You can find the best matching CLR type of simple element and attribute content by using the <xref:System.Xml.XPath.XPathNavigator.ValueType%2A> property.</span></span> <span data-ttu-id="73991-112">Aby uzyskać więcej informacji o mapowaniu z wbudowanych typów schematu na typy CLR, zobacz [Obsługa typu w ramach klas zestawu System.Xml](../../../../docs/standard/data/xml/type-support-in-the-system-xml-classes.md).</span><span class="sxs-lookup"><span data-stu-id="73991-112">For more information about the mapping from schema built-in types to CLR types, see [Type Support in the System.Xml Classes](../../../../docs/standard/data/xml/type-support-in-the-system-xml-classes.md).</span></span>  
  
-   <span data-ttu-id="73991-113">Wyświetla typy proste (CLR): Element lub atrybut o zawartości prostej mogą zawierać listę wartości oddzielonych biały znak.</span><span class="sxs-lookup"><span data-stu-id="73991-113">Lists of Simple (CLR) Types: An element or attribute with simple content can contain a list of values separated by white space.</span></span> <span data-ttu-id="73991-114">Wartości są określone przez schemat XML jako "type listy".</span><span class="sxs-lookup"><span data-stu-id="73991-114">The values are specified by an XML Schema to be a "list type."</span></span> <span data-ttu-id="73991-115">W przypadku braku schematu XML takie prostej zawartości będzie traktowane jako węzeł tekstowy jednego.</span><span class="sxs-lookup"><span data-stu-id="73991-115">In the absence of an XML Schema, such simple content would be treated as a single text node.</span></span> <span data-ttu-id="73991-116">Po udostępnieniu schematu XML jako szereg niepodzielnych wartości posiadającymi prosty typ, który jest mapowany do kolekcji obiektów CLR można ujawnić tej prostej zawartości.</span><span class="sxs-lookup"><span data-stu-id="73991-116">When an XML Schema is available, this simple content can be exposed as a series of atomic values each having a simple type that maps to a collection of CLR objects.</span></span> <span data-ttu-id="73991-117">Aby uzyskać więcej informacji o mapowaniu z wbudowanych typów schematu na typy CLR, zobacz [Obsługa typu w ramach klas zestawu System.Xml](../../../../docs/standard/data/xml/type-support-in-the-system-xml-classes.md).</span><span class="sxs-lookup"><span data-stu-id="73991-117">For more information about the mapping from schema built-in types to CLR types, see [Type Support in the System.Xml Classes](../../../../docs/standard/data/xml/type-support-in-the-system-xml-classes.md).</span></span>  
  
-   <span data-ttu-id="73991-118">Wartość: Sprawdzania poprawności schematu atrybutu lub elementu z typu prostego ma wartość wpisane.</span><span class="sxs-lookup"><span data-stu-id="73991-118">Typed Value: A schema-validated attribute or element with a simple type has a typed value.</span></span> <span data-ttu-id="73991-119">Ta wartość jest typu podstawowego, takich jak numeryczne, ciągu lub typu Data.</span><span class="sxs-lookup"><span data-stu-id="73991-119">This value is a primitive type such as a numeric, string, or date type.</span></span> <span data-ttu-id="73991-120">Wszystkie wbudowane typy proste w XSD mogą być mapowane na typy CLR, które zapewniają dostęp do wartości węzła jako typu bardziej odpowiednie, a nie tylko jako <xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="73991-120">All the built-in simple types in XSD can be mapped to CLR types that provide access to the value of a node as a more appropriate type instead of just as a <xref:System.String>.</span></span> <span data-ttu-id="73991-121">Element o atrybuty i elementy podrzędne jest uważana za typ złożony.</span><span class="sxs-lookup"><span data-stu-id="73991-121">An element with attributes or element children is considered to be a complex type.</span></span> <span data-ttu-id="73991-122">Wpisane wartości typu złożonego o zawartości prostej (tylko węzły tekstowe jako elementy podrzędne) jest taka sama jak w przypadku typu prostego jego zawartości.</span><span class="sxs-lookup"><span data-stu-id="73991-122">The typed value of a complex type with simple content (only text nodes as children) is the same as that of the simple type of its content.</span></span> <span data-ttu-id="73991-123">Wpisane wartość typ złożony z zawartością złożoną (jeden lub więcej elementów podrzędnych) jest wartość ciągu łączenia wszystkie jego podrzędne węzły tekstowe zwracane jako <xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="73991-123">The typed value of a complex type with complex content (one or more child elements) is the string value of the concatenation of all its child text nodes returned as a <xref:System.String>.</span></span> <span data-ttu-id="73991-124">Aby uzyskać więcej informacji o mapowaniu z wbudowanych typów schematu na typy CLR, zobacz [Obsługa typu w ramach klas zestawu System.Xml](../../../../docs/standard/data/xml/type-support-in-the-system-xml-classes.md).</span><span class="sxs-lookup"><span data-stu-id="73991-124">For more information about the mapping from schema built-in types to CLR types, see [Type Support in the System.Xml Classes](../../../../docs/standard/data/xml/type-support-in-the-system-xml-classes.md).</span></span>  
  
-   <span data-ttu-id="73991-125">Nazwa typu określonego schematu języka: W większości przypadków typy CLR, które są ustawione jako efekt uboczny stosowania zewnętrznych schematu, są używane do zapewnienia dostępu do wartości węzła.</span><span class="sxs-lookup"><span data-stu-id="73991-125">Schema-Language Specific Type Name: In most cases, the CLR types, which are set as a side-effect of applying an external schema, are used to provide access to the value of a node.</span></span> <span data-ttu-id="73991-126">Jednakże mogą wystąpić sytuacje, w których możesz chcieć sprawdzić typ skojarzony z określonym schematem zastosowane do dokumentu XML.</span><span class="sxs-lookup"><span data-stu-id="73991-126">However, there may be situations where you may want to examine the type associated with a particular schema applied to an XML document.</span></span> <span data-ttu-id="73991-127">Na przykład możesz przeszukiwać dokumentu XML wyodrębniania wszystkie elementy, które są określane mieć zawartości typu "PurchaseOrder" zgodnie ze schematu.</span><span class="sxs-lookup"><span data-stu-id="73991-127">For example, you may wish to search through an XML document, extracting all elements that are determined to have content of type "PurchaseOrder" according to an attached schema.</span></span> <span data-ttu-id="73991-128">Takie informacje o typie można ustawić tylko w wyniku sprawdzania poprawności schematu i tych informacji jest dostępny za pośrednictwem <xref:System.Xml.XPath.XPathNavigator.XmlType%2A> i <xref:System.Xml.XPath.XPathNavigator.SchemaInfo%2A> właściwości <xref:System.Xml.XPath.XPathNavigator> klasy.</span><span class="sxs-lookup"><span data-stu-id="73991-128">Such type information can be set only as a result of schema validation and this information is accessed through the <xref:System.Xml.XPath.XPathNavigator.XmlType%2A> and <xref:System.Xml.XPath.XPathNavigator.SchemaInfo%2A> properties of the <xref:System.Xml.XPath.XPathNavigator> class.</span></span> <span data-ttu-id="73991-129">Aby uzyskać więcej informacji zobacz sekcję wpis zestaw informacji o weryfikacji schematu (PSVI) poniżej.</span><span class="sxs-lookup"><span data-stu-id="73991-129">For more information, see The Post Schema Validation Infoset (PSVI) section below.</span></span>  
  
-   <span data-ttu-id="73991-130">Odbicie określonego typu język schematu: W innych przypadkach można uzyskać dodatkowe szczegóły dotyczące określonego schematu zastosowane do dokumentu XML.</span><span class="sxs-lookup"><span data-stu-id="73991-130">Schema-Language Specific Type Reflection: In other cases, you may want to obtain further details of the schema-specific type applied to an XML document.</span></span> <span data-ttu-id="73991-131">Na przykład podczas odczytywania pliku XML, które mogą mają zostać wyodrębnione `maxOccurs` atrybutu dla każdej prawidłowym węzłem w dokumencie XML w celu wykonywania niektórych obliczeń niestandardowych.</span><span class="sxs-lookup"><span data-stu-id="73991-131">For example, when reading an XML file, you may want to extract the `maxOccurs` attribute for each valid node in the XML document in order to perform some custom calculation.</span></span> <span data-ttu-id="73991-132">Ponieważ te informacje jest ustawiona tylko za pośrednictwem weryfikacji schematu, jest dostępny za pośrednictwem <xref:System.Xml.XPath.XPathNavigator.SchemaInfo%2A> właściwość <xref:System.Xml.XPath.XPathNavigator> klasy.</span><span class="sxs-lookup"><span data-stu-id="73991-132">Because this information is set only through schema validation, it is accessed through the <xref:System.Xml.XPath.XPathNavigator.SchemaInfo%2A> property of the <xref:System.Xml.XPath.XPathNavigator> class.</span></span> <span data-ttu-id="73991-133">Aby uzyskać więcej informacji zobacz sekcję wpis zestaw informacji o weryfikacji schematu (PSVI) poniżej.</span><span class="sxs-lookup"><span data-stu-id="73991-133">For more information, see The Post Schema Validation Infoset (PSVI) section below.</span></span>  
  
## <a name="xpathnavigator-typed-accessors"></a><span data-ttu-id="73991-134">Klasy XPathNavigator Typizowane metody dostępu</span><span class="sxs-lookup"><span data-stu-id="73991-134">XPathNavigator Typed Accessors</span></span>  
 <span data-ttu-id="73991-135">W poniższej tabeli przedstawiono różne właściwości i metod <xref:System.Xml.XPath.XPathNavigator> klasę, która może służyć do dostępu do informacji o typie, informacje o węźle.</span><span class="sxs-lookup"><span data-stu-id="73991-135">The following table shows the various properties and methods of the <xref:System.Xml.XPath.XPathNavigator> class that can be used to access the type information about a node.</span></span>  
  
|<span data-ttu-id="73991-136">Właściwość</span><span class="sxs-lookup"><span data-stu-id="73991-136">Property</span></span>|<span data-ttu-id="73991-137">Opis</span><span class="sxs-lookup"><span data-stu-id="73991-137">Description</span></span>|  
|--------------|-----------------|  
|<xref:System.Xml.XPath.XPathNavigator.XmlType%2A>|<span data-ttu-id="73991-138">Zawiera informacje o typie schematu XML dla węzła, jeśli jest on prawidłowy.</span><span class="sxs-lookup"><span data-stu-id="73991-138">This contains the XML schema type information for the node if it is valid.</span></span>|  
|<xref:System.Xml.XPath.XPathNavigator.SchemaInfo%2A>|<span data-ttu-id="73991-139">Zawiera zestaw informacji sprawdzania poprawności schematu wpis węzła, który zostanie dodany po weryfikacji.</span><span class="sxs-lookup"><span data-stu-id="73991-139">This contains the Post Schema Validation Infoset of the node that is added after validation.</span></span> <span data-ttu-id="73991-140">W tym informacje o typie schematu XML, a także informacje o ważności.</span><span class="sxs-lookup"><span data-stu-id="73991-140">This includes the XML schema type information, as well as validity information.</span></span>|  
|<xref:System.Xml.XPath.XPathNavigator.ValueType%2A>|<span data-ttu-id="73991-141">Typ CLR typizowaną wartość węzła.</span><span class="sxs-lookup"><span data-stu-id="73991-141">The CLR type of the typed value of the node.</span></span>|  
|<xref:System.Xml.XPath.XPathNavigator.TypedValue%2A>|<span data-ttu-id="73991-142">Zawartość węzła CLR jeden lub więcej wartości o typie jest najlepiej dopasowany do typu schematu XML węzła.</span><span class="sxs-lookup"><span data-stu-id="73991-142">The content of the node as one or more CLR values whose type is the closest match to the XML schema type of the node.</span></span>|  
|<xref:System.Xml.XPath.XPathNavigator.ValueAsBoolean%2A>|<span data-ttu-id="73991-143"><xref:System.String> Rzutować wartości bieżącego węzła <xref:System.Boolean> wartości z regułami rzutowania XPath 2.0 `xs:boolean`.</span><span class="sxs-lookup"><span data-stu-id="73991-143">The <xref:System.String> value of the current node cast to a <xref:System.Boolean> value, according to the XPath 2.0 casting rules for `xs:boolean`.</span></span>|  
|<xref:System.Xml.XPath.XPathNavigator.ValueAsDateTime%2A>|<span data-ttu-id="73991-144"><xref:System.String> Rzutować wartości bieżącego węzła <xref:System.DateTime> wartości z regułami rzutowania XPath 2.0 `xs:datetime`.</span><span class="sxs-lookup"><span data-stu-id="73991-144">The <xref:System.String> value of the current node cast to a <xref:System.DateTime> value, according to the XPath 2.0 casting rules for `xs:datetime`.</span></span>|  
|<xref:System.Xml.XPath.XPathNavigator.ValueAsDouble%2A>|<span data-ttu-id="73991-145"><xref:System.String> Rzutować wartości bieżącego węzła <xref:System.Double> wartości z regułami rzutowania XPath 2.0 `xsd:double`.</span><span class="sxs-lookup"><span data-stu-id="73991-145">The <xref:System.String> value of the current node cast to a <xref:System.Double> value, according to the XPath 2.0 casting rules for `xsd:double`.</span></span>|  
|<xref:System.Xml.XPath.XPathNavigator.ValueAsInt%2A>|<span data-ttu-id="73991-146"><xref:System.String> Rzutować wartości bieżącego węzła <xref:System.Int32> wartości z regułami rzutowania XPath 2.0 `xs:integer`.</span><span class="sxs-lookup"><span data-stu-id="73991-146">The <xref:System.String> value of the current node cast to a <xref:System.Int32> value, according to the XPath 2.0 casting rules for `xs:integer`.</span></span>|  
|<xref:System.Xml.XPath.XPathNavigator.ValueAsLong%2A>|<span data-ttu-id="73991-147"><xref:System.String> Rzutować wartości bieżącego węzła <xref:System.Int64> wartości z regułami rzutowania XPath 2.0 `xs:integer`.</span><span class="sxs-lookup"><span data-stu-id="73991-147">The <xref:System.String> value of the current node cast to a <xref:System.Int64> value, according to the XPath 2.0 casting rules for `xs:integer`.</span></span>|  
|<xref:System.Xml.XPath.XPathNavigator.ValueAs%2A>|<span data-ttu-id="73991-148">Zawartość węzła rzutowany na typ docelowy zgodnie z regułami rzutowania XPath 2.0.</span><span class="sxs-lookup"><span data-stu-id="73991-148">The contents of the node cast to the target type according to the XPath 2.0 casting rules.</span></span>|  
  
 <span data-ttu-id="73991-149">Aby uzyskać więcej informacji o mapowaniu z wbudowanych typów schematu na typy CLR, zobacz [Obsługa typu w ramach klas zestawu System.Xml](../../../../docs/standard/data/xml/type-support-in-the-system-xml-classes.md).</span><span class="sxs-lookup"><span data-stu-id="73991-149">For more information about the mapping from schema built-in types to CLR types, see [Type Support in the System.Xml Classes](../../../../docs/standard/data/xml/type-support-in-the-system-xml-classes.md).</span></span>  
  
## <a name="the-post-schema-validation-infoset-psvi"></a><span data-ttu-id="73991-150">Zestaw w informacji sprawdzania poprawności schematu Post (PSVI)</span><span class="sxs-lookup"><span data-stu-id="73991-150">The Post Schema Validation Infoset (PSVI)</span></span>  
 <span data-ttu-id="73991-151">Procesor schematu XML akceptuje zestaw informacji XML, jako dane wejściowe i konwertuje ją na wpis schematu sprawdzania poprawności zestaw informacji (PSVI).</span><span class="sxs-lookup"><span data-stu-id="73991-151">An XML Schema processor accepts an XML Infoset as input and converts it into a Post Schema Validation Infoset (PSVI).</span></span> <span data-ttu-id="73991-152">PSVI jest oryginalnym danych wejściowych XML zestaw informacji z nowe elementy informacje dodane i nowy właściwości dodawane do istniejących elementów informacji.</span><span class="sxs-lookup"><span data-stu-id="73991-152">A PSVI is the original input XML infoset with new information items added and new properties added to existing information items.</span></span> <span data-ttu-id="73991-153">Istnieją trzy klasy szerokiego informacji dodawanych do zestaw informacji XML w PSVI, które są udostępniane przez <xref:System.Xml.XPath.XPathNavigator>.</span><span class="sxs-lookup"><span data-stu-id="73991-153">There are three broad classes of information added to the XML Infoset in the PSVI that are exposed by the <xref:System.Xml.XPath.XPathNavigator>.</span></span>  
  
1.  <span data-ttu-id="73991-154">Wyniki sprawdzania poprawności: Informacje dotyczące tego, czy element lub atrybut został pomyślnie zweryfikowany czy nie.</span><span class="sxs-lookup"><span data-stu-id="73991-154">Validation Outcomes: Information as to whether an element or attribute was successfully validated or not.</span></span> <span data-ttu-id="73991-155">To jest uwidaczniany przez <xref:System.Xml.Schema.IXmlSchemaInfo.Validity%2A> właściwość <xref:System.Xml.XPath.XPathNavigator.SchemaInfo%2A> właściwość <xref:System.Xml.XPath.XPathNavigator> klasy.</span><span class="sxs-lookup"><span data-stu-id="73991-155">This is exposed by the <xref:System.Xml.Schema.IXmlSchemaInfo.Validity%2A> property of the <xref:System.Xml.XPath.XPathNavigator.SchemaInfo%2A> property of the <xref:System.Xml.XPath.XPathNavigator> class.</span></span>  
  
2.  <span data-ttu-id="73991-156">Domyślne informacje: Wskazanie, czy wartość elementu lub atrybutu uzyskano przy użyciu wartości domyślnych, określona w schemacie, czy nie.</span><span class="sxs-lookup"><span data-stu-id="73991-156">Default Information: Indications as to whether the value of the element or attribute was obtained via default values specified in the schema or not.</span></span> <span data-ttu-id="73991-157">To jest uwidaczniany przez <xref:System.Xml.Schema.IXmlSchemaInfo.IsDefault%2A> właściwość <xref:System.Xml.XPath.XPathNavigator.SchemaInfo%2A> właściwość <xref:System.Xml.XPath.XPathNavigator> klasy.</span><span class="sxs-lookup"><span data-stu-id="73991-157">This is exposed by the <xref:System.Xml.Schema.IXmlSchemaInfo.IsDefault%2A> property of the <xref:System.Xml.XPath.XPathNavigator.SchemaInfo%2A> property of the <xref:System.Xml.XPath.XPathNavigator> class.</span></span>  
  
3.  <span data-ttu-id="73991-158">Deklaracje typów: Odwołania do składników schematu, które mogą być definicje typów lub elementów i atrybutów deklaracji.</span><span class="sxs-lookup"><span data-stu-id="73991-158">Type Annotations: References to schema components that may be type definitions or element and attribute declarations.</span></span> <span data-ttu-id="73991-159"><xref:System.Xml.XPath.XPathNavigator.XmlType%2A> Właściwość <xref:System.Xml.XPath.XPathNavigator> zawiera informacje o określonym typie węzła, jeśli jest on prawidłowy.</span><span class="sxs-lookup"><span data-stu-id="73991-159">The <xref:System.Xml.XPath.XPathNavigator.XmlType%2A> property of the <xref:System.Xml.XPath.XPathNavigator> contains the specific type information of the node if it is valid.</span></span> <span data-ttu-id="73991-160">W przypadku ważności węzeł jest nieznany, takie jak kiedy została zweryfikowana następnie później edytować.</span><span class="sxs-lookup"><span data-stu-id="73991-160">If the validity of a node is unknown, such as when it was validated then subsequently edited.</span></span> <span data-ttu-id="73991-161">a następnie <xref:System.Xml.XPath.XPathNavigator.XmlType%2A> właściwość jest ustawiona na `null` , ale informacje o typie jest nadal dostępne z poziomu różnych właściwości obiektu <xref:System.Xml.XPath.XPathNavigator.SchemaInfo%2A> właściwość <xref:System.Xml.XPath.XPathNavigator> klasy.</span><span class="sxs-lookup"><span data-stu-id="73991-161">then the <xref:System.Xml.XPath.XPathNavigator.XmlType%2A> property is set to `null` but type information is still available from the various properties of the <xref:System.Xml.XPath.XPathNavigator.SchemaInfo%2A> property of the <xref:System.Xml.XPath.XPathNavigator> class.</span></span>  
  
 <span data-ttu-id="73991-162">W poniższym przykładzie pokazano, korzystając z informacji udostępnianych przez zestaw wpis schematu sprawdzania poprawności informacji <xref:System.Xml.XPath.XPathNavigator>.</span><span class="sxs-lookup"><span data-stu-id="73991-162">The following example illustrates using information in the Post Schema Validation Infoset exposed by the <xref:System.Xml.XPath.XPathNavigator>.</span></span>  
  
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
  
 <span data-ttu-id="73991-163">Przykład przyjmuje `books.xml` pliku jako dane wejściowe.</span><span class="sxs-lookup"><span data-stu-id="73991-163">The example takes the `books.xml` file as input.</span></span>  
  
```xml  
<books xmlns="http://www.contoso.com/books">  
    <book>  
        <title>Title</title>  
        <price>10.00</price>  
        <published>2003-12-31</published>  
    </book>  
</books>  
```  
  
 <span data-ttu-id="73991-164">Przykład pobiera również `books.xsd` schematu jako dane wejściowe.</span><span class="sxs-lookup"><span data-stu-id="73991-164">The example also takes the `books.xsd` schema as input.</span></span>  
  
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
  
## <a name="obtain-typed-values-using-valueas-properties"></a><span data-ttu-id="73991-165">Uzyskiwanie wartości Typizowane, za pomocą właściwości ValueAs</span><span class="sxs-lookup"><span data-stu-id="73991-165">Obtain Typed Values Using ValueAs Properties</span></span>  
 <span data-ttu-id="73991-166">Wpisane wartości węzła mogą być pobierane, uzyskując dostęp do <xref:System.Xml.XPath.XPathNavigator.TypedValue%2A> właściwość <xref:System.Xml.XPath.XPathNavigator>.</span><span class="sxs-lookup"><span data-stu-id="73991-166">The typed value of a node can be retrieved by accessing the <xref:System.Xml.XPath.XPathNavigator.TypedValue%2A> property of the <xref:System.Xml.XPath.XPathNavigator>.</span></span> <span data-ttu-id="73991-167">W niektórych przypadkach można przekonwertować wartości typizowane węzła do innego typu.</span><span class="sxs-lookup"><span data-stu-id="73991-167">In certain cases you may want to convert the typed value of a node to a different type.</span></span> <span data-ttu-id="73991-168">Typowym przykładem jest można uzyskać wartość liczbową z węzła XML.</span><span class="sxs-lookup"><span data-stu-id="73991-168">A common example is to get a numeric value from an XML node.</span></span> <span data-ttu-id="73991-169">Na przykład rozważmy następujący dokument XML niezweryfikowanych i bez typu.</span><span class="sxs-lookup"><span data-stu-id="73991-169">For example, consider the following unvalidated and untyped XML document.</span></span>  
  
```xml  
<books>  
    <book>  
        <title>Title</title>  
        <price>10.00</price>  
        <published>2003-12-31</published>  
    </book>  
</books>  
```  
  
 <span data-ttu-id="73991-170">Jeśli <xref:System.Xml.XPath.XPathNavigator> jest ustawiony na `price` elementu <xref:System.Xml.XPath.XPathNavigator.XmlType%2A> będzie właściwość `null`, <xref:System.Xml.XPath.XPathNavigator.ValueType%2A> będzie właściwość <xref:System.String>i <xref:System.Xml.XPath.XPathNavigator.TypedValue%2A> właściwość może być ciągiem `10.00`.</span><span class="sxs-lookup"><span data-stu-id="73991-170">If the <xref:System.Xml.XPath.XPathNavigator> is positioned on the `price` element the <xref:System.Xml.XPath.XPathNavigator.XmlType%2A> property would be `null`, the <xref:System.Xml.XPath.XPathNavigator.ValueType%2A> property would be <xref:System.String>, and the <xref:System.Xml.XPath.XPathNavigator.TypedValue%2A> property would be the string `10.00`.</span></span>  
  
 <span data-ttu-id="73991-171">Będzie jednak nadal możliwe do wyodrębnienia wartości jako wartość liczbową przy użyciu <xref:System.Xml.XPath.XPathItem.ValueAs%2A>, <xref:System.Xml.XPath.XPathNavigator.ValueAsDouble%2A>, <xref:System.Xml.XPath.XPathNavigator.ValueAsInt%2A>, lub <xref:System.Xml.XPath.XPathNavigator.ValueAsLong%2A> metody i właściwości.</span><span class="sxs-lookup"><span data-stu-id="73991-171">However, it is still possible to extract the value as a numeric value using the <xref:System.Xml.XPath.XPathItem.ValueAs%2A>, <xref:System.Xml.XPath.XPathNavigator.ValueAsDouble%2A>, <xref:System.Xml.XPath.XPathNavigator.ValueAsInt%2A>, or <xref:System.Xml.XPath.XPathNavigator.ValueAsLong%2A> method and properties.</span></span> <span data-ttu-id="73991-172">W poniższym przykładzie pokazano wykonywania takich rzutowanie za pomocą <xref:System.Xml.XPath.XPathItem.ValueAs%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="73991-172">The following example illustrates performing such a cast using the <xref:System.Xml.XPath.XPathItem.ValueAs%2A> method.</span></span>  
  
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
  
 <span data-ttu-id="73991-173">Aby uzyskać więcej informacji o mapowaniu z wbudowanych typów schematu na typy CLR, zobacz [Obsługa typu w ramach klas zestawu System.Xml](../../../../docs/standard/data/xml/type-support-in-the-system-xml-classes.md).</span><span class="sxs-lookup"><span data-stu-id="73991-173">For more information about the mapping from schema built-in types to CLR types, see [Type Support in the System.Xml Classes](../../../../docs/standard/data/xml/type-support-in-the-system-xml-classes.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="73991-174">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="73991-174">See also</span></span>

- <xref:System.Xml.XmlDocument>
- <xref:System.Xml.XPath.XPathDocument>
- <xref:System.Xml.XPath.XPathNavigator>
- [<span data-ttu-id="73991-175">Obsługa typu w ramach klas zestawu System.Xml</span><span class="sxs-lookup"><span data-stu-id="73991-175">Type Support in the System.Xml Classes</span></span>](../../../../docs/standard/data/xml/type-support-in-the-system-xml-classes.md)
- [<span data-ttu-id="73991-176">Przetwarzanie danych XML przy użyciu modelu danych XPath</span><span class="sxs-lookup"><span data-stu-id="73991-176">Process XML Data Using the XPath Data Model</span></span>](../../../../docs/standard/data/xml/process-xml-data-using-the-xpath-data-model.md)
- [<span data-ttu-id="73991-177">Nawigacja po zestawie węzłów przy użyciu klasy XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="73991-177">Node Set Navigation Using XPathNavigator</span></span>](../../../../docs/standard/data/xml/node-set-navigation-using-xpathnavigator.md)
- [<span data-ttu-id="73991-178">Nawigacja po atrybutach i przestrzeni nazw węzła przy użyciu klasy XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="73991-178">Attribute and Namespace Node Navigation Using XPathNavigator</span></span>](../../../../docs/standard/data/xml/attribute-and-namespace-node-navigation-using-xpathnavigator.md)
- [<span data-ttu-id="73991-179">Wyodrębnianie danych XML przy użyciu klasy XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="73991-179">Extract XML Data Using XPathNavigator</span></span>](../../../../docs/standard/data/xml/extract-xml-data-using-xpathnavigator.md)
