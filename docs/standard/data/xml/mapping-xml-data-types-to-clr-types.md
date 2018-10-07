---
title: Mapowanie typów danych XML na typy CLR
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: cabdfcad-f359-479b-b71c-8b2fad42ca49
author: mairaw
ms.author: mairaw
ms.openlocfilehash: a88d5bf99e2d9bb6465413cb5419058014d113a1
ms.sourcegitcommit: 586dbdcaef9767642436b1e4efbe88fb15473d6f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/06/2018
ms.locfileid: "48839047"
---
# <a name="mapping-xml-data-types-to-clr-types"></a><span data-ttu-id="b537e-102">Mapowanie typów danych XML na typy CLR</span><span class="sxs-lookup"><span data-stu-id="b537e-102">Mapping XML Data Types to CLR Types</span></span>

<span data-ttu-id="b537e-103">W poniższej tabeli opisano domyślne mapowanie między typami danych XML i popularnych typów środowiska uruchomieniowego (języka wspólnego CLR) języka.</span><span class="sxs-lookup"><span data-stu-id="b537e-103">The following table describes the default mapping between the XML data types and the common language runtime (CLR) types.</span></span>
  
> [!NOTE]
> <span data-ttu-id="b537e-104">`xs` i `xdt` prefiksy są mapowane na <https://www.w3.org/2001/XMLSchema> i <https://www.w3.org/2003/05/xpath-datatypes> URI przestrzeni nazw odpowiednio.</span><span class="sxs-lookup"><span data-stu-id="b537e-104">The `xs` and the `xdt` prefixes are mapped to the <https://www.w3.org/2001/XMLSchema> and the <https://www.w3.org/2003/05/xpath-datatypes> namespace URIs respectively.</span></span>
  
|<span data-ttu-id="b537e-105">Typ XML o NAZWIE</span><span class="sxs-lookup"><span data-stu-id="b537e-105">XML Type</span></span>|<span data-ttu-id="b537e-106">Typ CLR</span><span class="sxs-lookup"><span data-stu-id="b537e-106">CLR Type</span></span>|  
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
|`xs:gMmonth`|<xref:System.DateTime>|  
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
|<span data-ttu-id="b537e-107">Węzłem dokumentu</span><span class="sxs-lookup"><span data-stu-id="b537e-107">Document node</span></span>|<xref:System.Xml.XPath.XPathNavigator>|  
|<span data-ttu-id="b537e-108">Węzeł elementu</span><span class="sxs-lookup"><span data-stu-id="b537e-108">Element node</span></span>|<xref:System.Xml.XPath.XPathNavigator>|  
|<span data-ttu-id="b537e-109">Węzeł atrybutu</span><span class="sxs-lookup"><span data-stu-id="b537e-109">Attribute node</span></span>|<xref:System.Xml.XPath.XPathNavigator>|  
|<span data-ttu-id="b537e-110">Węzeł Namespace</span><span class="sxs-lookup"><span data-stu-id="b537e-110">Namespace node</span></span>|<xref:System.Xml.XPath.XPathNavigator>|  
|<span data-ttu-id="b537e-111">Węzeł tekstowy</span><span class="sxs-lookup"><span data-stu-id="b537e-111">Text node</span></span>|<xref:System.Xml.XPath.XPathNavigator>|  
|<span data-ttu-id="b537e-112">Węzeł komentarzy</span><span class="sxs-lookup"><span data-stu-id="b537e-112">Comment node</span></span>|<xref:System.Xml.XPath.XPathNavigator>|  
|<span data-ttu-id="b537e-113">Węzeł przetwarzania instrukcji</span><span class="sxs-lookup"><span data-stu-id="b537e-113">Processing instruction node</span></span>|<xref:System.Xml.XPath.XPathNavigator>|  
  
## <a name="see-also"></a><span data-ttu-id="b537e-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b537e-114">See also</span></span>

- [<span data-ttu-id="b537e-115">Obsługa typu w ramach klas zestawu System.Xml</span><span class="sxs-lookup"><span data-stu-id="b537e-115">Type Support in the System.Xml Classes</span></span>](../../../../docs/standard/data/xml/type-support-in-the-system-xml-classes.md)
