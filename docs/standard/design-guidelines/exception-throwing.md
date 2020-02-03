---
title: Zgłaszanie wyjątku
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- exceptions, throwing
- explicitly throwing exceptions
- throwing exceptions, design guidelines
ms.assetid: 5388e02b-52f5-460e-a2b5-eeafe60eeebe
ms.openlocfilehash: 18927d242c2ed957d2bc9f8b481beeed775a4e4e
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76741675"
---
# <a name="exception-throwing"></a><span data-ttu-id="014c6-102">Zgłaszanie wyjątku</span><span class="sxs-lookup"><span data-stu-id="014c6-102">Exception Throwing</span></span>
<span data-ttu-id="014c6-103">Zasady zgłaszania wyjątku opisane w tej sekcji wymagają odpowiedniej definicji znaczenia błędu wykonania.</span><span class="sxs-lookup"><span data-stu-id="014c6-103">Exception-throwing guidelines described in this section require a good definition of the meaning of execution failure.</span></span> <span data-ttu-id="014c6-104">Niepowodzenie wykonywania występuje zawsze, gdy członek nie może wykonać czynności, do których został zaprojektowany (co oznacza nazwa elementu członkowskiego).</span><span class="sxs-lookup"><span data-stu-id="014c6-104">Execution failure occurs whenever a member cannot do what it was designed to do (what the member name implies).</span></span> <span data-ttu-id="014c6-105">Na przykład, jeśli metoda `OpenFile` nie może zwrócić otwartego dojścia do pliku wywołującego, będzie ona traktowana jako błąd wykonania.</span><span class="sxs-lookup"><span data-stu-id="014c6-105">For example, if the `OpenFile` method cannot return an opened file handle to the caller, it would be considered an execution failure.</span></span>

 <span data-ttu-id="014c6-106">Większość deweloperów była wygodna z użyciem wyjątków dla błędów użycia, takich jak dzielenie przez zero lub puste odwołania.</span><span class="sxs-lookup"><span data-stu-id="014c6-106">Most developers have become comfortable with using exceptions for usage errors such as division by zero or null references.</span></span> <span data-ttu-id="014c6-107">W strukturze wyjątki są używane dla wszystkich warunków błędów, w tym błędów wykonania.</span><span class="sxs-lookup"><span data-stu-id="014c6-107">In the Framework, exceptions are used for all error conditions, including execution errors.</span></span>

 <span data-ttu-id="014c6-108">❌ nie zwracają kodów błędów.</span><span class="sxs-lookup"><span data-stu-id="014c6-108">❌ DO NOT return error codes.</span></span>

 <span data-ttu-id="014c6-109">Wyjątkiem są podstawowe metody raportowania błędów w strukturach.</span><span class="sxs-lookup"><span data-stu-id="014c6-109">Exceptions are the primary means of reporting errors in frameworks.</span></span>

 <span data-ttu-id="014c6-110">✔️ wykonywanie raportów przez wyrzucanie wyjątków.</span><span class="sxs-lookup"><span data-stu-id="014c6-110">✔️ DO report execution failures by throwing exceptions.</span></span>

 <span data-ttu-id="014c6-111">✔️ ROZWAŻYĆ zakończenie procesu, wywołując `System.Environment.FailFast` (funkcję .NET Framework 2,0), zamiast zgłaszać wyjątek, jeśli kod napotka sytuację, w której jest niebezpieczny do dalszej realizacji.</span><span class="sxs-lookup"><span data-stu-id="014c6-111">✔️ CONSIDER terminating the process by calling `System.Environment.FailFast` (.NET Framework 2.0 feature) instead of throwing an exception if your code encounters a situation where it is unsafe for further execution.</span></span>

 <span data-ttu-id="014c6-112">❌ nie należy używać wyjątków dla normalnego przepływu sterowania, jeśli jest to możliwe.</span><span class="sxs-lookup"><span data-stu-id="014c6-112">❌ DO NOT use exceptions for the normal flow of control, if possible.</span></span>

 <span data-ttu-id="014c6-113">Z wyjątkiem awarii systemu i operacji z potencjalnymi warunkami wyścigu, projektanci struktury powinni projektować interfejsy API, aby użytkownicy mogli pisać kod, który nie zgłasza wyjątków.</span><span class="sxs-lookup"><span data-stu-id="014c6-113">Except for system failures and operations with potential race conditions, framework designers should design APIs so users can write code that does not throw exceptions.</span></span> <span data-ttu-id="014c6-114">Na przykład można umożliwić sprawdzenie warunków wstępnych przed wywołaniem elementu członkowskiego, aby użytkownicy mogli pisać kod, który nie zgłasza wyjątków.</span><span class="sxs-lookup"><span data-stu-id="014c6-114">For example, you can provide a way to check preconditions before calling a member so users can write code that does not throw exceptions.</span></span>

 <span data-ttu-id="014c6-115">Element członkowski używany do sprawdzania warunków wstępnych innego elementu członkowskiego jest często nazywany testerem, a element członkowski, który faktycznie wykonuje prace, nosi nazwę DOER.</span><span class="sxs-lookup"><span data-stu-id="014c6-115">The member used to check preconditions of another member is often referred to as a tester, and the member that actually does the work is called a doer.</span></span>

 <span data-ttu-id="014c6-116">Istnieją przypadki, w których wzorzec testera DOER może mieć nieakceptowalne obciążenie wydajności.</span><span class="sxs-lookup"><span data-stu-id="014c6-116">There are cases when the Tester-Doer Pattern can have an unacceptable performance overhead.</span></span> <span data-ttu-id="014c6-117">W takich przypadkach należy wziąć pod uwagę ten wzór try-Parse (zobacz [wyjątki i wydajność](../../../docs/standard/design-guidelines/exceptions-and-performance.md) , aby uzyskać więcej informacji).</span><span class="sxs-lookup"><span data-stu-id="014c6-117">In such cases, the so-called Try-Parse Pattern should be considered (see [Exceptions and Performance](../../../docs/standard/design-guidelines/exceptions-and-performance.md) for more information).</span></span>

 <span data-ttu-id="014c6-118">✔️ ROZWAŻYĆ implikacje wydajności zgłaszania wyjątków.</span><span class="sxs-lookup"><span data-stu-id="014c6-118">✔️ CONSIDER the performance implications of throwing exceptions.</span></span> <span data-ttu-id="014c6-119">Stawki za 100 na sekundę mogą mieć zauważalny wpływ na wydajność większości aplikacji.</span><span class="sxs-lookup"><span data-stu-id="014c6-119">Throw rates above 100 per second are likely to noticeably impact the performance of most applications.</span></span>

 <span data-ttu-id="014c6-120">✔️ DO dokumentu wszystkie wyjątki zgłoszone przez publicznie wywoływanych członków z powodu naruszenia kontraktu elementu członkowskiego (a nie awarii systemu) i traktowania ich jako części kontraktu.</span><span class="sxs-lookup"><span data-stu-id="014c6-120">✔️ DO document all exceptions thrown by publicly callable members because of a violation of the member contract (rather than a system failure) and treat them as part of your contract.</span></span>

 <span data-ttu-id="014c6-121">Wyjątki, które są częścią kontraktu, nie powinny się zmieniać z jednej wersji na następną (tj. nie należy zmieniać typu wyjątku, a nowe wyjątki nie powinny być dodawane).</span><span class="sxs-lookup"><span data-stu-id="014c6-121">Exceptions that are a part of the contract should not change from one version to the next (i.e., exception type should not change, and new exceptions should not be added).</span></span>

 <span data-ttu-id="014c6-122">❌ nie mają publicznych składowych, które mogą zgłosić lub nie na podstawie jakiejś opcji.</span><span class="sxs-lookup"><span data-stu-id="014c6-122">❌ DO NOT have public members that can either throw or not based on some option.</span></span>

 <span data-ttu-id="014c6-123">❌ nie mają publicznych składowych, które zwracają wyjątki jako wartość zwrotną lub parametr `out`.</span><span class="sxs-lookup"><span data-stu-id="014c6-123">❌ DO NOT have public members that return exceptions as the return value or an `out` parameter.</span></span>

 <span data-ttu-id="014c6-124">Zwracanie wyjątków z publicznych interfejsów API zamiast zgłaszania ich przez wiele zalet raportowania błędów opartych na wyjątkach.</span><span class="sxs-lookup"><span data-stu-id="014c6-124">Returning exceptions from public APIs instead of throwing them defeats many of the benefits of exception-based error reporting.</span></span>

 <span data-ttu-id="014c6-125">✔️ ROZWAŻYĆ użycie metod konstruktora wyjątków.</span><span class="sxs-lookup"><span data-stu-id="014c6-125">✔️ CONSIDER using exception builder methods.</span></span>

 <span data-ttu-id="014c6-126">Często należy zgłosić ten sam wyjątek z różnych miejsc.</span><span class="sxs-lookup"><span data-stu-id="014c6-126">It is common to throw the same exception from different places.</span></span> <span data-ttu-id="014c6-127">Aby uniknąć przeładowanie kodu, należy użyć metod pomocnika, które tworzą wyjątki i inicjują ich właściwości.</span><span class="sxs-lookup"><span data-stu-id="014c6-127">To avoid code bloat, use helper methods that create exceptions and initialize their properties.</span></span>

 <span data-ttu-id="014c6-128">Ponadto elementy członkowskie, które generują wyjątki, nie są obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="014c6-128">Also, members that throw exceptions are not getting inlined.</span></span> <span data-ttu-id="014c6-129">Przeniesienie instrukcji throw wewnątrz konstruktora może pozwolić, aby element członkowski był wbudowany.</span><span class="sxs-lookup"><span data-stu-id="014c6-129">Moving the throw statement inside the builder might allow the member to be inlined.</span></span>

 <span data-ttu-id="014c6-130">❌ nie zgłaszaj wyjątków z bloków filtru wyjątków.</span><span class="sxs-lookup"><span data-stu-id="014c6-130">❌ DO NOT throw exceptions from exception filter blocks.</span></span>

 <span data-ttu-id="014c6-131">Gdy filtr wyjątku zgłasza wyjątek, wyjątek jest przechwytywany przez środowisko CLR, a filtr zwraca wartość false.</span><span class="sxs-lookup"><span data-stu-id="014c6-131">When an exception filter raises an exception, the exception is caught by the CLR, and the filter returns false.</span></span> <span data-ttu-id="014c6-132">Takie zachowanie jest odróżnienie od wykonywanych przez filtr i zwraca wartość false, dlatego trudno jest debugować.</span><span class="sxs-lookup"><span data-stu-id="014c6-132">This behavior is indistinguishable from the filter executing and returning false explicitly and is therefore very difficult to debug.</span></span>

 <span data-ttu-id="014c6-133">❌ UNIKAj jawnego zgłaszania wyjątków z bloków finally.</span><span class="sxs-lookup"><span data-stu-id="014c6-133">❌ AVOID explicitly throwing exceptions from finally blocks.</span></span> <span data-ttu-id="014c6-134">Niejawnie zgłoszone wyjątki powstałe w wyniku wywoływania metod wywołujących są akceptowalne.</span><span class="sxs-lookup"><span data-stu-id="014c6-134">Implicitly thrown exceptions resulting from calling methods that throw are acceptable.</span></span>

 <span data-ttu-id="014c6-135">*Fragmenty © 2005, 2009 Microsoft Corporation. Wszelkie prawa zastrzeżone.*</span><span class="sxs-lookup"><span data-stu-id="014c6-135">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>

 <span data-ttu-id="014c6-136">*Ponownie Wydrukowano przez uprawnienie Pearson Education, Inc. z [wytycznych dotyczących projektowania platformy: konwencje, idiomy i wzorce dla bibliotek .NET do wielokrotnego użytku, 2. wydanie](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) przez Krzysztof Cwalina i Brad Abrams, opublikowane 22, 2008 przez Addison-Wesley Professional w ramach serii Microsoft Windows Development.*</span><span class="sxs-lookup"><span data-stu-id="014c6-136">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>

## <a name="see-also"></a><span data-ttu-id="014c6-137">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="014c6-137">See also</span></span>

- [<span data-ttu-id="014c6-138">Struktura — zalecenia dotyczące projektowania</span><span class="sxs-lookup"><span data-stu-id="014c6-138">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
- [<span data-ttu-id="014c6-139">Wyjątki — zalecenia dotyczące projektowania</span><span class="sxs-lookup"><span data-stu-id="014c6-139">Design Guidelines for Exceptions</span></span>](../../../docs/standard/design-guidelines/exceptions.md)
