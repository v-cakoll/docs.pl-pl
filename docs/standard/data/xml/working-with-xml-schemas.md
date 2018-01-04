---
title: Praca z schematy XML
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: bbbcc70c-bf9a-4f6a-af72-1bab5384a187
caps.latest.revision: "3"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 1cfac14f934efb22f7cd39faceb232cc819b540e
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/23/2017
---
# <a name="working-with-xml-schemas"></a><span data-ttu-id="44bb1-102">Praca z schematy XML</span><span class="sxs-lookup"><span data-stu-id="44bb1-102">Working with XML Schemas</span></span>
<span data-ttu-id="44bb1-103">Aby zdefiniować strukturę dokumentu XML, a także jej relacje element, typy danych i ograniczeń zawartości, możesz użyć definicja typu dokumentu (DTD) ani schematu (XSD) języka definicji schematu XML.</span><span class="sxs-lookup"><span data-stu-id="44bb1-103">To define the structure of an XML document, as well as its element relationships, data types, and content constraints, you use a document type definition (DTD) or XML Schema definition language (XSD) schema.</span></span> <span data-ttu-id="44bb1-104">Mimo że dokument XML jest uznawany za poprawnie sformułowanym go spełnia wszystkie wymagania syntaktycznych zdefiniowane przez zalecenie sieci World Wide Web konsorcjum W3C Extensible Markup Language (XML) 1.0, nie jest traktowane prawidłowy chyba że oba jest poprawnie sformułowany i jest zgodna z ograniczeń zdefiniowanych przez jego definicja DTD lub schemat.</span><span class="sxs-lookup"><span data-stu-id="44bb1-104">Although an XML document is considered to be well-formed if it meets all the syntactical requirements defined by the World Wide Web Consortium (W3C) Extensible Markup Language (XML) 1.0 Recommendation, it is not considered valid unless it is both well-formed and conforms to the constraints defined by its DTD or schema.</span></span> <span data-ttu-id="44bb1-105">W związku z tym mimo że wszystkich ważnych dokumentów XML są poprawnie sformułowany, nie wszystkie poprawnie sformułowanym dokumentów XML są prawidłowe.</span><span class="sxs-lookup"><span data-stu-id="44bb1-105">Therefore, although all valid XML documents are well-formed, not all well-formed XML documents are valid.</span></span>  
  
 <span data-ttu-id="44bb1-106">Aby uzyskać więcej informacji na temat formatu XML, zobacz [W3C XML 1.0 zalecenie](http://go.microsoft.com/fwlink/?linkid=7269).</span><span class="sxs-lookup"><span data-stu-id="44bb1-106">For more information about XML, see the [W3C XML 1.0 Recommendation](http://go.microsoft.com/fwlink/?linkid=7269).</span></span> <span data-ttu-id="44bb1-107">Aby uzyskać więcej informacji na temat schematu XML, zobacz [W3C XML schematu część 1: zalecenie struktury](http://go.microsoft.com/fwlink/?linkid=48881) i [W3C XML schematu część 2: zalecenie typy danych](http://go.microsoft.com/fwlink/?linkid=17392) zalecenia.</span><span class="sxs-lookup"><span data-stu-id="44bb1-107">For more information about XML Schema, see the [W3C XML Schema Part 1: Structures Recommendation](http://go.microsoft.com/fwlink/?linkid=48881) and the [W3C XML Schema Part 2: Datatypes Recommendation](http://go.microsoft.com/fwlink/?linkid=17392) recommendations.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="44bb1-108">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="44bb1-108">In This Section</span></span>  
 [<span data-ttu-id="44bb1-109">Model SOM (XML Schema Object Model)</span><span class="sxs-lookup"><span data-stu-id="44bb1-109">XML Schema Object Model (SOM)</span></span>](../../../../docs/standard/data/xml/xml-schema-object-model-som.md)  
 <span data-ttu-id="44bb1-110">W tym artykule omówiono w modelu obiektu schematu (SOM) <xref:System.Xml.Schema?displayProperty=nameWithType> przestrzeni nazw, która udostępnia zestaw klas, który umożliwia odczytanie schematu definicji schematu języka (XSD) z pliku lub programowo tworzenie schematu w pamięci.</span><span class="sxs-lookup"><span data-stu-id="44bb1-110">Discusses the Schema Object Model (SOM) in the <xref:System.Xml.Schema?displayProperty=nameWithType> namespace that provides a set of classes that allows you to read a Schema definition language (XSD) schema from a file or programmatically create a schema in-memory.</span></span>  
  
 [<span data-ttu-id="44bb1-111">Klasa XmlSchemaSet na potrzeby kompilacji schematu</span><span class="sxs-lookup"><span data-stu-id="44bb1-111">XmlSchemaSet for Schema Compilation</span></span>](../../../../docs/standard/data/xml/xmlschemaset-for-schema-compilation.md)  
 <span data-ttu-id="44bb1-112">W tym artykule omówiono <xref:System.Xml.Schema.XmlSchemaSet> klasy czyli pamięci podręcznej, gdzie schematów XSD mogą być przechowywane i sprawdzania poprawności.</span><span class="sxs-lookup"><span data-stu-id="44bb1-112">Discusses the <xref:System.Xml.Schema.XmlSchemaSet> class that is a cache where XSD schemas can be stored and validated.</span></span>  
  
 [<span data-ttu-id="44bb1-113">Weryfikacja oparta na wypchnięciach przy użyciu klasy XmlSchemaValidator</span><span class="sxs-lookup"><span data-stu-id="44bb1-113">XmlSchemaValidator Push-Based Validation</span></span>](../../../../docs/standard/data/xml/xmlschemavalidator-push-based-validation.md)  
 <span data-ttu-id="44bb1-114">W tym artykule omówiono <xref:System.Xml.Schema.XmlSchemaValidator> klasy, która udostępnia mechanizm wydajne, wysokiej wydajności, aby sprawdzić poprawność danych XML względem schematów XSD w sposób wypychania.</span><span class="sxs-lookup"><span data-stu-id="44bb1-114">Discusses the <xref:System.Xml.Schema.XmlSchemaValidator> class that provides an efficient, high-performance mechanism to validate XML data against XSD schemas in a push-based manner.</span></span>  
  
 [<span data-ttu-id="44bb1-115">Wnioskowanie schematu XML</span><span class="sxs-lookup"><span data-stu-id="44bb1-115">Inferring an XML Schema</span></span>](../../../../docs/standard/data/xml/inferring-an-xml-schema.md)  
 <span data-ttu-id="44bb1-116">W tym artykule omówiono sposób użycia <xref:System.Xml.Schema.XmlSchemaInference> klasy na potrzeby wnioskowania dotyczącego schematu XSD ze struktury dokumentu XML.</span><span class="sxs-lookup"><span data-stu-id="44bb1-116">Discusses how to use the <xref:System.Xml.Schema.XmlSchemaInference> class to infer an XSD schema from the structure of an XML document.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="44bb1-117">Tematy pomocy</span><span class="sxs-lookup"><span data-stu-id="44bb1-117">Reference</span></span>  
 <span data-ttu-id="44bb1-118"><xref:System.Xml.Schema.XmlSchemaSet> &#124; <xref:System.Xml.Schema.XmlSchemaInference> &#124; <xref:System.Xml.XmlReader></span><span class="sxs-lookup"><span data-stu-id="44bb1-118"><xref:System.Xml.Schema.XmlSchemaSet> &#124; <xref:System.Xml.Schema.XmlSchemaInference> &#124; <xref:System.Xml.XmlReader></span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="44bb1-119">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="44bb1-119">Related Sections</span></span>  
 [<span data-ttu-id="44bb1-120">Weryfikowanie dokumentu XML w modelu DOM</span><span class="sxs-lookup"><span data-stu-id="44bb1-120">Validating an XML Document in the DOM</span></span>](../../../../docs/standard/data/xml/validating-an-xml-document-in-the-dom.md)  
 <span data-ttu-id="44bb1-121">W tym artykule omówiono sposób sprawdzania poprawności kodu XML w modelu DOM (Document Object).</span><span class="sxs-lookup"><span data-stu-id="44bb1-121">Discusses how to validate the XML in the Document Object Model (DOM).</span></span> <span data-ttu-id="44bb1-122">Sprawdzanie poprawności kodu XML, jak jest załadowane do modelu DOM lub sprawdzić wcześniej niezweryfikowanych dokumentu XML w modelu DOM.</span><span class="sxs-lookup"><span data-stu-id="44bb1-122">You can validate the XML as it is loaded into the DOM, or validate a previously unvalidated XML document in the DOM.</span></span>  
  
 [<span data-ttu-id="44bb1-123">Weryfikacja schematu przy użyciu klasy XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="44bb1-123">Schema Validation using XPathNavigator</span></span>](../../../../docs/standard/data/xml/schema-validation-using-xpathnavigator.md)  
 <span data-ttu-id="44bb1-124">W tym artykule omówiono sposób sprawdzania poprawności XML jest przejście i edytować za pomocą <xref:System.Xml.XPath.XPathNavigator> klasy.</span><span class="sxs-lookup"><span data-stu-id="44bb1-124">Discusses how to validate XML being navigated and edited using the <xref:System.Xml.XPath.XPathNavigator> class.</span></span>
