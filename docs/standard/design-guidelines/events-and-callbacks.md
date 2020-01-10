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
# <a name="events-and-callbacks"></a>Zdarzenia i wywołania zwrotne
Wywołania zwrotne to punkty rozszerzalności, które umożliwiają platformie wywołanie z powrotem do kodu użytkownika przez delegata. Te Delegaty są zwykle przesyłane do struktury za pomocą parametru metody.  
  
 Zdarzenia to specjalne przypadki wywołania zwrotnego, które obsługują wygodną i spójną składnię do dostarczania delegata (program obsługi zdarzeń). Ponadto uzupełnianie instrukcji i projektantów programu Visual Studio zapewnia pomoc przy korzystaniu z interfejsów API opartych na zdarzeniach. (Zobacz [projekt zdarzenia](../../../docs/standard/design-guidelines/event.md)).  
  
 **✓ CONSIDER** przy użyciu wywołań zwrotnych, aby użytkownicy mogli podać kod niestandardowy ma być wykonane przez platformę.  
  
 **✓ CONSIDER** użytkownicy mogą dostosować zachowanie framework bez konieczności opis obiektowego za pomocą zdarzeń.  
  
 **✓ DO** Preferuj zdarzeń przed zwykły wywołań zwrotnych, ponieważ są bardziej znane z szerszym deweloperów i są zintegrowane z usługą Visual Studio uzupełniania.  
  
 **X AVOID** przy użyciu wywołania zwrotne w wydajności wrażliwych interfejsów API.  
  
 **✓ DO** nowe `Func<...>`, `Action<...>`, lub `Expression<...>` typy zamiast niestandardowych delegatów, definiując interfejsów API wywołań zwrotnych.  
  
 `Func<...>` i `Action<...>` reprezentują delegatów ogólnych. `Expression<...>` reprezentuje definicje funkcji, które mogą być kompilowane i następnie wywoływane w środowisku uruchomieniowym, ale mogą być również serializowane i przesyłane do procesów zdalnych.  
  
 **✓ DO** mierzenie i rozumienie wpływ na wydajność programu przy użyciu `Expression<...>`, zamiast `Func<...>` i `Action<...>` delegatów.  
  
 typy `Expression<...>` są w większości przypadków logicznie równoważne z `Func<...>` i delegatów `Action<...>`. Główna różnica polega na tym, że Delegaty mają być używane w scenariuszach procesu lokalnego; wyrażenia są przeznaczone do przypadków, gdy są korzystne i możliwe do obliczenia wyrażenia w procesie lub na komputerze zdalnym.  
  
 **✓ DO** zrozumieć, że przez wywołanie metody delegata, są wykonania dowolnego kodu i który może mieć wpływ na zabezpieczenia, poprawność i zgodności.  
  
 *Fragmenty © 2005, 2009 Microsoft Corporation. Wszelkie prawa zastrzeżone.*  
  
 *Ponownie Wydrukowano przez uprawnienie Pearson Education, Inc. z [wytycznych dotyczących projektowania platformy: konwencje, idiomy i wzorce dla bibliotek .NET do wielokrotnego użytku, 2. wydanie](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) przez Krzysztof Cwalina i Brad Abrams, opublikowane 22, 2008 przez Addison-Wesley Professional w ramach serii Microsoft Windows Development.*  
  
## <a name="see-also"></a>Zobacz także

- [Projektowanie pod kątem rozszerzalności](../../../docs/standard/design-guidelines/designing-for-extensibility.md)
- [Struktura — zalecenia dotyczące projektowania](../../../docs/standard/design-guidelines/index.md)
