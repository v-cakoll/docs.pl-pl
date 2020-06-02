---
title: Używanie zestawu System.Xml
ms.date: 10/22/2008
ms.technology: dotnet-standard
ms.assetid: 82302f0d-a621-4c6f-b57d-999bd61f21a6
ms.openlocfilehash: 07828219f2e17be925d060fa3bb33a9209ecb62b
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/02/2020
ms.locfileid: "84291672"
---
# <a name="systemxml-usage"></a>Używanie zestawu System.Xml
W tej sekcji omówiono użycie kilku typów znajdujących się w <xref:System.Xml?displayProperty=nameWithType> przestrzeniach nazw, które mogą być używane do reprezentowania danych XML.

 ❌NIE używaj <xref:System.Xml.XmlNode> ani <xref:System.Xml.XmlDocument> do reprezentowania danych XML. Preferuj użycie wystąpień <xref:System.Xml.XPath.IXPathNavigable> , <xref:System.Xml.XmlReader> , <xref:System.Xml.XmlWriter> , lub podtypów <xref:System.Xml.Linq.XNode> zamiast. `XmlNode`i `XmlDocument` nie są przeznaczone do uwidaczniania w publicznych interfejsach API.

 ✔️ używać `XmlReader` , `IXPathNavigable` lub podtypów `XNode` jako danych wejściowych lub wyjściowych elementów członkowskich, które akceptują lub zwracają kod XML.

 Użyj tych streszczeń zamiast `XmlDocument` , `XmlNode` , lub <xref:System.Xml.XPath.XPathDocument> , ponieważ powoduje to oddzielenie metod od określonych implementacji dokumentu XML w pamięci i umożliwia im współpracujenie z wirtualnymi ŹRÓDŁAmi danych XML, które uwidaczniają `XNode` , `XmlReader` lub <xref:System.Xml.XPath.XPathNavigator> .

 ❌NIE podklasy `XmlDocument` , jeśli chcesz utworzyć typ reprezentujący Widok XML źródłowego modelu obiektów lub źródła danych.

 *Fragmenty © 2005, 2009 Microsoft Corporation. Wszelkie prawa zastrzeżone.*

 *Ponownie Wydrukowano przez uprawnienie Pearson Education, Inc. z [wytycznych dotyczących projektowania platformy: konwencje, idiomy i wzorce dla bibliotek .NET do wielokrotnego użytku, 2. wydanie](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) przez Krzysztof Cwalina i Brad Abrams, opublikowane 22, 2008 przez Addison-Wesley Professional w ramach serii Microsoft Windows Development.*

## <a name="see-also"></a>Zobacz także

- [Wskazówki dotyczące projektowania struktury](index.md)
- [Wskazówki dotyczące użycia](usage-guidelines.md)
