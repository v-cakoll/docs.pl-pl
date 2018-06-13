---
title: Nadawanie nazw zasobów
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- names [.NET Framework], localized resources
- localization, naming guidelines
- resource names
- global applications, naming guidelines
- international applications, naming guidelines
ms.assetid: 8b0e97f3-7877-44fd-bc76-e05d36d5d79c
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b7cfda4e6a340d040de02903b9b64f0339751c5c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33571189"
---
# <a name="naming-resources"></a><span data-ttu-id="653e1-102">Nadawanie nazw zasobów</span><span class="sxs-lookup"><span data-stu-id="653e1-102">Naming Resources</span></span>
<span data-ttu-id="653e1-103">Ponieważ zlokalizowania zasobów można odwoływać się za pośrednictwem niektórych obiektów tak jakby były to właściwości, nazewnictwa wytyczne dotyczące zasobów są podobne do właściwości wytyczne.</span><span class="sxs-lookup"><span data-stu-id="653e1-103">Because localizable resources can be referenced via certain objects as if they were properties, the naming guidelines for resources are similar to property guidelines.</span></span>  
  
 <span data-ttu-id="653e1-104">**CZY ✓** programu PascalCasing klucze zasobów.</span><span class="sxs-lookup"><span data-stu-id="653e1-104">**✓ DO** use PascalCasing in resource keys.</span></span>  
  
 <span data-ttu-id="653e1-105">**CZY ✓** Podaj opisową zamiast krótkich identyfikatorów.</span><span class="sxs-lookup"><span data-stu-id="653e1-105">**✓ DO** provide descriptive rather than short identifiers.</span></span>  
  
 <span data-ttu-id="653e1-106">**X nie** użyj słowa kluczowe specyficzne dla języka głównego języków CLR.</span><span class="sxs-lookup"><span data-stu-id="653e1-106">**X DO NOT** use language-specific keywords of the main CLR languages.</span></span>  
  
 <span data-ttu-id="653e1-107">**CZY ✓** Użyj tylko znaki alfanumeryczne oraz znaki podkreślenia w nazw zasobów.</span><span class="sxs-lookup"><span data-stu-id="653e1-107">**✓ DO** use only alphanumeric characters and underscores in naming resources.</span></span>  
  
 <span data-ttu-id="653e1-108">**CZY ✓** używać następującej konwencji nazewnictwa dla zasobów komunikat wyjątku.</span><span class="sxs-lookup"><span data-stu-id="653e1-108">**✓ DO** use the following naming convention for exception message resources.</span></span>  
  
 <span data-ttu-id="653e1-109">Identyfikator zasobu powinny być nazwa typu wyjątku plus krótki identyfikator wyjątku:</span><span class="sxs-lookup"><span data-stu-id="653e1-109">The resource identifier should be the exception type name plus a short identifier of the exception:</span></span>  
  
 `ArgumentExceptionIllegalCharacters`  
 `ArgumentExceptionInvalidName`  
 `ArgumentExceptionFileNameIsMalformed`  
  
 <span data-ttu-id="653e1-110">*Portions © 2005, 2009 Microsoft Corporation. Wszelkie prawa zastrzeżone.*</span><span class="sxs-lookup"><span data-stu-id="653e1-110">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="653e1-111">*Drukowane uprawnieniami wariancji x edukacji, Inc. z [Framework zaleceń dotyczących projektowania: konwencje, Idioms i wzorce dla bibliotek .NET wielokrotnego użytku, wydanie 2](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina i Abrams Brada opublikowane 22 Oct 2008 przez Professional Addison-Wesley jako część serii rozwoju systemu Windows firmy Microsoft.*</span><span class="sxs-lookup"><span data-stu-id="653e1-111">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="653e1-112">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="653e1-112">See Also</span></span>  
 [<span data-ttu-id="653e1-113">Struktura — zalecenia dotyczące projektowania</span><span class="sxs-lookup"><span data-stu-id="653e1-113">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)  
 [<span data-ttu-id="653e1-114">Wskazówki dotyczące nazewnictwa</span><span class="sxs-lookup"><span data-stu-id="653e1-114">Naming Guidelines</span></span>](../../../docs/standard/design-guidelines/naming-guidelines.md)
