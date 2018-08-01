---
title: Użycie zestawów System.Xml
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 82302f0d-a621-4c6f-b57d-999bd61f21a6
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ce9869d538b69af9beaa74be3300175f279b8f53
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33572817"
---
# <a name="systemxml-usage"></a><span data-ttu-id="fadc8-102">Użycie zestawów System.Xml</span><span class="sxs-lookup"><span data-stu-id="fadc8-102">System.Xml Usage</span></span>
<span data-ttu-id="fadc8-103">Ta sekcja zawiera informacje o użycie kilku typów znajdującej się w <xref:System.Xml?displayProperty=nameWithType> przestrzeni nazw, który może służyć do reprezentowania danych XML.</span><span class="sxs-lookup"><span data-stu-id="fadc8-103">This section talks about usage of several types residing in <xref:System.Xml?displayProperty=nameWithType> namespaces that can be used to represent XML data.</span></span>  
  
 <span data-ttu-id="fadc8-104">**X DO NOT** użyj <xref:System.Xml.XmlNode> lub <xref:System.Xml.XmlDocument> do reprezentowania danych XML.</span><span class="sxs-lookup"><span data-stu-id="fadc8-104">**X DO NOT** use <xref:System.Xml.XmlNode> or <xref:System.Xml.XmlDocument> to represent XML data.</span></span> <span data-ttu-id="fadc8-105">Preferuj za pomocą wystąpień <xref:System.Xml.XPath.IXPathNavigable>, <xref:System.Xml.XmlReader>, <xref:System.Xml.XmlWriter>, lub podtypów <xref:System.Xml.Linq.XNode> zamiast tego.</span><span class="sxs-lookup"><span data-stu-id="fadc8-105">Favor using instances of <xref:System.Xml.XPath.IXPathNavigable>, <xref:System.Xml.XmlReader>, <xref:System.Xml.XmlWriter>, or subtypes of <xref:System.Xml.Linq.XNode> instead.</span></span> <span data-ttu-id="fadc8-106">`XmlNode` i `XmlDocument` nie są przeznaczone do ujawnienia w publicznych interfejsach API.</span><span class="sxs-lookup"><span data-stu-id="fadc8-106">`XmlNode` and `XmlDocument` are not designed for exposing in public APIs.</span></span>  
  
 <span data-ttu-id="fadc8-107">**✓ DO** użyj `XmlReader`, `IXPathNavigable`, lub podtypów `XNode` jako wejście lub wyjście elementów członkowskich, które akceptują lub zwróć kod XML.</span><span class="sxs-lookup"><span data-stu-id="fadc8-107">**✓ DO** use `XmlReader`, `IXPathNavigable`, or subtypes of `XNode` as input or output of members that accept or return XML.</span></span>  
  
 <span data-ttu-id="fadc8-108">Użyj tych obiektów abstrakcyjnych zamiast `XmlDocument`, `XmlNode`, lub <xref:System.Xml.XPath.XPathDocument>, ponieważ to oddziela metody z określonej implementacji dokumentu XML w pamięci i umożliwia ich do pracy z wirtualnego źródła danych XML, które udostępniają `XNode` , `XmlReader`, lub <xref:System.Xml.XPath.XPathNavigator>.</span><span class="sxs-lookup"><span data-stu-id="fadc8-108">Use these abstractions instead of `XmlDocument`, `XmlNode`, or <xref:System.Xml.XPath.XPathDocument>, because this decouples the methods from specific implementations of an in-memory XML document and allows them to work with virtual XML data sources that expose `XNode`, `XmlReader`, or <xref:System.Xml.XPath.XPathNavigator>.</span></span>  
  
 <span data-ttu-id="fadc8-109">**X DO NOT** podklasy `XmlDocument` Jeśli chcesz utworzyć typ reprezentujący widoku źródłowego obiektu modelu lub źródła danych XML.</span><span class="sxs-lookup"><span data-stu-id="fadc8-109">**X DO NOT** subclass `XmlDocument` if you want to create a type representing an XML view of an underlying object model or data source.</span></span>  
  
 <span data-ttu-id="fadc8-110">*Portions © 2005, 2009 Microsoft Corporation. Wszelkie prawa zastrzeżone.*</span><span class="sxs-lookup"><span data-stu-id="fadc8-110">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="fadc8-111">*Drukowane uprawnieniami wariancji x edukacji, Inc. z [Framework zaleceń dotyczących projektowania: konwencje, Idioms i wzorce dla bibliotek .NET wielokrotnego użytku, wydanie 2](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina i Abrams Brada opublikowane 22 Oct 2008 przez Professional Addison-Wesley jako część serii rozwoju systemu Windows firmy Microsoft.*</span><span class="sxs-lookup"><span data-stu-id="fadc8-111">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fadc8-112">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="fadc8-112">See Also</span></span>  
 [<span data-ttu-id="fadc8-113">Struktura — zalecenia dotyczące projektowania</span><span class="sxs-lookup"><span data-stu-id="fadc8-113">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)  
 [<span data-ttu-id="fadc8-114">Zalecenia dotyczące użytkowania</span><span class="sxs-lookup"><span data-stu-id="fadc8-114">Usage Guidelines</span></span>](../../../docs/standard/design-guidelines/usage-guidelines.md)
