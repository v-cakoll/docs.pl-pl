---
title: Zgłaszanie wyjątku
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- exceptions, throwing
- explicitly throwing exceptions
- throwing exceptions, design guidelines
ms.assetid: 5388e02b-52f5-460e-a2b5-eeafe60eeebe
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9fbbe84811e3fa096b9e13c459143311bb75a198
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/15/2018
ms.locfileid: "45638444"
---
# <a name="exception-throwing"></a><span data-ttu-id="40294-102">Zgłaszanie wyjątku</span><span class="sxs-lookup"><span data-stu-id="40294-102">Exception Throwing</span></span>
<span data-ttu-id="40294-103">Zgłaszanie wyjątku wytyczne opisane w tej sekcji wymaga dobrych definicji znaczenie błąd wykonania.</span><span class="sxs-lookup"><span data-stu-id="40294-103">Exception-throwing guidelines described in this section require a good definition of the meaning of execution failure.</span></span> <span data-ttu-id="40294-104">Niepowodzenie wykonywania występuje zawsze, gdy członek nie, co zostało zaprojektowane w celu (co nazwa elementu członkowskiego oznacza).</span><span class="sxs-lookup"><span data-stu-id="40294-104">Execution failure occurs whenever a member cannot do what it was designed to do (what the member name implies).</span></span> <span data-ttu-id="40294-105">Na przykład jeśli `OpenFile` nie może zwracać dojście otwartego pliku do obiektu wywołującego, jego mogłoby być uważane za wystąpił błąd wykonania.</span><span class="sxs-lookup"><span data-stu-id="40294-105">For example, if the `OpenFile` method cannot return an opened file handle to the caller, it would be considered an execution failure.</span></span>  
  
 <span data-ttu-id="40294-106">Większość programistów stały się komfortowo, jednocześnie używania wyjątków do użycia błędy, takie jak dzielenie przez zero lub odwołania o wartości null.</span><span class="sxs-lookup"><span data-stu-id="40294-106">Most developers have become comfortable with using exceptions for usage errors such as division by zero or null references.</span></span> <span data-ttu-id="40294-107">W ramach wyjątki są używane dla wszystkich warunków błędu, w tym błędy wykonania.</span><span class="sxs-lookup"><span data-stu-id="40294-107">In the Framework, exceptions are used for all error conditions, including execution errors.</span></span>  
  
 <span data-ttu-id="40294-108">**X DO NOT** Zwróć kody błędów.</span><span class="sxs-lookup"><span data-stu-id="40294-108">**X DO NOT** return error codes.</span></span>  
  
 <span data-ttu-id="40294-109">Wyjątki są podstawowym sposobem raportowania błędów w struktur.</span><span class="sxs-lookup"><span data-stu-id="40294-109">Exceptions are the primary means of reporting errors in frameworks.</span></span>  
  
 <span data-ttu-id="40294-110">**✓ DO** Zgłoś błędy wykonania przez zgłaszanie wyjątków.</span><span class="sxs-lookup"><span data-stu-id="40294-110">**✓ DO** report execution failures by throwing exceptions.</span></span>  
  
 <span data-ttu-id="40294-111">**✓ CONSIDER** Trwa kończenie procesu przez wywołanie metody `System.Environment.FailFast` (funkcja .NET Framework 2.0) zamiast generowania wyjątku, jeśli kod napotkał sytuacji, gdy jest niebezpieczny dla dalszego wykonywania.</span><span class="sxs-lookup"><span data-stu-id="40294-111">**✓ CONSIDER** terminating the process by calling `System.Environment.FailFast` (.NET Framework 2.0 feature) instead of throwing an exception if your code encounters a situation where it is unsafe for further execution.</span></span>  
  
 <span data-ttu-id="40294-112">**X DO NOT** Użyj wyjątki dla przepływu sterowania, jeśli to możliwe.</span><span class="sxs-lookup"><span data-stu-id="40294-112">**X DO NOT** use exceptions for the normal flow of control, if possible.</span></span>  
  
 <span data-ttu-id="40294-113">Z wyjątkiem awarie systemu i operacji o potencjalnych sytuacji wyścigu projektantów framework należy projektować interfejsy API, dzięki czemu użytkownicy można napisać kod, który nie generuje wyjątków.</span><span class="sxs-lookup"><span data-stu-id="40294-113">Except for system failures and operations with potential race conditions, framework designers should design APIs so users can write code that does not throw exceptions.</span></span> <span data-ttu-id="40294-114">Na przykład można podać sposób, aby sprawdzić warunki wstępne, przed wywołaniem członka, dzięki czemu użytkownicy można napisać kod, który nie generuje wyjątków.</span><span class="sxs-lookup"><span data-stu-id="40294-114">For example, you can provide a way to check preconditions before calling a member so users can write code that does not throw exceptions.</span></span>  
  
 <span data-ttu-id="40294-115">Należy używać do sprawdzania warunków wstępnych innego członka jest często nazywany tester i nosi nazwę składowej, która faktycznie działa doer.</span><span class="sxs-lookup"><span data-stu-id="40294-115">The member used to check preconditions of another member is often referred to as a tester, and the member that actually does the work is called a doer.</span></span>  
  
 <span data-ttu-id="40294-116">Istnieją przypadki, gdy wzorzec Tester Doer może mieć zmniejszenie wydajności nie do przyjęcia.</span><span class="sxs-lookup"><span data-stu-id="40294-116">There are cases when the Tester-Doer Pattern can have an unacceptable performance overhead.</span></span> <span data-ttu-id="40294-117">W takiej sytuacji należy rozważyć tak zwane wzorzec analizy spróbuj (zobacz [wyjątki i wydajność](../../../docs/standard/design-guidelines/exceptions-and-performance.md) Aby uzyskać więcej informacji).</span><span class="sxs-lookup"><span data-stu-id="40294-117">In such cases, the so-called Try-Parse Pattern should be considered (see [Exceptions and Performance](../../../docs/standard/design-guidelines/exceptions-and-performance.md) for more information).</span></span>  
  
 <span data-ttu-id="40294-118">**✓ CONSIDER** skutki wydajności zgłaszanie wyjątków.</span><span class="sxs-lookup"><span data-stu-id="40294-118">**✓ CONSIDER** the performance implications of throwing exceptions.</span></span> <span data-ttu-id="40294-119">Stawki throw powyżej 100 na sekundę mogą znacznie wpłynąć na wydajność większości aplikacji.</span><span class="sxs-lookup"><span data-stu-id="40294-119">Throw rates above 100 per second are likely to noticeably impact the performance of most applications.</span></span>  
  
 <span data-ttu-id="40294-120">**✓ DO** dokumentu wszystkie wyjątki zgłaszane przez członków publicznie można wywołać z powodu naruszenia elementu członkowskiego kontraktu (zamiast awarii systemu) i je traktować jako część Umowy.</span><span class="sxs-lookup"><span data-stu-id="40294-120">**✓ DO** document all exceptions thrown by publicly callable members because of a violation of the member contract (rather than a system failure) and treat them as part of your contract.</span></span>  
  
 <span data-ttu-id="40294-121">Wyjątki, które są częścią kontraktu nie należy zmieniać z jednej wersji do następnego (czyli nie należy zmieniać typ wyjątku i nie należy dodawać nowych wyjątków).</span><span class="sxs-lookup"><span data-stu-id="40294-121">Exceptions that are a part of the contract should not change from one version to the next (i.e., exception type should not change, and new exceptions should not be added).</span></span>  
  
 <span data-ttu-id="40294-122">**X DO NOT** ma publicznych członków, których można albo throw lub nie na podstawie niektórych opcji.</span><span class="sxs-lookup"><span data-stu-id="40294-122">**X DO NOT** have public members that can either throw or not based on some option.</span></span>  
  
 <span data-ttu-id="40294-123">**X DO NOT** ma publicznych elementów członkowskich, które zwracają wyjątki jako wartości zwracane lub `out` parametru.</span><span class="sxs-lookup"><span data-stu-id="40294-123">**X DO NOT** have public members that return exceptions as the return value or an `out` parameter.</span></span>  
  
 <span data-ttu-id="40294-124">Zwracanie wyjątków z publicznych interfejsów API, zamiast zgłaszać ich unieważnia wiele korzyści zapewnianych przez raportowanie błędów opartą na wyjątkach.</span><span class="sxs-lookup"><span data-stu-id="40294-124">Returning exceptions from public APIs instead of throwing them defeats many of the benefits of exception-based error reporting.</span></span>  
  
 <span data-ttu-id="40294-125">**✓ CONSIDER** za pomocą metody konstruktora wyjątku.</span><span class="sxs-lookup"><span data-stu-id="40294-125">**✓ CONSIDER** using exception builder methods.</span></span>  
  
 <span data-ttu-id="40294-126">Jest wspólne dla tego samego wyjątku z różnych miejsc.</span><span class="sxs-lookup"><span data-stu-id="40294-126">It is common to throw the same exception from different places.</span></span> <span data-ttu-id="40294-127">Aby uniknąć rozrostu kodu, należy używać metod pomocników, tworzyć wyjątki, które inicjuje ich właściwości.</span><span class="sxs-lookup"><span data-stu-id="40294-127">To avoid code bloat, use helper methods that create exceptions and initialize their properties.</span></span>  
  
 <span data-ttu-id="40294-128">Ponadto nie pojawiają się elementy członkowskie, które zgłaszają wyjątki śródwierszowych.</span><span class="sxs-lookup"><span data-stu-id="40294-128">Also, members that throw exceptions are not getting inlined.</span></span> <span data-ttu-id="40294-129">Przenoszenie instrukcji "throw" w Konstruktorze może umożliwić elementu członkowskiego był śródwierszowy.</span><span class="sxs-lookup"><span data-stu-id="40294-129">Moving the throw statement inside the builder might allow the member to be inlined.</span></span>  
  
 <span data-ttu-id="40294-130">**X DO NOT** zgłaszanie wyjątków z bloki filtru wyjątków.</span><span class="sxs-lookup"><span data-stu-id="40294-130">**X DO NOT** throw exceptions from exception filter blocks.</span></span>  
  
 <span data-ttu-id="40294-131">Gdy filtra wyjątku zgłasza wyjątek, wyjątek przez środowisko CLR i filtr zwraca wartość false.</span><span class="sxs-lookup"><span data-stu-id="40294-131">When an exception filter raises an exception, the exception is caught by the CLR, and the filter returns false.</span></span> <span data-ttu-id="40294-132">To zachowanie jest nie do odróżnienia od filtrowania, wykonywanie i zwrócenie wartości false jawnie i dlatego jest bardzo trudno debugować.</span><span class="sxs-lookup"><span data-stu-id="40294-132">This behavior is indistinguishable from the filter executing and returning false explicitly and is therefore very difficult to debug.</span></span>  
  
 <span data-ttu-id="40294-133">**X AVOID** jawne zgłaszanie wyjątków z bloki finally.</span><span class="sxs-lookup"><span data-stu-id="40294-133">**X AVOID** explicitly throwing exceptions from finally blocks.</span></span> <span data-ttu-id="40294-134">Akceptowane są niejawnie zgłoszenia wyjątku, wynikające z wywołania metody, które generują.</span><span class="sxs-lookup"><span data-stu-id="40294-134">Implicitly thrown exceptions resulting from calling methods that throw are acceptable.</span></span>  
  
 <span data-ttu-id="40294-135">*Portions © 2005, 2009 Microsoft Corporation. Wszelkie prawa zastrzeżone.*</span><span class="sxs-lookup"><span data-stu-id="40294-135">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="40294-136">*Przedrukowano przez uprawnienie Pearson edukacji, Inc. z [wytyczne dotyczące projektowania Framework: konwencje Idiomy i wzorce wielokrotnego użytku, do bibliotek .NET, wydanie 2](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina i Brad Abrams opublikowane 22 Oct 2008 przez Professional Addison Wesley jako część serii rozwoju Windows firmy Microsoft.*</span><span class="sxs-lookup"><span data-stu-id="40294-136">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="40294-137">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="40294-137">See also</span></span>

- [<span data-ttu-id="40294-138">Struktura — zalecenia dotyczące projektowania</span><span class="sxs-lookup"><span data-stu-id="40294-138">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)  
- [<span data-ttu-id="40294-139">Wyjątki — zalecenia dotyczące projektowania</span><span class="sxs-lookup"><span data-stu-id="40294-139">Design Guidelines for Exceptions</span></span>](../../../docs/standard/design-guidelines/exceptions.md)
