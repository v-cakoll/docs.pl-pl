---
title: Obsługa typu w ramach klas zestawu System.Xml
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 63570538-06e3-4401-ad4d-ac50be90c7bf
author: mairaw
ms.author: mairaw
ms.openlocfilehash: bb47eec7153624b1822b6393bb4a1621b1cd63db
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62026890"
---
# <a name="type-support-in-the-systemxml-classes"></a>Obsługa typu w ramach klas zestawu System.Xml
W programie .NET Framework 2.0 główne klasy XML zostały rozszerzone i obejmują funkcje pomocy technicznej typu. <xref:System.Xml.XmlReader>, <xref:System.Xml.XmlWriter>, I <xref:System.Xml.XPath.XPathNavigator> klas obejmują funkcje pomocy technicznej typu, łącznie z możliwością do konwersji między typami schematu XML i typowych języka wspólnego (CLR).  
  
 W .NET Framework w wersji 2.0 <xref:System.Xml.XmlReader>, <xref:System.Xml.XmlWriter>, i <xref:System.Xml.XPath.XPathNavigator> klasy zostały rozszerzone i obejmują funkcje pomocy technicznej typu.  
  
- <xref:System.Xml.XmlReader> i <xref:System.Xml.XPath.XPathNavigator> zawierają klasy każdego **może** właściwość, która zwraca informacje o schemacie dla węzła.  
  
- **ReadContentAs** i **ReadElementContentAs** i metod <xref:System.Xml.XmlReader> klasy odczytaj wartość tekstową i przekonwertować go na wartość CLR w pojedynczym wywołaniu metody.  
  
- <xref:System.Xml.XmlWriter.WriteValue%2A> Metody <xref:System.Xml.XmlWriter> klasy konwertuje typ CLR na typ schematu XML podczas zapisywania na poziomie XML.  
  
- **ValueAs** i <xref:System.Xml.XPath.XPathNavigator.TypedValue%2A> właściwości <xref:System.Xml.XPath.XPathNavigator> klasy może zwracać wartości węzła i przekonwertować go na wartość CLR w pojedynczym wywołaniu metody.  
  
> [!NOTE]
>  W .NET Framework w wersji 1.0 <xref:System.Xml.XmlConvert> klasy był niezbędny do konwersji między typami CLR i schematu XML.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Mapowanie typów danych XML na typy CLR](../../../../docs/standard/data/xml/mapping-xml-data-types-to-clr-types.md)  
 W tym artykule opisano domyślne mapowania typów danych XML na typy CLR.  
  
 [Obsługiwane typy XML — uwagi dotyczące implementacji](../../../../docs/standard/data/xml/xml-type-support-implementation-notes.md)  
 W tym artykule omówiono, niektóre szczegóły implementacji typ pomocy technicznej.  
  
 [Konwersja typów danych XML](../../../../docs/standard/data/xml/conversion-of-xml-data-types.md)  
 Opisuje sposób używania <xref:System.Xml.XmlConvert> klasy do konwersji między typami CLR i schematu XML.  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Uzyskiwanie dostępu do silnie typizowanych danych XML przy użyciu klasy XPathNavigator](../../../../docs/standard/data/xml/accessing-strongly-typed-xml-data-using-xpathnavigator.md)
