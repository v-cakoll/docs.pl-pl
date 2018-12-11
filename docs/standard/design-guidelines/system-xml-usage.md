---
title: Używanie zestawu system.XML
ms.date: 10/22/2008
ms.technology: dotnet-standard
ms.assetid: 82302f0d-a621-4c6f-b57d-999bd61f21a6
author: KrzysztofCwalina
ms.openlocfilehash: fb0e1d3dc851f9726905dc375d50cf211dba8400
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/10/2018
ms.locfileid: "53149546"
---
# <a name="systemxml-usage"></a><span data-ttu-id="3016f-102">Używanie zestawu system.XML</span><span class="sxs-lookup"><span data-stu-id="3016f-102">System.Xml Usage</span></span>
<span data-ttu-id="3016f-103">Ta sekcja zawiera informacje o użycie kilku typów, znajdującymi się w <xref:System.Xml?displayProperty=nameWithType> przestrzenie nazw, który może służyć do reprezentowania danych XML.</span><span class="sxs-lookup"><span data-stu-id="3016f-103">This section talks about usage of several types residing in <xref:System.Xml?displayProperty=nameWithType> namespaces that can be used to represent XML data.</span></span>  
  
 <span data-ttu-id="3016f-104">**X DO NOT** użyj <xref:System.Xml.XmlNode> lub <xref:System.Xml.XmlDocument> do reprezentowania danych XML.</span><span class="sxs-lookup"><span data-stu-id="3016f-104">**X DO NOT** use <xref:System.Xml.XmlNode> or <xref:System.Xml.XmlDocument> to represent XML data.</span></span> <span data-ttu-id="3016f-105">Preferuj za pomocą wystąpień <xref:System.Xml.XPath.IXPathNavigable>, <xref:System.Xml.XmlReader>, <xref:System.Xml.XmlWriter>, lub podtypów <xref:System.Xml.Linq.XNode> zamiast tego.</span><span class="sxs-lookup"><span data-stu-id="3016f-105">Favor using instances of <xref:System.Xml.XPath.IXPathNavigable>, <xref:System.Xml.XmlReader>, <xref:System.Xml.XmlWriter>, or subtypes of <xref:System.Xml.Linq.XNode> instead.</span></span> <span data-ttu-id="3016f-106">`XmlNode` i `XmlDocument` nie są przeznaczone do ujawnienia w publicznych interfejsów API.</span><span class="sxs-lookup"><span data-stu-id="3016f-106">`XmlNode` and `XmlDocument` are not designed for exposing in public APIs.</span></span>  
  
 <span data-ttu-id="3016f-107">**✓ DO** użyj `XmlReader`, `IXPathNavigable`, lub podtypów `XNode` jako wejście lub wyjście elementów członkowskich, które akceptują lub zwróć kod XML.</span><span class="sxs-lookup"><span data-stu-id="3016f-107">**✓ DO** use `XmlReader`, `IXPathNavigable`, or subtypes of `XNode` as input or output of members that accept or return XML.</span></span>  
  
 <span data-ttu-id="3016f-108">Użyj tych abstrakcje zamiast `XmlDocument`, `XmlNode`, lub <xref:System.Xml.XPath.XPathDocument>, ponieważ to oddziela metody z określonych implementacji dokumentu XML w pamięci i umożliwia im do pracy z wirtualnego źródła danych XML, które uwidaczniają `XNode` , `XmlReader`, lub <xref:System.Xml.XPath.XPathNavigator>.</span><span class="sxs-lookup"><span data-stu-id="3016f-108">Use these abstractions instead of `XmlDocument`, `XmlNode`, or <xref:System.Xml.XPath.XPathDocument>, because this decouples the methods from specific implementations of an in-memory XML document and allows them to work with virtual XML data sources that expose `XNode`, `XmlReader`, or <xref:System.Xml.XPath.XPathNavigator>.</span></span>  
  
 <span data-ttu-id="3016f-109">**X DO NOT** podklasy `XmlDocument` Jeśli chcesz utworzyć typ reprezentujący widoku źródłowego obiektu modelu lub źródła danych XML.</span><span class="sxs-lookup"><span data-stu-id="3016f-109">**X DO NOT** subclass `XmlDocument` if you want to create a type representing an XML view of an underlying object model or data source.</span></span>  
  
 <span data-ttu-id="3016f-110">*Portions © 2005, 2009 Microsoft Corporation. Wszelkie prawa zastrzeżone.*</span><span class="sxs-lookup"><span data-stu-id="3016f-110">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="3016f-111">*Przedrukowano za uprawnienie Pearson edukacji, Inc. z [wytyczne dotyczące projektowania Framework: Konwencje, Idiomy i wzorców dla wielokrotnego użytku, do bibliotek .NET, wydanie 2](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina i Brad Abrams publikowane 22 Oct 2008 przez Addison Wesley Professional w ramach serii rozwoju Windows firmy Microsoft.*</span><span class="sxs-lookup"><span data-stu-id="3016f-111">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3016f-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="3016f-112">See also</span></span>

- [<span data-ttu-id="3016f-113">Struktura — zalecenia dotyczące projektowania</span><span class="sxs-lookup"><span data-stu-id="3016f-113">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)  
- [<span data-ttu-id="3016f-114">Zalecenia dotyczące użytkowania</span><span class="sxs-lookup"><span data-stu-id="3016f-114">Usage Guidelines</span></span>](../../../docs/standard/design-guidelines/usage-guidelines.md)
