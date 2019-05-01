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
ms.openlocfilehash: 5355666b95d75fc18d0188c978c186690ee9ccca
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61819707"
---
# <a name="dates-times-and-time-zones"></a>Daty, godziny i strefy czasowe

Oprócz podstawowego <xref:System.DateTime> struktury .NET zawiera następujące klasy obsługujące pracy ze strefami czasowymi:

* <xref:System.TimeZone>

  Klasa jest używana do pracy z systemu w lokalnej strefie czasowej i strefy uniwersalnego czasu koordynowanego (UTC). Funkcje <xref:System.TimeZone> klasy stopniu zostało zastąpione przez <xref:System.TimeZoneInfo> klasy.

* <xref:System.TimeZoneInfo>

  Klasa jest używana do pracy z dowolnym strefę czasową, która jest wstępnie zdefiniowane w systemie, tworzenie nowych stref czasowych i prosty sposób konwertowania daty i godziny w jednej strefie czasowej na inny. W nowych wdrożeniach należy używać <xref:System.TimeZoneInfo> klasy zamiast <xref:System.TimeZone> klasy.

* <xref:System.DateTimeOffset>

  Ta struktura jest używana do pracy z datami i czasy którego przesunięcie (lub różnicy) z czasu UTC jest znany. <xref:System.DateTimeOffset> Struktury łączy daty i wartości godziny z tego czasu przesunięcie względem czasu UTC. Ze względu na jego relację z czasu UTC, daty i godziny wartość jednoznacznie identyfikuje pojedynczy punkt w czasie. To sprawia, że <xref:System.DateTimeOffset> bardziej przenośny z jednego komputera na inny niż wartość <xref:System.DateTime> wartość.

Ta sekcja dokumentacji zawiera informacje potrzebne do pracy ze strefami czasowymi i tworzenie aplikacji uwzględniających strefy czasowe, które można przekonwertować daty i godziny w jednej strefie czasowej na inny.

## <a name="in-this-section"></a>W tej sekcji

[Przegląd stref czasowych](../../../docs/standard/datetime/time-zone-overview.md) w tym artykule omówiono terminologii, pojęcia i zagadnienia związane z tworzeniem aplikacji uwzględniających strefy czasowe.

[Wybieranie pomiędzy DateTime, DateTimeOffset, TimeSpan i TimeZoneInfo](../../../docs/standard/datetime/choosing-between-datetime.md) omówiono, kiedy należy używać <xref:System.DateTime>, <xref:System.DateTimeOffset>, i <xref:System.TimeZoneInfo> typów podczas pracy z danymi daty i godziny.

[Znajdowanie stref czasowych zdefiniowanych w systemie lokalnym](../../../docs/standard/datetime/finding-the-time-zones-on-local-system.md) opisano, jak wykazywanie stref czasowych znalezionych w systemie lokalnym.

[Instrukcje: Wykazywanie stref czasowych na komputerze](../../../docs/standard/datetime/enumerate-time-zones.md) zawiera przykłady, wyliczanie stref czasowych zdefiniowanych w rejestrze komputera i że umożliwienie użytkownikom wyboru wstępnie zdefiniowane strefy czasowej z listy.

[Instrukcje: Uzyskiwanie dostępu do wstępnie zdefiniowanych obiektów stref UTC i czasem lokalnym](../../../docs/standard/datetime/access-utc-and-local.md) opisano, jak uzyskać dostęp do uniwersalny czas koordynowany i lokalnej strefy czasowej.

[Instrukcje: Tworzenie wystąpień obiektów TimeZoneInfo](../../../docs/standard/datetime/instantiate-time-zone-info.md) w tym artykule opisano sposób tworzenia wystąpienia <xref:System.TimeZoneInfo> obiektu z rejestru systemu lokalnego.

[Tworzenie wystąpień obiektów DateTimeOffset](../../../docs/standard/datetime/instantiating-a-datetimeoffset-object.md) w tym artykule omówiono sposób, w którym <xref:System.DateTimeOffset> można utworzyć wystąpienia obiektu i w ten sposób <xref:System.DateTime> można przekonwertować wartości na <xref:System.DateTimeOffset> wartość.

[Instrukcje: Tworzenie stref czasowych bez reguł korygowania](../../../docs/standard/datetime/create-time-zones-without-adjustment-rules.md) w tym artykule opisano sposób tworzenia niestandardowa strefa czasowa, która nie obsługuje przejścia do i z czasu letniego.

[Instrukcje: Tworzenie stref czasowych przy użyciu reguł korygowania](../../../docs/standard/datetime/create-time-zones-with-adjustment-rules.md) w tym artykule opisano sposób tworzenia niestandardowa strefa czasowa, który obsługuje co najmniej jeden przejścia do i z czasu letniego.

[Zapisywanie i przywracanie stref czasowych](../../../docs/standard/datetime/saving-and-restoring-time-zones.md) w tym artykule opisano <xref:System.TimeZoneInfo> pomoc techniczna dotycząca serializacji i deserializacji obiektu danych strefy czasowej i przedstawia niektóre scenariusze, w których można użyć tych funkcji.

[Instrukcje: Zapisywanie stref czasowych w zasobie osadzonym](../../../docs/standard/datetime/save-time-zones-to-an-embedded-resource.md) w tym artykule opisano sposób tworzenia niestandardowej strefy czasowej i zapisać jego informacji w pliku zasobów.

[Instrukcje: Przywracanie stref czasowych z zasobu osadzonego](../../../docs/standard/datetime/restore-time-zones-from-an-embedded-resource.md) opisano, jak utworzyć niestandardowe strefach czasowych, które zostały zapisane do pliku zasobów osadzonych.

[Wykonywanie operacji arytmetycznych na wartościach dat i godzin](../../../docs/standard/datetime/performing-arithmetic-operations.md) omówiono problemy, które są zaangażowane w Dodawanie, odejmowanie i porównywanie <xref:System.DateTime> i <xref:System.DateTimeOffset> wartości.

[Instrukcje: Używanie stref czasowych w arytmetyka daty i godziny](../../../docs/standard/datetime/use-time-zones-in-arithmetic.md) w tym artykule omówiono sposób wykonywania arytmetyka daty i godziny odzwierciedlającą reguł korygowania strefę czasową.

[Konwertowanie pomiędzy DateTime i DateTimeOffset](../../../docs/standard/datetime/converting-between-datetime-and-offset.md) w tym artykule opisano sposób konwertowania między <xref:System.DateTime> i <xref:System.DateTimeOffset> wartości.

[Konwertowanie godzin między strefami czasowymi](../../../docs/standard/datetime/converting-between-time-zones.md) opisuje Konwertowanie godzin między strefami czasowymi.

[Instrukcje: Rozwiązywanie niejednoznacznych wartości czasu](../../../docs/standard/datetime/resolve-ambiguous-times.md) opisuje sposób rozwiązywania niejednoznaczny czas przez mapowania ich na strefy czasowej (czas standardowy).

[Instrukcje: Zezwala użytkownikom na rozwiązywanie niejednoznacznych wartości czasu](../../../docs/standard/datetime/let-users-resolve-ambiguous-times.md) w tym artykule opisano sposób umożliwić użytkownikowi określić mapowanie między niejednoznaczny czas lokalny i uniwersalny czas koordynowany.

## <a name="reference"></a>Tematy pomocy

<xref:System.TimeZoneInfo?displayProperty=nameWithType>
