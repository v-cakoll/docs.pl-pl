---
title: Obsługa typu w ramach klas zestawu System.Xml
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 63570538-06e3-4401-ad4d-ac50be90c7bf
ms.openlocfilehash: cec47d40a0353639bc17b880265f7c15f2f53ac4
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75710105"
---
# <a name="type-support-in-the-systemxml-classes"></a>Obsługa typu w ramach klas zestawu System.Xml
W .NET Framework w wersji 2,0 podstawowe klasy XML zostały ulepszone w celu uwzględnienia funkcji obsługi typu. Klasy <xref:System.Xml.XmlReader>, <xref:System.Xml.XmlWriter>i <xref:System.Xml.XPath.XPathNavigator> zawierają funkcje obsługi typu, w tym możliwość konwersji między typami schematu XML i typami środowiska uruchomieniowego języka wspólnego (CLR).  
  
 W .NET Framework w wersji 2,0, klasy <xref:System.Xml.XmlReader>, <xref:System.Xml.XmlWriter>i <xref:System.Xml.XPath.XPathNavigator> zostały ulepszone w celu uwzględnienia funkcji obsługi typu.  
  
- Klasy <xref:System.Xml.XmlReader> i <xref:System.Xml.XPath.XPathNavigator> zawierają Właściwość **SchemaInfo** , która zwraca informacje o schemacie w węźle.  
  
- **ReadContentAs** i **ReadElementContentAs** i metody <xref:System.Xml.XmlReader> klasy odczytają wartość tekstową i konwertują ją na wartość CLR w wywołaniu pojedynczej metody.  
  
- <xref:System.Xml.XmlWriter.WriteValue%2A> Metoda w <xref:System.Xml.XmlWriter> klasie konwertuje typ CLR na typ schematu XML podczas pisania kodu XML.  
  
- **ValueAs** i <xref:System.Xml.XPath.XPathNavigator.TypedValue%2A> właściwości <xref:System.Xml.XPath.XPathNavigator> klasy zwracają wartość węzła i konwertują ją na wartość CLR w pojedynczym wywołaniu metody.  
  
> [!NOTE]
> W .NET Framework w wersji 1,0 <xref:System.Xml.XmlConvert> Klasa była wymagana do konwersji między schematem XML i typami CLR.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Mapowanie typów danych XML na typy CLR](../../../../docs/standard/data/xml/mapping-xml-data-types-to-clr-types.md)  
 Opisuje domyślne mapowania typów danych XML na typy CLR.  
  
 [Obsługiwane typy XML — uwagi dotyczące implementacji](../../../../docs/standard/data/xml/xml-type-support-implementation-notes.md)  
 W tym artykule omówiono niektóre typy szczegółów implementacji.  
  
 [Konwersja typów danych XML](../../../../docs/standard/data/xml/conversion-of-xml-data-types.md)  
 Opisuje sposób użycia <xref:System.Xml.XmlConvert> klasy do konwersji między schematem XML i typami CLR.  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Uzyskiwanie dostępu do silnie typizowanych danych XML przy użyciu klasy XPathNavigator](../../../../docs/standard/data/xml/accessing-strongly-typed-xml-data-using-xpathnavigator.md)
