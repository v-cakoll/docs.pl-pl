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
ms.openlocfilehash: d46b3cdbddeb1b4e28b7108e7925bd3f086498d0
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73122303"
---
# <a name="dates-times-and-time-zones"></a>Daty, godziny i strefy czasowe

Oprócz podstawowej struktury <xref:System.DateTime> platforma .NET udostępnia następujące klasy, które obsługują pracę z strefami czasowymi:

* <xref:System.TimeZone>

  Użyj tej klasy, aby współdziałać z lokalną strefą czasową systemu i strefą czasu koordynowanego (UTC). Funkcjonalność klasy <xref:System.TimeZone> jest w znacznym stopniu zastępowana przez klasę <xref:System.TimeZoneInfo>.

* <xref:System.TimeZoneInfo>

  Ta klasa służy do pracy ze wszystkimi strefami czasowymi wstępnie zdefiniowanymi w systemie w celu tworzenia nowych stref czasowych oraz do łatwego konwertowania dat i godzin z jednej strefy czasowej na inną. W przypadku nowych rozwiązań należy użyć klasy <xref:System.TimeZoneInfo> zamiast klasy <xref:System.TimeZone>.

* <xref:System.DateTimeOffset>

  Ta struktura służy do pracy z datami i godzinami, których przesunięcie (lub różnica) od czasu UTC jest znane. Struktura <xref:System.DateTimeOffset> łączy wartość daty i godziny z przesunięciem czasu UTC. Ze względu na jego relację z czasem UTC, indywidualna wartość daty i godziny jednoznacznie identyfikuje pojedynczy punkt w czasie. Powoduje to, że wartość <xref:System.DateTimeOffset> będzie bardziej przenośna z jednego komputera na inny niż <xref:System.DateTime> wartość.

Ta sekcja dokumentacji zawiera informacje potrzebne do pracy z strefami czasowymi oraz do tworzenia aplikacji obsługujących strefy czasowe, które mogą konwertować daty i godziny z jednej strefy czasowej na inną.

## <a name="in-this-section"></a>W tej sekcji

[Przegląd strefy czasowej](../../../docs/standard/datetime/time-zone-overview.md) W tym artykule omówiono terminologię, koncepcje i problemy związane z tworzeniem aplikacji obsługujących strefy czasowe.

[Wybieranie między elementami DateTime, DateTimeOffset, TimeSpan i TimeZoneInfo](../../../docs/standard/datetime/choosing-between-datetime.md) W tym artykule omówiono, kiedy należy używać typów <xref:System.DateTime>, <xref:System.DateTimeOffset>i <xref:System.TimeZoneInfo> podczas pracy z danymi daty i godziny.

[Znajdowanie stref czasowych zdefiniowanych w systemie lokalnym](../../../docs/standard/datetime/finding-the-time-zones-on-local-system.md) Opisuje sposób wyliczania stref czasowych znalezionych w systemie lokalnym.

[Instrukcje: Wyliczanie stref czasowych na komputerze](../../../docs/standard/datetime/enumerate-time-zones.md) Zawiera przykłady, które wyliczają strefy czasowe zdefiniowane w rejestrze komputera i umożliwiają użytkownikom wybranie wstępnie zdefiniowanej strefy czasowej z listy.

[Instrukcje: uzyskiwanie dostępu do wstępnie zdefiniowanych obiektów czasu UTC i lokalnego strefy czasowej](../../../docs/standard/datetime/access-utc-and-local.md) Opisuje sposób dostępu do uniwersalnego czasu koordynowanego i lokalnej strefy czasowej.

[Instrukcje: Tworzenie wystąpienia obiektu TimeZoneInfo](../../../docs/standard/datetime/instantiate-time-zone-info.md) Opisuje sposób tworzenia wystąpienia obiektu <xref:System.TimeZoneInfo> z rejestru systemu lokalnego.

[Tworzenie wystąpienia obiektu DateTimeOffset](../../../docs/standard/datetime/instantiating-a-datetimeoffset-object.md) W tym artykule omówiono sposoby tworzenia wystąpienia <xref:System.DateTimeOffset> obiektu i sposoby, w których można skonwertować <xref:System.DateTime> wartość do wartości <xref:System.DateTimeOffset>.

[Instrukcje: Tworzenie stref czasowych bez reguł korygowania](../../../docs/standard/datetime/create-time-zones-without-adjustment-rules.md) Opisuje sposób tworzenia niestandardowej strefy czasowej, która nie obsługuje przejścia do i z czasu letniego.

[Instrukcje: Tworzenie stref czasowych przy użyciu reguł korygowania](../../../docs/standard/datetime/create-time-zones-with-adjustment-rules.md) Opisuje sposób tworzenia niestandardowej strefy czasowej, która obsługuje jeden lub więcej przejść do i z czasu letniego.

[Zapisywanie i przywracanie stref czasowych](../../../docs/standard/datetime/saving-and-restoring-time-zones.md) Opisuje <xref:System.TimeZoneInfo> obsługę serializacji i deserializacji danych strefy czasowej oraz przedstawia niektóre scenariusze, w których można używać tych funkcji.

[Instrukcje: zapisywanie stref czasowych w zasobie osadzonym](../../../docs/standard/datetime/save-time-zones-to-an-embedded-resource.md) Opisuje sposób tworzenia niestandardowej strefy czasowej i zapisywania jej informacji w pliku zasobów.

[Instrukcje: przywracanie stref czasowych z zasobu osadzonego](../../../docs/standard/datetime/restore-time-zones-from-an-embedded-resource.md) Opisuje sposób tworzenia wystąpienia niestandardowych stref czasowych, które zostały zapisane w osadzonym pliku zasobów.

[Wykonywanie operacji arytmetycznych z datami i godzinami](../../../docs/standard/datetime/performing-arithmetic-operations.md) W tym artykule omówiono problemy związane z dodawaniem, odejmowaniem i porównywaniem <xref:System.DateTime> i <xref:System.DateTimeOffset> wartości.

[Instrukcje: używanie stref czasowych w operacji arytmetycznych daty i czasu](../../../docs/standard/datetime/use-time-zones-in-arithmetic.md) W tym artykule omówiono sposób wykonywania operacji arytmetycznych daty i godziny, która odzwierciedla reguły dostosowania strefy czasowej.

[Konwertowanie między elementami DateTime i DateTimeOffset](../../../docs/standard/datetime/converting-between-datetime-and-offset.md) Opisuje sposób konwersji wartości <xref:System.DateTime> i <xref:System.DateTimeOffset>.

[Konwertowanie czasów między strefami czasowymi](../../../docs/standard/datetime/converting-between-time-zones.md) Opisuje sposób konwersji czasów z jednej strefy czasowej na inną.

[Instrukcje: Rozwiązywanie niejednoznacznych czasów](../../../docs/standard/datetime/resolve-ambiguous-times.md) Opisuje, jak rozpoznać niejednoznaczny czas, mapując go do czasu standardowego strefy czasowej.

[Instrukcje: pozwalanie użytkownikom na rozwiązywanie niejednoznacznych godzin](../../../docs/standard/datetime/let-users-resolve-ambiguous-times.md) Opisuje, jak zezwolić użytkownikowi na określenie mapowania między niejednoznacznym czasem lokalnym i uniwersalnym koordynowanym czasem.

## <a name="reference"></a>Tematy pomocy

<xref:System.TimeZoneInfo?displayProperty=nameWithType>
