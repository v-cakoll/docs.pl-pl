---
title: Zdarzenia i wywołania zwrotne
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- events [.NET Framework], extensibility
- methods [.NET Framework], callback
- callback methods
- callbacks
ms.assetid: 48b55c60-495f-4089-9396-97f9122bba7c
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 90cc40024de627f151a4d0df879a65e5900004b4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="events-and-callbacks"></a>Zdarzenia i wywołania zwrotne
Wywołania zwrotne to punkty rozszerzalności, umożliwiających framework do wywołania zwrotnego do kodu użytkownika za pośrednictwem pełnomocnika. Te obiekty delegowane są zazwyczaj przekazywane do struktury parametru metody.  
  
 Zdarzenia są szczególnych przypadkach wywołań zwrotnych, obsługująca składni wygodne i spójny dostarczanie delegata (procedura obsługi zdarzeń). Ponadto uzupełniania Visual Studio oraz projektantów zapewnianie pomocy w za pomocą opartego na zdarzeniach interfejsów API. (Zobacz [projektu zdarzeń](../../../docs/standard/design-guidelines/event.md).)  
  
 **ROZWAŻ ✓** przy użyciu wywołań zwrotnych, aby użytkownicy mogli podać kod niestandardowy ma być wykonane przez platformę.  
  
 **ROZWAŻ ✓** użytkownicy mogą dostosować zachowanie framework bez konieczności opis obiektowego za pomocą zdarzeń.  
  
 **CZY ✓** Preferuj zdarzeń przed zwykły wywołań zwrotnych, ponieważ są bardziej znane z szerszym deweloperów i są zintegrowane z usługą Visual Studio uzupełniania.  
  
 **X należy UNIKAĆ** przy użyciu wywołania zwrotne w wydajności wrażliwych interfejsów API.  
  
 **CZY ✓** nowe `Func<...>`, `Action<...>`, lub `Expression<...>` typy zamiast niestandardowych delegatów, definiując interfejsów API wywołań zwrotnych.  
  
 `Func<...>` i `Action<...>` reprezentują delegatów. `Expression<...>` reprezentuje definicji funkcji, które mogą być skompilowany i następnie wywołana w czasie wykonywania, ale może również być serializowane i przekazywane do procesów zdalnych.  
  
 **CZY ✓** mierzenie i rozumienie wpływ na wydajność programu przy użyciu `Expression<...>`, zamiast `Func<...>` i `Action<...>` delegatów.  
  
 `Expression<...>` typy są w większości przypadków logicznie odpowiednikiem `Func<...>` i `Action<...>` delegatów. Podstawowa różnica między nimi jest, że delegatów są przeznaczone do użycia w scenariuszach proces lokalny; wyrażenia są przeznaczone dla przypadków, w których jest korzystne i można obliczyć wyrażenia w maszynie lub zdalnego procesu.  
  
 **CZY ✓** zrozumieć, że przez wywołanie metody delegata, są wykonania dowolnego kodu i który może mieć wpływ na zabezpieczenia, poprawność i zgodności.  
  
 *Portions © 2005, 2009 Microsoft Corporation. Wszelkie prawa zastrzeżone.*  
  
 *Drukowane uprawnieniami wariancji x edukacji, Inc. z [Framework zaleceń dotyczących projektowania: konwencje, Idioms i wzorce dla bibliotek .NET wielokrotnego użytku, wydanie 2](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina i Abrams Brada opublikowane 22 Oct 2008 przez Professional Addison-Wesley jako część serii rozwoju systemu Windows firmy Microsoft.*  
  
## <a name="see-also"></a>Zobacz też  
 [Projektowanie pod kątem rozszerzalności](../../../docs/standard/design-guidelines/designing-for-extensibility.md)  
 [Struktura — zalecenia dotyczące projektowania](../../../docs/standard/design-guidelines/index.md)
