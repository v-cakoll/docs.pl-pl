---
title: 'Instrukcje: Tworzenie stref czasowych bez reguł korygowania'
ms.date: 04/10/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- time zones [.NET Framework], adjustment rule
- time zones [.NET Framework], creating
- adjustment rule [.NET Framework]
ms.assetid: a6af8647-7893-4f29-95a9-d94c65a6e8dd
ms.openlocfilehash: 1d8aae1284e9ee9871c6f201c6a00e0b547f95fa
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/02/2020
ms.locfileid: "84278041"
---
# <a name="how-to-create-time-zones-without-adjustment-rules"></a><span data-ttu-id="48ab2-102">Instrukcje: Tworzenie stref czasowych bez reguł korygowania</span><span class="sxs-lookup"><span data-stu-id="48ab2-102">How to: Create time zones without adjustment rules</span></span>

<span data-ttu-id="48ab2-103">Precyzyjne informacje o strefie czasowej, które są wymagane przez aplikację, mogą nie być obecne w określonym systemie z kilku powodów:</span><span class="sxs-lookup"><span data-stu-id="48ab2-103">The precise time zone information that is required by an application may not be present on a particular system for several reasons:</span></span>

- <span data-ttu-id="48ab2-104">Strefa czasowa nigdy nie została zdefiniowana w rejestrze systemu lokalnego.</span><span class="sxs-lookup"><span data-stu-id="48ab2-104">The time zone has never been defined in the local system's registry.</span></span>

- <span data-ttu-id="48ab2-105">Dane dotyczące strefy czasowej zostały zmodyfikowane lub usunięte z rejestru.</span><span class="sxs-lookup"><span data-stu-id="48ab2-105">Data about the time zone has been modified or removed from the registry.</span></span>

- <span data-ttu-id="48ab2-106">Strefa czasowa istnieje, ale nie ma dokładnej informacji na temat korekt stref czasowych w danym okresie historycznym.</span><span class="sxs-lookup"><span data-stu-id="48ab2-106">The time zone exists but does not have accurate information about time zone adjustments for a particular historic period.</span></span>

<span data-ttu-id="48ab2-107">W takich przypadkach można wywołać <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> metodę w celu zdefiniowania strefy czasowej wymaganej przez aplikację.</span><span class="sxs-lookup"><span data-stu-id="48ab2-107">In these cases, you can call the <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> method to define the time zone required by your application.</span></span> <span data-ttu-id="48ab2-108">Można użyć przeciążenia tej metody, aby utworzyć strefę czasową z lub bez reguł korekty.</span><span class="sxs-lookup"><span data-stu-id="48ab2-108">You can use the overloads of this method to create a time zone with or without adjustment rules.</span></span> <span data-ttu-id="48ab2-109">Jeśli strefa czasowa obsługuje czas letni, można zdefiniować korekty przy użyciu stałych lub przestawnych reguł korekty.</span><span class="sxs-lookup"><span data-stu-id="48ab2-109">If the time zone supports daylight saving time, you can define adjustments with either fixed or floating adjustment rules.</span></span> <span data-ttu-id="48ab2-110">(W przypadku definicji tych warunków Zobacz sekcję "terminologia strefy czasowej" w temacie [Omówienie strefy czasowej](time-zone-overview.md)).</span><span class="sxs-lookup"><span data-stu-id="48ab2-110">(For definitions of these terms, see the "Time Zone Terminology" section in [Time zone overview](time-zone-overview.md).)</span></span>

> [!IMPORTANT]
> <span data-ttu-id="48ab2-111">Niestandardowe strefy czasowe utworzone przez wywołanie <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> metody nie są dodawane do rejestru.</span><span class="sxs-lookup"><span data-stu-id="48ab2-111">Custom time zones created by calling the <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> method are not added to the registry.</span></span> <span data-ttu-id="48ab2-112">Zamiast tego można uzyskać do nich dostęp tylko za pomocą odwołania do obiektu zwróconego przez <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> wywołanie metody.</span><span class="sxs-lookup"><span data-stu-id="48ab2-112">Instead, they can be accessed only through the object reference returned by the <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> method call.</span></span>

<span data-ttu-id="48ab2-113">W tym temacie pokazano, jak utworzyć strefę czasową bez reguł korekty.</span><span class="sxs-lookup"><span data-stu-id="48ab2-113">This topic shows how to create a time zone without adjustment rules.</span></span> <span data-ttu-id="48ab2-114">Aby utworzyć strefę czasową, która obsługuje reguły dostosowania czasu letniego, zobacz [How to: Create czas Zones with Rules](create-time-zones-with-adjustment-rules.md).</span><span class="sxs-lookup"><span data-stu-id="48ab2-114">To create a time zone that supports daylight saving time adjustment rules, see [How to: Create time zones with adjustment rules](create-time-zones-with-adjustment-rules.md).</span></span>

### <a name="to-create-a-time-zone-without-adjustment-rules"></a><span data-ttu-id="48ab2-115">Aby utworzyć strefę czasową bez reguł korygowania</span><span class="sxs-lookup"><span data-stu-id="48ab2-115">To create a time zone without adjustment rules</span></span>

1. <span data-ttu-id="48ab2-116">Zdefiniuj nazwę wyświetlaną strefy czasowej.</span><span class="sxs-lookup"><span data-stu-id="48ab2-116">Define the time zone's display name.</span></span>

   <span data-ttu-id="48ab2-117">Nazwa wyświetlana jest zgodna z formatem standardowym, w którym przesunięcie strefy czasowej od skoordynowanego czasu uniwersalnego (UTC) jest ujęte w nawiasy i następuje przez ciąg identyfikujący strefę czasową, co najmniej jeden z miast w strefie czasowej lub jeden lub więcej krajów lub regionów w strefie czasowej.</span><span class="sxs-lookup"><span data-stu-id="48ab2-117">The display name follows a fairly standard format in which the time zone's offset from Coordinated Universal Time (UTC) is enclosed in parentheses and is followed by a string that identifies the time zone, one or more of the cities in the time zone, or one or more of the countries or regions in the time zone.</span></span>

2. <span data-ttu-id="48ab2-118">Zdefiniuj nazwę czasu standardowego strefy czasowej.</span><span class="sxs-lookup"><span data-stu-id="48ab2-118">Define the name of the time zone's standard time.</span></span> <span data-ttu-id="48ab2-119">Zazwyczaj ten ciąg jest również używany jako identyfikator strefy czasowej.</span><span class="sxs-lookup"><span data-stu-id="48ab2-119">Typically, this string is also used as the time zone's identifier.</span></span>

3. <span data-ttu-id="48ab2-120">Jeśli chcesz użyć innego identyfikatora niż nazwa standardowa strefy czasowej, zdefiniuj identyfikator strefy czasowej.</span><span class="sxs-lookup"><span data-stu-id="48ab2-120">If you want to use a different identifier than the time zone's standard name, define the time zone identifier.</span></span>

4. <span data-ttu-id="48ab2-121">Utwórz wystąpienie <xref:System.TimeSpan> obiektu, który definiuje przesunięcie strefy czasowej z czasu UTC.</span><span class="sxs-lookup"><span data-stu-id="48ab2-121">Instantiate a <xref:System.TimeSpan> object that defines the time zone's offset from UTC.</span></span> <span data-ttu-id="48ab2-122">Strefy czasowe, które są późniejsze niż UTC, są przesunięte pozytywnie.</span><span class="sxs-lookup"><span data-stu-id="48ab2-122">Time zones with times that are later than UTC have a positive offset.</span></span> <span data-ttu-id="48ab2-123">Strefy czasowe o porach wcześniejszym niż UTC mają ujemne przesunięcie.</span><span class="sxs-lookup"><span data-stu-id="48ab2-123">Time zones with times that are earlier than UTC have a negative offset.</span></span>

5. <span data-ttu-id="48ab2-124">Wywołaj <xref:System.TimeZoneInfo.CreateCustomTimeZone%28System.String%2CSystem.TimeSpan%2CSystem.String%2CSystem.String%29?displayProperty=nameWithType> metodę, aby utworzyć wystąpienie nowej strefy czasowej.</span><span class="sxs-lookup"><span data-stu-id="48ab2-124">Call the <xref:System.TimeZoneInfo.CreateCustomTimeZone%28System.String%2CSystem.TimeSpan%2CSystem.String%2CSystem.String%29?displayProperty=nameWithType> method to instantiate the new time zone.</span></span>

## <a name="example"></a><span data-ttu-id="48ab2-125">Przykład</span><span class="sxs-lookup"><span data-stu-id="48ab2-125">Example</span></span>

<span data-ttu-id="48ab2-126">W poniższym przykładzie zdefiniowano niestandardową strefę czasową dla Mawson, Antarktyda, która nie ma reguł korekty.</span><span class="sxs-lookup"><span data-stu-id="48ab2-126">The following example defines a custom time zone for Mawson, Antarctica, which has no adjustment rules.</span></span>

[!code-csharp[System.TimeZone2.CreateTimeZone#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.CreateTimeZone/cs/System.TimeZone2.CreateTimeZone.cs#1)]
[!code-vb[System.TimeZone2.CreateTimeZone#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.CreateTimeZone/vb/System.TimeZone2.CreateTimeZone.vb#1)]

<span data-ttu-id="48ab2-127">Ciąg przypisany do <xref:System.TimeZoneInfo.DisplayName%2A> właściwości jest zgodny z formatem standardowym, w którym przesunięcie strefy czasowej od czasu UTC następuje przyjazny opis strefy czasowej.</span><span class="sxs-lookup"><span data-stu-id="48ab2-127">The string assigned to the <xref:System.TimeZoneInfo.DisplayName%2A> property follows a standard format in which the time zone's offset from UTC is followed by a friendly description of the time zone.</span></span>

## <a name="compiling-the-code"></a><span data-ttu-id="48ab2-128">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="48ab2-128">Compiling the code</span></span>

<span data-ttu-id="48ab2-129">Ten przykład wymaga:</span><span class="sxs-lookup"><span data-stu-id="48ab2-129">This example requires:</span></span>

- <span data-ttu-id="48ab2-130">Że importowane są następujące przestrzenie nazw:</span><span class="sxs-lookup"><span data-stu-id="48ab2-130">That the following namespaces be imported:</span></span>

  [!code-csharp[System.TimeZone2.CreateTimeZone#6](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.CreateTimeZone/cs/System.TimeZone2.CreateTimeZone.cs#6)]
  [!code-vb[System.TimeZone2.CreateTimeZone#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.CreateTimeZone/vb/System.TimeZone2.CreateTimeZone.vb#6)]

## <a name="see-also"></a><span data-ttu-id="48ab2-131">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="48ab2-131">See also</span></span>

- [<span data-ttu-id="48ab2-132">Daty, godziny i strefy czasowe</span><span class="sxs-lookup"><span data-stu-id="48ab2-132">Dates, times, and time zones</span></span>](index.md)
- [<span data-ttu-id="48ab2-133">Strefy czasowe — omówienie</span><span class="sxs-lookup"><span data-stu-id="48ab2-133">Time zone overview</span></span>](time-zone-overview.md)
- [<span data-ttu-id="48ab2-134">Instrukcje: Tworzenie stref czasowych przy użyciu reguł korygowania</span><span class="sxs-lookup"><span data-stu-id="48ab2-134">How to: Create time zones with adjustment rules</span></span>](create-time-zones-with-adjustment-rules.md)
