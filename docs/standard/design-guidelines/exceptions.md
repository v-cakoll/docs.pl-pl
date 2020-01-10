---
title: Wyjątki — zalecenia dotyczące projektowania
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- exceptions [.NET Framework], design guidelines
- class library design guidelines [.NET Framework], exceptions
- errors [.NET Framework], exceptions
- reporting errors
ms.assetid: bc177b2f-7528-4ae4-83db-aacfb04b86d0
ms.openlocfilehash: b64b6052aeb99c6e878c1a9aac50e67bca7f8d2a
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75709377"
---
# <a name="design-guidelines-for-exceptions"></a><span data-ttu-id="5c04e-102">Wyjątki — zalecenia dotyczące projektowania</span><span class="sxs-lookup"><span data-stu-id="5c04e-102">Design Guidelines for Exceptions</span></span>
<span data-ttu-id="5c04e-103">Obsługa wyjątków ma wiele zalet w porównaniu z raportowaniem błędów zwracających wartość.</span><span class="sxs-lookup"><span data-stu-id="5c04e-103">Exception handling has many advantages over return-value-based error reporting.</span></span> <span data-ttu-id="5c04e-104">Dobry projekt platformy ułatwia deweloperom aplikacji wykorzystanie korzyści z wyjątków.</span><span class="sxs-lookup"><span data-stu-id="5c04e-104">Good framework design helps the application developer realize the benefits of exceptions.</span></span> <span data-ttu-id="5c04e-105">W tej sekcji omówiono zalety wyjątków i przedstawiono wskazówki dotyczące efektywnego korzystania z nich.</span><span class="sxs-lookup"><span data-stu-id="5c04e-105">This section discusses the benefits of exceptions and presents guidelines for using them effectively.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="5c04e-106">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="5c04e-106">In This Section</span></span>  
 [<span data-ttu-id="5c04e-107">Zgłaszanie wyjątku</span><span class="sxs-lookup"><span data-stu-id="5c04e-107">Exception Throwing</span></span>](../../../docs/standard/design-guidelines/exception-throwing.md)  
 [<span data-ttu-id="5c04e-108">Używanie standardowych typów wyjątków</span><span class="sxs-lookup"><span data-stu-id="5c04e-108">Using Standard Exception Types</span></span>](../../../docs/standard/design-guidelines/using-standard-exception-types.md)  
 [<span data-ttu-id="5c04e-109">Wyjątki i wydajność</span><span class="sxs-lookup"><span data-stu-id="5c04e-109">Exceptions and Performance</span></span>](../../../docs/standard/design-guidelines/exceptions-and-performance.md)  
 <span data-ttu-id="5c04e-110">*Fragmenty © 2005, 2009 Microsoft Corporation. Wszelkie prawa zastrzeżone.*</span><span class="sxs-lookup"><span data-stu-id="5c04e-110">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="5c04e-111">*Ponownie Wydrukowano przez uprawnienie Pearson Education, Inc. z [wytycznych dotyczących projektowania platformy: konwencje, idiomy i wzorce dla bibliotek .NET do wielokrotnego użytku, 2. wydanie](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) przez Krzysztof Cwalina i Brad Abrams, opublikowane 22, 2008 przez Addison-Wesley Professional w ramach serii Microsoft Windows Development.*</span><span class="sxs-lookup"><span data-stu-id="5c04e-111">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5c04e-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="5c04e-112">See also</span></span>

- [<span data-ttu-id="5c04e-113">Struktura — zalecenia dotyczące projektowania</span><span class="sxs-lookup"><span data-stu-id="5c04e-113">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
