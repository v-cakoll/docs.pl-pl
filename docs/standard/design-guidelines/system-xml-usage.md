---
title: Używanie zestawu System.Xml
ms.date: 10/22/2008
ms.technology: dotnet-standard
ms.assetid: 82302f0d-a621-4c6f-b57d-999bd61f21a6
ms.openlocfilehash: c57f5451526094d58066d7d391f41795f17732de
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75709039"
---
# <a name="systemxml-usage"></a>Używanie zestawu System.Xml
W tej sekcji omówiono użycie kilku typów znajdujących się w <xref:System.Xml?displayProperty=nameWithType> przestrzenie nazw, które mogą być używane do reprezentowania danych XML.  
  
 **X DO NOT** użyj <xref:System.Xml.XmlNode> lub <xref:System.Xml.XmlDocument> do reprezentowania danych XML. Zamiast tego Preferuj użycie wystąpień <xref:System.Xml.XPath.IXPathNavigable>, <xref:System.Xml.XmlReader>, <xref:System.Xml.XmlWriter>lub podtypów <xref:System.Xml.Linq.XNode>. `XmlNode` i `XmlDocument` nie są przeznaczone do uwidaczniania w publicznych interfejsach API.  
  
 **✓ DO** użyj `XmlReader`, `IXPathNavigable`, lub podtypów `XNode` jako wejście lub wyjście elementów członkowskich, które akceptują lub zwróć kod XML.  
  
 Użyj tych streszczeń zamiast `XmlDocument`, `XmlNode`lub <xref:System.Xml.XPath.XPathDocument>, ponieważ powoduje to oddzielenie metod od konkretnych implementacji dokumentu XML w pamięci i umożliwia ich współpracujenie z wirtualnymi źródłami danych XML, które uwidaczniają `XNode`, `XmlReader`lub <xref:System.Xml.XPath.XPathNavigator>.  
  
 **X DO NOT** podklasy `XmlDocument` Jeśli chcesz utworzyć typ reprezentujący widoku źródłowego obiektu modelu lub źródła danych XML.  
  
 *Fragmenty © 2005, 2009 Microsoft Corporation. Wszelkie prawa zastrzeżone.*  
  
 *Ponownie Wydrukowano przez uprawnienie Pearson Education, Inc. z [wytycznych dotyczących projektowania platformy: konwencje, idiomy i wzorce dla bibliotek .NET do wielokrotnego użytku, 2. wydanie](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) przez Krzysztof Cwalina i Brad Abrams, opublikowane 22, 2008 przez Addison-Wesley Professional w ramach serii Microsoft Windows Development.*  
  
## <a name="see-also"></a>Zobacz także

- [Struktura — zalecenia dotyczące projektowania](../../../docs/standard/design-guidelines/index.md)
- [Zalecenia dotyczące użytkowania](../../../docs/standard/design-guidelines/usage-guidelines.md)
