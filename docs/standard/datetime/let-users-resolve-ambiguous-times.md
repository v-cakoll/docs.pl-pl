---
title: 'Instrukcje: Pozwalanie użytkownikom na rozwiązywanie niejednoznacznych wartości czasu'
ms.date: 04/10/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- time zones [.NET Framework], ambiguous time
- ambiguous time [.NET Framework]
ms.assetid: bca874ee-5b68-4654-8bbd-3711220ef332
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: bf97f1a08c6df13ce639466fc07472926c63987f
ms.sourcegitcommit: 6f28b709592503d27077b16fff2e2eacca569992
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/28/2019
ms.locfileid: "70106623"
---
# <a name="how-to-let-users-resolve-ambiguous-times"></a><span data-ttu-id="587a4-102">Instrukcje: Pozwalanie użytkownikom na rozwiązywanie niejednoznacznych wartości czasu</span><span class="sxs-lookup"><span data-stu-id="587a4-102">How to: Let users resolve ambiguous times</span></span>

<span data-ttu-id="587a4-103">Niejednoznaczny czas to czas, który jest mapowany na więcej niż jeden uniwersalny czas koordynowany (UTC).</span><span class="sxs-lookup"><span data-stu-id="587a4-103">An ambiguous time is a time that maps to more than one Coordinated Universal Time (UTC).</span></span> <span data-ttu-id="587a4-104">Występuje, gdy czas zegara jest dostosowywany do tyłu, na przykład podczas przejścia od czasu letniego strefy czasowej do czasu standardowego.</span><span class="sxs-lookup"><span data-stu-id="587a4-104">It occurs when the clock time is adjusted back in time, such as during the transition from a time zone's daylight saving time to its standard time.</span></span> <span data-ttu-id="587a4-105">Podczas obsługi niejednoznacznego czasu można wykonać jedną z następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="587a4-105">When handling an ambiguous time, you can do one of the following:</span></span>

- <span data-ttu-id="587a4-106">Jeśli niejednoznaczny czas to element danych wprowadzonych przez użytkownika, można opuścić go użytkownikowi, aby rozwiązać niejednoznaczność.</span><span class="sxs-lookup"><span data-stu-id="587a4-106">If the ambiguous time is an item of data entered by the user, you can leave it to the user to resolve the ambiguity.</span></span>

- <span data-ttu-id="587a4-107">Założenie założeń dotyczących sposobu mapowania czasu na czas UTC.</span><span class="sxs-lookup"><span data-stu-id="587a4-107">Make an assumption about how the time maps to UTC.</span></span> <span data-ttu-id="587a4-108">Na przykład można założyć, że niejednoznaczny czas jest zawsze wyrażony w czasie standardowym strefy czasowej.</span><span class="sxs-lookup"><span data-stu-id="587a4-108">For example, you can assume that an ambiguous time is always expressed in the time zone's standard time.</span></span>

<span data-ttu-id="587a4-109">W tym temacie pokazano, jak zezwolić użytkownikowi na rozwiązywanie niejednoznacznego czasu.</span><span class="sxs-lookup"><span data-stu-id="587a4-109">This topic shows how to let a user resolve an ambiguous time.</span></span>

### <a name="to-let-a-user-resolve-an-ambiguous-time"></a><span data-ttu-id="587a4-110">Aby pozwolić użytkownikowi na rozwiązywanie niejednoznacznego czasu</span><span class="sxs-lookup"><span data-stu-id="587a4-110">To let a user resolve an ambiguous time</span></span>

1. <span data-ttu-id="587a4-111">Pobierz datę i godzinę wprowadzania danych przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="587a4-111">Get the date and time input by the user.</span></span>

2. <span data-ttu-id="587a4-112">Wywołaj <xref:System.TimeZoneInfo.IsAmbiguousTime%2A> metodę, aby określić, czy czas jest niejednoznaczny.</span><span class="sxs-lookup"><span data-stu-id="587a4-112">Call the <xref:System.TimeZoneInfo.IsAmbiguousTime%2A> method to determine whether the time is ambiguous.</span></span>

3. <span data-ttu-id="587a4-113">Jeśli czas jest niejednoznaczny, wywołaj <xref:System.TimeZoneInfo.GetAmbiguousTimeOffsets%2A> metodę, aby pobrać <xref:System.TimeSpan> tablicę obiektów.</span><span class="sxs-lookup"><span data-stu-id="587a4-113">If the time is ambiguous, call the <xref:System.TimeZoneInfo.GetAmbiguousTimeOffsets%2A> method to retrieve an array of <xref:System.TimeSpan> objects.</span></span> <span data-ttu-id="587a4-114">Każdy element w tablicy zawiera przesunięcie czasu UTC, do którego można mapować niejednoznaczny czas.</span><span class="sxs-lookup"><span data-stu-id="587a4-114">Each element in the array contains a UTC offset that the ambiguous time can map to.</span></span>

4. <span data-ttu-id="587a4-115">Zezwalaj użytkownikowi na wybranie żądanego przesunięcia.</span><span class="sxs-lookup"><span data-stu-id="587a4-115">Let the user select the desired offset.</span></span>

5. <span data-ttu-id="587a4-116">Pobierz datę i godzinę UTC, odejmując przesunięcie wybrane przez użytkownika od czasu lokalnego.</span><span class="sxs-lookup"><span data-stu-id="587a4-116">Get the UTC date and time by subtracting the offset selected by the user from the local time.</span></span>

6. <span data-ttu-id="587a4-117">`Shared` <xref:System.DateTime.SpecifyKind%2A> <xref:System.DateTime.Kind%2A> Wywołaj metodę <xref:System.DateTimeKind.Utc?displayProperty=nameWithType>(w Visual Basic .NET), aby ustawić właściwość Data i godzina UTC na wartość. `static`</span><span class="sxs-lookup"><span data-stu-id="587a4-117">Call the `static` (`Shared` in Visual Basic .NET) <xref:System.DateTime.SpecifyKind%2A> method to set the UTC date and time value's <xref:System.DateTime.Kind%2A> property to <xref:System.DateTimeKind.Utc?displayProperty=nameWithType>.</span></span>

## <a name="example"></a><span data-ttu-id="587a4-118">Przykład</span><span class="sxs-lookup"><span data-stu-id="587a4-118">Example</span></span>

<span data-ttu-id="587a4-119">Poniższy przykład powoduje, że użytkownik wprowadza datę i godzinę oraz, jeśli jest niejednoznaczny, umożliwia użytkownikowi wybranie czasu UTC, który jest mapowany na.</span><span class="sxs-lookup"><span data-stu-id="587a4-119">The following example prompts the user to enter a date and time and, if it is ambiguous, lets the user select the UTC time that the ambiguous time maps to.</span></span>

[!code-csharp[System.TimeZone2.Concepts#11](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Concepts/CS/TimeZone2Concepts.cs#11)]
[!code-vb[System.TimeZone2.Concepts#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Concepts/VB/TimeZone2Concepts.vb#11)]

<span data-ttu-id="587a4-120">Rdzeń przykładowego kodu używa tablicy <xref:System.TimeSpan> obiektów, aby wskazać możliwe przesunięcie niejednoznaczny czas od czasu UTC.</span><span class="sxs-lookup"><span data-stu-id="587a4-120">The core of the example code uses an array of <xref:System.TimeSpan> objects to indicate possible offsets of the ambiguous time from UTC.</span></span> <span data-ttu-id="587a4-121">Jednak te przesunięcia są mało znaczące dla użytkownika.</span><span class="sxs-lookup"><span data-stu-id="587a4-121">However, these offsets are unlikely to be meaningful to the user.</span></span> <span data-ttu-id="587a4-122">Aby wyjaśnić znaczenie przesunięć, kod również zawiera informacje o tym, czy przesunięcie reprezentuje czas standardowy czasu standardowego lub czasu letniego.</span><span class="sxs-lookup"><span data-stu-id="587a4-122">To clarify the meaning of the offsets, the code also notes whether an offset represents the local time zone's standard time or its daylight saving time.</span></span> <span data-ttu-id="587a4-123">Kod określa, który czas jest standardowy i czas jest okresowy, porównując przesunięcie z wartością <xref:System.TimeZoneInfo.BaseUtcOffset%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="587a4-123">The code determines which time is standard and which time is daylight by comparing the offset with the value of the <xref:System.TimeZoneInfo.BaseUtcOffset%2A> property.</span></span> <span data-ttu-id="587a4-124">Ta właściwość wskazuje różnicę między czasem UTC i strefą czasową (czas standardowy).</span><span class="sxs-lookup"><span data-stu-id="587a4-124">This property indicates the difference between the UTC and the time zone's standard time.</span></span>

<span data-ttu-id="587a4-125">W tym przykładzie wszystkie odwołania do lokalnej strefy czasowej są tworzone przez <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType> Właściwość; lokalna strefa czasowa nigdy nie jest przypisana do zmiennej obiektu.</span><span class="sxs-lookup"><span data-stu-id="587a4-125">In this example, all references to the local time zone are made through the <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType> property; the local time zone is never assigned to an object variable.</span></span> <span data-ttu-id="587a4-126">Jest to zalecane rozwiązanie, ponieważ wywołanie <xref:System.TimeZoneInfo.ClearCachedData%2A?displayProperty=nameWithType> metody unieważnia wszystkie obiekty, do których jest przypisana lokalna strefa czasowa.</span><span class="sxs-lookup"><span data-stu-id="587a4-126">This is a recommended practice because a call to the <xref:System.TimeZoneInfo.ClearCachedData%2A?displayProperty=nameWithType> method invalidates any objects that the local time zone is assigned to.</span></span>

## <a name="compiling-the-code"></a><span data-ttu-id="587a4-127">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="587a4-127">Compiling the code</span></span>

<span data-ttu-id="587a4-128">Ten przykład wymaga:</span><span class="sxs-lookup"><span data-stu-id="587a4-128">This example requires:</span></span>

- <span data-ttu-id="587a4-129">Że przestrzeń nazw ma zostać zaimportowana `using` przy użyciu instrukcji C# (wymaganej w kodzie). <xref:System></span><span class="sxs-lookup"><span data-stu-id="587a4-129">That the <xref:System> namespace be imported with the `using` statement (required in C# code).</span></span>

## <a name="see-also"></a><span data-ttu-id="587a4-130">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="587a4-130">See also</span></span>

- [<span data-ttu-id="587a4-131">Daty, godziny i strefy czasowe</span><span class="sxs-lookup"><span data-stu-id="587a4-131">Dates, times, and time zones</span></span>](../../../docs/standard/datetime/index.md)
- [<span data-ttu-id="587a4-132">Instrukcje: Rozwiązywanie niejednoznacznych czasów</span><span class="sxs-lookup"><span data-stu-id="587a4-132">How to: Resolve ambiguous times</span></span>](../../../docs/standard/datetime/resolve-ambiguous-times.md)
