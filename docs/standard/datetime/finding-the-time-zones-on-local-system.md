---
title: Znajdowanie stref czasowych zdefiniowanych w systemie lokalnym
ms.custom: 
ms.date: 04/10/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- time zones [.NET Framework], local
- time zones [.NET Framework], finding local system time zones
- time zone identifiers [.NET Framework]
- local time zone access
- time zones [.NET Framework], retrieving
- UTC times, finding local system time zones
- time zones [.NET Framework], UTC
ms.assetid: 3f63b1bc-9a4b-4bde-84ea-ab028a80d3e1
caps.latest.revision: "14"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: e61f05741c1edd86d9baad4f6ebc9f4e91318250
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/23/2017
---
# <a name="finding-the-time-zones-defined-on-a-local-system"></a><span data-ttu-id="f2ffc-102">Znajdowanie stref czasowych zdefiniowanych w systemie lokalnym</span><span class="sxs-lookup"><span data-stu-id="f2ffc-102">Finding the time zones defined on a local system</span></span>

<span data-ttu-id="f2ffc-103"><xref:System.TimeZoneInfo> Klasa nie ujawnia konstruktora publicznego.</span><span class="sxs-lookup"><span data-stu-id="f2ffc-103">The <xref:System.TimeZoneInfo> class does not expose a public constructor.</span></span> <span data-ttu-id="f2ffc-104">W związku z tym `new` — słowo kluczowe nie może służyć do tworzenia nowego <xref:System.TimeZoneInfo> obiektu.</span><span class="sxs-lookup"><span data-stu-id="f2ffc-104">As a result, the `new` keyword cannot be used to create a new <xref:System.TimeZoneInfo> object.</span></span> <span data-ttu-id="f2ffc-105">Zamiast tego <xref:System.TimeZoneInfo> są one tworzone przez pobranie informacji o wstępnie zdefiniowane strefy czasowe z rejestru lub przez tworzenie niestandardowych strefy czasowej.</span><span class="sxs-lookup"><span data-stu-id="f2ffc-105">Instead, <xref:System.TimeZoneInfo> objects are instantiated either by retrieving information on predefined time zones from the registry or by creating a custom time zone.</span></span> <span data-ttu-id="f2ffc-106">W tym temacie omówiono tworzenie wystąpień strefy czasowej z danych przechowywanych w rejestrze.</span><span class="sxs-lookup"><span data-stu-id="f2ffc-106">This topic discusses instantiating a time zone from data stored in the registry.</span></span> <span data-ttu-id="f2ffc-107">Ponadto `static` (`shared` w języku Visual Basic) właściwości <xref:System.TimeZoneInfo> klasy zapewnianie dostępu do uniwersalnego czasu koordynowanego (UTC) i w lokalnej strefie czasowej.</span><span class="sxs-lookup"><span data-stu-id="f2ffc-107">In addition, `static` (`shared` in Visual Basic) properties of the <xref:System.TimeZoneInfo> class provide access to Coordinated Universal Time (UTC) and the local time zone.</span></span>

> [!NOTE]
> <span data-ttu-id="f2ffc-108">Dla stref czasowych, które nie są zdefiniowane w rejestrze, można utworzyć niestandardowych stref czasowych, wywołując przeciążeń <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="f2ffc-108">For time zones that are not defined in the registry, you can create custom time zones by calling the overloads of the <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> method.</span></span> <span data-ttu-id="f2ffc-109">Tworzenie niestandardowych strefy czasowej została szczegółowo opisana w [porady: tworzenie stref czasowych bez reguł korygowania](../../../docs/standard/datetime/create-time-zones-without-adjustment-rules.md) i [porady: tworzenie stref czasowych przy użyciu reguł korygowania](../../../docs/standard/datetime/create-time-zones-with-adjustment-rules.md) tematy.</span><span class="sxs-lookup"><span data-stu-id="f2ffc-109">Creating a custom time zone is discussed in the [How to: Create time zones without adjustment rules](../../../docs/standard/datetime/create-time-zones-without-adjustment-rules.md) and [How to: Create time zones with adjustment rules](../../../docs/standard/datetime/create-time-zones-with-adjustment-rules.md) topics.</span></span> <span data-ttu-id="f2ffc-110">Ponadto można utworzyć wystąpienia <xref:System.TimeZoneInfo> obiektu przywracania jej z serializacji ciągu z <xref:System.TimeZoneInfo.FromSerializedString%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="f2ffc-110">In addition, you can instantiate a <xref:System.TimeZoneInfo> object by restoring it from a serialized string with the <xref:System.TimeZoneInfo.FromSerializedString%2A> method.</span></span> <span data-ttu-id="f2ffc-111">Serializację i deserializację <xref:System.TimeZoneInfo> obiektu została szczegółowo opisana w [porady: zapisywanie stref czasowych w zasobie osadzonym](../../../docs/standard/datetime/save-time-zones-to-an-embedded-resource.md) i [porady: Przywracanie stref czasowych z zasobu osadzonego](../../../docs/standard/datetime/restore-time-zones-from-an-embedded-resource.md) tematów.</span><span class="sxs-lookup"><span data-stu-id="f2ffc-111">Serializing and deserializing a <xref:System.TimeZoneInfo> object is discussed in the [How to: Save time zones to an embedded resource](../../../docs/standard/datetime/save-time-zones-to-an-embedded-resource.md) and [How to: Restore Time Zones from an Embedded Resource](../../../docs/standard/datetime/restore-time-zones-from-an-embedded-resource.md) topics.</span></span>

## <a name="accessing-individual-time-zones"></a><span data-ttu-id="f2ffc-112">Uzyskiwanie dostępu do poszczególnych stref czasowych</span><span class="sxs-lookup"><span data-stu-id="f2ffc-112">Accessing individual time zones</span></span>

<span data-ttu-id="f2ffc-113"><xref:System.TimeZoneInfo> Klasa udostępnia dwa obiekty wstępnie zdefiniowane strefy czasowej, które reprezentują czas UTC i w lokalnej strefie czasowej.</span><span class="sxs-lookup"><span data-stu-id="f2ffc-113">The <xref:System.TimeZoneInfo> class provides two predefined time zone objects that represent the UTC time and the local time zone.</span></span> <span data-ttu-id="f2ffc-114">Są one dostępne z <xref:System.TimeZoneInfo.Utc%2A> i <xref:System.TimeZoneInfo.Local%2A> właściwości, odpowiednio.</span><span class="sxs-lookup"><span data-stu-id="f2ffc-114">They are available from the <xref:System.TimeZoneInfo.Utc%2A> and <xref:System.TimeZoneInfo.Local%2A> properties, respectively.</span></span> <span data-ttu-id="f2ffc-115">Aby uzyskać instrukcje dotyczące uzyskiwania dostępu do czasu UTC, czy strefy czasu lokalnego, zobacz [porady: uzyskiwanie dostępu do wstępnie zdefiniowanych obiektów stref UTC i czasem lokalnym](../../../docs/standard/datetime/access-utc-and-local.md).</span><span class="sxs-lookup"><span data-stu-id="f2ffc-115">For instructions on accessing the UTC or local time zones, see [How to: Access the predefined UTC and local time zone objects](../../../docs/standard/datetime/access-utc-and-local.md).</span></span>

<span data-ttu-id="f2ffc-116">Można również utworzyć wystąpienie <xref:System.TimeZoneInfo> obiekt, który reprezentuje wszystkie strefy czasowej zdefiniowana w rejestrze.</span><span class="sxs-lookup"><span data-stu-id="f2ffc-116">You can also instantiate a <xref:System.TimeZoneInfo> object that represents any time zone defined in the registry.</span></span> <span data-ttu-id="f2ffc-117">Aby uzyskać instrukcje dotyczące tworzenia wystąpienia obiektu stref czasowych, zobacz [porady: Tworzenie wystąpień obiektów TimeZoneInfo](../../../docs/standard/datetime/instantiate-time-zone-info.md).</span><span class="sxs-lookup"><span data-stu-id="f2ffc-117">For instructions on instantiating a specific time zone object, see [How to: Instantiate a TimeZoneInfo object](../../../docs/standard/datetime/instantiate-time-zone-info.md).</span></span>

## <a name="time-zone-identifiers"></a><span data-ttu-id="f2ffc-118">Identyfikatory stref czasowych</span><span class="sxs-lookup"><span data-stu-id="f2ffc-118">Time zone identifiers</span></span>

<span data-ttu-id="f2ffc-119">Identyfikator strefy czasowej jest pole klucza, który unikatowo identyfikuje strefę czasową.</span><span class="sxs-lookup"><span data-stu-id="f2ffc-119">The time zone identifier is a key field that uniquely identifies the time zone.</span></span> <span data-ttu-id="f2ffc-120">Mimo że większość klawiszy jest stosunkowo krótkich, identyfikator strefy czasowej jest stosunkowo długo.</span><span class="sxs-lookup"><span data-stu-id="f2ffc-120">While most keys are relatively short, the time zone identifier is comparatively long.</span></span> <span data-ttu-id="f2ffc-121">W większości przypadków, jego wartość odpowiada <xref:System.TimeZoneInfo.StandardName%2A?displayProperty=nameWithType> właściwość, która jest używana do określenia nazwy strefy czasowej (czas standardowy).</span><span class="sxs-lookup"><span data-stu-id="f2ffc-121">In most cases, its value corresponds to the <xref:System.TimeZoneInfo.StandardName%2A?displayProperty=nameWithType> property, which is used to provide the name of the time zone's standard time.</span></span> <span data-ttu-id="f2ffc-122">Istnieją wyjątki.</span><span class="sxs-lookup"><span data-stu-id="f2ffc-122">However, there are exceptions.</span></span> <span data-ttu-id="f2ffc-123">Najlepszym sposobem, aby upewnić się, że należy podać prawidłowy identyfikator jest wykazywanie stref czasowych dostępna w systemie i zanotuj ich skojarzonych identyfikatorów.</span><span class="sxs-lookup"><span data-stu-id="f2ffc-123">The best way to make sure that you supply a valid identifier is to enumerate the time zones available on your system and note their associated identifiers.</span></span>

## <a name="see-also"></a><span data-ttu-id="f2ffc-124">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f2ffc-124">See also</span></span>

<span data-ttu-id="f2ffc-125">[Daty, godziny i strefy czasowe](../../../docs/standard/datetime/index.md)
[porady: uzyskiwanie dostępu do wstępnie zdefiniowanych obiektów stref UTC i czasem lokalnym](../../../docs/standard/datetime/access-utc-and-local.md)
[porady: Tworzenie wystąpień obiektów TimeZoneInfo](../../../docs/standard/datetime/instantiate-time-zone-info.md) 
 [Konwertowanie godzin między strefami czasowymi](../../../docs/standard/datetime/converting-between-time-zones.md)</span><span class="sxs-lookup"><span data-stu-id="f2ffc-125">[Dates, times, and time zones](../../../docs/standard/datetime/index.md)
[How to: Access the predefined UTC and local time zone objects](../../../docs/standard/datetime/access-utc-and-local.md)
[How to: Instantiate a TimeZoneInfo object](../../../docs/standard/datetime/instantiate-time-zone-info.md)
[Converting times between time zones](../../../docs/standard/datetime/converting-between-time-zones.md)</span></span>
