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
ms.openlocfilehash: 86602cd6e662b1b1057832247babc558ef67b79f
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/02/2020
ms.locfileid: "84276936"
---
# <a name="dates-times-and-time-zones"></a>Daty, godziny i strefy czasowe

Oprócz podstawowej <xref:System.DateTime> struktury platforma .NET udostępnia następujące klasy, które obsługują pracę z strefami czasowymi:

* <xref:System.TimeZone>

  Użyj tej klasy, aby współdziałać z lokalną strefą czasową systemu i strefą czasu koordynowanego (UTC). Funkcjonalność <xref:System.TimeZone> klasy jest w dużym stopniu zastępowana przez <xref:System.TimeZoneInfo> klasę.

* <xref:System.TimeZoneInfo>

  Ta klasa służy do pracy ze wszystkimi strefami czasowymi wstępnie zdefiniowanymi w systemie w celu tworzenia nowych stref czasowych oraz do łatwego konwertowania dat i godzin z jednej strefy czasowej na inną. W przypadku nowych rozwiązań należy użyć <xref:System.TimeZoneInfo> klasy zamiast <xref:System.TimeZone> klasy.

* <xref:System.DateTimeOffset>

  Ta struktura służy do pracy z datami i godzinami, których przesunięcie (lub różnica) od czasu UTC jest znane. <xref:System.DateTimeOffset>Struktura łączy wartość daty i godziny z przesunięciem czasu UTC. Ze względu na jego relację z czasem UTC, indywidualna wartość daty i godziny jednoznacznie identyfikuje pojedynczy punkt w czasie. Dzięki temu <xref:System.DateTimeOffset> wartość jest bardziej przenośna z jednego komputera na inny niż <xref:System.DateTime> wartość.

Ta sekcja dokumentacji zawiera informacje potrzebne do pracy z strefami czasowymi oraz do tworzenia aplikacji obsługujących strefy czasowe, które mogą konwertować daty i godziny z jednej strefy czasowej na inną.

## <a name="in-this-section"></a>W tej sekcji

[Przegląd strefy czasowej](time-zone-overview.md) W tym artykule omówiono terminologię, koncepcje i problemy związane z tworzeniem aplikacji obsługujących strefy czasowe.

[Wybieranie między elementami DateTime, DateTimeOffset, TimeSpan i TimeZoneInfo](choosing-between-datetime.md) W tym artykule omówiono, kiedy należy używać <xref:System.DateTime> <xref:System.DateTimeOffset> typów, i <xref:System.TimeZoneInfo> podczas pracy z danymi daty i godziny.

[Znajdowanie stref czasowych zdefiniowanych w systemie lokalnym](finding-the-time-zones-on-local-system.md) Opisuje sposób wyliczania stref czasowych znalezionych w systemie lokalnym.

[Instrukcje: Wyliczanie stref czasowych na komputerze](enumerate-time-zones.md) Zawiera przykłady, które wyliczają strefy czasowe zdefiniowane w rejestrze komputera i umożliwiają użytkownikom wybranie wstępnie zdefiniowanej strefy czasowej z listy.

[Instrukcje: uzyskiwanie dostępu do wstępnie zdefiniowanych obiektów czasu UTC i lokalnego strefy czasowej](access-utc-and-local.md) Opisuje sposób dostępu do uniwersalnego czasu koordynowanego i lokalnej strefy czasowej.

[Instrukcje: Tworzenie wystąpienia obiektu TimeZoneInfo](instantiate-time-zone-info.md) Opisuje sposób tworzenia wystąpienia <xref:System.TimeZoneInfo> obiektu z rejestru systemu lokalnego.

[Tworzenie wystąpienia obiektu DateTimeOffset](instantiating-a-datetimeoffset-object.md) Omówienie sposobów, w których <xref:System.DateTimeOffset> można utworzyć wystąpienie obiektu, oraz sposobów, w których <xref:System.DateTime> wartość może zostać przekonwertowana na <xref:System.DateTimeOffset> wartość.

[Instrukcje: Tworzenie stref czasowych bez reguł korygowania](create-time-zones-without-adjustment-rules.md) Opisuje sposób tworzenia niestandardowej strefy czasowej, która nie obsługuje przejścia do i z czasu letniego.

[Instrukcje: Tworzenie stref czasowych przy użyciu reguł korygowania](create-time-zones-with-adjustment-rules.md) Opisuje sposób tworzenia niestandardowej strefy czasowej, która obsługuje jeden lub więcej przejść do i z czasu letniego.

[Zapisywanie i przywracanie stref czasowych](saving-and-restoring-time-zones.md) Opisuje <xref:System.TimeZoneInfo> obsługę serializacji i deserializacji danych strefy czasowej oraz przedstawia niektóre scenariusze, w których można używać tych funkcji.

[Instrukcje: zapisywanie stref czasowych w zasobie osadzonym](save-time-zones-to-an-embedded-resource.md) Opisuje sposób tworzenia niestandardowej strefy czasowej i zapisywania jej informacji w pliku zasobów.

[Instrukcje: przywracanie stref czasowych z zasobu osadzonego](restore-time-zones-from-an-embedded-resource.md) Opisuje sposób tworzenia wystąpienia niestandardowych stref czasowych, które zostały zapisane w osadzonym pliku zasobów.

[Wykonywanie operacji arytmetycznych z datami i godzinami](performing-arithmetic-operations.md) W tym artykule omówiono problemy związane z dodawaniem, odejmowaniem i porównywaniem <xref:System.DateTime> oraz <xref:System.DateTimeOffset> wartościami.

[Instrukcje: używanie stref czasowych w operacji arytmetycznych daty i czasu](use-time-zones-in-arithmetic.md) W tym artykule omówiono sposób wykonywania operacji arytmetycznych daty i godziny, która odzwierciedla reguły dostosowania strefy czasowej.

[Konwertowanie między elementami DateTime i DateTimeOffset](converting-between-datetime-and-offset.md) Opisuje sposób konwersji <xref:System.DateTime> <xref:System.DateTimeOffset> wartości i.

[Konwertowanie czasów między strefami czasowymi](converting-between-time-zones.md) Opisuje sposób konwersji czasów z jednej strefy czasowej na inną.

[Instrukcje: Rozwiązywanie niejednoznacznych czasów](resolve-ambiguous-times.md) Opisuje, jak rozpoznać niejednoznaczny czas, mapując go do czasu standardowego strefy czasowej.

[Instrukcje: pozwalanie użytkownikom na rozwiązywanie niejednoznacznych godzin](let-users-resolve-ambiguous-times.md) Opisuje, jak zezwolić użytkownikowi na określenie mapowania między niejednoznacznym czasem lokalnym i uniwersalnym koordynowanym czasem.

## <a name="reference"></a>Tematy pomocy

<xref:System.TimeZoneInfo?displayProperty=nameWithType>
