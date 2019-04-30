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
author: KrzysztofCwalina
ms.openlocfilehash: 60c3d25138c224f5eabf44d06b6c9a8373eb5f96
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61669059"
---
# <a name="design-guidelines-for-exceptions"></a><span data-ttu-id="30d4d-102">Wyjątki — zalecenia dotyczące projektowania</span><span class="sxs-lookup"><span data-stu-id="30d4d-102">Design Guidelines for Exceptions</span></span>
<span data-ttu-id="30d4d-103">Obsługa wyjątków ma wiele zalet za pośrednictwem raportowania błędów na podstawie wartości powrotu.</span><span class="sxs-lookup"><span data-stu-id="30d4d-103">Exception handling has many advantages over return-value-based error reporting.</span></span> <span data-ttu-id="30d4d-104">Dobre framework projektu pomaga Deweloper aplikacji korzystać z zalet wyjątków.</span><span class="sxs-lookup"><span data-stu-id="30d4d-104">Good framework design helps the application developer realize the benefits of exceptions.</span></span> <span data-ttu-id="30d4d-105">W tej sekcji omówiono korzyści wynikające z wyjątków i przedstawiono wskazówki dotyczące skutecznego korzystania z nich.</span><span class="sxs-lookup"><span data-stu-id="30d4d-105">This section discusses the benefits of exceptions and presents guidelines for using them effectively.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="30d4d-106">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="30d4d-106">In This Section</span></span>  
 [<span data-ttu-id="30d4d-107">Zgłaszanie wyjątku</span><span class="sxs-lookup"><span data-stu-id="30d4d-107">Exception Throwing</span></span>](../../../docs/standard/design-guidelines/exception-throwing.md)  
 [<span data-ttu-id="30d4d-108">Używanie standardowych typów wyjątków</span><span class="sxs-lookup"><span data-stu-id="30d4d-108">Using Standard Exception Types</span></span>](../../../docs/standard/design-guidelines/using-standard-exception-types.md)  
 [<span data-ttu-id="30d4d-109">Wyjątki i wydajność</span><span class="sxs-lookup"><span data-stu-id="30d4d-109">Exceptions and Performance</span></span>](../../../docs/standard/design-guidelines/exceptions-and-performance.md)  
 <span data-ttu-id="30d4d-110">*Portions © 2005, 2009 Microsoft Corporation. Wszelkie prawa zastrzeżone.*</span><span class="sxs-lookup"><span data-stu-id="30d4d-110">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="30d4d-111">*Przedrukowano za uprawnienie Pearson edukacji, Inc. z [wytyczne dotyczące projektowania Framework: Konwencje, Idiomy i wzorców dla wielokrotnego użytku, do bibliotek .NET, wydanie 2](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina i Brad Abrams publikowane 22 Oct 2008 przez Addison Wesley Professional w ramach serii rozwoju Windows firmy Microsoft.*</span><span class="sxs-lookup"><span data-stu-id="30d4d-111">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="30d4d-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="30d4d-112">See also</span></span>

- [<span data-ttu-id="30d4d-113">Struktura — zalecenia dotyczące projektowania</span><span class="sxs-lookup"><span data-stu-id="30d4d-113">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
