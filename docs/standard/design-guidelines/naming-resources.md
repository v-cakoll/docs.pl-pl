---
title: Nazewnictwo zasobów
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- names [.NET Framework], localized resources
- localization, naming guidelines
- resource names
- global applications, naming guidelines
- international applications, naming guidelines
ms.assetid: 8b0e97f3-7877-44fd-bc76-e05d36d5d79c
ms.openlocfilehash: b64a3ef6e12f8ea1abf7efd9c22f2f4333dda5c8
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75709169"
---
# <a name="naming-resources"></a><span data-ttu-id="b6472-102">Nazewnictwo zasobów</span><span class="sxs-lookup"><span data-stu-id="b6472-102">Naming Resources</span></span>
<span data-ttu-id="b6472-103">Ponieważ zasoby lokalizowalne mogą być przywoływane za pośrednictwem pewnych obiektów, tak jakby były właściwościami, wskazówki dotyczące nazewnictwa dla zasobów są podobne do wytycznych dotyczących właściwości.</span><span class="sxs-lookup"><span data-stu-id="b6472-103">Because localizable resources can be referenced via certain objects as if they were properties, the naming guidelines for resources are similar to property guidelines.</span></span>  
  
 <span data-ttu-id="b6472-104">**✓ DO** programu PascalCasing klucze zasobów.</span><span class="sxs-lookup"><span data-stu-id="b6472-104">**✓ DO** use PascalCasing in resource keys.</span></span>  
  
 <span data-ttu-id="b6472-105">**✓ DO** Podaj opisową zamiast krótkich identyfikatorów.</span><span class="sxs-lookup"><span data-stu-id="b6472-105">**✓ DO** provide descriptive rather than short identifiers.</span></span>  
  
 <span data-ttu-id="b6472-106">**X DO NOT** użyj słowa kluczowe specyficzne dla języka głównego języków CLR.</span><span class="sxs-lookup"><span data-stu-id="b6472-106">**X DO NOT** use language-specific keywords of the main CLR languages.</span></span>  
  
 <span data-ttu-id="b6472-107">**✓ DO** Użyj tylko znaki alfanumeryczne oraz znaki podkreślenia w nazw zasobów.</span><span class="sxs-lookup"><span data-stu-id="b6472-107">**✓ DO** use only alphanumeric characters and underscores in naming resources.</span></span>  
  
 <span data-ttu-id="b6472-108">**✓ DO** używać następującej konwencji nazewnictwa dla zasobów komunikat wyjątku.</span><span class="sxs-lookup"><span data-stu-id="b6472-108">**✓ DO** use the following naming convention for exception message resources.</span></span>  
  
 <span data-ttu-id="b6472-109">Identyfikator zasobu powinien być nazwą typu wyjątku i krótkim identyfikatorem wyjątku:</span><span class="sxs-lookup"><span data-stu-id="b6472-109">The resource identifier should be the exception type name plus a short identifier of the exception:</span></span>  
  
 `ArgumentExceptionIllegalCharacters`  
 `ArgumentExceptionInvalidName`  
 `ArgumentExceptionFileNameIsMalformed`  
  
 <span data-ttu-id="b6472-110">*Fragmenty © 2005, 2009 Microsoft Corporation. Wszelkie prawa zastrzeżone.*</span><span class="sxs-lookup"><span data-stu-id="b6472-110">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="b6472-111">*Ponownie Wydrukowano przez uprawnienie Pearson Education, Inc. z [wytycznych dotyczących projektowania platformy: konwencje, idiomy i wzorce dla bibliotek .NET do wielokrotnego użytku, 2. wydanie](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) przez Krzysztof Cwalina i Brad Abrams, opublikowane 22, 2008 przez Addison-Wesley Professional w ramach serii Microsoft Windows Development.*</span><span class="sxs-lookup"><span data-stu-id="b6472-111">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b6472-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b6472-112">See also</span></span>

- [<span data-ttu-id="b6472-113">Struktura — zalecenia dotyczące projektowania</span><span class="sxs-lookup"><span data-stu-id="b6472-113">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
- [<span data-ttu-id="b6472-114">Wskazówki dotyczące nazewnictwa</span><span class="sxs-lookup"><span data-stu-id="b6472-114">Naming Guidelines</span></span>](../../../docs/standard/design-guidelines/naming-guidelines.md)
