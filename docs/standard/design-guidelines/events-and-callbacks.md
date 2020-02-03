---
title: Zdarzenia i wywołania zwrotne
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- events [.NET Framework], extensibility
- methods [.NET Framework], callback
- callback methods
- callbacks
ms.assetid: 48b55c60-495f-4089-9396-97f9122bba7c
ms.openlocfilehash: 7dab759ba48104530fc41e46f6f2bba18d6c4456
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76741660"
---
# <a name="events-and-callbacks"></a><span data-ttu-id="cad72-102">Zdarzenia i wywołania zwrotne</span><span class="sxs-lookup"><span data-stu-id="cad72-102">Events and Callbacks</span></span>
<span data-ttu-id="cad72-103">Wywołania zwrotne to punkty rozszerzalności, które umożliwiają platformie wywołanie z powrotem do kodu użytkownika przez delegata.</span><span class="sxs-lookup"><span data-stu-id="cad72-103">Callbacks are extensibility points that allow a framework to call back into user code through a delegate.</span></span> <span data-ttu-id="cad72-104">Te Delegaty są zwykle przesyłane do struktury za pomocą parametru metody.</span><span class="sxs-lookup"><span data-stu-id="cad72-104">These delegates are usually passed to the framework through a parameter of a method.</span></span>

 <span data-ttu-id="cad72-105">Zdarzenia to specjalne przypadki wywołania zwrotnego, które obsługują wygodną i spójną składnię do dostarczania delegata (program obsługi zdarzeń).</span><span class="sxs-lookup"><span data-stu-id="cad72-105">Events are a special case of callbacks that supports convenient and consistent syntax for supplying the delegate (an event handler).</span></span> <span data-ttu-id="cad72-106">Ponadto uzupełnianie instrukcji i projektantów programu Visual Studio zapewnia pomoc przy korzystaniu z interfejsów API opartych na zdarzeniach.</span><span class="sxs-lookup"><span data-stu-id="cad72-106">In addition, Visual Studio’s statement completion and designers provide help in using event-based APIs.</span></span> <span data-ttu-id="cad72-107">(Zobacz [projekt zdarzenia](../../../docs/standard/design-guidelines/event.md)).</span><span class="sxs-lookup"><span data-stu-id="cad72-107">(See [Event Design](../../../docs/standard/design-guidelines/event.md).)</span></span>

 <span data-ttu-id="cad72-108">✔️ ROZWAŻYĆ użycie wywołania zwrotnego, aby umożliwić użytkownikom udostępnianie niestandardowego kodu do wykonania przez platformę.</span><span class="sxs-lookup"><span data-stu-id="cad72-108">✔️ CONSIDER using callbacks to allow users to provide custom code to be executed by the framework.</span></span>

 <span data-ttu-id="cad72-109">✔️ ROZWAŻYĆ użycie zdarzeń, aby umożliwić użytkownikom dostosowanie zachowania struktury bez konieczności poznania projektu zorientowanego obiektowo.</span><span class="sxs-lookup"><span data-stu-id="cad72-109">✔️ CONSIDER using events to allow users to customize the behavior of a framework without the need for understanding object-oriented design.</span></span>

 <span data-ttu-id="cad72-110">✔️ Preferuj zdarzenia przez zwykłe wywołania zwrotne, ponieważ są one bardziej znane dla szerszego zakresu deweloperów i są zintegrowane z uzupełnianiem instrukcji programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="cad72-110">✔️ DO prefer events over plain callbacks, because they are more familiar to a broader range of developers and are integrated with Visual Studio statement completion.</span></span>

 <span data-ttu-id="cad72-111">❌ unikać używania wywołań zwrotnych w interfejsach API z uwzględnieniem wydajności.</span><span class="sxs-lookup"><span data-stu-id="cad72-111">❌ AVOID using callbacks in performance-sensitive APIs.</span></span>

 <span data-ttu-id="cad72-112">Podczas definiowania interfejsów API z wywołaniami zwrotnymi ✔️ używać nowych typów `Func<...>`, `Action<...>`lub `Expression<...>` zamiast niestandardowych delegatów.</span><span class="sxs-lookup"><span data-stu-id="cad72-112">✔️ DO use the new `Func<...>`, `Action<...>`, or `Expression<...>` types instead of custom delegates, when defining APIs with callbacks.</span></span>

 <span data-ttu-id="cad72-113">`Func<...>` i `Action<...>` reprezentują delegatów ogólnych.</span><span class="sxs-lookup"><span data-stu-id="cad72-113">`Func<...>` and `Action<...>` represent generic delegates.</span></span> <span data-ttu-id="cad72-114">`Expression<...>` reprezentuje definicje funkcji, które mogą być kompilowane i następnie wywoływane w środowisku uruchomieniowym, ale mogą być również serializowane i przesyłane do procesów zdalnych.</span><span class="sxs-lookup"><span data-stu-id="cad72-114">`Expression<...>` represents function definitions that can be compiled and subsequently invoked at runtime but can also be serialized and passed to remote processes.</span></span>

 <span data-ttu-id="cad72-115">✔️ DO mierzenia i zrozumienia implikacji wydajności przy użyciu `Expression<...>`, zamiast używać `Func<...>` i `Action<...>` delegatów.</span><span class="sxs-lookup"><span data-stu-id="cad72-115">✔️ DO measure and understand performance implications of using `Expression<...>`, instead of using `Func<...>` and `Action<...>` delegates.</span></span>

 <span data-ttu-id="cad72-116">typy `Expression<...>` są w większości przypadków logicznie równoważne z `Func<...>` i delegatów `Action<...>`.</span><span class="sxs-lookup"><span data-stu-id="cad72-116">`Expression<...>` types are in most cases logically equivalent to `Func<...>` and `Action<...>` delegates.</span></span> <span data-ttu-id="cad72-117">Główna różnica polega na tym, że Delegaty mają być używane w scenariuszach procesu lokalnego; wyrażenia są przeznaczone do przypadków, gdy są korzystne i możliwe do obliczenia wyrażenia w procesie lub na komputerze zdalnym.</span><span class="sxs-lookup"><span data-stu-id="cad72-117">The main difference between them is that the delegates are intended to be used in local process scenarios; expressions are intended for cases where it’s beneficial and possible to evaluate the expression in a remote process or machine.</span></span>

 <span data-ttu-id="cad72-118">✔️ zrozumieć, że wywołując delegata, wykonujesz dowolny kod, który może mieć wpływ na bezpieczeństwo, prawidłowość i zgodność.</span><span class="sxs-lookup"><span data-stu-id="cad72-118">✔️ DO understand that by calling a delegate, you are executing arbitrary code and that could have security, correctness, and compatibility repercussions.</span></span>

 <span data-ttu-id="cad72-119">*Fragmenty © 2005, 2009 Microsoft Corporation. Wszelkie prawa zastrzeżone.*</span><span class="sxs-lookup"><span data-stu-id="cad72-119">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>

 <span data-ttu-id="cad72-120">*Ponownie Wydrukowano przez uprawnienie Pearson Education, Inc. z [wytycznych dotyczących projektowania platformy: konwencje, idiomy i wzorce dla bibliotek .NET do wielokrotnego użytku, 2. wydanie](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) przez Krzysztof Cwalina i Brad Abrams, opublikowane 22, 2008 przez Addison-Wesley Professional w ramach serii Microsoft Windows Development.*</span><span class="sxs-lookup"><span data-stu-id="cad72-120">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>

## <a name="see-also"></a><span data-ttu-id="cad72-121">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="cad72-121">See also</span></span>

- [<span data-ttu-id="cad72-122">Projektowanie pod kątem rozszerzalności</span><span class="sxs-lookup"><span data-stu-id="cad72-122">Designing for Extensibility</span></span>](../../../docs/standard/design-guidelines/designing-for-extensibility.md)
- [<span data-ttu-id="cad72-123">Struktura — zalecenia dotyczące projektowania</span><span class="sxs-lookup"><span data-stu-id="cad72-123">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
