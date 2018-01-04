---
title: "Zdarzenia i wywołania zwrotne"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- events [.NET Framework], extensibility
- methods [.NET Framework], callback
- callback methods
- callbacks
ms.assetid: 48b55c60-495f-4089-9396-97f9122bba7c
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 39dd4e31e84e455b72ce53bd8abffd650ce77dfc
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/23/2017
---
# <a name="events-and-callbacks"></a>Zdarzenia i wywołania zwrotne
Wywołania zwrotne to punkty rozszerzalności, umożliwiających framework do wywołania zwrotnego do kodu użytkownika za pośrednictwem pełnomocnika. Te obiekty delegowane są zazwyczaj przekazywane do struktury parametru metody.  
  
 Zdarzenia są szczególnych przypadkach wywołań zwrotnych, obsługująca składni wygodne i spójny dostarczanie delegata (procedura obsługi zdarzeń). Ponadto uzupełniania Visual Studio oraz projektantów zapewnianie pomocy w za pomocą opartego na zdarzeniach interfejsów API. (Zobacz [projektu zdarzeń](../../../docs/standard/design-guidelines/event.md).)  
  
 **ROZWAŻ ✓** przy użyciu wywołań zwrotnych, aby użytkownicy mogli podać kod niestandardowy ma być wykonane przez platformę.  
  
 **ROZWAŻ ✓** użytkownicy mogą dostosować zachowanie framework bez konieczności opis obiektowego za pomocą zdarzeń.  
  
 **CZY ✓** Preferuj zdarzeń przed zwykły wywołań zwrotnych, ponieważ są bardziej znane z szerszym deweloperów i są zintegrowane z usługą Visual Studio uzupełniania.  
  
 **X należy UNIKAĆ** przy użyciu wywołania zwrotne w wydajności wrażliwych interfejsów API.  
  
 **CZY ✓** nowe `Func<...>`, `Action<...>`, lub `Expression<...>` typy zamiast niestandardowych delegatów, definiując interfejsów API wywołań zwrotnych.  
  
 `Func<...>`i `Action<...>` reprezentują delegatów. `Expression<...>`reprezentuje definicji funkcji, które mogą być skompilowany i następnie wywołana w czasie wykonywania, ale może również być serializowane i przekazywane do procesów zdalnych.  
  
 **CZY ✓** mierzenie i rozumienie wpływ na wydajność programu przy użyciu `Expression<...>`, zamiast `Func<...>` i `Action<...>` delegatów.  
  
 `Expression<...>`typy są w większości przypadków logicznie odpowiednikiem `Func<...>` i `Action<...>` delegatów. Podstawowa różnica między nimi jest, że delegatów są przeznaczone do użycia w scenariuszach proces lokalny; wyrażenia są przeznaczone dla przypadków, w których jest korzystne i można obliczyć wyrażenia w maszynie lub zdalnego procesu.  
  
 **CZY ✓** zrozumieć, że przez wywołanie metody delegata, są wykonania dowolnego kodu i który może mieć wpływ na zabezpieczenia, poprawność i zgodności.  
  
 *Fragmenty © 2005, 2009 Microsoft Corporation. Wszelkie prawa zastrzeżone.*  
  
 *Drukowane uprawnieniami wariancji x edukacji, Inc. z [Framework zaleceń dotyczących projektowania: konwencje, Idioms i wzorce dla bibliotek .NET wielokrotnego użytku, wydanie 2](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina i Abrams Brada opublikowane 22 Oct 2008 przez Professional Addison-Wesley jako część serii rozwoju systemu Windows firmy Microsoft.*  
  
## <a name="see-also"></a>Zobacz też  
 [Projektowanie pod kątem rozszerzalności](../../../docs/standard/design-guidelines/designing-for-extensibility.md)  
 [Struktura — zalecenia dotyczące projektowania](../../../docs/standard/design-guidelines/index.md)
