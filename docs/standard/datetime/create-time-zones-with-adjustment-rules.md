---
title: "Porady: tworzenie stref czasowych przy użyciu reguł korygowania"
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
- time zones [.NET Framework], creating
- time zones [.NET Framework], and adjustment rules
- adjustment rule [.NET Framework]
ms.assetid: c52ef192-13a9-435f-8015-3b12eae8c47c
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 75e1867e810090bf35a0dfc7def5785747f94382
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-create-time-zones-with-adjustment-rules"></a><span data-ttu-id="59f89-102">Porady: tworzenie stref czasowych przy użyciu reguł korygowania</span><span class="sxs-lookup"><span data-stu-id="59f89-102">How to: Create time zones with adjustment rules</span></span>

<span data-ttu-id="59f89-103">Wymagane przez aplikację informacje o strefie czasowej dokładne mogą nie występować w określonym systemie z kilku powodów:</span><span class="sxs-lookup"><span data-stu-id="59f89-103">The precise time zone information that is required by an application may not be present on a particular system for several reasons:</span></span>

* <span data-ttu-id="59f89-104">Strefa czasowa nigdy nie został zdefiniowany w rejestrze systemu lokalnego.</span><span class="sxs-lookup"><span data-stu-id="59f89-104">The time zone has never been defined in the local system's registry.</span></span>

* <span data-ttu-id="59f89-105">Dane dotyczące strefy czasowej został zmodyfikowany lub usunięty z rejestru.</span><span class="sxs-lookup"><span data-stu-id="59f89-105">Data about the time zone has been modified or removed from the registry.</span></span>

* <span data-ttu-id="59f89-106">Strefa czasowa nie ma dokładnych informacji o ustawienia strefy czasowej określonym okresie historycznych.</span><span class="sxs-lookup"><span data-stu-id="59f89-106">The time zone does not have accurate information about time zone adjustments for a particular historic period.</span></span>

<span data-ttu-id="59f89-107">W takich przypadkach można wywołać <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> metodę, aby określić strefę czasową wymagane przez aplikację.</span><span class="sxs-lookup"><span data-stu-id="59f89-107">In these cases, you can call the <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> method to define the time zone required by your application.</span></span> <span data-ttu-id="59f89-108">Przeciążenie tej metody można użyć do tworzenia strefy czasowej z lub bez reguł korygowania.</span><span class="sxs-lookup"><span data-stu-id="59f89-108">You can use the overloads of this method to create a time zone with or without adjustment rules.</span></span> <span data-ttu-id="59f89-109">Jeśli strefa czasowa obsługuje czasu letniego, można zdefiniować dostosowania przy użyciu albo reguł korygowania stałym lub zmiennoprzecinkową.</span><span class="sxs-lookup"><span data-stu-id="59f89-109">If the time zone supports daylight saving time, you can define adjustments with either fixed or floating adjustment rules.</span></span> <span data-ttu-id="59f89-110">(Definicje tych postanowień, zobacz sekcję "Terminologii strefy czasowej" w [Przegląd stref czasowych](../../../docs/standard/datetime/time-zone-overview.md).)</span><span class="sxs-lookup"><span data-stu-id="59f89-110">(For definitions of these terms, see the "Time Zone Terminology" section in [Time zone overview](../../../docs/standard/datetime/time-zone-overview.md).)</span></span>

> [!IMPORTANT]
> <span data-ttu-id="59f89-111">Utworzone przez wywołanie niestandardowych stref czasowych <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> metody nie zostaną dodane do rejestru.</span><span class="sxs-lookup"><span data-stu-id="59f89-111">Custom time zones created by calling the <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> method are not added to the registry.</span></span> <span data-ttu-id="59f89-112">Zamiast tego są one dostępne tylko za pośrednictwem zwracane przez odwołanie do obiektu <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> wywołania metody.</span><span class="sxs-lookup"><span data-stu-id="59f89-112">Instead, they can be accessed only through the object reference returned by the <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> method call.</span></span>

<span data-ttu-id="59f89-113">W tym temacie przedstawiono sposób tworzenia strefy czasowej przy użyciu reguł korygowania.</span><span class="sxs-lookup"><span data-stu-id="59f89-113">This topic shows how to create a time zone with adjustment rules.</span></span> <span data-ttu-id="59f89-114">Aby utworzyć strefę czasową, która nie obsługuje reguł korygowania czasu letniego, zobacz [porady: tworzenie stref czasowych bez reguł korygowania](../../../docs/standard/datetime/create-time-zones-without-adjustment-rules.md).</span><span class="sxs-lookup"><span data-stu-id="59f89-114">To create a time zone that does not support daylight saving time adjustment rules, see [How to: Create Time Zones Without Adjustment Rules](../../../docs/standard/datetime/create-time-zones-without-adjustment-rules.md).</span></span>

### <a name="to-create-a-time-zone-with-floating-adjustment-rules"></a><span data-ttu-id="59f89-115">Aby utworzyć strefę czasową z zmiennoprzecinkową reguł korygowania</span><span class="sxs-lookup"><span data-stu-id="59f89-115">To create a time zone with floating adjustment rules</span></span>

1. <span data-ttu-id="59f89-116">Dla każdego dostosowanie (który jest dla każdego przejścia od i z powrotem do (czas standardowy) w określonym interwale) wykonaj następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="59f89-116">For each adjustment (that is, for each transition away from and back to standard time over a particular time interval), do the following:</span></span>

    1. <span data-ttu-id="59f89-117">Zdefiniuj godzinę rozpoczęcia przejścia do dostosowania strefy czasowej.</span><span class="sxs-lookup"><span data-stu-id="59f89-117">Define the starting transition time for the time zone adjustment.</span></span>

       <span data-ttu-id="59f89-118">Należy wywołać <xref:System.TimeZoneInfo.TransitionTime.CreateFloatingDateRule%2A?displayProperty=nameWithType> — metoda i przekaż go <xref:System.DateTime> wartość, która definiuje czas przejścia, wartość całkowitą, który definiuje miesiąca przejścia, wartość całkowitą, który definiuje tygodnia, w którym następuje przejście i <xref:System.DayOfWeek> wartość, która określa dzień tygodnia, w którym następuje przejście.</span><span class="sxs-lookup"><span data-stu-id="59f89-118">You must call the <xref:System.TimeZoneInfo.TransitionTime.CreateFloatingDateRule%2A?displayProperty=nameWithType> method and pass it a <xref:System.DateTime> value that defines the time of the transition, an integer value that defines the month of the transition, an integer value that defines the week on which the transition occurs, and a <xref:System.DayOfWeek> value that defines the day of the week on which the transition occurs.</span></span> <span data-ttu-id="59f89-119">Tworzy wywołanie tej metody <xref:System.TimeZoneInfo.TransitionTime> obiektu.</span><span class="sxs-lookup"><span data-stu-id="59f89-119">This method call instantiates a <xref:System.TimeZoneInfo.TransitionTime> object.</span></span>

    2. <span data-ttu-id="59f89-120">Zdefiniuj godzinę zakończenia przejścia do dostosowania strefy czasowej.</span><span class="sxs-lookup"><span data-stu-id="59f89-120">Define the ending transition time for the time zone adjustment.</span></span> <span data-ttu-id="59f89-121">Wymaga to innym wywołaniu <xref:System.TimeZoneInfo.TransitionTime.CreateFloatingDateRule%2A?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="59f89-121">This requires another call to the <xref:System.TimeZoneInfo.TransitionTime.CreateFloatingDateRule%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="59f89-122">Wywołanie tej metody tworzy drugi <xref:System.TimeZoneInfo.TransitionTime> obiektu.</span><span class="sxs-lookup"><span data-stu-id="59f89-122">This method call instantiates a second <xref:System.TimeZoneInfo.TransitionTime> object.</span></span>

    3. <span data-ttu-id="59f89-123">Wywołanie <xref:System.TimeZoneInfo.AdjustmentRule.CreateAdjustmentRule%2A> — metoda i przekaż go skuteczne daty rozpoczęcia i zakończenia korekty, <xref:System.TimeSpan> obiektu, który definiuje czas przejścia i dwa <xref:System.TimeZoneInfo.TransitionTime> obiektów, które definiują podczas przejścia do i z letniego czas wystąpić.</span><span class="sxs-lookup"><span data-stu-id="59f89-123">Call the <xref:System.TimeZoneInfo.AdjustmentRule.CreateAdjustmentRule%2A> method and pass it the effective start and end dates of the adjustment, a <xref:System.TimeSpan> object that defines the amount of time in the transition, and the two <xref:System.TimeZoneInfo.TransitionTime> objects that define when the transitions to and from daylight saving time occur.</span></span> <span data-ttu-id="59f89-124">Tworzy wywołanie tej metody <xref:System.TimeZoneInfo.AdjustmentRule> obiektu.</span><span class="sxs-lookup"><span data-stu-id="59f89-124">This method call instantiates a <xref:System.TimeZoneInfo.AdjustmentRule> object.</span></span>

    4. <span data-ttu-id="59f89-125">Przypisz <xref:System.TimeZoneInfo.AdjustmentRule> obiektu do tablicy <xref:System.TimeZoneInfo.AdjustmentRule> obiektów.</span><span class="sxs-lookup"><span data-stu-id="59f89-125">Assign the <xref:System.TimeZoneInfo.AdjustmentRule> object to an array of <xref:System.TimeZoneInfo.AdjustmentRule> objects.</span></span>

2. <span data-ttu-id="59f89-126">Zdefiniuj nazwę wyświetlaną strefy czasowej.</span><span class="sxs-lookup"><span data-stu-id="59f89-126">Define the time zone's display name.</span></span> <span data-ttu-id="59f89-127">Dość standardowy format, w którym przesunięcie strefy czasowej z uniwersalnego czasu koordynowanego (UTC) jest ujęta w nawiasy i następuje ciąg identyfikujący strefy czasowej, jeden lub więcej miast w strefie czasowej lub jeden lub kilka Rada następuje nazwa wyświetlana zapisy lub regiony w strefie czasowej.</span><span class="sxs-lookup"><span data-stu-id="59f89-127">The display name follows a fairly standard format in which the time zone's offset from Coordinated Universal Time (UTC) is enclosed in parentheses and is followed by a string that identifies the time zone, one or more of the cities in the time zone, or one or more of the countries or regions in the time zone.</span></span>

3. <span data-ttu-id="59f89-128">Zdefiniuj nazwę strefy czasowej (czas standardowy).</span><span class="sxs-lookup"><span data-stu-id="59f89-128">Define the name of the time zone's standard time.</span></span> <span data-ttu-id="59f89-129">Zazwyczaj ten ciąg jest również używane jako identyfikator strefy czasowej.</span><span class="sxs-lookup"><span data-stu-id="59f89-129">Typically, this string is also used as the time zone's identifier.</span></span>

4. <span data-ttu-id="59f89-130">Zdefiniuj nazwę strefy czasowej czasu.</span><span class="sxs-lookup"><span data-stu-id="59f89-130">Define the name of the time zone's daylight time.</span></span>

5. <span data-ttu-id="59f89-131">Jeśli chcesz użyć innego identyfikatora niż nazwa standardowa strefy czasowej, należy zdefiniować identyfikator strefy czasowej.</span><span class="sxs-lookup"><span data-stu-id="59f89-131">If you want to use a different identifier than the time zone's standard name, define the time zone identifier.</span></span>

6. <span data-ttu-id="59f89-132">Utwórz wystąpienie <xref:System.TimeSpan> obiektu, który definiuje przesunięcie strefy czasowej z czasem UTC.</span><span class="sxs-lookup"><span data-stu-id="59f89-132">Instantiate a <xref:System.TimeSpan> object that defines the time zone's offset from UTC.</span></span> <span data-ttu-id="59f89-133">Strefy czasowe wraz z czasem, które są później niż czas UTC mają przesunięcie dodatnią.</span><span class="sxs-lookup"><span data-stu-id="59f89-133">Time zones with times that are later than UTC have a positive offset.</span></span> <span data-ttu-id="59f89-134">Strefy czasowe wraz z czasem, które są starsze niż UTC mają ujemne przesunięcie.</span><span class="sxs-lookup"><span data-stu-id="59f89-134">Time zones with times that are earlier than UTC have a negative offset.</span></span>

7. <span data-ttu-id="59f89-135">Wywołanie <xref:System.TimeZoneInfo.CreateCustomTimeZone%28System.String%2CSystem.TimeSpan%2CSystem.String%2CSystem.String%2CSystem.String%2CSystem.TimeZoneInfo.AdjustmentRule%5B%5D%29?displayProperty=nameWithType> metody można utworzyć nowej strefy czasowej.</span><span class="sxs-lookup"><span data-stu-id="59f89-135">Call the <xref:System.TimeZoneInfo.CreateCustomTimeZone%28System.String%2CSystem.TimeSpan%2CSystem.String%2CSystem.String%2CSystem.String%2CSystem.TimeZoneInfo.AdjustmentRule%5B%5D%29?displayProperty=nameWithType> method to instantiate the new time zone.</span></span>

## <a name="example"></a><span data-ttu-id="59f89-136">Przykład</span><span class="sxs-lookup"><span data-stu-id="59f89-136">Example</span></span>

<span data-ttu-id="59f89-137">W poniższym przykładzie zdefiniowano centralnej standardowa strefy czasowej dla Stanów Zjednoczonych, zawiera reguły korekty dla różnych interwałów z 1918 bieżącej.</span><span class="sxs-lookup"><span data-stu-id="59f89-137">The following example defines a Central Standard Time zone for the United States that includes adjustment rules for a variety of time intervals from 1918 to the present.</span></span>

[!code-csharp[System.TimeZone2.CreateTimeZone#5](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.CreateTimeZone/cs/System.TimeZone2.CreateTimeZone.cs#5)]
[!code-vb[System.TimeZone2.CreateTimeZone#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.CreateTimeZone/vb/System.TimeZone2.CreateTimeZone.vb#5)]

<span data-ttu-id="59f89-138">Strefa czasowa utworzone w tym przykładzie ma wiele reguł korygowania.</span><span class="sxs-lookup"><span data-stu-id="59f89-138">The time zone created in this example has multiple adjustment rules.</span></span> <span data-ttu-id="59f89-139">Należy uważać, aby upewnić się, że skuteczne daty rozpoczęcia i zakończenia reguły korekty nie pokrywają się z datami inna reguła korekty.</span><span class="sxs-lookup"><span data-stu-id="59f89-139">Care must be taken to ensure that the effective start and end dates of any adjustment rule do not overlap with the dates of another adjustment rule.</span></span> <span data-ttu-id="59f89-140">Jeśli występuje nakładanie się <xref:System.InvalidTimeZoneException> jest generowany.</span><span class="sxs-lookup"><span data-stu-id="59f89-140">If there is an overlap, an <xref:System.InvalidTimeZoneException> is thrown.</span></span>

<span data-ttu-id="59f89-141">Na liczby zmiennoprzecinkowe reguł korygowania, wartość 5 jest przekazywana do `week` parametr <xref:System.TimeZoneInfo.TransitionTime.CreateFloatingDateRule%2A> metody, aby wskazać, że w danym miesiącu ostatniego tygodnia następuje przejście.</span><span class="sxs-lookup"><span data-stu-id="59f89-141">For floating adjustment rules, the value 5 is passed to the `week` parameter of the <xref:System.TimeZoneInfo.TransitionTime.CreateFloatingDateRule%2A> method to indicate that the transition occurs on the last week of a particular month.</span></span>

<span data-ttu-id="59f89-142">Podczas tworzenia tablicy <xref:System.TimeZoneInfo.AdjustmentRule> obiektów do użycia w <xref:System.TimeZoneInfo.CreateCustomTimeZone%28System.String%2CSystem.TimeSpan%2CSystem.String%2CSystem.String%2CSystem.String%2CSystem.TimeZoneInfo.AdjustmentRule%5B%5D%29?displayProperty=nameWithType> wywołanie metody kodu można zainicjować tablicy do rozmiaru wymagane przez liczby korekt ma zostać utworzony dla strefy czasowej.</span><span class="sxs-lookup"><span data-stu-id="59f89-142">In creating the array of <xref:System.TimeZoneInfo.AdjustmentRule> objects to use in the <xref:System.TimeZoneInfo.CreateCustomTimeZone%28System.String%2CSystem.TimeSpan%2CSystem.String%2CSystem.String%2CSystem.String%2CSystem.TimeZoneInfo.AdjustmentRule%5B%5D%29?displayProperty=nameWithType> method call, the code could initialize the array to the size required by the number of adjustments to be created for the time zone.</span></span> <span data-ttu-id="59f89-143">Zamiast tego wywołuje ten przykładowy kod <xref:System.Collections.Generic.List%601.Add%2A> metody w celu dodania poszczególnych reguł dopasowania do ogólnego <xref:System.Collections.Generic.List%601> Kolekcja <xref:System.TimeZoneInfo.AdjustmentRule> obiektów.</span><span class="sxs-lookup"><span data-stu-id="59f89-143">Instead, this code example calls the <xref:System.Collections.Generic.List%601.Add%2A> method to add each adjustment rule to a generic <xref:System.Collections.Generic.List%601> collection of <xref:System.TimeZoneInfo.AdjustmentRule> objects.</span></span> <span data-ttu-id="59f89-144">Kod wywołuje <xref:System.Collections.Generic.List%601.CopyTo%2A> metody, aby skopiować członków tej kolekcji do tablicy.</span><span class="sxs-lookup"><span data-stu-id="59f89-144">The code then calls the <xref:System.Collections.Generic.List%601.CopyTo%2A> method to copy the members of this collection to the array.</span></span>

<span data-ttu-id="59f89-145">Funkcja <xref:System.TimeZoneInfo.TransitionTime.CreateFixedDateRule%2A> metodę, aby zdefiniować dostosowania stałych.</span><span class="sxs-lookup"><span data-stu-id="59f89-145">The example also uses the <xref:System.TimeZoneInfo.TransitionTime.CreateFixedDateRule%2A> method to define fixed-date adjustments.</span></span> <span data-ttu-id="59f89-146">Jest to podobne do wywoływania <xref:System.TimeZoneInfo.TransitionTime.CreateFloatingDateRule%2A> metody, z wyjątkiem, że wymaga tylko czas, miesiąc i dzień parametrów przejścia.</span><span class="sxs-lookup"><span data-stu-id="59f89-146">This is similar to calling the <xref:System.TimeZoneInfo.TransitionTime.CreateFloatingDateRule%2A> method, except that it requires only the time, month, and day of the transition parameters.</span></span>

<span data-ttu-id="59f89-147">Przykład można przetestować przy użyciu kodu, takie jak następujące:</span><span class="sxs-lookup"><span data-stu-id="59f89-147">The example can be tested using code such as the following:</span></span>

[!code-csharp[System.TimeZone2.CreateTimeZone#7](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.CreateTimeZone/cs/System.TimeZone2.CreateTimeZone.cs#7)]
[!code-vb[System.TimeZone2.CreateTimeZone#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.CreateTimeZone/vb/System.TimeZone2.CreateTimeZone.vb#7)]

## <a name="compiling-the-code"></a><span data-ttu-id="59f89-148">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="59f89-148">Compiling the code</span></span>

<span data-ttu-id="59f89-149">Ten przykład wymaga:</span><span class="sxs-lookup"><span data-stu-id="59f89-149">This example requires:</span></span>

* <span data-ttu-id="59f89-150">Odwołania do System.Core.dll dodania do projektu.</span><span class="sxs-lookup"><span data-stu-id="59f89-150">That a reference to System.Core.dll be added to the project.</span></span>

* <span data-ttu-id="59f89-151">Czy następujących przestrzeni nazw można importować:</span><span class="sxs-lookup"><span data-stu-id="59f89-151">That the following namespaces be imported:</span></span>

  [!code-csharp[System.TimeZone2.CreateTimeZone#6](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.CreateTimeZone/cs/System.TimeZone2.CreateTimeZone.cs#6)]
  [!code-vb[System.TimeZone2.CreateTimeZone#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.CreateTimeZone/vb/System.TimeZone2.CreateTimeZone.vb#6)]

## <a name="see-also"></a><span data-ttu-id="59f89-152">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="59f89-152">See also</span></span>

<span data-ttu-id="59f89-153">[Daty, godziny i strefy czasowe](../../../docs/standard/datetime/index.md)
[Przegląd stref czasowych](../../../docs/standard/datetime/time-zone-overview.md)
[porady: tworzenie stref czasowych bez reguł korygowania](../../../docs/standard/datetime/create-time-zones-without-adjustment-rules.md)</span><span class="sxs-lookup"><span data-stu-id="59f89-153">[Dates, times, and time zones](../../../docs/standard/datetime/index.md)
[Time zone overview](../../../docs/standard/datetime/time-zone-overview.md)
[How to: Create time zones without adjustment rules](../../../docs/standard/datetime/create-time-zones-without-adjustment-rules.md)</span></span>
