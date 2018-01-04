---
title: Daty, godziny i strefy czasowe
ms.custom: 
ms.date: 04/10/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- time zone objects [.NET Framework]
- date and time data [.NET Framework]
- time zones [.NET Framework]
- times [.NET Framework], time zones
- time [.NET Framework], time zones
ms.assetid: 295c16e0-641b-4771-94b3-39c1ffa98c13
caps.latest.revision: "22"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 47681f129c428cdae2be5e493fc6ac31719cab28
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/23/2017
---
# <a name="dates-times-and-time-zones"></a>Daty, godziny i strefy czasowe

Oprócz podstawowych <xref:System.DateTime> struktury .NET zapewnia następujące klasy obsługujące pracy ze strefami czasowymi:

* <xref:System.TimeZone>

  Klasa używana do pracy z systemu lokalnej strefie czasowej i strefy uniwersalny czas koordynowany (UTC). Funkcje <xref:System.TimeZone> klasy przede wszystkim zostało zastąpione przez <xref:System.TimeZoneInfo> klasy.

* <xref:System.TimeZoneInfo>

  Klasa używana do pracy z dowolnego strefy czasowej, który jest wstępnie zdefiniowane w systemie, tworzenie nowych stref czasowych i łatwo konwertowania dat i godzin między strefami czasowymi do innego. Do tworzenia nowej aplikacji, użyj <xref:System.TimeZoneInfo> klasy zamiast <xref:System.TimeZone> klasy.

* <xref:System.DateTimeOffset>

  Ta struktura jest używana do pracy z dat i godzin którego przesunięcie (lub różnica) od czasu UTC jest znany. <xref:System.DateTimeOffset> Struktury łączy datę i godzinę z tego czasu przesunięcie od czasu UTC. Ze względu na jego relacji do UTC, daty i godziny wartość jednoznacznie identyfikuje pojedynczy punkt w czasie. Dzięki temu <xref:System.DateTimeOffset> przenośną z jednego komputera na inny niż wartość <xref:System.DateTime> wartość.

Ta sekcja dokumentacji zawiera informacje potrzebne do pracy z stref czasowych i do tworzenia aplikacji obsługujących strefę czasową można przekonwertować daty i godziny między strefami czasowymi do innego.

## <a name="in-this-section"></a>W tej sekcji

[Przegląd stref czasowych](../../../docs/standard/datetime/time-zone-overview.md) omówiono terminologii, pojęcia i problemy związane z tworzeniem aplikacji obsługujących strefę czasową.

[Wybieranie pomiędzy DateTime, DateTimeOffset, TimeSpan i TimeZoneInfo](../../../docs/standard/datetime/choosing-between-datetime.md) omówiono, kiedy należy używać <xref:System.DateTime>, <xref:System.DateTimeOffset>, i <xref:System.TimeZoneInfo> typy podczas pracy z danych daty i godziny.

[Znajdowanie stref czasowych zdefiniowanych w systemie lokalnym](../../../docs/standard/datetime/finding-the-time-zones-on-local-system.md) opisuje sposób wykazywanie stref czasowych znaleziono w systemie lokalnym.

[Porady: wykazywanie stref czasowych na komputerze](../../../docs/standard/datetime/enumerate-time-zones.md) przykłady, które wyliczanie stref czasowych zdefiniowanych w rejestrze komputera i który użytkownicy wybiorą z listy wstępnie zdefiniowanych strefy czasowej.

[Porady: uzyskiwanie dostępu do wstępnie zdefiniowanych obiektów stref UTC i czasem lokalnym](../../../docs/standard/datetime/access-utc-and-local.md) opisano, jak uzyskać dostęp do uniwersalnego czasu koordynowanego i w lokalnej strefie czasowej.

[Porady: Tworzenie wystąpień obiektów TimeZoneInfo](../../../docs/standard/datetime/instantiate-time-zone-info.md) zawiera opis sposobu tworzenia wystąpienia <xref:System.TimeZoneInfo> obiektu z rejestru systemu lokalnego.

[Tworzenie wystąpień obiektów DateTimeOffset](../../../docs/standard/datetime/instantiating-a-datetimeoffset-object.md) omówiono sposoby, w którym <xref:System.DateTimeOffset> można utworzyć wystąpienia obiektu oraz sposobów, w którym <xref:System.DateTime> można przekonwertować wartości <xref:System.DateTimeOffset> wartość.

[Porady: tworzenie stref czasowych bez reguł korygowania](../../../docs/standard/datetime/create-time-zones-without-adjustment-rules.md) opisuje sposób tworzenia niestandardowych strefy czasowej, która nie obsługuje przejścia do i z czasu letniego.

[Porady: tworzenie stref czasowych przy użyciu reguł korygowania](../../../docs/standard/datetime/create-time-zones-with-adjustment-rules.md) opisuje sposób tworzenia niestandardowych strefy czasowej, który obsługuje co najmniej jednego przejścia do i z czasu letniego.

[Zapisywanie i przywracanie stref czasowych](../../../docs/standard/datetime/saving-and-restoring-time-zones.md) w tym artykule opisano <xref:System.TimeZoneInfo> obsługuje do serializacji i deserializacji strefa czasowa danych i przedstawiono niektóre scenariusze, w których można użyć tych funkcji.

[Porady: zapisywanie stref czasowych w zasobie osadzonym](../../../docs/standard/datetime/save-time-zones-to-an-embedded-resource.md) w tym artykule opisano sposób tworzenia niestandardowych strefę czasową i Zapisz informacje w pliku zasobu.

[Porady: Przywracanie stref czasowych z zasobu osadzonego](../../../docs/standard/datetime/restore-time-zones-from-an-embedded-resource.md) zawiera opis sposobu tworzenia wystąpienia niestandardowych stref czasowych, które zostały zapisane do pliku zasobu osadzonego.

[Wykonywanie operacji arytmetycznych na daty i godziny](../../../docs/standard/datetime/performing-arithmetic-operations.md) w tym artykule omówiono zagadnienia związane z dodanie, usunięcie i porównywanie <xref:System.DateTime> i <xref:System.DateTimeOffset> wartości.

[Porady: użycie stref czasowych w arytmetyczne daty i czasu](../../../docs/standard/datetime/use-time-zones-in-arithmetic.md) omówiono sposób wykonywania arytmetyczne daty i czasu odzwierciedlający reguł korygowania strefę czasową.

[Konwertowanie pomiędzy DateTime i DateTimeOffset](../../../docs/standard/datetime/converting-between-datetime-and-offset.md) zawiera opis sposobu konwersji między <xref:System.DateTime> i <xref:System.DateTimeOffset> wartości.

[Konwertowanie godzin między strefami czasowymi](../../../docs/standard/datetime/converting-between-time-zones.md) opisano sposób przekonwertować godzin między strefami czasowymi.

[Porady: Rozwiązywanie niejednoznacznych wartości czasu](../../../docs/standard/datetime/resolve-ambiguous-times.md) opisuje sposób rozwiązania niejednoznaczny czas przez mapowanie go na strefie czasowej (czas standardowy).

[Porady: zezwala użytkownikom na rozwiązywanie niejednoznacznych wartości czasu](../../../docs/standard/datetime/let-users-resolve-ambiguous-times.md) opisano sposób umożliwić użytkownikowi określić mapowanie między niejednoznaczny czas lokalny i uniwersalny czas koordynowany.

## <a name="reference"></a>Tematy pomocy

<xref:System.TimeZoneInfo?displayProperty=nameWithType>
