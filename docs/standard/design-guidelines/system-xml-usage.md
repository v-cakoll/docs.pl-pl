---
title: Używanie zestawu System.Xml
ms.date: 10/22/2008
ms.technology: dotnet-standard
ms.assetid: 82302f0d-a621-4c6f-b57d-999bd61f21a6
author: KrzysztofCwalina
ms.openlocfilehash: fc94ac62d1f2413c5f51446a8f6d0a52d9151557
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61650131"
---
# <a name="systemxml-usage"></a>Używanie zestawu System.Xml
Ta sekcja zawiera informacje o użycie kilku typów, znajdującymi się w <xref:System.Xml?displayProperty=nameWithType> przestrzenie nazw, który może służyć do reprezentowania danych XML.  
  
 **X DO NOT** użyj <xref:System.Xml.XmlNode> lub <xref:System.Xml.XmlDocument> do reprezentowania danych XML. Preferuj za pomocą wystąpień <xref:System.Xml.XPath.IXPathNavigable>, <xref:System.Xml.XmlReader>, <xref:System.Xml.XmlWriter>, lub podtypów <xref:System.Xml.Linq.XNode> zamiast tego. `XmlNode` i `XmlDocument` nie są przeznaczone do ujawnienia w publicznych interfejsów API.  
  
 **✓ DO** użyj `XmlReader`, `IXPathNavigable`, lub podtypów `XNode` jako wejście lub wyjście elementów członkowskich, które akceptują lub zwróć kod XML.  
  
 Użyj tych abstrakcje zamiast `XmlDocument`, `XmlNode`, lub <xref:System.Xml.XPath.XPathDocument>, ponieważ to oddziela metody z określonych implementacji dokumentu XML w pamięci i umożliwia im do pracy z wirtualnego źródła danych XML, które uwidaczniają `XNode` , `XmlReader`, lub <xref:System.Xml.XPath.XPathNavigator>.  
  
 **X DO NOT** podklasy `XmlDocument` Jeśli chcesz utworzyć typ reprezentujący widoku źródłowego obiektu modelu lub źródła danych XML.  
  
 *Portions © 2005, 2009 Microsoft Corporation. Wszelkie prawa zastrzeżone.*  
  
 *Przedrukowano za uprawnienie Pearson edukacji, Inc. z [wytyczne dotyczące projektowania Framework: Konwencje, Idiomy i wzorców dla wielokrotnego użytku, do bibliotek .NET, wydanie 2](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina i Brad Abrams publikowane 22 Oct 2008 przez Addison Wesley Professional w ramach serii rozwoju Windows firmy Microsoft.*  
  
## <a name="see-also"></a>Zobacz także

- [Struktura — zalecenia dotyczące projektowania](../../../docs/standard/design-guidelines/index.md)
- [Zalecenia dotyczące użytkowania](../../../docs/standard/design-guidelines/usage-guidelines.md)
