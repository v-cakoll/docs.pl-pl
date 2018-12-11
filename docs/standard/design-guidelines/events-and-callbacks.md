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
# <a name="events-and-callbacks"></a>Zdarzenia i wywołania zwrotne
Wywołania zwrotne są punkty rozszerzeń, umożliwiające to platforma do wywołania zwrotnego w kodzie użytkownika za pośrednictwem pełnomocnika. Te delegaty są zazwyczaj przekazywane Framework parametr metody.  
  
 Zdarzenia są w wyjątkowym przypadku okna wywołań zwrotnych, obsługujące składni wygodne i spójny dla podanie delegata (program obsługi zdarzeń). Ponadto uzupełniania instrukcji i projektantów programu Visual Studio zapewnianie pomocy w przy użyciu interfejsów API opartych na zdarzenie. (Zobacz [projekt zdarzenia](../../../docs/standard/design-guidelines/event.md).)  
  
 **✓ CONSIDER** przy użyciu wywołań zwrotnych, aby użytkownicy mogli podać kod niestandardowy ma być wykonane przez platformę.  
  
 **✓ CONSIDER** użytkownicy mogą dostosować zachowanie framework bez konieczności opis obiektowego za pomocą zdarzeń.  
  
 **✓ DO** Preferuj zdarzeń przed zwykły wywołań zwrotnych, ponieważ są bardziej znane z szerszym deweloperów i są zintegrowane z usługą Visual Studio uzupełniania.  
  
 **X AVOID** przy użyciu wywołania zwrotne w wydajności wrażliwych interfejsów API.  
  
 **✓ DO** nowe `Func<...>`, `Action<...>`, lub `Expression<...>` typy zamiast niestandardowych delegatów, definiując interfejsów API wywołań zwrotnych.  
  
 `Func<...>` i `Action<...>` reprezentują delegatów ogólnych. `Expression<...>` reprezentuje definicje funkcji, które zostanie skompilowany i następnie wywoływana w czasie wykonywania, ale może również być serializowany i przekazywane do procesów zdalnych.  
  
 **✓ DO** mierzenie i rozumienie wpływ na wydajność programu przy użyciu `Expression<...>`, zamiast `Func<...>` i `Action<...>` delegatów.  
  
 `Expression<...>` typy są w większości przypadków logicznie równoważne `Func<...>` i `Action<...>` delegatów. Główna różnica między nimi jest, że delegatów są przeznaczone do użycia w scenariuszach lokalnych procesu; wyrażenia są przeznaczone dla przypadkach, gdy jest korzystne i możliwych można obliczyć wartości wyrażenia w proces zdalnego lub maszyny.  
  
 **✓ DO** zrozumieć, że przez wywołanie metody delegata, są wykonania dowolnego kodu i który może mieć wpływ na zabezpieczenia, poprawność i zgodności.  
  
 *Portions © 2005, 2009 Microsoft Corporation. Wszelkie prawa zastrzeżone.*  
  
 *Przedrukowano za uprawnienie Pearson edukacji, Inc. z [wytyczne dotyczące projektowania Framework: Konwencje, Idiomy i wzorców dla wielokrotnego użytku, do bibliotek .NET, wydanie 2](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina i Brad Abrams publikowane 22 Oct 2008 przez Addison Wesley Professional w ramach serii rozwoju Windows firmy Microsoft.*  
  
## <a name="see-also"></a>Zobacz także

- [Projektowanie pod kątem rozszerzalności](../../../docs/standard/design-guidelines/designing-for-extensibility.md)  
- [Struktura — zalecenia dotyczące projektowania](../../../docs/standard/design-guidelines/index.md)
