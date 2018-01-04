---
title: "Omówienie modelu obiektu schematu XML"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 896a1e12-5655-42c6-8cdd-89c12862b34b
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: e18a3151228ea7edb5a8380f6ed707ee88d369e5
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/23/2017
---
# <a name="xml-schema-object-model-overview"></a><span data-ttu-id="a680e-102">Omówienie modelu obiektu schematu XML</span><span class="sxs-lookup"><span data-stu-id="a680e-102">XML Schema Object Model Overview</span></span>
<span data-ttu-id="a680e-103">Model obiektu schematu (SOM) w programie Microsoft .NET Framework jest sformatowany interfejs API, który służy do tworzenia, edytowania i Zweryfikuj schematy programowo.</span><span class="sxs-lookup"><span data-stu-id="a680e-103">The Schema Object Model (SOM) in the Microsoft .NET Framework is a rich API that allows you to create, edit, and validate schemas programmatically.</span></span> <span data-ttu-id="a680e-104">SOM działa na dokumentach schematów XML w sposób podobny do modelu DOM (Document Object) funkcjonowania w dokumentach XML.</span><span class="sxs-lookup"><span data-stu-id="a680e-104">The SOM operates on XML schema documents similarly to the way the Document Object Model (DOM) operates on XML documents.</span></span> <span data-ttu-id="a680e-105">Dokumenty XML schematu są prawidłowe pliki XML, które po załadowaniu do SOM, zmienić znaczenie dotyczących struktury i ważności inne dokumenty XML, które są zgodne ze schematem.</span><span class="sxs-lookup"><span data-stu-id="a680e-105">XML schema documents are valid XML files that, once loaded into the SOM, convey meaning about the structure and validity of other XML documents which conform to the schema.</span></span>  
  
 <span data-ttu-id="a680e-106">Schemat jest dokument XML, który definiuje klasę dokumentów XML, określając struktury lub modelu dokumentów XML dla określonego schematu.</span><span class="sxs-lookup"><span data-stu-id="a680e-106">A schema is an XML document that defines a class of XML documents by specifying the structure or model of XML documents for a particular schema.</span></span> <span data-ttu-id="a680e-107">Schemat wymieniono ograniczenia dotyczące zawartość dokumentów XML i opisano słownictwa (reguły lub gramatyki), który dokumentów XML zgodne należy wykonać, aby można je było uważać schematu prawidłowe z określonego schematu.</span><span class="sxs-lookup"><span data-stu-id="a680e-107">A schema identifies the constraints on the content of the XML documents, and describes the vocabulary (rules or grammar) that compliant XML documents must follow in order to be considered schema-valid with that particular schema.</span></span> <span data-ttu-id="a680e-108">Weryfikacja dokumentu XML jest proces, który zapewnia, że dokument odpowiada gramatyki określonej w schemacie.</span><span class="sxs-lookup"><span data-stu-id="a680e-108">Validation of an XML document is the process that ensures that the document conforms to the grammar specified by the schema.</span></span>  
  
 <span data-ttu-id="a680e-109">Poniżej przedstawiono sposoby SOM interfejsu API w programie .NET Framework umożliwia tworzenie, edytowanie i Zweryfikuj schematy.</span><span class="sxs-lookup"><span data-stu-id="a680e-109">The following are ways the SOM API in the .NET Framework enables you to create, edit, and validate schemas.</span></span>  
  
-   <span data-ttu-id="a680e-110">Załaduj i Zapisz prawidłowe schematy do i z plików.</span><span class="sxs-lookup"><span data-stu-id="a680e-110">Load and save valid schemas to and from files.</span></span>  
  
-   <span data-ttu-id="a680e-111">Tworzenie przy użyciu klasy jednoznacznie schematów w pamięci.</span><span class="sxs-lookup"><span data-stu-id="a680e-111">Create in-memory schemas using strongly typed classes.</span></span>  
  
-   <span data-ttu-id="a680e-112">Interakcje z <xref:System.Xml.Schema.XmlSchemaSet> klasy do pamięci podręcznej, kompilowania i pobrać schematów.</span><span class="sxs-lookup"><span data-stu-id="a680e-112">Interact with the <xref:System.Xml.Schema.XmlSchemaSet> class to cache, compile, and retrieve schemas.</span></span>  
  
-   <span data-ttu-id="a680e-113">Interakcje z <xref:System.Xml.XmlReader.Create%2A> metody <xref:System.Xml.XmlReader> klasy do sprawdzania poprawności dokumentów wystąpienie XML względem schematów.</span><span class="sxs-lookup"><span data-stu-id="a680e-113">Interact with the <xref:System.Xml.XmlReader.Create%2A> method of the <xref:System.Xml.XmlReader> class to validate XML instance documents against schemas.</span></span>  
  
-   <span data-ttu-id="a680e-114">Tworzenie edytory za tworzenie i obsługę schematów.</span><span class="sxs-lookup"><span data-stu-id="a680e-114">Build editors for creating and maintaining schemas.</span></span>  
  
-   <span data-ttu-id="a680e-115">Edytuj dynamicznie schematu, które mogą być spełnione i zapisywane do użycia w weryfikacji dokumentów wystąpienie XML.</span><span class="sxs-lookup"><span data-stu-id="a680e-115">Dynamically edit a schema that can be complied and saved for use in the validation of XML instance documents.</span></span>  
  
## <a name="the-schema-object-model"></a><span data-ttu-id="a680e-116">Model obiektu schematu</span><span class="sxs-lookup"><span data-stu-id="a680e-116">The Schema Object Model</span></span>  
 <span data-ttu-id="a680e-117">SOM składa się z rozbudowany zestaw klas w <xref:System.Xml.Schema?displayProperty=nameWithType> przestrzeni nazw odpowiadające elementom w schemacie XML.</span><span class="sxs-lookup"><span data-stu-id="a680e-117">The SOM consists of an extensive set of classes in the <xref:System.Xml.Schema?displayProperty=nameWithType> namespace corresponding to the elements in an XML schema.</span></span> <span data-ttu-id="a680e-118">Na przykład `<xsd:schema>...</xsd:schema>` mapuje element <xref:System.Xml.Schema.XmlSchema?displayProperty=nameWithType> klasy i wszystkie informacje, które mogą być zawarte w `<xsd:schema/>` elementu można przedstawić przy użyciu <xref:System.Xml.Schema.XmlSchema> klasy.</span><span class="sxs-lookup"><span data-stu-id="a680e-118">For example, the `<xsd:schema>...</xsd:schema>` element maps to the <xref:System.Xml.Schema.XmlSchema?displayProperty=nameWithType> class, and all the information that can be contained within an `<xsd:schema/>` element can be represented using the <xref:System.Xml.Schema.XmlSchema> class.</span></span> <span data-ttu-id="a680e-119">Podobnie `<xsd:element>...</xsd:element>` i `<xsd:attribute>...</xsd:attribute>` elementy mapy do <xref:System.Xml.Schema.XmlSchemaElement?displayProperty=nameWithType> i <xref:System.Xml.Schema.XmlSchemaAttribute?displayProperty=nameWithType> odpowiednio klasy.</span><span class="sxs-lookup"><span data-stu-id="a680e-119">Similarly, the `<xsd:element>...</xsd:element>` and `<xsd:attribute>...</xsd:attribute>` elements map to the <xref:System.Xml.Schema.XmlSchemaElement?displayProperty=nameWithType> and <xref:System.Xml.Schema.XmlSchemaAttribute?displayProperty=nameWithType> classes respectively.</span></span> <span data-ttu-id="a680e-120">To mapowanie nadal dla wszystkich elementów schematu XML tworzenia modelu obiektu schematu XML w <xref:System.Xml.Schema> przedstawione na diagramie, znajdujący się w przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="a680e-120">This mapping continues for all the elements of an XML schema creating an XML schema object model in the <xref:System.Xml.Schema> namespace illustrated in the diagram that follows.</span></span>  
  
 <span data-ttu-id="a680e-121">![Model obiektu System.Xml.Schema](../../../../docs/standard/data/xml/media/xmlschemaobjmodeloverview.gif "XMLSchemaObjModelOverview")</span><span class="sxs-lookup"><span data-stu-id="a680e-121">![System.Xml.Schema Object Model](../../../../docs/standard/data/xml/media/xmlschemaobjmodeloverview.gif "XMLSchemaObjModelOverview")</span></span>  
  
 <span data-ttu-id="a680e-122">Aby uzyskać więcej informacji o poszczególnych klasach w <xref:System.Xml.Schema> przestrzeni nazw, zobacz <xref:System.Xml.Schema> przestrzeni nazw dokumentacji w bibliotece klas programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="a680e-122">For more information about each class in the <xref:System.Xml.Schema> namespace, see the <xref:System.Xml.Schema> namespace reference documentation in the .NET Framework class library.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a680e-123">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a680e-123">See Also</span></span>  
 [<span data-ttu-id="a680e-124">Odczytywanie i zapisywanie schematów XML</span><span class="sxs-lookup"><span data-stu-id="a680e-124">Reading and Writing XML Schemas</span></span>](../../../../docs/standard/data/xml/reading-and-writing-xml-schemas.md)  
 [<span data-ttu-id="a680e-125">Tworzenie schematów XML</span><span class="sxs-lookup"><span data-stu-id="a680e-125">Building XML Schemas</span></span>](../../../../docs/standard/data/xml/building-xml-schemas.md)  
 [<span data-ttu-id="a680e-126">Przechodzenie schematów XML</span><span class="sxs-lookup"><span data-stu-id="a680e-126">Traversing XML Schemas</span></span>](../../../../docs/standard/data/xml/traversing-xml-schemas.md)  
 [<span data-ttu-id="a680e-127">Edytowanie schematów XML</span><span class="sxs-lookup"><span data-stu-id="a680e-127">Editing XML Schemas</span></span>](../../../../docs/standard/data/xml/editing-xml-schemas.md)  
 [<span data-ttu-id="a680e-128">Uwzględnianie lub importowanie schematów XML</span><span class="sxs-lookup"><span data-stu-id="a680e-128">Including or Importing XML Schemas</span></span>](../../../../docs/standard/data/xml/including-or-importing-xml-schemas.md)  
 [<span data-ttu-id="a680e-129">Klasa XmlSchemaSet na potrzeby kompilacji schematu</span><span class="sxs-lookup"><span data-stu-id="a680e-129">XmlSchemaSet for Schema Compilation</span></span>](../../../../docs/standard/data/xml/xmlschemaset-for-schema-compilation.md)  
 [<span data-ttu-id="a680e-130">Zestaw informacji po kompilacji schematu</span><span class="sxs-lookup"><span data-stu-id="a680e-130">Post-Schema Compilation Infoset</span></span>](../../../../docs/standard/data/xml/post-schema-compilation-infoset.md)
