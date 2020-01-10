---
title: Mapowanie typów danych XML na typy CLR
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: cabdfcad-f359-479b-b71c-8b2fad42ca49
ms.openlocfilehash: 536c8dcd03d98879e24ae62d2b8a47e36564aaf6
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75710664"
---
# <a name="mapping-xml-data-types-to-clr-types"></a><span data-ttu-id="67b0c-102">Mapowanie typów danych XML na typy CLR</span><span class="sxs-lookup"><span data-stu-id="67b0c-102">Mapping XML Data Types to CLR Types</span></span>

<span data-ttu-id="67b0c-103">W poniższej tabeli opisano domyślne mapowanie między typami danych XML a typami środowiska uruchomieniowego języka wspólnego (CLR).</span><span class="sxs-lookup"><span data-stu-id="67b0c-103">The following table describes the default mapping between the XML data types and the common language runtime (CLR) types.</span></span>

> [!NOTE]
> <span data-ttu-id="67b0c-104">`xs` i prefiksy `xdt` są mapowane odpowiednio do <https://www.w3.org/2001/XMLSchema> oraz identyfikatorów URI <https://www.w3.org/2003/05/xpath-datatypes> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="67b0c-104">The `xs` and the `xdt` prefixes are mapped to the <https://www.w3.org/2001/XMLSchema> and the <https://www.w3.org/2003/05/xpath-datatypes> namespace URIs respectively.</span></span>

|<span data-ttu-id="67b0c-105">Typ XML</span><span class="sxs-lookup"><span data-stu-id="67b0c-105">XML Type</span></span>|<span data-ttu-id="67b0c-106">Typ CLR</span><span class="sxs-lookup"><span data-stu-id="67b0c-106">CLR Type</span></span>|
|--------------|--------------|
|`xs:anyURI`|<xref:System.Uri>|
|`xs:base64Binary`|`Byte[]`|
|`xs:boolean`|<xref:System.Boolean>|
|`xs:byte`|<xref:System.SByte>|
|`xs:date`|<xref:System.DateTime>|
|`xs:dateTime`|<xref:System.DateTime>|
|`xs:decimal`|<xref:System.Decimal>|
|`xs:double`|<xref:System.Double>|
|`xs:duration`|<xref:System.TimeSpan>|
|`xs:ENTITIES`|`String[]`|
|`xs:ENTITY`|<xref:System.String>|
|`xs:float`|<xref:System.Single>|
|`xs:gDay`|<xref:System.DateTime>|
|`xs:gMonthDay`|<xref:System.DateTime>|
|`xs:gYear`|<xref:System.DateTime>|
|`xs:gYearMonth`|<xref:System.DateTime>|
|`xs:hexBinary`|`Byte[]`|
|`xs:ID`|<xref:System.String>|
|`xs:IDREF`|<xref:System.String>|
|`xs:IDREFS`|`String[]`|
|`xs:int`|<xref:System.Int32>|
|`xs:integer`|<xref:System.Decimal>|
|`xs:language`|<xref:System.String>|
|`xs:long`|<xref:System.Int64>|
|`xs:gMonth`|<xref:System.DateTime>|
|`xs:Name`|<xref:System.String>|
|`xs:NCName`|<xref:System.String>|
|`xs:negativeInteger`|<xref:System.Decimal>|
|`xs:NMTOKEN`|<xref:System.String>|
|`xs:NMTOKENS`|`String[]`|
|`xs:nonNegativeInteger`|<xref:System.Decimal>|
|`xs:nonPositiveInteger`|<xref:System.Decimal>|
|`xs:normalizedString`|<xref:System.String>|
|`xs:NOTATION`|<xref:System.Xml.XmlQualifiedName>|
|`xs:positiveInteger`|<xref:System.Decimal>|
|`xs:QName`|<xref:System.Xml.XmlQualifiedName>|
|`xs:short`|<xref:System.Int16>|
|`xs:string`|<xref:System.String>|
|`xs:time`|<xref:System.DateTime>|
|`xs:token`|<xref:System.String>|
|`xs:unsignedByte`|<xref:System.Byte>|
|`xs:unsignedInt`|<xref:System.UInt32>|
|`xs:unsignedLong`|<xref:System.UInt64>|
|`xs:unsignedShort`|<xref:System.UInt16>|
|`xdt:dayTimeDuration`|<xref:System.TimeSpan>|
|`xdt:yearMonthDuration`|<xref:System.TimeSpan>|
|`xdt:untypedAtomic`|<xref:System.String>|
|`xdt:anyAtomicType`|<xref:System.Object>|
|`xs:anySimpleType`|<xref:System.String>|
|<span data-ttu-id="67b0c-107">Węzeł dokumentu</span><span class="sxs-lookup"><span data-stu-id="67b0c-107">Document node</span></span>|<xref:System.Xml.XPath.XPathNavigator>|
|<span data-ttu-id="67b0c-108">Węzeł elementu</span><span class="sxs-lookup"><span data-stu-id="67b0c-108">Element node</span></span>|<xref:System.Xml.XPath.XPathNavigator>|
|<span data-ttu-id="67b0c-109">Węzeł atrybutu</span><span class="sxs-lookup"><span data-stu-id="67b0c-109">Attribute node</span></span>|<xref:System.Xml.XPath.XPathNavigator>|
|<span data-ttu-id="67b0c-110">Węzeł przestrzeni nazw</span><span class="sxs-lookup"><span data-stu-id="67b0c-110">Namespace node</span></span>|<xref:System.Xml.XPath.XPathNavigator>|
|<span data-ttu-id="67b0c-111">Węzeł tekstu</span><span class="sxs-lookup"><span data-stu-id="67b0c-111">Text node</span></span>|<xref:System.Xml.XPath.XPathNavigator>|
|<span data-ttu-id="67b0c-112">Węzeł komentarza</span><span class="sxs-lookup"><span data-stu-id="67b0c-112">Comment node</span></span>|<xref:System.Xml.XPath.XPathNavigator>|
|<span data-ttu-id="67b0c-113">Przetwarzanie węzła instrukcji</span><span class="sxs-lookup"><span data-stu-id="67b0c-113">Processing instruction node</span></span>|<xref:System.Xml.XPath.XPathNavigator>|

## <a name="see-also"></a><span data-ttu-id="67b0c-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="67b0c-114">See also</span></span>

- [<span data-ttu-id="67b0c-115">Obsługa typu w ramach klas zestawu System.Xml</span><span class="sxs-lookup"><span data-stu-id="67b0c-115">Type Support in the System.Xml Classes</span></span>](../../../../docs/standard/data/xml/type-support-in-the-system-xml-classes.md)
