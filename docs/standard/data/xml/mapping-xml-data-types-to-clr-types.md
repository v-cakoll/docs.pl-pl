---
title: Mapowanie typu danych XML na typy CLR
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: cabdfcad-f359-479b-b71c-8b2fad42ca49
caps.latest.revision: "2"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 3b6e67d27de33e61f5d5190249e90ac48e1aaaec
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="mapping-xml-data-types-to-clr-types"></a><span data-ttu-id="1ba92-102">Mapowanie typu danych XML na typy CLR</span><span class="sxs-lookup"><span data-stu-id="1ba92-102">Mapping XML Data Types to CLR Types</span></span>
<span data-ttu-id="1ba92-103">W poniższej tabeli opisano domyślne mapowanie między typami danych XML i języka typowych środowiska uruchomieniowego (języka wspólnego CLR).</span><span class="sxs-lookup"><span data-stu-id="1ba92-103">The following table describes the default mapping between the XML data types and the common language runtime (CLR) types.</span></span>  
  
## <a name="the-following-table-describes-the-default-mappings-of-an-xml-data-type-to-a-clr-type"></a><span data-ttu-id="1ba92-104">W poniższej tabeli opisano domyślne mapowania typu danych XML do typu CLR.</span><span class="sxs-lookup"><span data-stu-id="1ba92-104">The following table describes the default mappings of an XML data type to a CLR type.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1ba92-105">`xs` i `xdt` prefiksy są mapowane na http://www.w3.org/2001/XMLSchema i URI przestrzeni nazw http://www.w3.org/2003/05/xpath-datatypes odpowiednio.</span><span class="sxs-lookup"><span data-stu-id="1ba92-105">The `xs` and the `xdt` prefixes are mapped to the http://www.w3.org/2001/XMLSchema and the http://www.w3.org/2003/05/xpath-datatypes namespace URIs respectively.</span></span>  
  
|<span data-ttu-id="1ba92-106">Typ XML</span><span class="sxs-lookup"><span data-stu-id="1ba92-106">XML Type</span></span>|<span data-ttu-id="1ba92-107">Typ CLR</span><span class="sxs-lookup"><span data-stu-id="1ba92-107">CLR Type</span></span>|  
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
|<span data-ttu-id="1ba92-108">Węzeł dokumentu</span><span class="sxs-lookup"><span data-stu-id="1ba92-108">Document node</span></span>|<xref:System.Xml.XPath.XPathNavigator>|  
|<span data-ttu-id="1ba92-109">Węzeł elementu</span><span class="sxs-lookup"><span data-stu-id="1ba92-109">Element node</span></span>|<xref:System.Xml.XPath.XPathNavigator>|  
|<span data-ttu-id="1ba92-110">Węzeł atrybutu</span><span class="sxs-lookup"><span data-stu-id="1ba92-110">Attribute node</span></span>|<xref:System.Xml.XPath.XPathNavigator>|  
|<span data-ttu-id="1ba92-111">Namespace węzła</span><span class="sxs-lookup"><span data-stu-id="1ba92-111">Namespace node</span></span>|<xref:System.Xml.XPath.XPathNavigator>|  
|<span data-ttu-id="1ba92-112">Węzeł tekstowy</span><span class="sxs-lookup"><span data-stu-id="1ba92-112">Text node</span></span>|<xref:System.Xml.XPath.XPathNavigator>|  
|<span data-ttu-id="1ba92-113">Węzeł komentarzy</span><span class="sxs-lookup"><span data-stu-id="1ba92-113">Comment node</span></span>|<xref:System.Xml.XPath.XPathNavigator>|  
|<span data-ttu-id="1ba92-114">Węzeł instrukcja przetwarzania</span><span class="sxs-lookup"><span data-stu-id="1ba92-114">Processing instruction node</span></span>|<xref:System.Xml.XPath.XPathNavigator>|  
  
## <a name="see-also"></a><span data-ttu-id="1ba92-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="1ba92-115">See Also</span></span>  
 [<span data-ttu-id="1ba92-116">Obsługa typu do zestawów System.Xml klas</span><span class="sxs-lookup"><span data-stu-id="1ba92-116">Type Support in the System.Xml Classes</span></span>](../../../../docs/standard/data/xml/type-support-in-the-system-xml-classes.md)
