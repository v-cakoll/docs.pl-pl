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
# <a name="dates-times-and-time-zones"></a><span data-ttu-id="d0f8a-102">Daty, godziny i strefy czasowe</span><span class="sxs-lookup"><span data-stu-id="d0f8a-102">Dates, times, and time zones</span></span>

<span data-ttu-id="d0f8a-103">Oprócz podstawowego <xref:System.DateTime> struktury .NET zawiera następujące klasy obsługujące pracy ze strefami czasowymi:</span><span class="sxs-lookup"><span data-stu-id="d0f8a-103">In addition to the basic <xref:System.DateTime> structure, .NET provides the following classes that support working with time zones:</span></span>

* <xref:System.TimeZone>

  <span data-ttu-id="d0f8a-104">Klasa jest używana do pracy z systemu w lokalnej strefie czasowej i strefy uniwersalnego czasu koordynowanego (UTC). Funkcje <xref:System.TimeZone> klasy stopniu zostało zastąpione przez <xref:System.TimeZoneInfo> klasy.</span><span class="sxs-lookup"><span data-stu-id="d0f8a-104">Use this class to work with the system's local time zone and the Coordinated Universal Time (UTC) zone.The functionality of the <xref:System.TimeZone> class is largely superseded by the <xref:System.TimeZoneInfo> class.</span></span>

* <xref:System.TimeZoneInfo>

  <span data-ttu-id="d0f8a-105">Klasa jest używana do pracy z dowolnym strefę czasową, która jest wstępnie zdefiniowane w systemie, tworzenie nowych stref czasowych i prosty sposób konwertowania daty i godziny w jednej strefie czasowej na inny.</span><span class="sxs-lookup"><span data-stu-id="d0f8a-105">Use this class to work with any time zone that is predefined on a system, to create new time zones, and to easily convert dates and times from one time zone to another.</span></span> <span data-ttu-id="d0f8a-106">W nowych wdrożeniach należy używać <xref:System.TimeZoneInfo> klasy zamiast <xref:System.TimeZone> klasy.</span><span class="sxs-lookup"><span data-stu-id="d0f8a-106">For new development, use the <xref:System.TimeZoneInfo> class instead of the <xref:System.TimeZone> class.</span></span>

* <xref:System.DateTimeOffset>

  <span data-ttu-id="d0f8a-107">Ta struktura jest używana do pracy z datami i czasy którego przesunięcie (lub różnicy) z czasu UTC jest znany.</span><span class="sxs-lookup"><span data-stu-id="d0f8a-107">Use this structure to work with dates and times whose offset (or difference) from UTC is known.</span></span> <span data-ttu-id="d0f8a-108"><xref:System.DateTimeOffset> Struktury łączy daty i wartości godziny z tego czasu przesunięcie względem czasu UTC.</span><span class="sxs-lookup"><span data-stu-id="d0f8a-108">The <xref:System.DateTimeOffset> structure combines a date and time value with that time's offset from UTC.</span></span> <span data-ttu-id="d0f8a-109">Ze względu na jego relację z czasu UTC, daty i godziny wartość jednoznacznie identyfikuje pojedynczy punkt w czasie.</span><span class="sxs-lookup"><span data-stu-id="d0f8a-109">Because of its relationship to UTC, an individual date and time value unambiguously identifies a single point in time.</span></span> <span data-ttu-id="d0f8a-110">To sprawia, że <xref:System.DateTimeOffset> bardziej przenośny z jednego komputera na inny niż wartość <xref:System.DateTime> wartość.</span><span class="sxs-lookup"><span data-stu-id="d0f8a-110">This makes a <xref:System.DateTimeOffset> value more portable from one computer to another than a <xref:System.DateTime> value.</span></span>

<span data-ttu-id="d0f8a-111">Ta sekcja dokumentacji zawiera informacje potrzebne do pracy ze strefami czasowymi i tworzenie aplikacji uwzględniających strefy czasowe, które można przekonwertować daty i godziny w jednej strefie czasowej na inny.</span><span class="sxs-lookup"><span data-stu-id="d0f8a-111">This section of the documentation provides the information that you need to work with time zones and to create time zone-aware applications that can convert dates and times from one time zone to another.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="d0f8a-112">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="d0f8a-112">In this section</span></span>

<span data-ttu-id="d0f8a-113">[Przegląd stref czasowych](../../../docs/standard/datetime/time-zone-overview.md) w tym artykule omówiono terminologii, pojęcia i zagadnienia związane z tworzeniem aplikacji uwzględniających strefy czasowe.</span><span class="sxs-lookup"><span data-stu-id="d0f8a-113">[Time zone overview](../../../docs/standard/datetime/time-zone-overview.md) Discusses the terminology, concepts, and issues involved in creating time zone-aware applications.</span></span>

<span data-ttu-id="d0f8a-114">[Wybieranie pomiędzy DateTime, DateTimeOffset, TimeSpan i TimeZoneInfo](../../../docs/standard/datetime/choosing-between-datetime.md) omówiono, kiedy należy używać <xref:System.DateTime>, <xref:System.DateTimeOffset>, i <xref:System.TimeZoneInfo> typów podczas pracy z danymi daty i godziny.</span><span class="sxs-lookup"><span data-stu-id="d0f8a-114">[Choosing between DateTime, DateTimeOffset, TimeSpan, and TimeZoneInfo](../../../docs/standard/datetime/choosing-between-datetime.md) Discusses when to use the <xref:System.DateTime>, <xref:System.DateTimeOffset>, and <xref:System.TimeZoneInfo> types when working with date and time data.</span></span>

<span data-ttu-id="d0f8a-115">[Znajdowanie stref czasowych zdefiniowanych w systemie lokalnym](../../../docs/standard/datetime/finding-the-time-zones-on-local-system.md) opisano, jak wykazywanie stref czasowych znalezionych w systemie lokalnym.</span><span class="sxs-lookup"><span data-stu-id="d0f8a-115">[Finding the time zones defined on a local system](../../../docs/standard/datetime/finding-the-time-zones-on-local-system.md) Describes how to enumerate the time zones found on a local system.</span></span>

<span data-ttu-id="d0f8a-116">[Instrukcje: Wykazywanie stref czasowych na komputerze](../../../docs/standard/datetime/enumerate-time-zones.md) zawiera przykłady, wyliczanie stref czasowych zdefiniowanych w rejestrze komputera i że umożliwienie użytkownikom wyboru wstępnie zdefiniowane strefy czasowej z listy.</span><span class="sxs-lookup"><span data-stu-id="d0f8a-116">[How to: Enumerate time zones present on a computer](../../../docs/standard/datetime/enumerate-time-zones.md) Provides examples that enumerate the time zones defined in a computer's registry and that let users select a predefined time zone from a list.</span></span>

<span data-ttu-id="d0f8a-117">[Instrukcje: Uzyskiwanie dostępu do wstępnie zdefiniowanych obiektów stref UTC i czasem lokalnym](../../../docs/standard/datetime/access-utc-and-local.md) opisano, jak uzyskać dostęp do uniwersalny czas koordynowany i lokalnej strefy czasowej.</span><span class="sxs-lookup"><span data-stu-id="d0f8a-117">[How to: Access the predefined UTC and local time zone objects](../../../docs/standard/datetime/access-utc-and-local.md) Describes how to access Coordinated Universal Time and the local time zone.</span></span>

<span data-ttu-id="d0f8a-118">[Instrukcje: Tworzenie wystąpień obiektów TimeZoneInfo](../../../docs/standard/datetime/instantiate-time-zone-info.md) w tym artykule opisano sposób tworzenia wystąpienia <xref:System.TimeZoneInfo> obiektu z rejestru systemu lokalnego.</span><span class="sxs-lookup"><span data-stu-id="d0f8a-118">[How to: Instantiate a TimeZoneInfo object](../../../docs/standard/datetime/instantiate-time-zone-info.md) Describes how to instantiate a <xref:System.TimeZoneInfo> object from the local system registry.</span></span>

<span data-ttu-id="d0f8a-119">[Tworzenie wystąpień obiektów DateTimeOffset](../../../docs/standard/datetime/instantiating-a-datetimeoffset-object.md) w tym artykule omówiono sposób, w którym <xref:System.DateTimeOffset> można utworzyć wystąpienia obiektu i w ten sposób <xref:System.DateTime> można przekonwertować wartości na <xref:System.DateTimeOffset> wartość.</span><span class="sxs-lookup"><span data-stu-id="d0f8a-119">[Instantiating a DateTimeOffset object](../../../docs/standard/datetime/instantiating-a-datetimeoffset-object.md) Discusses the ways in which a <xref:System.DateTimeOffset> object can be instantiated, and the ways in which a <xref:System.DateTime> value can be converted to a <xref:System.DateTimeOffset> value.</span></span>

<span data-ttu-id="d0f8a-120">[Instrukcje: Tworzenie stref czasowych bez reguł korygowania](../../../docs/standard/datetime/create-time-zones-without-adjustment-rules.md) w tym artykule opisano sposób tworzenia niestandardowa strefa czasowa, która nie obsługuje przejścia do i z czasu letniego.</span><span class="sxs-lookup"><span data-stu-id="d0f8a-120">[How to: Create time zones without adjustment rules](../../../docs/standard/datetime/create-time-zones-without-adjustment-rules.md) Describes how to create a custom time zone that does not support the transition to and from daylight saving time.</span></span>

<span data-ttu-id="d0f8a-121">[Instrukcje: Tworzenie stref czasowych przy użyciu reguł korygowania](../../../docs/standard/datetime/create-time-zones-with-adjustment-rules.md) w tym artykule opisano sposób tworzenia niestandardowa strefa czasowa, który obsługuje co najmniej jeden przejścia do i z czasu letniego.</span><span class="sxs-lookup"><span data-stu-id="d0f8a-121">[How to: Create time zones with adjustment rules](../../../docs/standard/datetime/create-time-zones-with-adjustment-rules.md) Describes how to create a custom time zone that supports one or more transitions to and from daylight saving time.</span></span>

<span data-ttu-id="d0f8a-122">[Zapisywanie i przywracanie stref czasowych](../../../docs/standard/datetime/saving-and-restoring-time-zones.md) w tym artykule opisano <xref:System.TimeZoneInfo> pomoc techniczna dotycząca serializacji i deserializacji obiektu danych strefy czasowej i przedstawia niektóre scenariusze, w których można użyć tych funkcji.</span><span class="sxs-lookup"><span data-stu-id="d0f8a-122">[Saving and restoring time zones](../../../docs/standard/datetime/saving-and-restoring-time-zones.md) Describes <xref:System.TimeZoneInfo> support for serialization and deserialization of time zone data and illustrates some of the scenarios in which these features can be used.</span></span>

<span data-ttu-id="d0f8a-123">[Instrukcje: Zapisywanie stref czasowych w zasobie osadzonym](../../../docs/standard/datetime/save-time-zones-to-an-embedded-resource.md) w tym artykule opisano sposób tworzenia niestandardowej strefy czasowej i zapisać jego informacji w pliku zasobów.</span><span class="sxs-lookup"><span data-stu-id="d0f8a-123">[How to: Save time zones to an embedded resource](../../../docs/standard/datetime/save-time-zones-to-an-embedded-resource.md) Describes how to create a custom time zone and save its information in a resource file.</span></span>

<span data-ttu-id="d0f8a-124">[Instrukcje: Przywracanie stref czasowych z zasobu osadzonego](../../../docs/standard/datetime/restore-time-zones-from-an-embedded-resource.md) opisano, jak utworzyć niestandardowe strefach czasowych, które zostały zapisane do pliku zasobów osadzonych.</span><span class="sxs-lookup"><span data-stu-id="d0f8a-124">[How to: Restore time zones from an embedded resource](../../../docs/standard/datetime/restore-time-zones-from-an-embedded-resource.md) Describes how to instantiate custom time zones that have been saved to an embedded resource file.</span></span>

<span data-ttu-id="d0f8a-125">[Wykonywanie operacji arytmetycznych na wartościach dat i godzin](../../../docs/standard/datetime/performing-arithmetic-operations.md) omówiono problemy, które są zaangażowane w Dodawanie, odejmowanie i porównywanie <xref:System.DateTime> i <xref:System.DateTimeOffset> wartości.</span><span class="sxs-lookup"><span data-stu-id="d0f8a-125">[Performing arithmetic operations with dates and times](../../../docs/standard/datetime/performing-arithmetic-operations.md) Discusses the issues involved in adding, subtracting, and comparing <xref:System.DateTime> and <xref:System.DateTimeOffset> values.</span></span>

<span data-ttu-id="d0f8a-126">[Instrukcje: Używanie stref czasowych w arytmetyka daty i godziny](../../../docs/standard/datetime/use-time-zones-in-arithmetic.md) w tym artykule omówiono sposób wykonywania arytmetyka daty i godziny odzwierciedlającą reguł korygowania strefę czasową.</span><span class="sxs-lookup"><span data-stu-id="d0f8a-126">[How to: Use time zones in date and time arithmetic](../../../docs/standard/datetime/use-time-zones-in-arithmetic.md) Discusses how to perform date and time arithmetic that reflects a time zone's adjustment rules.</span></span>

<span data-ttu-id="d0f8a-127">[Konwertowanie pomiędzy DateTime i DateTimeOffset](../../../docs/standard/datetime/converting-between-datetime-and-offset.md) w tym artykule opisano sposób konwertowania między <xref:System.DateTime> i <xref:System.DateTimeOffset> wartości.</span><span class="sxs-lookup"><span data-stu-id="d0f8a-127">[Converting between DateTime and DateTimeOffset](../../../docs/standard/datetime/converting-between-datetime-and-offset.md) Describes how to convert between <xref:System.DateTime> and <xref:System.DateTimeOffset> values.</span></span>

<span data-ttu-id="d0f8a-128">[Konwertowanie godzin między strefami czasowymi](../../../docs/standard/datetime/converting-between-time-zones.md) opisuje Konwertowanie godzin między strefami czasowymi.</span><span class="sxs-lookup"><span data-stu-id="d0f8a-128">[Converting times between time zones](../../../docs/standard/datetime/converting-between-time-zones.md) Describes how to convert times from one time zone to another.</span></span>

<span data-ttu-id="d0f8a-129">[Instrukcje: Rozwiązywanie niejednoznacznych wartości czasu](../../../docs/standard/datetime/resolve-ambiguous-times.md) opisuje sposób rozwiązywania niejednoznaczny czas przez mapowania ich na strefy czasowej (czas standardowy).</span><span class="sxs-lookup"><span data-stu-id="d0f8a-129">[How to: Resolve ambiguous times](../../../docs/standard/datetime/resolve-ambiguous-times.md) Describes how to resolve an ambiguous time by mapping it to the time zone's standard time.</span></span>

<span data-ttu-id="d0f8a-130">[Instrukcje: Zezwala użytkownikom na rozwiązywanie niejednoznacznych wartości czasu](../../../docs/standard/datetime/let-users-resolve-ambiguous-times.md) w tym artykule opisano sposób umożliwić użytkownikowi określić mapowanie między niejednoznaczny czas lokalny i uniwersalny czas koordynowany.</span><span class="sxs-lookup"><span data-stu-id="d0f8a-130">[How to: Let users resolve ambiguous times](../../../docs/standard/datetime/let-users-resolve-ambiguous-times.md) Describes how to let a user determine the mapping between an ambiguous local time and Coordinated Universal Time.</span></span>

## <a name="reference"></a><span data-ttu-id="d0f8a-131">Tematy pomocy</span><span class="sxs-lookup"><span data-stu-id="d0f8a-131">Reference</span></span>

<xref:System.TimeZoneInfo?displayProperty=nameWithType>
