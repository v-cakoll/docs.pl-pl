---
title: Wyrzucanie wyjątków
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- exceptions, throwing
- explicitly throwing exceptions
- throwing exceptions, design guidelines
ms.assetid: 5388e02b-52f5-460e-a2b5-eeafe60eeebe
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7a493e6591d90ce05a652e48807f63fa90764a91
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33573724"
---
# <a name="exception-throwing"></a><span data-ttu-id="73f44-102">Wyrzucanie wyjątków</span><span class="sxs-lookup"><span data-stu-id="73f44-102">Exception Throwing</span></span>
<span data-ttu-id="73f44-103">Wytyczne zgłaszanie wyjątków opisanych w tej sekcji wymaga dobrej definicji znaczenie błąd wykonania.</span><span class="sxs-lookup"><span data-stu-id="73f44-103">Exception-throwing guidelines described in this section require a good definition of the meaning of execution failure.</span></span> <span data-ttu-id="73f44-104">Niepowodzenie wykonania występuje zawsze, gdy element członkowski nie może wykonać, co zostało zaprojektowane w celu (co nazwa elementu członkowskiego oznacza).</span><span class="sxs-lookup"><span data-stu-id="73f44-104">Execution failure occurs whenever a member cannot do what it was designed to do (what the member name implies).</span></span> <span data-ttu-id="73f44-105">Na przykład jeśli `OpenFile` nie może zwracać dojście otwartego pliku do obiektu wywołującego, jego mogą być uważane za błąd wykonania.</span><span class="sxs-lookup"><span data-stu-id="73f44-105">For example, if the `OpenFile` method cannot return an opened file handle to the caller, it would be considered an execution failure.</span></span>  
  
 <span data-ttu-id="73f44-106">Większość deweloperów stały się doświadczenia w używaniu wyjątki użycia błędów, takich jak dzielenie przez zero lub puste odwołania.</span><span class="sxs-lookup"><span data-stu-id="73f44-106">Most developers have become comfortable with using exceptions for usage errors such as division by zero or null references.</span></span> <span data-ttu-id="73f44-107">W ramach wyjątki są używane dla wszystkich warunków błędu, w tym błędy wykonania.</span><span class="sxs-lookup"><span data-stu-id="73f44-107">In the Framework, exceptions are used for all error conditions, including execution errors.</span></span>  
  
 <span data-ttu-id="73f44-108">**X nie** Zwróć kody błędów.</span><span class="sxs-lookup"><span data-stu-id="73f44-108">**X DO NOT** return error codes.</span></span>  
  
 <span data-ttu-id="73f44-109">Wyjątki są podstawowy sposób raportowanie błędów w struktury.</span><span class="sxs-lookup"><span data-stu-id="73f44-109">Exceptions are the primary means of reporting errors in frameworks.</span></span>  
  
 <span data-ttu-id="73f44-110">**CZY ✓** Zgłoś błędy wykonania przez zgłaszanie wyjątków.</span><span class="sxs-lookup"><span data-stu-id="73f44-110">**✓ DO** report execution failures by throwing exceptions.</span></span>  
  
 <span data-ttu-id="73f44-111">**ROZWAŻ ✓** Trwa kończenie procesu przez wywołanie metody `System.Environment.FailFast` (funkcja .NET Framework 2.0) zamiast generowania wyjątku, jeśli kod napotkał sytuacji, gdy jest niebezpieczny dla dalszego wykonywania.</span><span class="sxs-lookup"><span data-stu-id="73f44-111">**✓ CONSIDER** terminating the process by calling `System.Environment.FailFast` (.NET Framework 2.0 feature) instead of throwing an exception if your code encounters a situation where it is unsafe for further execution.</span></span>  
  
 <span data-ttu-id="73f44-112">**X nie** Użyj wyjątki dla przepływu sterowania, jeśli to możliwe.</span><span class="sxs-lookup"><span data-stu-id="73f44-112">**X DO NOT** use exceptions for the normal flow of control, if possible.</span></span>  
  
 <span data-ttu-id="73f44-113">Z wyjątkiem operacji o potencjalnych sytuacji wyścigu i awarie systemu framework Designer należy projektować interfejsów API tak użytkowników można napisać kod, który nie zgłaszają wyjątki.</span><span class="sxs-lookup"><span data-stu-id="73f44-113">Except for system failures and operations with potential race conditions, framework designers should design APIs so users can write code that does not throw exceptions.</span></span> <span data-ttu-id="73f44-114">Można na przykład można podać sposób sprawdzania warunków wstępnych przed wywołaniem członka, więc użytkowników można napisać kod, który nie zgłaszają wyjątki.</span><span class="sxs-lookup"><span data-stu-id="73f44-114">For example, you can provide a way to check preconditions before calling a member so users can write code that does not throw exceptions.</span></span>  
  
 <span data-ttu-id="73f44-115">Element członkowski używany do sprawdzania warunków wstępnych dla innego elementu członkowskiego jest często określany jako tester, a element członkowski, który wykonuje rzeczywistą pracę nosi nazwę doer.</span><span class="sxs-lookup"><span data-stu-id="73f44-115">The member used to check preconditions of another member is often referred to as a tester, and the member that actually does the work is called a doer.</span></span>  
  
 <span data-ttu-id="73f44-116">Istnieją przypadki, gdy wzorzec Tester Doer może mieć zmniejszenie wydajności nie do przyjęcia.</span><span class="sxs-lookup"><span data-stu-id="73f44-116">There are cases when the Tester-Doer Pattern can have an unacceptable performance overhead.</span></span> <span data-ttu-id="73f44-117">W takiej sytuacji należy rozważyć tak zwane wzorzec spróbuj analizy (zobacz [wyjątki i wydajności](../../../docs/standard/design-guidelines/exceptions-and-performance.md) Aby uzyskać więcej informacji).</span><span class="sxs-lookup"><span data-stu-id="73f44-117">In such cases, the so-called Try-Parse Pattern should be considered (see [Exceptions and Performance](../../../docs/standard/design-guidelines/exceptions-and-performance.md) for more information).</span></span>  
  
 <span data-ttu-id="73f44-118">**ROZWAŻ ✓** skutki wydajności zgłaszanie wyjątków.</span><span class="sxs-lookup"><span data-stu-id="73f44-118">**✓ CONSIDER** the performance implications of throwing exceptions.</span></span> <span data-ttu-id="73f44-119">Stawki throw powyżej 100 na sekundę mogą znacznie wpłynąć na wydajność większości aplikacji.</span><span class="sxs-lookup"><span data-stu-id="73f44-119">Throw rates above 100 per second are likely to noticeably impact the performance of most applications.</span></span>  
  
 <span data-ttu-id="73f44-120">**CZY ✓** dokumentu wszystkie wyjątki zgłaszane przez członków publicznie można wywołać z powodu naruszenia elementu członkowskiego kontraktu (zamiast awarii systemu) i je traktować jako część Umowy.</span><span class="sxs-lookup"><span data-stu-id="73f44-120">**✓ DO** document all exceptions thrown by publicly callable members because of a violation of the member contract (rather than a system failure) and treat them as part of your contract.</span></span>  
  
 <span data-ttu-id="73f44-121">Wyjątki, które są częścią kontraktu nie należy zmieniać z jedną wersję do następnego (tj. typ wyjątku nie należy zmieniać i nie należy dodawać nowych wyjątków).</span><span class="sxs-lookup"><span data-stu-id="73f44-121">Exceptions that are a part of the contract should not change from one version to the next (i.e., exception type should not change, and new exceptions should not be added).</span></span>  
  
 <span data-ttu-id="73f44-122">**X nie** ma publicznych członków, których można albo throw lub nie na podstawie niektórych opcji.</span><span class="sxs-lookup"><span data-stu-id="73f44-122">**X DO NOT** have public members that can either throw or not based on some option.</span></span>  
  
 <span data-ttu-id="73f44-123">**X nie** ma publicznych elementów członkowskich, które zwracają wyjątki jako wartości zwracane lub `out` parametru.</span><span class="sxs-lookup"><span data-stu-id="73f44-123">**X DO NOT** have public members that return exceptions as the return value or an `out` parameter.</span></span>  
  
 <span data-ttu-id="73f44-124">Zwracanie wyjątki z publiczne interfejsy API, zamiast je zgłaszanie pozbawia wiele zalet raportowanie błędów na podstawie wyjątku.</span><span class="sxs-lookup"><span data-stu-id="73f44-124">Returning exceptions from public APIs instead of throwing them defeats many of the benefits of exception-based error reporting.</span></span>  
  
 <span data-ttu-id="73f44-125">**ROZWAŻ ✓** za pomocą metody konstruktora wyjątku.</span><span class="sxs-lookup"><span data-stu-id="73f44-125">**✓ CONSIDER** using exception builder methods.</span></span>  
  
 <span data-ttu-id="73f44-126">Są często, aby zgłosić ten sam wyjątek w różnych miejscach.</span><span class="sxs-lookup"><span data-stu-id="73f44-126">It is common to throw the same exception from different places.</span></span> <span data-ttu-id="73f44-127">Aby uniknąć rozrostu kodu, należy użyć metody pomocnicze, które Tworzenie wyjątków i zainicjuj ich właściwości.</span><span class="sxs-lookup"><span data-stu-id="73f44-127">To avoid code bloat, use helper methods that create exceptions and initialize their properties.</span></span>  
  
 <span data-ttu-id="73f44-128">Ponadto nie otrzymują elementów członkowskich, które zgłaszają wyjątki śródwierszowych.</span><span class="sxs-lookup"><span data-stu-id="73f44-128">Also, members that throw exceptions are not getting inlined.</span></span> <span data-ttu-id="73f44-129">Przenoszenie instrukcję throw do konstruktora mogą zezwalać elementu członkowskiego był śródwierszowy.</span><span class="sxs-lookup"><span data-stu-id="73f44-129">Moving the throw statement inside the builder might allow the member to be inlined.</span></span>  
  
 <span data-ttu-id="73f44-130">**X nie** zgłaszanie wyjątków z bloki filtru wyjątków.</span><span class="sxs-lookup"><span data-stu-id="73f44-130">**X DO NOT** throw exceptions from exception filter blocks.</span></span>  
  
 <span data-ttu-id="73f44-131">Gdy filtru wyjątków zgłasza wyjątek, wyjątek zostanie przechwycony przez środowisko CLR, a filtr zwraca wartość false.</span><span class="sxs-lookup"><span data-stu-id="73f44-131">When an exception filter raises an exception, the exception is caught by the CLR, and the filter returns false.</span></span> <span data-ttu-id="73f44-132">To zachowanie jest można odróżnić od filtru wykonywania i zwrócenie wartości false w sposób jawny i dlatego jest bardzo trudne do debugowania.</span><span class="sxs-lookup"><span data-stu-id="73f44-132">This behavior is indistinguishable from the filter executing and returning false explicitly and is therefore very difficult to debug.</span></span>  
  
 <span data-ttu-id="73f44-133">**X należy UNIKAĆ** jawne zgłaszanie wyjątków z bloki finally.</span><span class="sxs-lookup"><span data-stu-id="73f44-133">**X AVOID** explicitly throwing exceptions from finally blocks.</span></span> <span data-ttu-id="73f44-134">Niejawnie zgłoszenia wyjątku będącym wynikiem wywołania metody, które zgłaszają są dozwolone.</span><span class="sxs-lookup"><span data-stu-id="73f44-134">Implicitly thrown exceptions resulting from calling methods that throw are acceptable.</span></span>  
  
 <span data-ttu-id="73f44-135">*Portions © 2005, 2009 Microsoft Corporation. Wszelkie prawa zastrzeżone.*</span><span class="sxs-lookup"><span data-stu-id="73f44-135">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="73f44-136">*Drukowane uprawnieniami wariancji x edukacji, Inc. z [Framework zaleceń dotyczących projektowania: konwencje, Idioms i wzorce dla bibliotek .NET wielokrotnego użytku, wydanie 2](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina i Abrams Brada opublikowane 22 Oct 2008 przez Professional Addison-Wesley jako część serii rozwoju systemu Windows firmy Microsoft.*</span><span class="sxs-lookup"><span data-stu-id="73f44-136">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="73f44-137">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="73f44-137">See Also</span></span>  
 [<span data-ttu-id="73f44-138">Struktura — zalecenia dotyczące projektowania</span><span class="sxs-lookup"><span data-stu-id="73f44-138">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)  
 [<span data-ttu-id="73f44-139">Wyjątki — zalecenia dotyczące projektowania</span><span class="sxs-lookup"><span data-stu-id="73f44-139">Design Guidelines for Exceptions</span></span>](../../../docs/standard/design-guidelines/exceptions.md)
