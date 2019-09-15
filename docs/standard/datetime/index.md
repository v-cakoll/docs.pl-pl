---
title: Daty, godziny i strefy czasowe
ms.date: 04/10/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- time zone objects [.NET Framework]
- date and time data [.NET Framework]
- time zones [.NET Framework]
- times [.NET Framework], time zones
- time [.NET Framework], time zones
ms.assetid: 295c16e0-641b-4771-94b3-39c1ffa98c13
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 03a5594b689a52b641ecece0f9a92fb6cdfe5735
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/14/2019
ms.locfileid: "70991285"
---
# <a name="dates-times-and-time-zones"></a>Daty, godziny i strefy czasowe

Oprócz podstawowej <xref:System.DateTime> struktury platforma .NET udostępnia następujące klasy, które obsługują pracę z strefami czasowymi:

* <xref:System.TimeZone>

  Użyj tej klasy, aby współdziałać z lokalną strefą czasową systemu i strefą czasu koordynowanego (UTC). Funkcjonalność <xref:System.TimeZone> klasy jest w dużym stopniu zastępowana <xref:System.TimeZoneInfo> przez klasę.

* <xref:System.TimeZoneInfo>

  Ta klasa służy do pracy ze wszystkimi strefami czasowymi wstępnie zdefiniowanymi w systemie w celu tworzenia nowych stref czasowych oraz do łatwego konwertowania dat i godzin z jednej strefy czasowej na inną. W przypadku nowych rozwiązań należy użyć <xref:System.TimeZoneInfo> klasy zamiast <xref:System.TimeZone> klasy.

* <xref:System.DateTimeOffset>

  Ta struktura służy do pracy z datami i godzinami, których przesunięcie (lub różnica) od czasu UTC jest znane. <xref:System.DateTimeOffset> Struktura łączy wartość daty i godziny z przesunięciem czasu UTC. Ze względu na jego relację z czasem UTC, indywidualna wartość daty i godziny jednoznacznie identyfikuje pojedynczy punkt w czasie. Dzięki temu wartość <xref:System.DateTimeOffset> jest bardziej przenośna z jednego komputera na inny <xref:System.DateTime> niż wartość.

Ta sekcja dokumentacji zawiera informacje potrzebne do pracy z strefami czasowymi oraz do tworzenia aplikacji obsługujących strefy czasowe, które mogą konwertować daty i godziny z jednej strefy czasowej na inną.

## <a name="in-this-section"></a>W tej sekcji

[Przegląd strefy czasowej](../../../docs/standard/datetime/time-zone-overview.md) W tym artykule omówiono terminologię, koncepcje i problemy związane z tworzeniem aplikacji obsługujących strefy czasowe.

[Wybieranie między elementami DateTime, DateTimeOffset, TimeSpan i TimeZoneInfo](../../../docs/standard/datetime/choosing-between-datetime.md) W tym artykule omówiono <xref:System.DateTime>, kiedy należy używać typów, <xref:System.DateTimeOffset>i <xref:System.TimeZoneInfo> podczas pracy z danymi daty i godziny.

[Znajdowanie stref czasowych zdefiniowanych w systemie lokalnym](../../../docs/standard/datetime/finding-the-time-zones-on-local-system.md) Opisuje sposób wyliczania stref czasowych znalezionych w systemie lokalnym.

[Instrukcje: Wyliczenie strefy czasowe obecne na komputerze](../../../docs/standard/datetime/enumerate-time-zones.md) zawiera przykłady, które wyliczają strefy czasowe zdefiniowane w rejestrze komputera i umożliwiają użytkownikom wybranie wstępnie zdefiniowanej strefy czasowej z listy.

[Instrukcje: Dostęp do wstępnie zdefiniowanych obiektów](../../../docs/standard/datetime/access-utc-and-local.md) czasu UTC i lokalnej strefy czasowej opisuje sposób dostępu do uniwersalnego czasu koordynowanego i lokalnej strefy czasowej.

[Instrukcje: Utworzenie wystąpienia obiektu](../../../docs/standard/datetime/instantiate-time-zone-info.md) TimeZoneInfo opisuje sposób tworzenia <xref:System.TimeZoneInfo> wystąpienia obiektu z rejestru systemu lokalnego.

[Tworzenie wystąpienia obiektu DateTimeOffset](../../../docs/standard/datetime/instantiating-a-datetimeoffset-object.md) Omówienie sposobów, w których <xref:System.DateTimeOffset> można utworzyć wystąpienie obiektu, oraz sposobów, w <xref:System.DateTime> których wartość <xref:System.DateTimeOffset> może zostać przekonwertowana na wartość.

[Instrukcje: Tworzenie stref czasowych bez reguł](../../../docs/standard/datetime/create-time-zones-without-adjustment-rules.md) korygowania opisuje sposób tworzenia niestandardowej strefy czasowej, która nie obsługuje przejścia do i z czasu letniego.

[Instrukcje: Tworzenie stref czasowych przy użyciu](../../../docs/standard/datetime/create-time-zones-with-adjustment-rules.md) reguł korygowania opisuje sposób tworzenia niestandardowej strefy czasowej, która obsługuje jedno lub więcej przejść do i z czasu letniego.

[Zapisywanie i przywracanie stref czasowych](../../../docs/standard/datetime/saving-and-restoring-time-zones.md) Opisuje <xref:System.TimeZoneInfo> obsługę serializacji i deserializacji danych strefy czasowej oraz przedstawia niektóre scenariusze, w których można używać tych funkcji.

[Instrukcje: Zapisywanie stref czasowych w osadzonym](../../../docs/standard/datetime/save-time-zones-to-an-embedded-resource.md) zasobie opisuje sposób tworzenia niestandardowej strefy czasowej i zapisywania jej informacji w pliku zasobów.

[Instrukcje: Przywróć strefy czasowe z osadzonego](../../../docs/standard/datetime/restore-time-zones-from-an-embedded-resource.md) zasobu opisują sposób tworzenia niestandardowych stref czasowych, które zostały zapisane w osadzonym pliku zasobów.

[Wykonywanie operacji arytmetycznych z datami i godzinami](../../../docs/standard/datetime/performing-arithmetic-operations.md) W tym artykule omówiono problemy związane z dodawaniem, odejmowaniem <xref:System.DateTime> i <xref:System.DateTimeOffset> porównywaniem oraz wartościami.

[Instrukcje: Użycie stref czasowych w operacji arytmetycznych](../../../docs/standard/datetime/use-time-zones-in-arithmetic.md) daty i godziny omawia sposób wykonywania operacji arytmetycznych daty i czasu, która odzwierciedla reguły dostosowania strefy czasowej.

[Konwertowanie między elementami DateTime i DateTimeOffset](../../../docs/standard/datetime/converting-between-datetime-and-offset.md) Opisuje sposób konwersji <xref:System.DateTime> wartości i <xref:System.DateTimeOffset> .

[Konwertowanie czasów między strefami czasowymi](../../../docs/standard/datetime/converting-between-time-zones.md) Opisuje sposób konwersji czasów z jednej strefy czasowej na inną.

[Instrukcje: Rozpoznaj niejednoznaczny czas, aby określić, jak rozpoznać niejednoznaczne czasy](../../../docs/standard/datetime/resolve-ambiguous-times.md) , mapując go do czasu standardowego strefy czasowej.

[Instrukcje: Pozwól użytkownikom na rozwiązywanie](../../../docs/standard/datetime/let-users-resolve-ambiguous-times.md) niejednoznacznych czasów, w jaki sposób można określić mapowanie między niejednoznacznym czasem lokalnym i uniwersalnym koordynowanym czasem.

## <a name="reference"></a>Tematy pomocy

<xref:System.TimeZoneInfo?displayProperty=nameWithType>
