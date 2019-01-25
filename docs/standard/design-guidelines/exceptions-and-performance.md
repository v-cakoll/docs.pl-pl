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
author: KrzysztofCwalina
ms.openlocfilehash: f9fe3045d8bd8b4d625c5cd49bc18574ebb740de
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54707729"
---
# <a name="exceptions-and-performance"></a><span data-ttu-id="bd4b2-102">Wyjątki i wydajność</span><span class="sxs-lookup"><span data-stu-id="bd4b2-102">Exceptions and Performance</span></span>
<span data-ttu-id="bd4b2-103">Jednym problemem wspólnej związanym z wyjątków jest, że wyjątki są używane do kodu, który regularnie zakończy się niepowodzeniem, wydajność wdrożenia zostaną niedopuszczalne.</span><span class="sxs-lookup"><span data-stu-id="bd4b2-103">One common concern related to exceptions is that if exceptions are used for code that routinely fails, the performance of the implementation will be unacceptable.</span></span> <span data-ttu-id="bd4b2-104">Jest to prawidłowy niepożądane.</span><span class="sxs-lookup"><span data-stu-id="bd4b2-104">This is a valid concern.</span></span> <span data-ttu-id="bd4b2-105">Gdy członek zgłasza wyjątek, jego wydajność może być rzędów wolniej.</span><span class="sxs-lookup"><span data-stu-id="bd4b2-105">When a member throws an exception, its performance can be orders of magnitude slower.</span></span> <span data-ttu-id="bd4b2-106">Jednak jest możliwe uzyskanie wysoką wydajność podczas ściśle przestrzega wytycznych wyjątków, które nie zezwalają na używanie kodów błędów.</span><span class="sxs-lookup"><span data-stu-id="bd4b2-106">However, it is possible to achieve good performance while strictly adhering to the exception guidelines that disallow using error codes.</span></span> <span data-ttu-id="bd4b2-107">Dwa wzorce opisane w tej sekcji sugerują sposoby wykonania tej czynności.</span><span class="sxs-lookup"><span data-stu-id="bd4b2-107">Two patterns described in this section suggest ways to do this.</span></span>  
  
 <span data-ttu-id="bd4b2-108">**X DO NOT** używa kody błędów ze względu na problemy, czy wyjątki może negatywnie wpłynąć na wydajność.</span><span class="sxs-lookup"><span data-stu-id="bd4b2-108">**X DO NOT** use error codes because of concerns that exceptions might affect performance negatively.</span></span>  
  
 <span data-ttu-id="bd4b2-109">Aby zwiększyć wydajność, jest możliwe użycie wzorca Tester Doer lub wzorzec spróbuj analizy, opisane w dwóch następnych sekcjach.</span><span class="sxs-lookup"><span data-stu-id="bd4b2-109">To improve performance, it is possible to use either the Tester-Doer Pattern or the Try-Parse Pattern, described in the next two sections.</span></span>  
  
## <a name="tester-doer-pattern"></a><span data-ttu-id="bd4b2-110">Wzorzec Tester Doer</span><span class="sxs-lookup"><span data-stu-id="bd4b2-110">Tester-Doer Pattern</span></span>  
 <span data-ttu-id="bd4b2-111">Czasami można poprawić wydajność, elementu członkowskiego Zgłaszanie wyjątku w, dzieląc element członkowski do dwóch.</span><span class="sxs-lookup"><span data-stu-id="bd4b2-111">Sometimes performance of an exception-throwing member can be improved by breaking the member into two.</span></span> <span data-ttu-id="bd4b2-112">Przyjrzyjmy się <xref:System.Collections.Generic.ICollection%601.Add%2A> metody <xref:System.Collections.Generic.ICollection%601> interfejsu.</span><span class="sxs-lookup"><span data-stu-id="bd4b2-112">Let’s look at the <xref:System.Collections.Generic.ICollection%601.Add%2A> method of the <xref:System.Collections.Generic.ICollection%601> interface.</span></span>  
  
```  
ICollection<int> numbers = ...   
numbers.Add(1);  
```  
  
 <span data-ttu-id="bd4b2-113">Metoda `Add` zgłasza wyjątek, jeśli kolekcja jest tylko do odczytu.</span><span class="sxs-lookup"><span data-stu-id="bd4b2-113">The method `Add` throws if the collection is read-only.</span></span> <span data-ttu-id="bd4b2-114">Może to być problem z wydajnością w scenariuszach, gdzie oczekiwano wywołania metody które często nie powiedzie się.</span><span class="sxs-lookup"><span data-stu-id="bd4b2-114">This can be a performance problem in scenarios where the method call is expected to fail often.</span></span> <span data-ttu-id="bd4b2-115">Sposoby, aby rozwiązać ten problem jest do sprawdzenia, czy kolekcja jest zapisywalny, zanim spróbujesz dodać wartość.</span><span class="sxs-lookup"><span data-stu-id="bd4b2-115">One of the ways to mitigate the problem is to test whether the collection is writable before trying to add a value.</span></span>  
  
```  
ICollection<int> numbers = ...   
...  
if(!numbers.IsReadOnly){  
    numbers.Add(1);  
}  
```  
  
 <span data-ttu-id="bd4b2-116">Element członkowski, używany do sprawdzania warunku, który w tym przykładzie jest to właściwość `IsReadOnly`, jest określany jako tester.</span><span class="sxs-lookup"><span data-stu-id="bd4b2-116">The member used to test a condition, which in our example is the property `IsReadOnly`, is referred to as the tester.</span></span> <span data-ttu-id="bd4b2-117">Element członkowski, używany do wykonywania operacji potencjalnie zgłaszanie, `Add` metody w naszym przykładzie jest określany jako doer.</span><span class="sxs-lookup"><span data-stu-id="bd4b2-117">The member used to perform a potentially throwing operation, the `Add` method in our example, is referred to as the doer.</span></span>  
  
 <span data-ttu-id="bd4b2-118">**✓ CONSIDER** wzorzec Tester Doer dla elementów członkowskich, które zgłaszają wyjątki, może być wspólnych scenariuszy, aby uniknąć problemów z wydajnością związane z wyjątków.</span><span class="sxs-lookup"><span data-stu-id="bd4b2-118">**✓ CONSIDER** the Tester-Doer Pattern for members that might throw exceptions in common scenarios to avoid performance problems related to exceptions.</span></span>  
  
## <a name="try-parse-pattern"></a><span data-ttu-id="bd4b2-119">Try-Parse wzorzec</span><span class="sxs-lookup"><span data-stu-id="bd4b2-119">Try-Parse Pattern</span></span>  
 <span data-ttu-id="bd4b2-120">W przypadku interfejsów API bardzo wrażliwego na wydajność należy użyć wzorca jeszcze szybciej niż wzorzec Tester Doer opisanego w poprzedniej sekcji.</span><span class="sxs-lookup"><span data-stu-id="bd4b2-120">For extremely performance-sensitive APIs, an even faster pattern than the Tester-Doer Pattern described in the previous section should be used.</span></span> <span data-ttu-id="bd4b2-121">Wzorzec wymaga dostosowania nazwy elementu członkowskiego się dobrze zdefiniowanych testu zamierzone, Zapisz część semantyki elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="bd4b2-121">The pattern calls for adjusting the member name to make a well-defined test case a part of the member semantics.</span></span> <span data-ttu-id="bd4b2-122">Na przykład <xref:System.DateTime> definiuje <xref:System.DateTime.Parse%2A> metodę, która zgłasza wyjątek, jeśli podczas analizowania ciągu kończy się niepowodzeniem.</span><span class="sxs-lookup"><span data-stu-id="bd4b2-122">For example, <xref:System.DateTime> defines a <xref:System.DateTime.Parse%2A> method that throws an exception if parsing of a string fails.</span></span> <span data-ttu-id="bd4b2-123">Definiuje również odpowiedni <xref:System.DateTime.TryParse%2A> metodę, która próbuje zanalizować, ale zwraca wartość false w przypadku analizowania zakończy się niepowodzeniem i zwraca wynik pomyślnie analizy przy użyciu `out` parametru.</span><span class="sxs-lookup"><span data-stu-id="bd4b2-123">It also defines a corresponding <xref:System.DateTime.TryParse%2A> method that attempts to parse, but returns false if parsing is unsuccessful and returns the result of a successful parsing using an `out` parameter.</span></span>  
  
```  
public struct DateTime {  
    public static DateTime Parse(string dateTime){   
        ...   
    }  
    public static bool TryParse(string dateTime, out DateTime result){  
        ...  
    }  
}  
```  
  
 <span data-ttu-id="bd4b2-124">Korzystając z tego wzorca, należy zdefiniować funkcje spróbuj w warunkach strict.</span><span class="sxs-lookup"><span data-stu-id="bd4b2-124">When using this pattern, it is important to define the try functionality in strict terms.</span></span> <span data-ttu-id="bd4b2-125">Jeśli element członkowski nie powiedzie się z innego powodu niż spróbuj dobrze zdefiniowanych, elementu członkowskiego musi nadal wyjątku odpowiednie.</span><span class="sxs-lookup"><span data-stu-id="bd4b2-125">If the member fails for any reason other than the well-defined try, the member must still throw a corresponding exception.</span></span>  
  
 <span data-ttu-id="bd4b2-126">**✓ CONSIDER** wzorzec spróbuj analizy dla elementów członkowskich, które zgłaszają wyjątki, może być wspólnych scenariuszy, aby uniknąć problemów z wydajnością związane z wyjątków.</span><span class="sxs-lookup"><span data-stu-id="bd4b2-126">**✓ CONSIDER** the Try-Parse Pattern for members that might throw exceptions in common scenarios to avoid performance problems related to exceptions.</span></span>  
  
 <span data-ttu-id="bd4b2-127">**✓ DO** Użyj prefiksu "Try" i wartość logiczną zwracanego typu dla metody implementacja tego wzorca.</span><span class="sxs-lookup"><span data-stu-id="bd4b2-127">**✓ DO** use the prefix "Try" and Boolean return type for methods implementing this pattern.</span></span>  
  
 <span data-ttu-id="bd4b2-128">**✓ DO** Podaj elementu członkowskiego zgłaszanie wyjątków dla każdego elementu członkowskiego przy użyciu wzorca spróbuj analizy.</span><span class="sxs-lookup"><span data-stu-id="bd4b2-128">**✓ DO** provide an exception-throwing member for each member using the Try-Parse Pattern.</span></span>  
  
 <span data-ttu-id="bd4b2-129">*Portions © 2005, 2009 Microsoft Corporation. Wszelkie prawa zastrzeżone.*</span><span class="sxs-lookup"><span data-stu-id="bd4b2-129">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="bd4b2-130">*Przedrukowano za uprawnienie Pearson edukacji, Inc. z [wytyczne dotyczące projektowania Framework: Konwencje, Idiomy i wzorców dla wielokrotnego użytku, do bibliotek .NET, wydanie 2](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina i Brad Abrams publikowane 22 Oct 2008 przez Addison Wesley Professional w ramach serii rozwoju Windows firmy Microsoft.*</span><span class="sxs-lookup"><span data-stu-id="bd4b2-130">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bd4b2-131">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="bd4b2-131">See also</span></span>

- [<span data-ttu-id="bd4b2-132">Struktura — zalecenia dotyczące projektowania</span><span class="sxs-lookup"><span data-stu-id="bd4b2-132">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
- [<span data-ttu-id="bd4b2-133">Wyjątki — zalecenia dotyczące projektowania</span><span class="sxs-lookup"><span data-stu-id="bd4b2-133">Design Guidelines for Exceptions</span></span>](../../../docs/standard/design-guidelines/exceptions.md)
