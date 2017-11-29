---
title: "Obsługa typu do zestawów System.Xml klas"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 63570538-06e3-4401-ad4d-ac50be90c7bf
caps.latest.revision: "4"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 14821ef78f20d1ff303afacb42415e4017a92742
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="type-support-in-the-systemxml-classes"></a>Obsługa typu do zestawów System.Xml klas
W programie .NET Framework w wersji 2.0 podstawowe klasy XML zostały rozszerzone i obejmują funkcje obsługi typu. <xref:System.Xml.XmlReader>, <xref:System.Xml.XmlWriter>, I <xref:System.Xml.XPath.XPathNavigator> klasy zawierają funkcje obsługi typu, łącznie z możliwością konwersji między typami schematu XML i typowych języka wspólnego (CLR).  
  
 W programie .NET Framework w wersji 2.0 <xref:System.Xml.XmlReader>, <xref:System.Xml.XmlWriter>, i <xref:System.Xml.XPath.XPathNavigator> klasy zostały rozszerzone i obejmują funkcje obsługi typu.  
  
-   <xref:System.Xml.XmlReader> i <xref:System.Xml.XPath.XPathNavigator> obejmują klasy każdego **SchemaInfo** właściwości zwracające informacje o schemacie na węźle.  
  
-   **ReadContentAs** i **ReadElementContentAs** i metody <xref:System.Xml.XmlReader> klasy odczytu wartość tekstową i przekonwertować go na wartość CLR w wywołaniu pojedynczej metody.  
  
-   <xref:System.Xml.XmlWriter.WriteValue%2A> Metoda <xref:System.Xml.XmlWriter> klasy konwertuje typu CLR na typ schematu XML podczas zapisywania XML.  
  
-   **ValueAs** i <xref:System.Xml.XPath.XPathNavigator.TypedValue%2A> właściwości <xref:System.Xml.XPath.XPathNavigator> klasy może zwracać wartości węzła i przekonwertować go na wartość CLR w wywołaniu pojedynczej metody.  
  
> [!NOTE]
>  W programie .NET Framework w wersji 1.0 <xref:System.Xml.XmlConvert> klasy było wymagane do konwersji między typami CLR i schematu XML.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Mapowanie typu danych XML na typy CLR](../../../../docs/standard/data/xml/mapping-xml-data-types-to-clr-types.md)  
 W tym artykule opisano domyślne mapowania typów danych XML do typów CLR.  
  
 [XML uwagi dotyczące implementacji pomocy technicznej dla typu](../../../../docs/standard/data/xml/xml-type-support-implementation-notes.md)  
 Omówiono niektóre szczegóły implementacji typu pomocy technicznej.  
  
 [Konwersja typów danych XML](../../../../docs/standard/data/xml/conversion-of-xml-data-types.md)  
 Informacje dotyczące używania <xref:System.Xml.XmlConvert> klasy do konwersji między typami CLR i schematu XML.  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Uzyskiwanie dostępu do silnie typu danych XML przy użyciu parametrem XPathNavigator](../../../../docs/standard/data/xml/accessing-strongly-typed-xml-data-using-xpathnavigator.md)
