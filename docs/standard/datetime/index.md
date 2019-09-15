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
# <a name="dates-times-and-time-zones"></a><span data-ttu-id="f0f92-102">Daty, godziny i strefy czasowe</span><span class="sxs-lookup"><span data-stu-id="f0f92-102">Dates, times, and time zones</span></span>

<span data-ttu-id="f0f92-103">Oprócz podstawowej <xref:System.DateTime> struktury platforma .NET udostępnia następujące klasy, które obsługują pracę z strefami czasowymi:</span><span class="sxs-lookup"><span data-stu-id="f0f92-103">In addition to the basic <xref:System.DateTime> structure, .NET provides the following classes that support working with time zones:</span></span>

* <xref:System.TimeZone>

  <span data-ttu-id="f0f92-104">Użyj tej klasy, aby współdziałać z lokalną strefą czasową systemu i strefą czasu koordynowanego (UTC).</span><span class="sxs-lookup"><span data-stu-id="f0f92-104">Use this class to work with the system's local time zone and the Coordinated Universal Time (UTC) zone.</span></span> <span data-ttu-id="f0f92-105">Funkcjonalność <xref:System.TimeZone> klasy jest w dużym stopniu zastępowana <xref:System.TimeZoneInfo> przez klasę.</span><span class="sxs-lookup"><span data-stu-id="f0f92-105">The functionality of the <xref:System.TimeZone> class is largely superseded by the <xref:System.TimeZoneInfo> class.</span></span>

* <xref:System.TimeZoneInfo>

  <span data-ttu-id="f0f92-106">Ta klasa służy do pracy ze wszystkimi strefami czasowymi wstępnie zdefiniowanymi w systemie w celu tworzenia nowych stref czasowych oraz do łatwego konwertowania dat i godzin z jednej strefy czasowej na inną.</span><span class="sxs-lookup"><span data-stu-id="f0f92-106">Use this class to work with any time zone that is predefined on a system, to create new time zones, and to easily convert dates and times from one time zone to another.</span></span> <span data-ttu-id="f0f92-107">W przypadku nowych rozwiązań należy użyć <xref:System.TimeZoneInfo> klasy zamiast <xref:System.TimeZone> klasy.</span><span class="sxs-lookup"><span data-stu-id="f0f92-107">For new development, use the <xref:System.TimeZoneInfo> class instead of the <xref:System.TimeZone> class.</span></span>

* <xref:System.DateTimeOffset>

  <span data-ttu-id="f0f92-108">Ta struktura służy do pracy z datami i godzinami, których przesunięcie (lub różnica) od czasu UTC jest znane.</span><span class="sxs-lookup"><span data-stu-id="f0f92-108">Use this structure to work with dates and times whose offset (or difference) from UTC is known.</span></span> <span data-ttu-id="f0f92-109"><xref:System.DateTimeOffset> Struktura łączy wartość daty i godziny z przesunięciem czasu UTC.</span><span class="sxs-lookup"><span data-stu-id="f0f92-109">The <xref:System.DateTimeOffset> structure combines a date and time value with that time's offset from UTC.</span></span> <span data-ttu-id="f0f92-110">Ze względu na jego relację z czasem UTC, indywidualna wartość daty i godziny jednoznacznie identyfikuje pojedynczy punkt w czasie.</span><span class="sxs-lookup"><span data-stu-id="f0f92-110">Because of its relationship to UTC, an individual date and time value unambiguously identifies a single point in time.</span></span> <span data-ttu-id="f0f92-111">Dzięki temu wartość <xref:System.DateTimeOffset> jest bardziej przenośna z jednego komputera na inny <xref:System.DateTime> niż wartość.</span><span class="sxs-lookup"><span data-stu-id="f0f92-111">This makes a <xref:System.DateTimeOffset> value more portable from one computer to another than a <xref:System.DateTime> value.</span></span>

<span data-ttu-id="f0f92-112">Ta sekcja dokumentacji zawiera informacje potrzebne do pracy z strefami czasowymi oraz do tworzenia aplikacji obsługujących strefy czasowe, które mogą konwertować daty i godziny z jednej strefy czasowej na inną.</span><span class="sxs-lookup"><span data-stu-id="f0f92-112">This section of the documentation provides the information that you need to work with time zones and to create time zone-aware applications that can convert dates and times from one time zone to another.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="f0f92-113">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="f0f92-113">In this section</span></span>

<span data-ttu-id="f0f92-114">[Przegląd strefy czasowej](../../../docs/standard/datetime/time-zone-overview.md) W tym artykule omówiono terminologię, koncepcje i problemy związane z tworzeniem aplikacji obsługujących strefy czasowe.</span><span class="sxs-lookup"><span data-stu-id="f0f92-114">[Time zone overview](../../../docs/standard/datetime/time-zone-overview.md) Discusses the terminology, concepts, and issues involved in creating time zone-aware applications.</span></span>

<span data-ttu-id="f0f92-115">[Wybieranie między elementami DateTime, DateTimeOffset, TimeSpan i TimeZoneInfo](../../../docs/standard/datetime/choosing-between-datetime.md) W tym artykule omówiono <xref:System.DateTime>, kiedy należy używać typów, <xref:System.DateTimeOffset>i <xref:System.TimeZoneInfo> podczas pracy z danymi daty i godziny.</span><span class="sxs-lookup"><span data-stu-id="f0f92-115">[Choosing between DateTime, DateTimeOffset, TimeSpan, and TimeZoneInfo](../../../docs/standard/datetime/choosing-between-datetime.md) Discusses when to use the <xref:System.DateTime>, <xref:System.DateTimeOffset>, and <xref:System.TimeZoneInfo> types when working with date and time data.</span></span>

<span data-ttu-id="f0f92-116">[Znajdowanie stref czasowych zdefiniowanych w systemie lokalnym](../../../docs/standard/datetime/finding-the-time-zones-on-local-system.md) Opisuje sposób wyliczania stref czasowych znalezionych w systemie lokalnym.</span><span class="sxs-lookup"><span data-stu-id="f0f92-116">[Finding the time zones defined on a local system](../../../docs/standard/datetime/finding-the-time-zones-on-local-system.md) Describes how to enumerate the time zones found on a local system.</span></span>

<span data-ttu-id="f0f92-117">[Instrukcje: Wyliczenie strefy czasowe obecne na komputerze](../../../docs/standard/datetime/enumerate-time-zones.md) zawiera przykłady, które wyliczają strefy czasowe zdefiniowane w rejestrze komputera i umożliwiają użytkownikom wybranie wstępnie zdefiniowanej strefy czasowej z listy.</span><span class="sxs-lookup"><span data-stu-id="f0f92-117">[How to: Enumerate time zones present on a computer](../../../docs/standard/datetime/enumerate-time-zones.md) Provides examples that enumerate the time zones defined in a computer's registry and that let users select a predefined time zone from a list.</span></span>

<span data-ttu-id="f0f92-118">[Instrukcje: Dostęp do wstępnie zdefiniowanych obiektów](../../../docs/standard/datetime/access-utc-and-local.md) czasu UTC i lokalnej strefy czasowej opisuje sposób dostępu do uniwersalnego czasu koordynowanego i lokalnej strefy czasowej.</span><span class="sxs-lookup"><span data-stu-id="f0f92-118">[How to: Access the predefined UTC and local time zone objects](../../../docs/standard/datetime/access-utc-and-local.md) Describes how to access Coordinated Universal Time and the local time zone.</span></span>

<span data-ttu-id="f0f92-119">[Instrukcje: Utworzenie wystąpienia obiektu](../../../docs/standard/datetime/instantiate-time-zone-info.md) TimeZoneInfo opisuje sposób tworzenia <xref:System.TimeZoneInfo> wystąpienia obiektu z rejestru systemu lokalnego.</span><span class="sxs-lookup"><span data-stu-id="f0f92-119">[How to: Instantiate a TimeZoneInfo object](../../../docs/standard/datetime/instantiate-time-zone-info.md) Describes how to instantiate a <xref:System.TimeZoneInfo> object from the local system registry.</span></span>

<span data-ttu-id="f0f92-120">[Tworzenie wystąpienia obiektu DateTimeOffset](../../../docs/standard/datetime/instantiating-a-datetimeoffset-object.md) Omówienie sposobów, w których <xref:System.DateTimeOffset> można utworzyć wystąpienie obiektu, oraz sposobów, w <xref:System.DateTime> których wartość <xref:System.DateTimeOffset> może zostać przekonwertowana na wartość.</span><span class="sxs-lookup"><span data-stu-id="f0f92-120">[Instantiating a DateTimeOffset object](../../../docs/standard/datetime/instantiating-a-datetimeoffset-object.md) Discusses the ways in which a <xref:System.DateTimeOffset> object can be instantiated, and the ways in which a <xref:System.DateTime> value can be converted to a <xref:System.DateTimeOffset> value.</span></span>

<span data-ttu-id="f0f92-121">[Instrukcje: Tworzenie stref czasowych bez reguł](../../../docs/standard/datetime/create-time-zones-without-adjustment-rules.md) korygowania opisuje sposób tworzenia niestandardowej strefy czasowej, która nie obsługuje przejścia do i z czasu letniego.</span><span class="sxs-lookup"><span data-stu-id="f0f92-121">[How to: Create time zones without adjustment rules](../../../docs/standard/datetime/create-time-zones-without-adjustment-rules.md) Describes how to create a custom time zone that does not support the transition to and from daylight saving time.</span></span>

<span data-ttu-id="f0f92-122">[Instrukcje: Tworzenie stref czasowych przy użyciu](../../../docs/standard/datetime/create-time-zones-with-adjustment-rules.md) reguł korygowania opisuje sposób tworzenia niestandardowej strefy czasowej, która obsługuje jedno lub więcej przejść do i z czasu letniego.</span><span class="sxs-lookup"><span data-stu-id="f0f92-122">[How to: Create time zones with adjustment rules](../../../docs/standard/datetime/create-time-zones-with-adjustment-rules.md) Describes how to create a custom time zone that supports one or more transitions to and from daylight saving time.</span></span>

<span data-ttu-id="f0f92-123">[Zapisywanie i przywracanie stref czasowych](../../../docs/standard/datetime/saving-and-restoring-time-zones.md) Opisuje <xref:System.TimeZoneInfo> obsługę serializacji i deserializacji danych strefy czasowej oraz przedstawia niektóre scenariusze, w których można używać tych funkcji.</span><span class="sxs-lookup"><span data-stu-id="f0f92-123">[Saving and restoring time zones](../../../docs/standard/datetime/saving-and-restoring-time-zones.md) Describes <xref:System.TimeZoneInfo> support for serialization and deserialization of time zone data and illustrates some of the scenarios in which these features can be used.</span></span>

<span data-ttu-id="f0f92-124">[Instrukcje: Zapisywanie stref czasowych w osadzonym](../../../docs/standard/datetime/save-time-zones-to-an-embedded-resource.md) zasobie opisuje sposób tworzenia niestandardowej strefy czasowej i zapisywania jej informacji w pliku zasobów.</span><span class="sxs-lookup"><span data-stu-id="f0f92-124">[How to: Save time zones to an embedded resource](../../../docs/standard/datetime/save-time-zones-to-an-embedded-resource.md) Describes how to create a custom time zone and save its information in a resource file.</span></span>

<span data-ttu-id="f0f92-125">[Instrukcje: Przywróć strefy czasowe z osadzonego](../../../docs/standard/datetime/restore-time-zones-from-an-embedded-resource.md) zasobu opisują sposób tworzenia niestandardowych stref czasowych, które zostały zapisane w osadzonym pliku zasobów.</span><span class="sxs-lookup"><span data-stu-id="f0f92-125">[How to: Restore time zones from an embedded resource](../../../docs/standard/datetime/restore-time-zones-from-an-embedded-resource.md) Describes how to instantiate custom time zones that have been saved to an embedded resource file.</span></span>

<span data-ttu-id="f0f92-126">[Wykonywanie operacji arytmetycznych z datami i godzinami](../../../docs/standard/datetime/performing-arithmetic-operations.md) W tym artykule omówiono problemy związane z dodawaniem, odejmowaniem <xref:System.DateTime> i <xref:System.DateTimeOffset> porównywaniem oraz wartościami.</span><span class="sxs-lookup"><span data-stu-id="f0f92-126">[Performing arithmetic operations with dates and times](../../../docs/standard/datetime/performing-arithmetic-operations.md) Discusses the issues involved in adding, subtracting, and comparing <xref:System.DateTime> and <xref:System.DateTimeOffset> values.</span></span>

<span data-ttu-id="f0f92-127">[Instrukcje: Użycie stref czasowych w operacji arytmetycznych](../../../docs/standard/datetime/use-time-zones-in-arithmetic.md) daty i godziny omawia sposób wykonywania operacji arytmetycznych daty i czasu, która odzwierciedla reguły dostosowania strefy czasowej.</span><span class="sxs-lookup"><span data-stu-id="f0f92-127">[How to: Use time zones in date and time arithmetic](../../../docs/standard/datetime/use-time-zones-in-arithmetic.md) Discusses how to perform date and time arithmetic that reflects a time zone's adjustment rules.</span></span>

<span data-ttu-id="f0f92-128">[Konwertowanie między elementami DateTime i DateTimeOffset](../../../docs/standard/datetime/converting-between-datetime-and-offset.md) Opisuje sposób konwersji <xref:System.DateTime> wartości i <xref:System.DateTimeOffset> .</span><span class="sxs-lookup"><span data-stu-id="f0f92-128">[Converting between DateTime and DateTimeOffset](../../../docs/standard/datetime/converting-between-datetime-and-offset.md) Describes how to convert between <xref:System.DateTime> and <xref:System.DateTimeOffset> values.</span></span>

<span data-ttu-id="f0f92-129">[Konwertowanie czasów między strefami czasowymi](../../../docs/standard/datetime/converting-between-time-zones.md) Opisuje sposób konwersji czasów z jednej strefy czasowej na inną.</span><span class="sxs-lookup"><span data-stu-id="f0f92-129">[Converting times between time zones](../../../docs/standard/datetime/converting-between-time-zones.md) Describes how to convert times from one time zone to another.</span></span>

<span data-ttu-id="f0f92-130">[Instrukcje: Rozpoznaj niejednoznaczny czas, aby określić, jak rozpoznać niejednoznaczne czasy](../../../docs/standard/datetime/resolve-ambiguous-times.md) , mapując go do czasu standardowego strefy czasowej.</span><span class="sxs-lookup"><span data-stu-id="f0f92-130">[How to: Resolve ambiguous times](../../../docs/standard/datetime/resolve-ambiguous-times.md) Describes how to resolve an ambiguous time by mapping it to the time zone's standard time.</span></span>

<span data-ttu-id="f0f92-131">[Instrukcje: Pozwól użytkownikom na rozwiązywanie](../../../docs/standard/datetime/let-users-resolve-ambiguous-times.md) niejednoznacznych czasów, w jaki sposób można określić mapowanie między niejednoznacznym czasem lokalnym i uniwersalnym koordynowanym czasem.</span><span class="sxs-lookup"><span data-stu-id="f0f92-131">[How to: Let users resolve ambiguous times](../../../docs/standard/datetime/let-users-resolve-ambiguous-times.md) Describes how to let a user determine the mapping between an ambiguous local time and Coordinated Universal Time.</span></span>

## <a name="reference"></a><span data-ttu-id="f0f92-132">Tematy pomocy</span><span class="sxs-lookup"><span data-stu-id="f0f92-132">Reference</span></span>

<xref:System.TimeZoneInfo?displayProperty=nameWithType>
