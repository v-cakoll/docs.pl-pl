---
title: Wytyczne dotyczące projektowania dla wyjątków
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- exceptions [.NET Framework], design guidelines
- class library design guidelines [.NET Framework], exceptions
- errors [.NET Framework], exceptions
- reporting errors
ms.assetid: bc177b2f-7528-4ae4-83db-aacfb04b86d0
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 51cc5296a7b3f6d75b5e56d6bbc74330fa147848
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2018
ms.locfileid: "43876638"
---
# <a name="design-guidelines-for-exceptions"></a><span data-ttu-id="d0748-102">Wytyczne dotyczące projektowania dla wyjątków</span><span class="sxs-lookup"><span data-stu-id="d0748-102">Design Guidelines for Exceptions</span></span>
<span data-ttu-id="d0748-103">Obsługa wyjątków ma wiele zalet za pośrednictwem raportowania błędów na podstawie wartości powrotu.</span><span class="sxs-lookup"><span data-stu-id="d0748-103">Exception handling has many advantages over return-value-based error reporting.</span></span> <span data-ttu-id="d0748-104">Dobre framework projektu pomaga Deweloper aplikacji korzystać z zalet wyjątków.</span><span class="sxs-lookup"><span data-stu-id="d0748-104">Good framework design helps the application developer realize the benefits of exceptions.</span></span> <span data-ttu-id="d0748-105">W tej sekcji omówiono korzyści wynikające z wyjątków i przedstawiono wskazówki dotyczące skutecznego korzystania z nich.</span><span class="sxs-lookup"><span data-stu-id="d0748-105">This section discusses the benefits of exceptions and presents guidelines for using them effectively.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="d0748-106">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="d0748-106">In This Section</span></span>  
 [<span data-ttu-id="d0748-107">Zgłaszanie wyjątku</span><span class="sxs-lookup"><span data-stu-id="d0748-107">Exception Throwing</span></span>](../../../docs/standard/design-guidelines/exception-throwing.md)  
 [<span data-ttu-id="d0748-108">Używanie standardowych typów wyjątków</span><span class="sxs-lookup"><span data-stu-id="d0748-108">Using Standard Exception Types</span></span>](../../../docs/standard/design-guidelines/using-standard-exception-types.md)  
 [<span data-ttu-id="d0748-109">Wyjątki i wydajność</span><span class="sxs-lookup"><span data-stu-id="d0748-109">Exceptions and Performance</span></span>](../../../docs/standard/design-guidelines/exceptions-and-performance.md)  
 <span data-ttu-id="d0748-110">*Portions © 2005, 2009 Microsoft Corporation. Wszelkie prawa zastrzeżone.*</span><span class="sxs-lookup"><span data-stu-id="d0748-110">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="d0748-111">*Przedrukowano przez uprawnienie Pearson edukacji, Inc. z [wytyczne dotyczące projektowania Framework: konwencje Idiomy i wzorce wielokrotnego użytku, do bibliotek .NET, wydanie 2](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina i Brad Abrams opublikowane 22 Oct 2008 przez Professional Addison Wesley jako część serii rozwoju Windows firmy Microsoft.*</span><span class="sxs-lookup"><span data-stu-id="d0748-111">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d0748-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d0748-112">See also</span></span>

- [<span data-ttu-id="d0748-113">Struktura — zalecenia dotyczące projektowania</span><span class="sxs-lookup"><span data-stu-id="d0748-113">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
