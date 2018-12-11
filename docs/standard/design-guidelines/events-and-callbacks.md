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
author: KrzysztofCwalina
ms.openlocfilehash: c9ed52c5a313676baeba66f5cb79c7a56927babb
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/10/2018
ms.locfileid: "53154427"
---
# <a name="events-and-callbacks"></a><span data-ttu-id="43f89-102">Zdarzenia i wywołania zwrotne</span><span class="sxs-lookup"><span data-stu-id="43f89-102">Events and Callbacks</span></span>
<span data-ttu-id="43f89-103">Wywołania zwrotne są punkty rozszerzeń, umożliwiające to platforma do wywołania zwrotnego w kodzie użytkownika za pośrednictwem pełnomocnika.</span><span class="sxs-lookup"><span data-stu-id="43f89-103">Callbacks are extensibility points that allow a framework to call back into user code through a delegate.</span></span> <span data-ttu-id="43f89-104">Te delegaty są zazwyczaj przekazywane Framework parametr metody.</span><span class="sxs-lookup"><span data-stu-id="43f89-104">These delegates are usually passed to the framework through a parameter of a method.</span></span>  
  
 <span data-ttu-id="43f89-105">Zdarzenia są w wyjątkowym przypadku okna wywołań zwrotnych, obsługujące składni wygodne i spójny dla podanie delegata (program obsługi zdarzeń).</span><span class="sxs-lookup"><span data-stu-id="43f89-105">Events are a special case of callbacks that supports convenient and consistent syntax for supplying the delegate (an event handler).</span></span> <span data-ttu-id="43f89-106">Ponadto uzupełniania instrukcji i projektantów programu Visual Studio zapewnianie pomocy w przy użyciu interfejsów API opartych na zdarzenie.</span><span class="sxs-lookup"><span data-stu-id="43f89-106">In addition, Visual Studio’s statement completion and designers provide help in using event-based APIs.</span></span> <span data-ttu-id="43f89-107">(Zobacz [projekt zdarzenia](../../../docs/standard/design-guidelines/event.md).)</span><span class="sxs-lookup"><span data-stu-id="43f89-107">(See [Event Design](../../../docs/standard/design-guidelines/event.md).)</span></span>  
  
 <span data-ttu-id="43f89-108">**✓ CONSIDER** przy użyciu wywołań zwrotnych, aby użytkownicy mogli podać kod niestandardowy ma być wykonane przez platformę.</span><span class="sxs-lookup"><span data-stu-id="43f89-108">**✓ CONSIDER** using callbacks to allow users to provide custom code to be executed by the framework.</span></span>  
  
 <span data-ttu-id="43f89-109">**✓ CONSIDER** użytkownicy mogą dostosować zachowanie framework bez konieczności opis obiektowego za pomocą zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="43f89-109">**✓ CONSIDER** using events to allow users to customize the behavior of a framework without the need for understanding object-oriented design.</span></span>  
  
 <span data-ttu-id="43f89-110">**✓ DO** Preferuj zdarzeń przed zwykły wywołań zwrotnych, ponieważ są bardziej znane z szerszym deweloperów i są zintegrowane z usługą Visual Studio uzupełniania.</span><span class="sxs-lookup"><span data-stu-id="43f89-110">**✓ DO** prefer events over plain callbacks, because they are more familiar to a broader range of developers and are integrated with Visual Studio statement completion.</span></span>  
  
 <span data-ttu-id="43f89-111">**X AVOID** przy użyciu wywołania zwrotne w wydajności wrażliwych interfejsów API.</span><span class="sxs-lookup"><span data-stu-id="43f89-111">**X AVOID** using callbacks in performance-sensitive APIs.</span></span>  
  
 <span data-ttu-id="43f89-112">**✓ DO** nowe `Func<...>`, `Action<...>`, lub `Expression<...>` typy zamiast niestandardowych delegatów, definiując interfejsów API wywołań zwrotnych.</span><span class="sxs-lookup"><span data-stu-id="43f89-112">**✓ DO** use the new `Func<...>`, `Action<...>`, or `Expression<...>` types instead of custom delegates, when defining APIs with callbacks.</span></span>  
  
 <span data-ttu-id="43f89-113">`Func<...>` i `Action<...>` reprezentują delegatów ogólnych.</span><span class="sxs-lookup"><span data-stu-id="43f89-113">`Func<...>` and `Action<...>` represent generic delegates.</span></span> <span data-ttu-id="43f89-114">`Expression<...>` reprezentuje definicje funkcji, które zostanie skompilowany i następnie wywoływana w czasie wykonywania, ale może również być serializowany i przekazywane do procesów zdalnych.</span><span class="sxs-lookup"><span data-stu-id="43f89-114">`Expression<...>` represents function definitions that can be compiled and subsequently invoked at runtime but can also be serialized and passed to remote processes.</span></span>  
  
 <span data-ttu-id="43f89-115">**✓ DO** mierzenie i rozumienie wpływ na wydajność programu przy użyciu `Expression<...>`, zamiast `Func<...>` i `Action<...>` delegatów.</span><span class="sxs-lookup"><span data-stu-id="43f89-115">**✓ DO** measure and understand performance implications of using `Expression<...>`, instead of using `Func<...>` and `Action<...>` delegates.</span></span>  
  
 <span data-ttu-id="43f89-116">`Expression<...>` typy są w większości przypadków logicznie równoważne `Func<...>` i `Action<...>` delegatów.</span><span class="sxs-lookup"><span data-stu-id="43f89-116">`Expression<...>` types are in most cases logically equivalent to `Func<...>` and `Action<...>` delegates.</span></span> <span data-ttu-id="43f89-117">Główna różnica między nimi jest, że delegatów są przeznaczone do użycia w scenariuszach lokalnych procesu; wyrażenia są przeznaczone dla przypadkach, gdy jest korzystne i możliwych można obliczyć wartości wyrażenia w proces zdalnego lub maszyny.</span><span class="sxs-lookup"><span data-stu-id="43f89-117">The main difference between them is that the delegates are intended to be used in local process scenarios; expressions are intended for cases where it’s beneficial and possible to evaluate the expression in a remote process or machine.</span></span>  
  
 <span data-ttu-id="43f89-118">**✓ DO** zrozumieć, że przez wywołanie metody delegata, są wykonania dowolnego kodu i który może mieć wpływ na zabezpieczenia, poprawność i zgodności.</span><span class="sxs-lookup"><span data-stu-id="43f89-118">**✓ DO** understand that by calling a delegate, you are executing arbitrary code and that could have security, correctness, and compatibility repercussions.</span></span>  
  
 <span data-ttu-id="43f89-119">*Portions © 2005, 2009 Microsoft Corporation. Wszelkie prawa zastrzeżone.*</span><span class="sxs-lookup"><span data-stu-id="43f89-119">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="43f89-120">*Przedrukowano za uprawnienie Pearson edukacji, Inc. z [wytyczne dotyczące projektowania Framework: Konwencje, Idiomy i wzorców dla wielokrotnego użytku, do bibliotek .NET, wydanie 2](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina i Brad Abrams publikowane 22 Oct 2008 przez Addison Wesley Professional w ramach serii rozwoju Windows firmy Microsoft.*</span><span class="sxs-lookup"><span data-stu-id="43f89-120">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="43f89-121">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="43f89-121">See also</span></span>

- [<span data-ttu-id="43f89-122">Projektowanie pod kątem rozszerzalności</span><span class="sxs-lookup"><span data-stu-id="43f89-122">Designing for Extensibility</span></span>](../../../docs/standard/design-guidelines/designing-for-extensibility.md)  
- [<span data-ttu-id="43f89-123">Struktura — zalecenia dotyczące projektowania</span><span class="sxs-lookup"><span data-stu-id="43f89-123">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
