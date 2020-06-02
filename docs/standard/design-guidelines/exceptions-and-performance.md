---
title: Wyjątki i wydajność
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- tester-doer pattern
- TryParse pattern
- exceptions, throwing
- exceptions, performance
- throwing exceptions, performance
ms.assetid: 3ad6aad9-08e6-4232-b336-0e301f2493e6
ms.openlocfilehash: a558547f0e6770e7e76ca31f760d6e2f55c712db
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/02/2020
ms.locfileid: "84289788"
---
# <a name="exceptions-and-performance"></a><span data-ttu-id="f853e-102">Wyjątki i wydajność</span><span class="sxs-lookup"><span data-stu-id="f853e-102">Exceptions and Performance</span></span>
<span data-ttu-id="f853e-103">Jeden typowy problem związany z wyjątkami polega na tym, że jeśli wyjątki są używane dla kodu, który rutynowie kończy się niepowodzeniem, wydajność implementacji będzie nieakceptowalna.</span><span class="sxs-lookup"><span data-stu-id="f853e-103">One common concern related to exceptions is that if exceptions are used for code that routinely fails, the performance of the implementation will be unacceptable.</span></span> <span data-ttu-id="f853e-104">Jest to prawidłowy problem.</span><span class="sxs-lookup"><span data-stu-id="f853e-104">This is a valid concern.</span></span> <span data-ttu-id="f853e-105">Gdy element członkowski zgłasza wyjątek, jego wydajność może być Rzędna wolniej.</span><span class="sxs-lookup"><span data-stu-id="f853e-105">When a member throws an exception, its performance can be orders of magnitude slower.</span></span> <span data-ttu-id="f853e-106">Istnieje jednak możliwość osiągnięcia odpowiedniej wydajności, ale ściśle przestrzeganie wytycznych dotyczących wyjątków, które nie zezwalają na używanie kodów błędów.</span><span class="sxs-lookup"><span data-stu-id="f853e-106">However, it is possible to achieve good performance while strictly adhering to the exception guidelines that disallow using error codes.</span></span> <span data-ttu-id="f853e-107">Dwa wzorce opisane w tej sekcji sugerują sposoby wykonania tej czynności.</span><span class="sxs-lookup"><span data-stu-id="f853e-107">Two patterns described in this section suggest ways to do this.</span></span>

 <span data-ttu-id="f853e-108">❌NIE używaj kodów błędów ze względu na to, że wyjątki mogą negatywnie wpłynąć na wydajność.</span><span class="sxs-lookup"><span data-stu-id="f853e-108">❌ DO NOT use error codes because of concerns that exceptions might affect performance negatively.</span></span>

 <span data-ttu-id="f853e-109">Aby zwiększyć wydajność, można użyć wzorca testera-DOER lub wzorca try-Parse, opisanego w następnych dwóch sekcjach.</span><span class="sxs-lookup"><span data-stu-id="f853e-109">To improve performance, it is possible to use either the Tester-Doer Pattern or the Try-Parse Pattern, described in the next two sections.</span></span>

## <a name="tester-doer-pattern"></a><span data-ttu-id="f853e-110">Tester — wzorzec DOER</span><span class="sxs-lookup"><span data-stu-id="f853e-110">Tester-Doer Pattern</span></span>
 <span data-ttu-id="f853e-111">Czasami można poprawić wydajność zgłaszanego przez wyjątek, dzieląc element członkowski na dwa.</span><span class="sxs-lookup"><span data-stu-id="f853e-111">Sometimes performance of an exception-throwing member can be improved by breaking the member into two.</span></span> <span data-ttu-id="f853e-112">Przyjrzyjmy się <xref:System.Collections.Generic.ICollection%601.Add%2A> metodzie <xref:System.Collections.Generic.ICollection%601> interfejsu.</span><span class="sxs-lookup"><span data-stu-id="f853e-112">Let’s look at the <xref:System.Collections.Generic.ICollection%601.Add%2A> method of the <xref:System.Collections.Generic.ICollection%601> interface.</span></span>

```csharp
ICollection<int> numbers = ...
numbers.Add(1);
```

 <span data-ttu-id="f853e-113">Metoda `Add` zgłasza, czy kolekcja jest tylko do odczytu.</span><span class="sxs-lookup"><span data-stu-id="f853e-113">The method `Add` throws if the collection is read-only.</span></span> <span data-ttu-id="f853e-114">Może to być problem z wydajnością w scenariuszach, w których wywoływanie metody często kończy się niepowodzeniem.</span><span class="sxs-lookup"><span data-stu-id="f853e-114">This can be a performance problem in scenarios where the method call is expected to fail often.</span></span> <span data-ttu-id="f853e-115">Jednym ze sposobów, aby wyeliminować problem, jest przetestowanie, czy kolekcja jest zapisywalna przed podjęciem próby dodania wartości.</span><span class="sxs-lookup"><span data-stu-id="f853e-115">One of the ways to mitigate the problem is to test whether the collection is writable before trying to add a value.</span></span>

```csharp
ICollection<int> numbers = ...
...
if (!numbers.IsReadOnly)
{
    numbers.Add(1);
}
```

 <span data-ttu-id="f853e-116">Element członkowski używany do testowania warunku, który w naszym przykładzie jest właściwością `IsReadOnly` , jest nazywany testerem.</span><span class="sxs-lookup"><span data-stu-id="f853e-116">The member used to test a condition, which in our example is the property `IsReadOnly`, is referred to as the tester.</span></span> <span data-ttu-id="f853e-117">Element członkowski używany do wykonywania potencjalnie wyrzucania operacji, `Add` Metoda w naszym przykładzie, jest określany jako DOER.</span><span class="sxs-lookup"><span data-stu-id="f853e-117">The member used to perform a potentially throwing operation, the `Add` method in our example, is referred to as the doer.</span></span>

 <span data-ttu-id="f853e-118">✔️ ROZWAŻYĆ wzorzec testera DOER dla elementów członkowskich, które mogą zgłosić wyjątki w typowych scenariuszach, aby uniknąć problemów z wydajnością związanych z wyjątkami.</span><span class="sxs-lookup"><span data-stu-id="f853e-118">✔️ CONSIDER the Tester-Doer Pattern for members that might throw exceptions in common scenarios to avoid performance problems related to exceptions.</span></span>

## <a name="try-parse-pattern"></a><span data-ttu-id="f853e-119">Wzorzec try-Parse</span><span class="sxs-lookup"><span data-stu-id="f853e-119">Try-Parse Pattern</span></span>
 <span data-ttu-id="f853e-120">W przypadku skrajnie wrażliwych na wydajność interfejsów API, jeszcze szybszym wzorcem niż wzorzec test-DOER opisany w poprzedniej sekcji.</span><span class="sxs-lookup"><span data-stu-id="f853e-120">For extremely performance-sensitive APIs, an even faster pattern than the Tester-Doer Pattern described in the previous section should be used.</span></span> <span data-ttu-id="f853e-121">Wzorzec wywołuje zmianę nazwy elementu członkowskiego, aby uczynić dobrze zdefiniowanym przypadkiem testowym częścią semantyki elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="f853e-121">The pattern calls for adjusting the member name to make a well-defined test case a part of the member semantics.</span></span> <span data-ttu-id="f853e-122">Na przykład <xref:System.DateTime> definiuje <xref:System.DateTime.Parse%2A> metodę, która zgłasza wyjątek, jeśli analizowanie ciągu kończy się niepowodzeniem.</span><span class="sxs-lookup"><span data-stu-id="f853e-122">For example, <xref:System.DateTime> defines a <xref:System.DateTime.Parse%2A> method that throws an exception if parsing of a string fails.</span></span> <span data-ttu-id="f853e-123">Definiuje również odpowiadającą <xref:System.DateTime.TryParse%2A> metodę, która próbuje analizować, ale zwraca wartość false, jeśli analiza nie powiedzie się i zwraca wynik pomyślnej analizy przy użyciu `out` parametru.</span><span class="sxs-lookup"><span data-stu-id="f853e-123">It also defines a corresponding <xref:System.DateTime.TryParse%2A> method that attempts to parse, but returns false if parsing is unsuccessful and returns the result of a successful parsing using an `out` parameter.</span></span>

```csharp
public struct DateTime
{
    public static DateTime Parse(string dateTime)
    {
        ...
    }
    public static bool TryParse(string dateTime, out DateTime result)
    {
        ...
    }
}
```

 <span data-ttu-id="f853e-124">W przypadku korzystania z tego wzorca ważne jest, aby zdefiniować funkcje try w rygorystycznych warunkach.</span><span class="sxs-lookup"><span data-stu-id="f853e-124">When using this pattern, it is important to define the try functionality in strict terms.</span></span> <span data-ttu-id="f853e-125">Jeśli element członkowski nie powiedzie się z jakiegokolwiek powodu, który jest inny niż wyraźnie zdefiniowane, element członkowski musi nadal zgłosić odpowiedni wyjątek.</span><span class="sxs-lookup"><span data-stu-id="f853e-125">If the member fails for any reason other than the well-defined try, the member must still throw a corresponding exception.</span></span>

 <span data-ttu-id="f853e-126">✔️ ROZWAŻmy wzorzec try-Parse dla elementów członkowskich, które mogą zgłosić wyjątki w typowych scenariuszach, aby uniknąć problemów z wydajnością związanych z wyjątkami.</span><span class="sxs-lookup"><span data-stu-id="f853e-126">✔️ CONSIDER the Try-Parse Pattern for members that might throw exceptions in common scenarios to avoid performance problems related to exceptions.</span></span>

 <span data-ttu-id="f853e-127">✔️ Użyj prefiksu "try" i typu zwracanego Boolean dla metod implementujących ten wzorzec.</span><span class="sxs-lookup"><span data-stu-id="f853e-127">✔️ DO use the prefix "Try" and Boolean return type for methods implementing this pattern.</span></span>

 <span data-ttu-id="f853e-128">✔️ DO podania wyjątku — zgłaszanie elementu członkowskiego dla każdego elementu członkowskiego przy użyciu wzorca try-Parse.</span><span class="sxs-lookup"><span data-stu-id="f853e-128">✔️ DO provide an exception-throwing member for each member using the Try-Parse Pattern.</span></span>

 <span data-ttu-id="f853e-129">*Fragmenty © 2005, 2009 Microsoft Corporation. Wszelkie prawa zastrzeżone.*</span><span class="sxs-lookup"><span data-stu-id="f853e-129">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>

 <span data-ttu-id="f853e-130">*Ponownie Wydrukowano przez uprawnienie Pearson Education, Inc. z [wytycznych dotyczących projektowania platformy: konwencje, idiomy i wzorce dla bibliotek .NET do wielokrotnego użytku, 2. wydanie](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) przez Krzysztof Cwalina i Brad Abrams, opublikowane 22, 2008 przez Addison-Wesley Professional w ramach serii Microsoft Windows Development.*</span><span class="sxs-lookup"><span data-stu-id="f853e-130">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>

## <a name="see-also"></a><span data-ttu-id="f853e-131">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f853e-131">See also</span></span>

- [<span data-ttu-id="f853e-132">Wskazówki dotyczące projektowania struktury</span><span class="sxs-lookup"><span data-stu-id="f853e-132">Framework Design Guidelines</span></span>](index.md)
- [<span data-ttu-id="f853e-133">Wyjątki — zalecenia dotyczące projektowania</span><span class="sxs-lookup"><span data-stu-id="f853e-133">Design Guidelines for Exceptions</span></span>](exceptions.md)
