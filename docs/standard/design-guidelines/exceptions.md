---
title: "Wskazówek dotyczących wyjątków"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- exceptions [.NET Framework], design guidelines
- class library design guidelines [.NET Framework], exceptions
- errors [.NET Framework], exceptions
- reporting errors
ms.assetid: bc177b2f-7528-4ae4-83db-aacfb04b86d0
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 30ee456632070f778d51d7fb40475a795a0f620b
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="design-guidelines-for-exceptions"></a><span data-ttu-id="be17f-102">Wskazówek dotyczących wyjątków</span><span class="sxs-lookup"><span data-stu-id="be17f-102">Design Guidelines for Exceptions</span></span>
<span data-ttu-id="be17f-103">Obsługa wyjątków ma wiele zalet w porównaniu z raportowania błędów na podstawie wartości zwracane.</span><span class="sxs-lookup"><span data-stu-id="be17f-103">Exception handling has many advantages over return-value-based error reporting.</span></span> <span data-ttu-id="be17f-104">Projektowanie dobrej framework pomaga Deweloper aplikacji wykorzystać zalety wyjątków.</span><span class="sxs-lookup"><span data-stu-id="be17f-104">Good framework design helps the application developer realize the benefits of exceptions.</span></span> <span data-ttu-id="be17f-105">W tej sekcji omówiono wyjątków zalet i przedstawia wskazówki dotyczące używania ich skutecznie.</span><span class="sxs-lookup"><span data-stu-id="be17f-105">This section discusses the benefits of exceptions and presents guidelines for using them effectively.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="be17f-106">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="be17f-106">In This Section</span></span>  
 [<span data-ttu-id="be17f-107">Wyrzucanie wyjątków</span><span class="sxs-lookup"><span data-stu-id="be17f-107">Exception Throwing</span></span>](../../../docs/standard/design-guidelines/exception-throwing.md)  
 [<span data-ttu-id="be17f-108">Używanie typów wyjątków standardowe</span><span class="sxs-lookup"><span data-stu-id="be17f-108">Using Standard Exception Types</span></span>](../../../docs/standard/design-guidelines/using-standard-exception-types.md)  
 [<span data-ttu-id="be17f-109">Wyjątki i wydajności</span><span class="sxs-lookup"><span data-stu-id="be17f-109">Exceptions and Performance</span></span>](../../../docs/standard/design-guidelines/exceptions-and-performance.md)  
 <span data-ttu-id="be17f-110">*Fragmenty © 2005, 2009 Microsoft Corporation. Wszelkie prawa zastrzeżone.*</span><span class="sxs-lookup"><span data-stu-id="be17f-110">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="be17f-111">*Drukowane uprawnieniami wariancji x edukacji, Inc. z [Framework zaleceń dotyczących projektowania: konwencje, Idioms i wzorce dla bibliotek .NET wielokrotnego użytku, wydanie 2](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina i Abrams Brada opublikowane 22 Oct 2008 przez Professional Addison-Wesley jako część serii rozwoju systemu Windows firmy Microsoft.*</span><span class="sxs-lookup"><span data-stu-id="be17f-111">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="be17f-112">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="be17f-112">See Also</span></span>  
 [<span data-ttu-id="be17f-113">Wytyczne dotyczące projektowania Framework</span><span class="sxs-lookup"><span data-stu-id="be17f-113">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
