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
ms.openlocfilehash: 80c16e29f1d8a0653295ebc3cf25be6fb78b7dc9
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75709416"
---
# <a name="events-and-callbacks"></a><span data-ttu-id="d76c7-102">Zdarzenia i wywołania zwrotne</span><span class="sxs-lookup"><span data-stu-id="d76c7-102">Events and Callbacks</span></span>
<span data-ttu-id="d76c7-103">Wywołania zwrotne to punkty rozszerzalności, które umożliwiają platformie wywołanie z powrotem do kodu użytkownika przez delegata.</span><span class="sxs-lookup"><span data-stu-id="d76c7-103">Callbacks are extensibility points that allow a framework to call back into user code through a delegate.</span></span> <span data-ttu-id="d76c7-104">Te Delegaty są zwykle przesyłane do struktury za pomocą parametru metody.</span><span class="sxs-lookup"><span data-stu-id="d76c7-104">These delegates are usually passed to the framework through a parameter of a method.</span></span>  
  
 <span data-ttu-id="d76c7-105">Zdarzenia to specjalne przypadki wywołania zwrotnego, które obsługują wygodną i spójną składnię do dostarczania delegata (program obsługi zdarzeń).</span><span class="sxs-lookup"><span data-stu-id="d76c7-105">Events are a special case of callbacks that supports convenient and consistent syntax for supplying the delegate (an event handler).</span></span> <span data-ttu-id="d76c7-106">Ponadto uzupełnianie instrukcji i projektantów programu Visual Studio zapewnia pomoc przy korzystaniu z interfejsów API opartych na zdarzeniach.</span><span class="sxs-lookup"><span data-stu-id="d76c7-106">In addition, Visual Studio’s statement completion and designers provide help in using event-based APIs.</span></span> <span data-ttu-id="d76c7-107">(Zobacz [projekt zdarzenia](../../../docs/standard/design-guidelines/event.md)).</span><span class="sxs-lookup"><span data-stu-id="d76c7-107">(See [Event Design](../../../docs/standard/design-guidelines/event.md).)</span></span>  
  
 <span data-ttu-id="d76c7-108">**✓ CONSIDER** przy użyciu wywołań zwrotnych, aby użytkownicy mogli podać kod niestandardowy ma być wykonane przez platformę.</span><span class="sxs-lookup"><span data-stu-id="d76c7-108">**✓ CONSIDER** using callbacks to allow users to provide custom code to be executed by the framework.</span></span>  
  
 <span data-ttu-id="d76c7-109">**✓ CONSIDER** użytkownicy mogą dostosować zachowanie framework bez konieczności opis obiektowego za pomocą zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="d76c7-109">**✓ CONSIDER** using events to allow users to customize the behavior of a framework without the need for understanding object-oriented design.</span></span>  
  
 <span data-ttu-id="d76c7-110">**✓ DO** Preferuj zdarzeń przed zwykły wywołań zwrotnych, ponieważ są bardziej znane z szerszym deweloperów i są zintegrowane z usługą Visual Studio uzupełniania.</span><span class="sxs-lookup"><span data-stu-id="d76c7-110">**✓ DO** prefer events over plain callbacks, because they are more familiar to a broader range of developers and are integrated with Visual Studio statement completion.</span></span>  
  
 <span data-ttu-id="d76c7-111">**X AVOID** przy użyciu wywołania zwrotne w wydajności wrażliwych interfejsów API.</span><span class="sxs-lookup"><span data-stu-id="d76c7-111">**X AVOID** using callbacks in performance-sensitive APIs.</span></span>  
  
 <span data-ttu-id="d76c7-112">**✓ DO** nowe `Func<...>`, `Action<...>`, lub `Expression<...>` typy zamiast niestandardowych delegatów, definiując interfejsów API wywołań zwrotnych.</span><span class="sxs-lookup"><span data-stu-id="d76c7-112">**✓ DO** use the new `Func<...>`, `Action<...>`, or `Expression<...>` types instead of custom delegates, when defining APIs with callbacks.</span></span>  
  
 <span data-ttu-id="d76c7-113">`Func<...>` i `Action<...>` reprezentują delegatów ogólnych.</span><span class="sxs-lookup"><span data-stu-id="d76c7-113">`Func<...>` and `Action<...>` represent generic delegates.</span></span> <span data-ttu-id="d76c7-114">`Expression<...>` reprezentuje definicje funkcji, które mogą być kompilowane i następnie wywoływane w środowisku uruchomieniowym, ale mogą być również serializowane i przesyłane do procesów zdalnych.</span><span class="sxs-lookup"><span data-stu-id="d76c7-114">`Expression<...>` represents function definitions that can be compiled and subsequently invoked at runtime but can also be serialized and passed to remote processes.</span></span>  
  
 <span data-ttu-id="d76c7-115">**✓ DO** mierzenie i rozumienie wpływ na wydajność programu przy użyciu `Expression<...>`, zamiast `Func<...>` i `Action<...>` delegatów.</span><span class="sxs-lookup"><span data-stu-id="d76c7-115">**✓ DO** measure and understand performance implications of using `Expression<...>`, instead of using `Func<...>` and `Action<...>` delegates.</span></span>  
  
 <span data-ttu-id="d76c7-116">typy `Expression<...>` są w większości przypadków logicznie równoważne z `Func<...>` i delegatów `Action<...>`.</span><span class="sxs-lookup"><span data-stu-id="d76c7-116">`Expression<...>` types are in most cases logically equivalent to `Func<...>` and `Action<...>` delegates.</span></span> <span data-ttu-id="d76c7-117">Główna różnica polega na tym, że Delegaty mają być używane w scenariuszach procesu lokalnego; wyrażenia są przeznaczone do przypadków, gdy są korzystne i możliwe do obliczenia wyrażenia w procesie lub na komputerze zdalnym.</span><span class="sxs-lookup"><span data-stu-id="d76c7-117">The main difference between them is that the delegates are intended to be used in local process scenarios; expressions are intended for cases where it’s beneficial and possible to evaluate the expression in a remote process or machine.</span></span>  
  
 <span data-ttu-id="d76c7-118">**✓ DO** zrozumieć, że przez wywołanie metody delegata, są wykonania dowolnego kodu i który może mieć wpływ na zabezpieczenia, poprawność i zgodności.</span><span class="sxs-lookup"><span data-stu-id="d76c7-118">**✓ DO** understand that by calling a delegate, you are executing arbitrary code and that could have security, correctness, and compatibility repercussions.</span></span>  
  
 <span data-ttu-id="d76c7-119">*Fragmenty © 2005, 2009 Microsoft Corporation. Wszelkie prawa zastrzeżone.*</span><span class="sxs-lookup"><span data-stu-id="d76c7-119">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="d76c7-120">*Ponownie Wydrukowano przez uprawnienie Pearson Education, Inc. z [wytycznych dotyczących projektowania platformy: konwencje, idiomy i wzorce dla bibliotek .NET do wielokrotnego użytku, 2. wydanie](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) przez Krzysztof Cwalina i Brad Abrams, opublikowane 22, 2008 przez Addison-Wesley Professional w ramach serii Microsoft Windows Development.*</span><span class="sxs-lookup"><span data-stu-id="d76c7-120">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d76c7-121">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d76c7-121">See also</span></span>

- [<span data-ttu-id="d76c7-122">Projektowanie pod kątem rozszerzalności</span><span class="sxs-lookup"><span data-stu-id="d76c7-122">Designing for Extensibility</span></span>](../../../docs/standard/design-guidelines/designing-for-extensibility.md)
- [<span data-ttu-id="d76c7-123">Struktura — zalecenia dotyczące projektowania</span><span class="sxs-lookup"><span data-stu-id="d76c7-123">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
