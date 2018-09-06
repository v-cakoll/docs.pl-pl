---
title: Mapowanie typów danych XML na typy CLR
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: cabdfcad-f359-479b-b71c-8b2fad42ca49
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 9cff30147da82896fb3a757ba2fed16d794ec3c9
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2018
ms.locfileid: "44037925"
---
# <a name="mapping-xml-data-types-to-clr-types"></a>Mapowanie typów danych XML na typy CLR
W poniższej tabeli opisano domyślne mapowanie między typami danych XML i popularnych typów środowiska uruchomieniowego (języka wspólnego CLR) języka.  
  
## <a name="the-following-table-describes-the-default-mappings-of-an-xml-data-type-to-a-clr-type"></a>W poniższej tabeli opisano domyślne mapowania typu danych XML do typu CLR.  
  
> [!NOTE]
>  `xs` i `xdt` prefiksy są mapowane na http://www.w3.org/2001/XMLSchema i http://www.w3.org/2003/05/xpath-datatypes URI przestrzeni nazw odpowiednio.  
  
|Typ XML o NAZWIE|Typ CLR|  
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
|Węzłem dokumentu|<xref:System.Xml.XPath.XPathNavigator>|  
|Węzeł elementu|<xref:System.Xml.XPath.XPathNavigator>|  
|Węzeł atrybutu|<xref:System.Xml.XPath.XPathNavigator>|  
|Węzeł Namespace|<xref:System.Xml.XPath.XPathNavigator>|  
|Węzeł tekstowy|<xref:System.Xml.XPath.XPathNavigator>|  
|Węzeł komentarzy|<xref:System.Xml.XPath.XPathNavigator>|  
|Węzeł przetwarzania instrukcji|<xref:System.Xml.XPath.XPathNavigator>|  
  
## <a name="see-also"></a>Zobacz także

- [Obsługa typu w ramach klas zestawu System.Xml](../../../../docs/standard/data/xml/type-support-in-the-system-xml-classes.md)
