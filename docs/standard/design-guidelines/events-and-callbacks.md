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
ms.openlocfilehash: 4000944c3b913f71bc18462cea9062e9237ae53f
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85619536"
---
# <a name="events-and-callbacks"></a>Zdarzenia i wywołania zwrotne
Wywołania zwrotne to punkty rozszerzalności, które umożliwiają platformie wywołanie z powrotem do kodu użytkownika przez delegata. Te Delegaty są zwykle przesyłane do struktury za pomocą parametru metody.

 Zdarzenia to specjalne przypadki wywołania zwrotnego, które obsługują wygodną i spójną składnię do dostarczania delegata (program obsługi zdarzeń). Ponadto uzupełnianie instrukcji i projektantów programu Visual Studio zapewnia pomoc przy korzystaniu z interfejsów API opartych na zdarzeniach. (Zobacz [projekt zdarzenia](event.md)).

 ✔️ ROZWAŻYĆ użycie wywołania zwrotnego, aby umożliwić użytkownikom udostępnianie niestandardowego kodu do wykonania przez platformę.

 ✔️ ROZWAŻYĆ użycie zdarzeń, aby umożliwić użytkownikom dostosowanie zachowania struktury bez konieczności poznania projektu zorientowanego obiektowo.

 ✔️ Preferuj zdarzenia przez zwykłe wywołania zwrotne, ponieważ są one bardziej znane dla szerszego zakresu deweloperów i są zintegrowane z uzupełnianiem instrukcji programu Visual Studio.

 ❌UNIKAj używania wywołań zwrotnych w interfejsach API z uwzględnieniem wydajności.

 `Func<...>` `Action<...>` `Expression<...>` podczas definiowania interfejsów API z wywołaniami zwrotnymi ✔️ używać nowych typów zamiast niestandardowych delegatów.

 `Func<...>`i `Action<...>` reprezentuje delegatów ogólnych. `Expression<...>`reprezentuje definicje funkcji, które mogą być kompilowane i następnie wywoływane w czasie wykonywania, ale mogą być również serializowane i przesyłane do procesów zdalnych.

 ✔️ DO mierzenia i zrozumienia implikacji wydajności przy użyciu `Expression<...>` , zamiast używać `Func<...>` i `Action<...>` delegatów.

 `Expression<...>`typy są w większości przypadków logicznie równoważne z `Func<...>` i `Action<...>` delegatów. Główna różnica polega na tym, że Delegaty mają być używane w scenariuszach procesu lokalnego; wyrażenia są przeznaczone do przypadków, gdy są korzystne i możliwe do obliczenia wyrażenia w procesie lub na komputerze zdalnym.

 ✔️ zrozumieć, że wywołując delegata, wykonujesz dowolny kod, który może mieć wpływ na bezpieczeństwo, prawidłowość i zgodność.

 *Fragmenty &copy; 2005, 2009 Microsoft Corporation. Wszelkie prawa zastrzeżone.*

 *Ponownie Wydrukowano przez uprawnienie Pearson Education, Inc. z [wytycznych dotyczących projektowania platformy: konwencje, idiomy i wzorce dla bibliotek .NET do wielokrotnego użytku, 2. wydanie](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) przez Krzysztof Cwalina i Brad Abrams, opublikowane 22, 2008 przez Addison-Wesley Professional w ramach serii Microsoft Windows Development.*

## <a name="see-also"></a>Zobacz także

- [Projektowanie pod kątem rozszerzalności](designing-for-extensibility.md)
- [Wskazówki dotyczące projektowania struktury](index.md)
