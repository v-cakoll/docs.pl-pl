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
# <a name="systemxml-usage"></a><span data-ttu-id="1b6e3-102">Używanie zestawu System.Xml</span><span class="sxs-lookup"><span data-stu-id="1b6e3-102">System.Xml Usage</span></span>
<span data-ttu-id="1b6e3-103">W tej sekcji omówiono użycie kilku typów znajdujących się w <xref:System.Xml?displayProperty=nameWithType> przestrzeniach nazw, które mogą być używane do reprezentowania danych XML.</span><span class="sxs-lookup"><span data-stu-id="1b6e3-103">This section talks about usage of several types residing in <xref:System.Xml?displayProperty=nameWithType> namespaces that can be used to represent XML data.</span></span>

 <span data-ttu-id="1b6e3-104">❌NIE używaj <xref:System.Xml.XmlNode> ani <xref:System.Xml.XmlDocument> do reprezentowania danych XML.</span><span class="sxs-lookup"><span data-stu-id="1b6e3-104">❌ DO NOT use <xref:System.Xml.XmlNode> or <xref:System.Xml.XmlDocument> to represent XML data.</span></span> <span data-ttu-id="1b6e3-105">Preferuj użycie wystąpień <xref:System.Xml.XPath.IXPathNavigable> , <xref:System.Xml.XmlReader> , <xref:System.Xml.XmlWriter> , lub podtypów <xref:System.Xml.Linq.XNode> zamiast.</span><span class="sxs-lookup"><span data-stu-id="1b6e3-105">Favor using instances of <xref:System.Xml.XPath.IXPathNavigable>, <xref:System.Xml.XmlReader>, <xref:System.Xml.XmlWriter>, or subtypes of <xref:System.Xml.Linq.XNode> instead.</span></span> <span data-ttu-id="1b6e3-106">`XmlNode`i `XmlDocument` nie są przeznaczone do uwidaczniania w publicznych interfejsach API.</span><span class="sxs-lookup"><span data-stu-id="1b6e3-106">`XmlNode` and `XmlDocument` are not designed for exposing in public APIs.</span></span>

 <span data-ttu-id="1b6e3-107">✔️ używać `XmlReader` , `IXPathNavigable` lub podtypów `XNode` jako danych wejściowych lub wyjściowych elementów członkowskich, które akceptują lub zwracają kod XML.</span><span class="sxs-lookup"><span data-stu-id="1b6e3-107">✔️ DO use `XmlReader`, `IXPathNavigable`, or subtypes of `XNode` as input or output of members that accept or return XML.</span></span>

 <span data-ttu-id="1b6e3-108">Użyj tych streszczeń zamiast `XmlDocument` , `XmlNode` , lub <xref:System.Xml.XPath.XPathDocument> , ponieważ powoduje to oddzielenie metod od określonych implementacji dokumentu XML w pamięci i umożliwia im współpracujenie z wirtualnymi ŹRÓDŁAmi danych XML, które uwidaczniają `XNode` , `XmlReader` lub <xref:System.Xml.XPath.XPathNavigator> .</span><span class="sxs-lookup"><span data-stu-id="1b6e3-108">Use these abstractions instead of `XmlDocument`, `XmlNode`, or <xref:System.Xml.XPath.XPathDocument>, because this decouples the methods from specific implementations of an in-memory XML document and allows them to work with virtual XML data sources that expose `XNode`, `XmlReader`, or <xref:System.Xml.XPath.XPathNavigator>.</span></span>

 <span data-ttu-id="1b6e3-109">❌NIE podklasy `XmlDocument` , jeśli chcesz utworzyć typ reprezentujący Widok XML źródłowego modelu obiektów lub źródła danych.</span><span class="sxs-lookup"><span data-stu-id="1b6e3-109">❌ DO NOT subclass `XmlDocument` if you want to create a type representing an XML view of an underlying object model or data source.</span></span>

 <span data-ttu-id="1b6e3-110">*Fragmenty © 2005, 2009 Microsoft Corporation. Wszelkie prawa zastrzeżone.*</span><span class="sxs-lookup"><span data-stu-id="1b6e3-110">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>

 <span data-ttu-id="1b6e3-111">*Ponownie Wydrukowano przez uprawnienie Pearson Education, Inc. z [wytycznych dotyczących projektowania platformy: konwencje, idiomy i wzorce dla bibliotek .NET do wielokrotnego użytku, 2. wydanie](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) przez Krzysztof Cwalina i Brad Abrams, opublikowane 22, 2008 przez Addison-Wesley Professional w ramach serii Microsoft Windows Development.*</span><span class="sxs-lookup"><span data-stu-id="1b6e3-111">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>

## <a name="see-also"></a><span data-ttu-id="1b6e3-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="1b6e3-112">See also</span></span>

- [<span data-ttu-id="1b6e3-113">Wskazówki dotyczące projektowania struktury</span><span class="sxs-lookup"><span data-stu-id="1b6e3-113">Framework Design Guidelines</span></span>](index.md)
- [<span data-ttu-id="1b6e3-114">Wskazówki dotyczące użycia</span><span class="sxs-lookup"><span data-stu-id="1b6e3-114">Usage Guidelines</span></span>](usage-guidelines.md)
