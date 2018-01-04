---
title: "Porady: tworzenie stref czasowych bez reguł korygowania"
ms.custom: 
ms.date: 04/10/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- time zones [.NET Framework], adjustment rule
- time zones [.NET Framework], creating
- adjustment rule [.NET Framework]
ms.assetid: a6af8647-7893-4f29-95a9-d94c65a6e8dd
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 14c5e02ce5af03d063260af19e9dd1a970a93ab6
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/23/2017
---
# <a name="how-to-create-time-zones-without-adjustment-rules"></a><span data-ttu-id="e51dd-102">Porady: tworzenie stref czasowych bez reguł korygowania</span><span class="sxs-lookup"><span data-stu-id="e51dd-102">How to: Create time zones without adjustment rules</span></span>

<span data-ttu-id="e51dd-103">Wymagane przez aplikację informacje o strefie czasowej dokładne mogą nie występować w określonym systemie z kilku powodów:</span><span class="sxs-lookup"><span data-stu-id="e51dd-103">The precise time zone information that is required by an application may not be present on a particular system for several reasons:</span></span>

* <span data-ttu-id="e51dd-104">Strefa czasowa nigdy nie został zdefiniowany w rejestrze systemu lokalnego.</span><span class="sxs-lookup"><span data-stu-id="e51dd-104">The time zone has never been defined in the local system's registry.</span></span>

* <span data-ttu-id="e51dd-105">Dane dotyczące strefy czasowej został zmodyfikowany lub usunięty z rejestru.</span><span class="sxs-lookup"><span data-stu-id="e51dd-105">Data about the time zone has been modified or removed from the registry.</span></span>

* <span data-ttu-id="e51dd-106">Strefa czasowa istnieje, ale nie ma dokładnych informacji o ustawienia strefy czasowej określonym okresie historycznych.</span><span class="sxs-lookup"><span data-stu-id="e51dd-106">The time zone exists but does not have accurate information about time zone adjustments for a particular historic period.</span></span>

<span data-ttu-id="e51dd-107">W takich przypadkach można wywołać <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> metodę, aby określić strefę czasową wymagane przez aplikację.</span><span class="sxs-lookup"><span data-stu-id="e51dd-107">In these cases, you can call the <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> method to define the time zone required by your application.</span></span> <span data-ttu-id="e51dd-108">Przeciążenie tej metody można użyć do tworzenia strefy czasowej z lub bez reguł korygowania.</span><span class="sxs-lookup"><span data-stu-id="e51dd-108">You can use the overloads of this method to create a time zone with or without adjustment rules.</span></span> <span data-ttu-id="e51dd-109">Jeśli strefa czasowa obsługuje czasu letniego, można zdefiniować dostosowania przy użyciu albo reguł korygowania stałym lub zmiennoprzecinkową.</span><span class="sxs-lookup"><span data-stu-id="e51dd-109">If the time zone supports daylight saving time, you can define adjustments with either fixed or floating adjustment rules.</span></span> <span data-ttu-id="e51dd-110">(Definicje tych postanowień, zobacz sekcję "Terminologii strefy czasowej" w [Przegląd stref czasowych](../../../docs/standard/datetime/time-zone-overview.md).)</span><span class="sxs-lookup"><span data-stu-id="e51dd-110">(For definitions of these terms, see the "Time Zone Terminology" section in [Time zone overview](../../../docs/standard/datetime/time-zone-overview.md).)</span></span>

> [!IMPORTANT]
> <span data-ttu-id="e51dd-111">Utworzone przez wywołanie niestandardowych stref czasowych <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> metody nie zostaną dodane do rejestru.</span><span class="sxs-lookup"><span data-stu-id="e51dd-111">Custom time zones created by calling the <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> method are not added to the registry.</span></span> <span data-ttu-id="e51dd-112">Zamiast tego są one dostępne tylko za pośrednictwem zwracane przez odwołanie do obiektu <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> wywołania metody.</span><span class="sxs-lookup"><span data-stu-id="e51dd-112">Instead, they can be accessed only through the object reference returned by the <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> method call.</span></span>

<span data-ttu-id="e51dd-113">W tym temacie przedstawiono sposób tworzenia strefy czasowej bez reguł korygowania.</span><span class="sxs-lookup"><span data-stu-id="e51dd-113">This topic shows how to create a time zone without adjustment rules.</span></span> <span data-ttu-id="e51dd-114">Aby utworzyć strefę czasową obsługującą reguł korygowania czasu letniego, zobacz [porady: tworzenie stref czasowych przy użyciu reguł korygowania](../../../docs/standard/datetime/create-time-zones-with-adjustment-rules.md).</span><span class="sxs-lookup"><span data-stu-id="e51dd-114">To create a time zone that supports daylight saving time adjustment rules, see [How to: Create time zones with adjustment rules](../../../docs/standard/datetime/create-time-zones-with-adjustment-rules.md).</span></span>

### <a name="to-create-a-time-zone-without-adjustment-rules"></a><span data-ttu-id="e51dd-115">Aby utworzyć strefę czasową bez reguł korygowania</span><span class="sxs-lookup"><span data-stu-id="e51dd-115">To create a time zone without adjustment rules</span></span>

1. <span data-ttu-id="e51dd-116">Zdefiniuj nazwę wyświetlaną strefy czasowej.</span><span class="sxs-lookup"><span data-stu-id="e51dd-116">Define the time zone's display name.</span></span>

   <span data-ttu-id="e51dd-117">Dość standardowy format, w którym przesunięcie strefy czasowej z uniwersalnego czasu koordynowanego (UTC) jest ujęta w nawiasy i następuje ciąg identyfikujący strefy czasowej, jeden lub więcej miast w strefie czasowej lub jeden lub kilka Rada następuje nazwa wyświetlana zapisy lub regiony w strefie czasowej.</span><span class="sxs-lookup"><span data-stu-id="e51dd-117">The display name follows a fairly standard format in which the time zone's offset from Coordinated Universal Time (UTC) is enclosed in parentheses and is followed by a string that identifies the time zone, one or more of the cities in the time zone, or one or more of the countries or regions in the time zone.</span></span>

2. <span data-ttu-id="e51dd-118">Zdefiniuj nazwę strefy czasowej (czas standardowy).</span><span class="sxs-lookup"><span data-stu-id="e51dd-118">Define the name of the time zone's standard time.</span></span> <span data-ttu-id="e51dd-119">Zazwyczaj ten ciąg jest również używane jako identyfikator strefy czasowej.</span><span class="sxs-lookup"><span data-stu-id="e51dd-119">Typically, this string is also used as the time zone's identifier.</span></span>

3. <span data-ttu-id="e51dd-120">Jeśli chcesz użyć innego identyfikatora niż nazwa standardowa strefy czasowej, należy zdefiniować identyfikator strefy czasowej.</span><span class="sxs-lookup"><span data-stu-id="e51dd-120">If you want to use a different identifier than the time zone's standard name, define the time zone identifier.</span></span>

4. <span data-ttu-id="e51dd-121">Utwórz wystąpienie <xref:System.TimeSpan> obiektu, który definiuje przesunięcie strefy czasowej z czasem UTC.</span><span class="sxs-lookup"><span data-stu-id="e51dd-121">Instantiate a <xref:System.TimeSpan> object that defines the time zone's offset from UTC.</span></span> <span data-ttu-id="e51dd-122">Strefy czasowe wraz z czasem, które są później niż czas UTC mają przesunięcie dodatnią.</span><span class="sxs-lookup"><span data-stu-id="e51dd-122">Time zones with times that are later than UTC have a positive offset.</span></span> <span data-ttu-id="e51dd-123">Strefy czasowe wraz z czasem, które są starsze niż UTC mają ujemne przesunięcie.</span><span class="sxs-lookup"><span data-stu-id="e51dd-123">Time zones with times that are earlier than UTC have a negative offset.</span></span>

5. <span data-ttu-id="e51dd-124">Wywołanie <xref:System.TimeZoneInfo.CreateCustomTimeZone%28System.String%2CSystem.TimeSpan%2CSystem.String%2CSystem.String%29?displayProperty=nameWithType> metody można utworzyć nowej strefy czasowej.</span><span class="sxs-lookup"><span data-stu-id="e51dd-124">Call the <xref:System.TimeZoneInfo.CreateCustomTimeZone%28System.String%2CSystem.TimeSpan%2CSystem.String%2CSystem.String%29?displayProperty=nameWithType> method to instantiate the new time zone.</span></span>

## <a name="example"></a><span data-ttu-id="e51dd-125">Przykład</span><span class="sxs-lookup"><span data-stu-id="e51dd-125">Example</span></span>

<span data-ttu-id="e51dd-126">W poniższym przykładzie zdefiniowano niestandardowe strefę czasową dla Mawson, Antarktyka, który nie ma dopasowania reguł.</span><span class="sxs-lookup"><span data-stu-id="e51dd-126">The following example defines a custom time zone for Mawson, Antarctica, which has no adjustment rules.</span></span>

[!code-csharp[System.TimeZone2.CreateTimeZone#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.CreateTimeZone/cs/System.TimeZone2.CreateTimeZone.cs#1)]
[!code-vb[System.TimeZone2.CreateTimeZone#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.CreateTimeZone/vb/System.TimeZone2.CreateTimeZone.vb#1)]

<span data-ttu-id="e51dd-127">Ciąg znaków przypisany do <xref:System.TimeZoneInfo.DisplayName%2A> właściwości następuje standardowy format, w którym przesunięcie strefy czasowej z UTC następuje przyjazny opis strefy czasowej.</span><span class="sxs-lookup"><span data-stu-id="e51dd-127">The string assigned to the <xref:System.TimeZoneInfo.DisplayName%2A> property follows a standard format in which the time zone's offset from UTC is followed by a friendly description of the time zone.</span></span>

## <a name="compiling-the-code"></a><span data-ttu-id="e51dd-128">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="e51dd-128">Compiling the code</span></span>

<span data-ttu-id="e51dd-129">Ten przykład wymaga:</span><span class="sxs-lookup"><span data-stu-id="e51dd-129">This example requires:</span></span>

* <span data-ttu-id="e51dd-130">Odwołania do System.Core.dll dodania do projektu.</span><span class="sxs-lookup"><span data-stu-id="e51dd-130">That a reference to System.Core.dll be added to the project.</span></span>

* <span data-ttu-id="e51dd-131">Czy następujących przestrzeni nazw można importować:</span><span class="sxs-lookup"><span data-stu-id="e51dd-131">That the following namespaces be imported:</span></span>

  [!code-csharp[System.TimeZone2.CreateTimeZone#6](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.CreateTimeZone/cs/System.TimeZone2.CreateTimeZone.cs#6)]
  [!code-vb[System.TimeZone2.CreateTimeZone#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.CreateTimeZone/vb/System.TimeZone2.CreateTimeZone.vb#6)]

## <a name="see-also"></a><span data-ttu-id="e51dd-132">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e51dd-132">See also</span></span>

<span data-ttu-id="e51dd-133">[Daty, godziny i strefy czasowe](../../../docs/standard/datetime/index.md)
[Przegląd stref czasowych](../../../docs/standard/datetime/time-zone-overview.md)
[porady: tworzenie stref czasowych przy użyciu reguł korygowania](../../../docs/standard/datetime/create-time-zones-with-adjustment-rules.md)</span><span class="sxs-lookup"><span data-stu-id="e51dd-133">[Dates, times, and time zones](../../../docs/standard/datetime/index.md)
[Time zone overview](../../../docs/standard/datetime/time-zone-overview.md)
[How to: Create time zones with adjustment rules](../../../docs/standard/datetime/create-time-zones-with-adjustment-rules.md)</span></span>
