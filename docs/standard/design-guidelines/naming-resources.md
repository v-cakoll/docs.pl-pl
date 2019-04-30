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
author: KrzysztofCwalina
ms.openlocfilehash: 44627aafd9ec779625413a0862412a8f6c408109
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61756887"
---
# <a name="naming-resources"></a><span data-ttu-id="3c789-102">Nazewnictwo zasobów</span><span class="sxs-lookup"><span data-stu-id="3c789-102">Naming Resources</span></span>
<span data-ttu-id="3c789-103">Ponieważ lokalizowalne zasoby mogą być przywoływane za pośrednictwem niektórych obiektów, tak jakby były one właściwości, wskazówkami nazewnictwa dla zasobów są podobne do wytycznych właściwości.</span><span class="sxs-lookup"><span data-stu-id="3c789-103">Because localizable resources can be referenced via certain objects as if they were properties, the naming guidelines for resources are similar to property guidelines.</span></span>  
  
 <span data-ttu-id="3c789-104">**✓ DO** programu PascalCasing klucze zasobów.</span><span class="sxs-lookup"><span data-stu-id="3c789-104">**✓ DO** use PascalCasing in resource keys.</span></span>  
  
 <span data-ttu-id="3c789-105">**✓ DO** Podaj opisową zamiast krótkich identyfikatorów.</span><span class="sxs-lookup"><span data-stu-id="3c789-105">**✓ DO** provide descriptive rather than short identifiers.</span></span>  
  
 <span data-ttu-id="3c789-106">**X DO NOT** użyj słowa kluczowe specyficzne dla języka głównego języków CLR.</span><span class="sxs-lookup"><span data-stu-id="3c789-106">**X DO NOT** use language-specific keywords of the main CLR languages.</span></span>  
  
 <span data-ttu-id="3c789-107">**✓ DO** Użyj tylko znaki alfanumeryczne oraz znaki podkreślenia w nazw zasobów.</span><span class="sxs-lookup"><span data-stu-id="3c789-107">**✓ DO** use only alphanumeric characters and underscores in naming resources.</span></span>  
  
 <span data-ttu-id="3c789-108">**✓ DO** używać następującej konwencji nazewnictwa dla zasobów komunikat wyjątku.</span><span class="sxs-lookup"><span data-stu-id="3c789-108">**✓ DO** use the following naming convention for exception message resources.</span></span>  
  
 <span data-ttu-id="3c789-109">Identyfikator zasobu powinna być nazwa typu wyjątku oraz krótki identyfikator wyjątku:</span><span class="sxs-lookup"><span data-stu-id="3c789-109">The resource identifier should be the exception type name plus a short identifier of the exception:</span></span>  
  
 `ArgumentExceptionIllegalCharacters`  
 `ArgumentExceptionInvalidName`  
 `ArgumentExceptionFileNameIsMalformed`  
  
 <span data-ttu-id="3c789-110">*Portions © 2005, 2009 Microsoft Corporation. Wszelkie prawa zastrzeżone.*</span><span class="sxs-lookup"><span data-stu-id="3c789-110">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="3c789-111">*Przedrukowano za uprawnienie Pearson edukacji, Inc. z [wytyczne dotyczące projektowania Framework: Konwencje, Idiomy i wzorców dla wielokrotnego użytku, do bibliotek .NET, wydanie 2](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina i Brad Abrams publikowane 22 Oct 2008 przez Addison Wesley Professional w ramach serii rozwoju Windows firmy Microsoft.*</span><span class="sxs-lookup"><span data-stu-id="3c789-111">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3c789-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="3c789-112">See also</span></span>

- [<span data-ttu-id="3c789-113">Struktura — zalecenia dotyczące projektowania</span><span class="sxs-lookup"><span data-stu-id="3c789-113">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
- [<span data-ttu-id="3c789-114">Wskazówki dotyczące nazewnictwa</span><span class="sxs-lookup"><span data-stu-id="3c789-114">Naming Guidelines</span></span>](../../../docs/standard/design-guidelines/naming-guidelines.md)
