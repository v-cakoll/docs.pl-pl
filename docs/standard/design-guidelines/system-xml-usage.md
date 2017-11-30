---
title: "Użycie zestawów System.Xml"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 82302f0d-a621-4c6f-b57d-999bd61f21a6
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: a9bfa0f984f97e774d00a64fc3fd8489b3d5b40e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="systemxml-usage"></a>Użycie zestawów System.Xml
Ta sekcja zawiera informacje o użycie kilku typów znajdującej się w <xref:System.Xml?displayProperty=nameWithType> przestrzeni nazw, który może służyć do reprezentowania danych XML.  
  
 **X nie** użyj <xref:System.Xml.XmlNode> lub <xref:System.Xml.XmlDocument> do reprezentowania danych XML. Preferuj za pomocą wystąpień <xref:System.Xml.XPath.IXPathNavigable>, <xref:System.Xml.XmlReader>, <xref:System.Xml.XmlWriter>, lub podtypów <xref:System.Xml.Linq.XNode> zamiast tego. `XmlNode`i `XmlDocument` nie są przeznaczone do ujawnienia w publicznych interfejsach API.  
  
 **CZY ✓** użyj `XmlReader`, `IXPathNavigable`, lub podtypów `XNode` jako wejście lub wyjście elementów członkowskich, które akceptują lub zwróć kod XML.  
  
 Użyj tych obiektów abstrakcyjnych zamiast `XmlDocument`, `XmlNode`, lub <xref:System.Xml.XPath.XPathDocument>, ponieważ to oddziela metody z określonej implementacji dokumentu XML w pamięci i umożliwia ich do pracy z wirtualnego źródła danych XML, które udostępniają `XNode` , `XmlReader`, lub <xref:System.Xml.XPath.XPathNavigator>.  
  
 **X nie** podklasy `XmlDocument` Jeśli chcesz utworzyć typ reprezentujący widoku źródłowego obiektu modelu lub źródła danych XML.  
  
 *Fragmenty © 2005, 2009 Microsoft Corporation. Wszelkie prawa zastrzeżone.*  
  
 *Drukowane uprawnieniami wariancji x edukacji, Inc. z [Framework zaleceń dotyczących projektowania: konwencje, Idioms i wzorce dla bibliotek .NET wielokrotnego użytku, wydanie 2](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina i Abrams Brada opublikowane 22 Oct 2008 przez Professional Addison-Wesley jako część serii rozwoju systemu Windows firmy Microsoft.*  
  
## <a name="see-also"></a>Zobacz też  
 [Wytyczne dotyczące projektowania Framework](../../../docs/standard/design-guidelines/index.md)  
 [Wskazówki dotyczące użycia](../../../docs/standard/design-guidelines/usage-guidelines.md)
