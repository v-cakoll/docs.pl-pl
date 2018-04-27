---
title: Zdarzenia i wywołania zwrotne
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology: dotnet-standard
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- events [.NET Framework], extensibility
- methods [.NET Framework], callback
- callback methods
- callbacks
ms.assetid: 48b55c60-495f-4089-9396-97f9122bba7c
caps.latest.revision: 10
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 6a6851d1be543fe356827cad67b28cafdc9e56c2
ms.sourcegitcommit: 2e8acae16ae802f2d6d04e3ce0a6dbf04e476513
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2018
---
# <a name="events-and-callbacks"></a><span data-ttu-id="0828e-102">Zdarzenia i wywołania zwrotne</span><span class="sxs-lookup"><span data-stu-id="0828e-102">Events and Callbacks</span></span>
<span data-ttu-id="0828e-103">Wywołania zwrotne to punkty rozszerzalności, umożliwiających framework do wywołania zwrotnego do kodu użytkownika za pośrednictwem pełnomocnika.</span><span class="sxs-lookup"><span data-stu-id="0828e-103">Callbacks are extensibility points that allow a framework to call back into user code through a delegate.</span></span> <span data-ttu-id="0828e-104">Te obiekty delegowane są zazwyczaj przekazywane do struktury parametru metody.</span><span class="sxs-lookup"><span data-stu-id="0828e-104">These delegates are usually passed to the framework through a parameter of a method.</span></span>  
  
 <span data-ttu-id="0828e-105">Zdarzenia są szczególnych przypadkach wywołań zwrotnych, obsługująca składni wygodne i spójny dostarczanie delegata (procedura obsługi zdarzeń).</span><span class="sxs-lookup"><span data-stu-id="0828e-105">Events are a special case of callbacks that supports convenient and consistent syntax for supplying the delegate (an event handler).</span></span> <span data-ttu-id="0828e-106">Ponadto uzupełniania Visual Studio oraz projektantów zapewnianie pomocy w za pomocą opartego na zdarzeniach interfejsów API.</span><span class="sxs-lookup"><span data-stu-id="0828e-106">In addition, Visual Studio’s statement completion and designers provide help in using event-based APIs.</span></span> <span data-ttu-id="0828e-107">(Zobacz [projektu zdarzeń](../../../docs/standard/design-guidelines/event.md).)</span><span class="sxs-lookup"><span data-stu-id="0828e-107">(See [Event Design](../../../docs/standard/design-guidelines/event.md).)</span></span>  
  
 <span data-ttu-id="0828e-108">**ROZWAŻ ✓** przy użyciu wywołań zwrotnych, aby użytkownicy mogli podać kod niestandardowy ma być wykonane przez platformę.</span><span class="sxs-lookup"><span data-stu-id="0828e-108">**✓ CONSIDER** using callbacks to allow users to provide custom code to be executed by the framework.</span></span>  
  
 <span data-ttu-id="0828e-109">**ROZWAŻ ✓** użytkownicy mogą dostosować zachowanie framework bez konieczności opis obiektowego za pomocą zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="0828e-109">**✓ CONSIDER** using events to allow users to customize the behavior of a framework without the need for understanding object-oriented design.</span></span>  
  
 <span data-ttu-id="0828e-110">**CZY ✓** Preferuj zdarzeń przed zwykły wywołań zwrotnych, ponieważ są bardziej znane z szerszym deweloperów i są zintegrowane z usługą Visual Studio uzupełniania.</span><span class="sxs-lookup"><span data-stu-id="0828e-110">**✓ DO** prefer events over plain callbacks, because they are more familiar to a broader range of developers and are integrated with Visual Studio statement completion.</span></span>  
  
 <span data-ttu-id="0828e-111">**X należy UNIKAĆ** przy użyciu wywołania zwrotne w wydajności wrażliwych interfejsów API.</span><span class="sxs-lookup"><span data-stu-id="0828e-111">**X AVOID** using callbacks in performance-sensitive APIs.</span></span>  
  
 <span data-ttu-id="0828e-112">**CZY ✓** nowe `Func<...>`, `Action<...>`, lub `Expression<...>` typy zamiast niestandardowych delegatów, definiując interfejsów API wywołań zwrotnych.</span><span class="sxs-lookup"><span data-stu-id="0828e-112">**✓ DO** use the new `Func<...>`, `Action<...>`, or `Expression<...>` types instead of custom delegates, when defining APIs with callbacks.</span></span>  
  
 <span data-ttu-id="0828e-113">`Func<...>` i `Action<...>` reprezentują delegatów.</span><span class="sxs-lookup"><span data-stu-id="0828e-113">`Func<...>` and `Action<...>` represent generic delegates.</span></span> <span data-ttu-id="0828e-114">`Expression<...>` reprezentuje definicji funkcji, które mogą być skompilowany i następnie wywołana w czasie wykonywania, ale może również być serializowane i przekazywane do procesów zdalnych.</span><span class="sxs-lookup"><span data-stu-id="0828e-114">`Expression<...>` represents function definitions that can be compiled and subsequently invoked at runtime but can also be serialized and passed to remote processes.</span></span>  
  
 <span data-ttu-id="0828e-115">**CZY ✓** mierzenie i rozumienie wpływ na wydajność programu przy użyciu `Expression<...>`, zamiast `Func<...>` i `Action<...>` delegatów.</span><span class="sxs-lookup"><span data-stu-id="0828e-115">**✓ DO** measure and understand performance implications of using `Expression<...>`, instead of using `Func<...>` and `Action<...>` delegates.</span></span>  
  
 <span data-ttu-id="0828e-116">`Expression<...>` typy są w większości przypadków logicznie odpowiednikiem `Func<...>` i `Action<...>` delegatów.</span><span class="sxs-lookup"><span data-stu-id="0828e-116">`Expression<...>` types are in most cases logically equivalent to `Func<...>` and `Action<...>` delegates.</span></span> <span data-ttu-id="0828e-117">Podstawowa różnica między nimi jest, że delegatów są przeznaczone do użycia w scenariuszach proces lokalny; wyrażenia są przeznaczone dla przypadków, w których jest korzystne i można obliczyć wyrażenia w maszynie lub zdalnego procesu.</span><span class="sxs-lookup"><span data-stu-id="0828e-117">The main difference between them is that the delegates are intended to be used in local process scenarios; expressions are intended for cases where it’s beneficial and possible to evaluate the expression in a remote process or machine.</span></span>  
  
 <span data-ttu-id="0828e-118">**CZY ✓** zrozumieć, że przez wywołanie metody delegata, są wykonania dowolnego kodu i który może mieć wpływ na zabezpieczenia, poprawność i zgodności.</span><span class="sxs-lookup"><span data-stu-id="0828e-118">**✓ DO** understand that by calling a delegate, you are executing arbitrary code and that could have security, correctness, and compatibility repercussions.</span></span>  
  
 <span data-ttu-id="0828e-119">*Portions © 2005, 2009 Microsoft Corporation. Wszelkie prawa zastrzeżone.*</span><span class="sxs-lookup"><span data-stu-id="0828e-119">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="0828e-120">*Drukowane uprawnieniami wariancji x edukacji, Inc. z [Framework zaleceń dotyczących projektowania: konwencje, Idioms i wzorce dla bibliotek .NET wielokrotnego użytku, wydanie 2](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina i Abrams Brada opublikowane 22 Oct 2008 przez Professional Addison-Wesley jako część serii rozwoju systemu Windows firmy Microsoft.*</span><span class="sxs-lookup"><span data-stu-id="0828e-120">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0828e-121">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="0828e-121">See Also</span></span>  
 [<span data-ttu-id="0828e-122">Projektowanie pod kątem rozszerzalności</span><span class="sxs-lookup"><span data-stu-id="0828e-122">Designing for Extensibility</span></span>](../../../docs/standard/design-guidelines/designing-for-extensibility.md)  
 [<span data-ttu-id="0828e-123">Struktura — zalecenia dotyczące projektowania</span><span class="sxs-lookup"><span data-stu-id="0828e-123">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
