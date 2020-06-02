---
title: 'Instrukcje: Rozwiązywanie niejednoznacznych wartości czasu'
ms.date: 04/10/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- time zones [.NET Framework], ambiguous time
- ambiguous time [.NET Framework]
ms.assetid: 2cf5fb25-492c-4875-9245-98cac8348e97
ms.openlocfilehash: ad69c0984a9d8c01ebd2198486cd0f6492a6116e
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/02/2020
ms.locfileid: "84281508"
---
# <a name="how-to-resolve-ambiguous-times"></a><span data-ttu-id="235c1-102">Instrukcje: Rozwiązywanie niejednoznacznych wartości czasu</span><span class="sxs-lookup"><span data-stu-id="235c1-102">How to: Resolve ambiguous times</span></span>

<span data-ttu-id="235c1-103">Niejednoznaczny czas to czas, który jest mapowany na więcej niż jeden uniwersalny czas koordynowany (UTC).</span><span class="sxs-lookup"><span data-stu-id="235c1-103">An ambiguous time is a time that maps to more than one Coordinated Universal Time (UTC).</span></span> <span data-ttu-id="235c1-104">Występuje, gdy czas zegara jest dostosowywany do tyłu, na przykład podczas przejścia od czasu letniego strefy czasowej do czasu standardowego.</span><span class="sxs-lookup"><span data-stu-id="235c1-104">It occurs when the clock time is adjusted back in time, such as during the transition from a time zone's daylight saving time to its standard time.</span></span> <span data-ttu-id="235c1-105">Podczas obsługi niejednoznacznego czasu można wykonać jedną z następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="235c1-105">When handling an ambiguous time, you can do one of the following:</span></span>

- <span data-ttu-id="235c1-106">Założenie założeń dotyczących sposobu mapowania czasu na czas UTC.</span><span class="sxs-lookup"><span data-stu-id="235c1-106">Make an assumption about how the time maps to UTC.</span></span> <span data-ttu-id="235c1-107">Na przykład można założyć, że niejednoznaczny czas jest zawsze wyrażony w czasie standardowym strefy czasowej.</span><span class="sxs-lookup"><span data-stu-id="235c1-107">For example, you can assume that an ambiguous time is always expressed in the time zone's standard time.</span></span>

- <span data-ttu-id="235c1-108">Jeśli niejednoznaczny czas to element danych wprowadzonych przez użytkownika, można opuścić go użytkownikowi, aby rozwiązać niejednoznaczność.</span><span class="sxs-lookup"><span data-stu-id="235c1-108">If the ambiguous time is an item of data entered by the user, you can leave it to the user to resolve the ambiguity.</span></span>

<span data-ttu-id="235c1-109">W tym temacie pokazano, jak rozpoznać niejednoznaczny czas przez założenie, że reprezentuje czas standardowy strefy czasowej.</span><span class="sxs-lookup"><span data-stu-id="235c1-109">This topic shows how to resolve an ambiguous time by assuming that it represents the time zone's standard time.</span></span>

### <a name="to-map-an-ambiguous-time-to-a-time-zones-standard-time"></a><span data-ttu-id="235c1-110">Aby zamapować niejednoznaczny czas na czas standardowy strefy czasowej</span><span class="sxs-lookup"><span data-stu-id="235c1-110">To map an ambiguous time to a time zone's standard time</span></span>

1. <span data-ttu-id="235c1-111">Wywołaj <xref:System.TimeZoneInfo.IsAmbiguousTime%2A> metodę, aby określić, czy czas jest niejednoznaczny.</span><span class="sxs-lookup"><span data-stu-id="235c1-111">Call the <xref:System.TimeZoneInfo.IsAmbiguousTime%2A> method to determine whether the time is ambiguous.</span></span>

2. <span data-ttu-id="235c1-112">Jeśli czas jest niejednoznaczny, Odejmij czas od <xref:System.TimeSpan> obiektu zwróconego przez właściwość strefy czasowej <xref:System.TimeZoneInfo.BaseUtcOffset%2A> .</span><span class="sxs-lookup"><span data-stu-id="235c1-112">If the time is ambiguous, subtract the time from the <xref:System.TimeSpan> object returned by the time zone's <xref:System.TimeZoneInfo.BaseUtcOffset%2A> property.</span></span>

3. <span data-ttu-id="235c1-113">Wywołaj `static` `Shared` metodę (w Visual Basic .NET), <xref:System.DateTime.SpecifyKind%2A> Aby ustawić właściwość Data i godzina UTC <xref:System.DateTime.Kind%2A> na wartość <xref:System.DateTimeKind.Utc?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="235c1-113">Call the `static` (`Shared` in Visual Basic .NET) <xref:System.DateTime.SpecifyKind%2A> method to set the UTC date and time value's <xref:System.DateTime.Kind%2A> property to <xref:System.DateTimeKind.Utc?displayProperty=nameWithType>.</span></span>

## <a name="example"></a><span data-ttu-id="235c1-114">Przykład</span><span class="sxs-lookup"><span data-stu-id="235c1-114">Example</span></span>

<span data-ttu-id="235c1-115">Poniższy przykład ilustruje sposób konwertowania niejednoznacznego czasu na czas UTC przez założenie, że reprezentuje on lokalną strefę czasową.</span><span class="sxs-lookup"><span data-stu-id="235c1-115">The following example illustrates how to convert an ambiguous time to UTC by assuming that it represents the local time zone's standard time.</span></span>

[!code-csharp[System.TimeZone2.Concepts#10](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Concepts/CS/TimeZone2Concepts.cs#10)]
[!code-vb[System.TimeZone2.Concepts#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Concepts/VB/TimeZone2Concepts.vb#10)]

<span data-ttu-id="235c1-116">Przykład składa się z metody o nazwie `ResolveAmbiguousTime` , która określa, czy <xref:System.DateTime> wartość przeniesiona do niej jest niejednoznaczna.</span><span class="sxs-lookup"><span data-stu-id="235c1-116">The example consists of a method named `ResolveAmbiguousTime` that determines whether the <xref:System.DateTime> value passed to it is ambiguous.</span></span> <span data-ttu-id="235c1-117">Jeśli wartość jest niejednoznaczna, metoda zwraca <xref:System.DateTime> wartość, która reprezentuje odpowiadający czas UTC.</span><span class="sxs-lookup"><span data-stu-id="235c1-117">If the value is ambiguous, the method returns a <xref:System.DateTime> value that represents the corresponding UTC time.</span></span> <span data-ttu-id="235c1-118">Metoda obsługuje tę konwersję poprzez odjęcie wartości właściwości lokalnej strefy czasowej <xref:System.TimeZoneInfo.BaseUtcOffset%2A> od czasu lokalnego.</span><span class="sxs-lookup"><span data-stu-id="235c1-118">The method handles this conversion by subtracting the value of the local time zone's <xref:System.TimeZoneInfo.BaseUtcOffset%2A> property from the local time.</span></span>

<span data-ttu-id="235c1-119">Zwykle niejednoznaczny czas jest obsługiwany przez wywołanie <xref:System.TimeZoneInfo.GetAmbiguousTimeOffsets%2A> metody w celu pobrania tablicy <xref:System.TimeSpan> obiektów, które zawierają niejednoznaczne możliwe przesunięcie czasu UTC.</span><span class="sxs-lookup"><span data-stu-id="235c1-119">Ordinarily, an ambiguous time is handled by calling the <xref:System.TimeZoneInfo.GetAmbiguousTimeOffsets%2A> method to retrieve an array of <xref:System.TimeSpan> objects that contain the ambiguous time's possible UTC offsets.</span></span> <span data-ttu-id="235c1-120">Jednak w tym przykładzie to arbitralne założenie, że niejednoznaczny czas powinien być zawsze mapowany do czasu standardowego strefy czasowej.</span><span class="sxs-lookup"><span data-stu-id="235c1-120">However, this example makes the arbitrary assumption that an ambiguous time should always be mapped to the time zone's standard time.</span></span> <span data-ttu-id="235c1-121"><xref:System.TimeZoneInfo.BaseUtcOffset%2A>Właściwość zwraca przesunięcie między czasem UTC i strefą czasową (czas standardowy).</span><span class="sxs-lookup"><span data-stu-id="235c1-121">The <xref:System.TimeZoneInfo.BaseUtcOffset%2A> property returns the offset between UTC and a time zone's standard time.</span></span>

<span data-ttu-id="235c1-122">W tym przykładzie wszystkie odwołania do lokalnej strefy czasowej są tworzone przez <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType> Właściwość; lokalna strefa czasowa nigdy nie jest przypisana do zmiennej obiektu.</span><span class="sxs-lookup"><span data-stu-id="235c1-122">In this example, all references to the local time zone are made through the <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType> property; the local time zone is never assigned to an object variable.</span></span> <span data-ttu-id="235c1-123">Jest to zalecane rozwiązanie, ponieważ wywołanie <xref:System.TimeZoneInfo.ClearCachedData%2A?displayProperty=nameWithType> metody unieważnia wszystkie obiekty, do których jest przypisana lokalna strefa czasowa.</span><span class="sxs-lookup"><span data-stu-id="235c1-123">This is a recommended practice because a call to the <xref:System.TimeZoneInfo.ClearCachedData%2A?displayProperty=nameWithType> method invalidates any objects that the local time zone is assigned to.</span></span>

## <a name="compiling-the-code"></a><span data-ttu-id="235c1-124">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="235c1-124">Compiling the code</span></span>

<span data-ttu-id="235c1-125">Ten przykład wymaga:</span><span class="sxs-lookup"><span data-stu-id="235c1-125">This example requires:</span></span>

- <span data-ttu-id="235c1-126">Że <xref:System> przestrzeń nazw ma zostać zaimportowana przy użyciu `using` instrukcji (wymaganej w kodzie C#).</span><span class="sxs-lookup"><span data-stu-id="235c1-126">That the <xref:System> namespace be imported with the `using` statement (required in C# code).</span></span>

## <a name="see-also"></a><span data-ttu-id="235c1-127">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="235c1-127">See also</span></span>

- [<span data-ttu-id="235c1-128">Daty, godziny i strefy czasowe</span><span class="sxs-lookup"><span data-stu-id="235c1-128">Dates, times, and time zones</span></span>](index.md)
- [<span data-ttu-id="235c1-129">Instrukcje: Pozwalanie użytkownikom na rozwiązywanie niejednoznacznych wartości czasu</span><span class="sxs-lookup"><span data-stu-id="235c1-129">How to: Let users resolve ambiguous times</span></span>](let-users-resolve-ambiguous-times.md)
