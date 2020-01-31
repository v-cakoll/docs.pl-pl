---
title: Używanie standardowych typów wyjątków
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- throwing exceptions, standard types
- catching exceptions
- exceptions, catching
- exceptions, throwing
ms.assetid: ab22ce03-78f9-4dca-8824-c7ed3bdccc27
ms.openlocfilehash: 3caa94d9a39966614161e4b19201dcf6065776a2
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76743543"
---
# <a name="using-standard-exception-types"></a><span data-ttu-id="34dfa-102">Używanie standardowych typów wyjątków</span><span class="sxs-lookup"><span data-stu-id="34dfa-102">Using Standard Exception Types</span></span>
<span data-ttu-id="34dfa-103">W tej sekcji opisano standardowe wyjątki udostępniane przez środowisko oraz szczegóły ich użycia.</span><span class="sxs-lookup"><span data-stu-id="34dfa-103">This section describes the standard exceptions provided by the Framework and the details of their usage.</span></span> <span data-ttu-id="34dfa-104">Lista nie jest kompletna.</span><span class="sxs-lookup"><span data-stu-id="34dfa-104">The list is by no means exhaustive.</span></span> <span data-ttu-id="34dfa-105">Zapoznaj się z dokumentacją dotyczącą .NET Framework, aby uzyskać informacje na temat użycia innych typów wyjątków struktury.</span><span class="sxs-lookup"><span data-stu-id="34dfa-105">Please refer to the .NET Framework reference documentation for usage of other Framework exception types.</span></span>

## <a name="exception-and-systemexception"></a><span data-ttu-id="34dfa-106">Wyjątek i SystemException</span><span class="sxs-lookup"><span data-stu-id="34dfa-106">Exception and SystemException</span></span>
 <span data-ttu-id="34dfa-107">❌ nie Generuj <xref:System.Exception?displayProperty=nameWithType> lub <xref:System.SystemException?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="34dfa-107">❌ DO NOT throw <xref:System.Exception?displayProperty=nameWithType> or <xref:System.SystemException?displayProperty=nameWithType>.</span></span>

 <span data-ttu-id="34dfa-108">❌ nie przechwycić `System.Exception` lub `System.SystemException` w kodzie struktury, chyba że zamierzasz ponownie zgłosić.</span><span class="sxs-lookup"><span data-stu-id="34dfa-108">❌ DO NOT catch `System.Exception` or `System.SystemException` in framework code, unless you intend to rethrow.</span></span>

 <span data-ttu-id="34dfa-109">❌ unikać przechwytywania `System.Exception` lub `System.SystemException`, z wyjątkiem obsługi wyjątków najwyższego poziomu.</span><span class="sxs-lookup"><span data-stu-id="34dfa-109">❌ AVOID catching `System.Exception` or `System.SystemException`, except in top-level exception handlers.</span></span>

## <a name="applicationexception"></a><span data-ttu-id="34dfa-110">ApplicationException</span><span class="sxs-lookup"><span data-stu-id="34dfa-110">ApplicationException</span></span>
 <span data-ttu-id="34dfa-111">❌ nie zgłaszaj ani nie pochodzą z <xref:System.ApplicationException>.</span><span class="sxs-lookup"><span data-stu-id="34dfa-111">❌ DO NOT throw or derive from <xref:System.ApplicationException>.</span></span>

## <a name="invalidoperationexception"></a><span data-ttu-id="34dfa-112">InvalidOperationException</span><span class="sxs-lookup"><span data-stu-id="34dfa-112">InvalidOperationException</span></span>
 <span data-ttu-id="34dfa-113">✔️ zgłosić <xref:System.InvalidOperationException>, jeśli obiekt jest w niewłaściwym stanie.</span><span class="sxs-lookup"><span data-stu-id="34dfa-113">✔️ DO throw an <xref:System.InvalidOperationException> if the object is in an inappropriate state.</span></span>

## <a name="argumentexception-argumentnullexception-and-argumentoutofrangeexception"></a><span data-ttu-id="34dfa-114">Argumentyexception, ArgumentNullException i wyjątku ArgumentOutOfRangeException</span><span class="sxs-lookup"><span data-stu-id="34dfa-114">ArgumentException, ArgumentNullException, and ArgumentOutOfRangeException</span></span>
 <span data-ttu-id="34dfa-115">✔️ zgłosić <xref:System.ArgumentException> lub jeden z jego podtypów, jeśli do elementu członkowskiego są przekazane złe argumenty.</span><span class="sxs-lookup"><span data-stu-id="34dfa-115">✔️ DO throw <xref:System.ArgumentException> or one of its subtypes if bad arguments are passed to a member.</span></span> <span data-ttu-id="34dfa-116">Preferuj najbardziej pochodny typ wyjątku, jeśli ma zastosowanie.</span><span class="sxs-lookup"><span data-stu-id="34dfa-116">Prefer the most derived exception type, if applicable.</span></span>

 <span data-ttu-id="34dfa-117">✔️ ustawia właściwość `ParamName` podczas zgłaszania jednej z podklas `ArgumentException`.</span><span class="sxs-lookup"><span data-stu-id="34dfa-117">✔️ DO set the `ParamName` property when throwing one of the subclasses of `ArgumentException`.</span></span>

 <span data-ttu-id="34dfa-118">Ta właściwość reprezentuje nazwę parametru, który spowodował zgłoszenie wyjątku.</span><span class="sxs-lookup"><span data-stu-id="34dfa-118">This property represents the name of the parameter that caused the exception to be thrown.</span></span> <span data-ttu-id="34dfa-119">Należy pamiętać, że właściwość można ustawić przy użyciu jednego z przeciążeń konstruktora.</span><span class="sxs-lookup"><span data-stu-id="34dfa-119">Note that the property can be set using one of the constructor overloads.</span></span>

 <span data-ttu-id="34dfa-120">✔️ używać `value` jako nazwy niejawnego parametru wartości metod ustawiających właściwości.</span><span class="sxs-lookup"><span data-stu-id="34dfa-120">✔️ DO use `value` for the name of the implicit value parameter of property setters.</span></span>

## <a name="nullreferenceexception-indexoutofrangeexception-and-accessviolationexception"></a><span data-ttu-id="34dfa-121">NullReferenceException, IndexOutOfRangeException i AccessViolationException</span><span class="sxs-lookup"><span data-stu-id="34dfa-121">NullReferenceException, IndexOutOfRangeException, and AccessViolationException</span></span>
 <span data-ttu-id="34dfa-122">❌ nie umożliwiają publicznie wywoływanych interfejsów API jawnie lub niejawnie zgłosić <xref:System.NullReferenceException>, <xref:System.AccessViolationException>lub <xref:System.IndexOutOfRangeException>.</span><span class="sxs-lookup"><span data-stu-id="34dfa-122">❌ DO NOT allow publicly callable APIs to explicitly or implicitly throw <xref:System.NullReferenceException>, <xref:System.AccessViolationException>, or <xref:System.IndexOutOfRangeException>.</span></span> <span data-ttu-id="34dfa-123">Te wyjątki są zastrzeżone i zgłaszane przez aparat wykonywania, a w większości przypadków wskazują usterkę.</span><span class="sxs-lookup"><span data-stu-id="34dfa-123">These exceptions are reserved and thrown by the execution engine and in most cases indicate a bug.</span></span>

 <span data-ttu-id="34dfa-124">Wykonaj sprawdzanie argumentów, aby uniknąć zgłaszania tych wyjątków.</span><span class="sxs-lookup"><span data-stu-id="34dfa-124">Do argument checking to avoid throwing these exceptions.</span></span> <span data-ttu-id="34dfa-125">Zgłaszanie tych wyjątków ujawnia szczegóły implementacji metody, która może ulec zmianie w czasie.</span><span class="sxs-lookup"><span data-stu-id="34dfa-125">Throwing these exceptions exposes implementation details of your method that might change over time.</span></span>

## <a name="stackoverflowexception"></a><span data-ttu-id="34dfa-126">StackOverflowException</span><span class="sxs-lookup"><span data-stu-id="34dfa-126">StackOverflowException</span></span>
 <span data-ttu-id="34dfa-127">NIE należy jawnie zgłosić <xref:System.StackOverflowException>❌.</span><span class="sxs-lookup"><span data-stu-id="34dfa-127">❌ DO NOT explicitly throw <xref:System.StackOverflowException>.</span></span> <span data-ttu-id="34dfa-128">Wyjątek powinien być jawnie wygenerowany tylko przez środowisko CLR.</span><span class="sxs-lookup"><span data-stu-id="34dfa-128">The exception should be explicitly thrown only by the CLR.</span></span>

 <span data-ttu-id="34dfa-129">NIE przechwytuje `StackOverflowException`❌.</span><span class="sxs-lookup"><span data-stu-id="34dfa-129">❌ DO NOT catch `StackOverflowException`.</span></span>

 <span data-ttu-id="34dfa-130">Niemal niemożliwe jest zapisanie kodu zarządzanego, który pozostaje spójny w obecności dowolnego przepełnienia stosu.</span><span class="sxs-lookup"><span data-stu-id="34dfa-130">It is almost impossible to write managed code that remains consistent in the presence of arbitrary stack overflows.</span></span> <span data-ttu-id="34dfa-131">Niezarządzane części środowiska CLR pozostają spójne przy użyciu sond do przenoszenia nadprzepływów stosu do dobrze zdefiniowanych miejsc, a nie do tworzenia kopii zapasowych z dowolnego przepełnienia stosu.</span><span class="sxs-lookup"><span data-stu-id="34dfa-131">The unmanaged parts of the CLR remain consistent by using probes to move stack overflows to well-defined places rather than by backing out from arbitrary stack overflows.</span></span>

## <a name="outofmemoryexception"></a><span data-ttu-id="34dfa-132">OutOfMemoryException</span><span class="sxs-lookup"><span data-stu-id="34dfa-132">OutOfMemoryException</span></span>
 <span data-ttu-id="34dfa-133">NIE należy jawnie zgłosić <xref:System.OutOfMemoryException>❌.</span><span class="sxs-lookup"><span data-stu-id="34dfa-133">❌ DO NOT explicitly throw <xref:System.OutOfMemoryException>.</span></span> <span data-ttu-id="34dfa-134">Ten wyjątek jest zgłaszany tylko przez infrastrukturę środowiska CLR.</span><span class="sxs-lookup"><span data-stu-id="34dfa-134">This exception is to be thrown only by the CLR infrastructure.</span></span>

## <a name="comexception-sehexception-and-executionengineexception"></a><span data-ttu-id="34dfa-135">ComException, SEHException — i ExecutionEngineException</span><span class="sxs-lookup"><span data-stu-id="34dfa-135">ComException, SEHException, and ExecutionEngineException</span></span>
 <span data-ttu-id="34dfa-136">❌ nie zgłaszaj jawnie <xref:System.Runtime.InteropServices.COMException>, <xref:System.ExecutionEngineException>i <xref:System.Runtime.InteropServices.SEHException>.</span><span class="sxs-lookup"><span data-stu-id="34dfa-136">❌ DO NOT explicitly throw <xref:System.Runtime.InteropServices.COMException>,  <xref:System.ExecutionEngineException>, and <xref:System.Runtime.InteropServices.SEHException>.</span></span> <span data-ttu-id="34dfa-137">Te wyjątki są zgłaszane tylko przez infrastrukturę środowiska CLR.</span><span class="sxs-lookup"><span data-stu-id="34dfa-137">These exceptions are to be thrown only by the CLR infrastructure.</span></span>

 <span data-ttu-id="34dfa-138">*Fragmenty © 2005, 2009 Microsoft Corporation. Wszelkie prawa zastrzeżone.*</span><span class="sxs-lookup"><span data-stu-id="34dfa-138">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>

 <span data-ttu-id="34dfa-139">*Ponownie Wydrukowano przez uprawnienie Pearson Education, Inc. z [wytycznych dotyczących projektowania platformy: konwencje, idiomy i wzorce dla bibliotek .NET do wielokrotnego użytku, 2. wydanie](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) przez Krzysztof Cwalina i Brad Abrams, opublikowane 22, 2008 przez Addison-Wesley Professional w ramach serii Microsoft Windows Development.*</span><span class="sxs-lookup"><span data-stu-id="34dfa-139">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>

## <a name="see-also"></a><span data-ttu-id="34dfa-140">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="34dfa-140">See also</span></span>

- [<span data-ttu-id="34dfa-141">Struktura — zalecenia dotyczące projektowania</span><span class="sxs-lookup"><span data-stu-id="34dfa-141">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
- [<span data-ttu-id="34dfa-142">Wyjątki — zalecenia dotyczące projektowania</span><span class="sxs-lookup"><span data-stu-id="34dfa-142">Design Guidelines for Exceptions</span></span>](../../../docs/standard/design-guidelines/exceptions.md)
