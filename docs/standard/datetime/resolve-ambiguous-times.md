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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1c98f47613479c40804dce254261c560d829d91c
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/14/2019
ms.locfileid: "65586359"
---
# <a name="how-to-resolve-ambiguous-times"></a><span data-ttu-id="b41ec-102">Instrukcje: Rozwiązywanie niejednoznacznych wartości czasu</span><span class="sxs-lookup"><span data-stu-id="b41ec-102">How to: Resolve ambiguous times</span></span>

<span data-ttu-id="b41ec-103">Niejednoznaczny czas to czas, który mapuje do więcej niż jeden uniwersalnego czasu koordynowanego (UTC).</span><span class="sxs-lookup"><span data-stu-id="b41ec-103">An ambiguous time is a time that maps to more than one Coordinated Universal Time (UTC).</span></span> <span data-ttu-id="b41ec-104">Występuje ona, gdy czas zegara jest uwzględniany w czasie, takie jak podczas przechodzenia na strefę czasową czasu jego (czas standardowy).</span><span class="sxs-lookup"><span data-stu-id="b41ec-104">It occurs when the clock time is adjusted back in time, such as during the transition from a time zone's daylight saving time to its standard time.</span></span> <span data-ttu-id="b41ec-105">Podczas obsługi niejednoznaczny czas, możesz wykonać jedną z następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="b41ec-105">When handling an ambiguous time, you can do one of the following:</span></span>

* <span data-ttu-id="b41ec-106">Należy z założenia na temat sposobu mapowania czasu UTC.</span><span class="sxs-lookup"><span data-stu-id="b41ec-106">Make an assumption about how the time maps to UTC.</span></span> <span data-ttu-id="b41ec-107">Na przykład można założyć, że że niejednoznaczny czas jest zawsze wyrażona w strefie czasowej (czas standardowy).</span><span class="sxs-lookup"><span data-stu-id="b41ec-107">For example, you can assume that an ambiguous time is always expressed in the time zone's standard time.</span></span>

* <span data-ttu-id="b41ec-108">Niejednoznaczny czas w przypadku elementu danych wprowadzonych przez użytkownika, można pozostawić go do użytkownika, aby rozstrzygnąć niejednoznaczność.</span><span class="sxs-lookup"><span data-stu-id="b41ec-108">If the ambiguous time is an item of data entered by the user, you can leave it to the user to resolve the ambiguity.</span></span>

<span data-ttu-id="b41ec-109">W tym temacie przedstawiono sposób niejednoznaczny czas, przez rozwiązania, przy założeniu, że reprezentuje strefy czasowej (czas standardowy).</span><span class="sxs-lookup"><span data-stu-id="b41ec-109">This topic shows how to resolve an ambiguous time by assuming that it represents the time zone's standard time.</span></span>

### <a name="to-map-an-ambiguous-time-to-a-time-zones-standard-time"></a><span data-ttu-id="b41ec-110">Aby zamapować niejednoznaczny czas na strefy czasowej (czas standardowy)</span><span class="sxs-lookup"><span data-stu-id="b41ec-110">To map an ambiguous time to a time zone's standard time</span></span>

1. <span data-ttu-id="b41ec-111">Wywołaj <xref:System.TimeZoneInfo.IsAmbiguousTime%2A> metodę pozwala ustalić, czy czas jest niejednoznaczna.</span><span class="sxs-lookup"><span data-stu-id="b41ec-111">Call the <xref:System.TimeZoneInfo.IsAmbiguousTime%2A> method to determine whether the time is ambiguous.</span></span>

2. <span data-ttu-id="b41ec-112">Jeśli czas jest niejednoznaczny, Odejmij czasu od <xref:System.TimeSpan> obiektu zwróconego przez strefę czasową <xref:System.TimeZoneInfo.BaseUtcOffset%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="b41ec-112">If the time is ambiguous, subtract the time from the <xref:System.TimeSpan> object returned by the time zone's <xref:System.TimeZoneInfo.BaseUtcOffset%2A> property.</span></span>

3. <span data-ttu-id="b41ec-113">Wywołaj `static` (`Shared` w języku Visual Basic .NET) <xref:System.DateTime.SpecifyKind%2A> metodę, aby ustawić UTC daty i godziny wartości <xref:System.DateTime.Kind%2A> właściwość <xref:System.DateTimeKind.Utc?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="b41ec-113">Call the `static` (`Shared` in Visual Basic .NET) <xref:System.DateTime.SpecifyKind%2A> method to set the UTC date and time value's <xref:System.DateTime.Kind%2A> property to <xref:System.DateTimeKind.Utc?displayProperty=nameWithType>.</span></span>

## <a name="example"></a><span data-ttu-id="b41ec-114">Przykład</span><span class="sxs-lookup"><span data-stu-id="b41ec-114">Example</span></span>

<span data-ttu-id="b41ec-115">Poniższy przykład ilustruje sposób konwertowania niejednoznaczny czas UTC, przy założeniu, że reprezentuje czas standardowy strefy czasu lokalnego.</span><span class="sxs-lookup"><span data-stu-id="b41ec-115">The following example illustrates how to convert an ambiguous time to UTC by assuming that it represents the local time zone's standard time.</span></span>

[!code-csharp[System.TimeZone2.Concepts#10](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Concepts/CS/TimeZone2Concepts.cs#10)]
[!code-vb[System.TimeZone2.Concepts#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Concepts/VB/TimeZone2Concepts.vb#10)]

<span data-ttu-id="b41ec-116">Przykład zawiera metodę o nazwie `ResolveAmbiguousTime` określający, czy <xref:System.DateTime> wartością przekazywaną do niego jest niejednoznaczna.</span><span class="sxs-lookup"><span data-stu-id="b41ec-116">The example consists of a method named `ResolveAmbiguousTime` that determines whether the <xref:System.DateTime> value passed to it is ambiguous.</span></span> <span data-ttu-id="b41ec-117">Jeśli wartość jest niejednoznaczny, metoda zwraca <xref:System.DateTime> wartość, która reprezentuje odpowiedni czas UTC.</span><span class="sxs-lookup"><span data-stu-id="b41ec-117">If the value is ambiguous, the method returns a <xref:System.DateTime> value that represents the corresponding UTC time.</span></span> <span data-ttu-id="b41ec-118">Ta konwersja jest obsługiwała przez odjęcie wartości lokalnej strefy czasowej <xref:System.TimeZoneInfo.BaseUtcOffset%2A> właściwości od czasu lokalnego.</span><span class="sxs-lookup"><span data-stu-id="b41ec-118">The method handles this conversion by subtracting the value of the local time zone's <xref:System.TimeZoneInfo.BaseUtcOffset%2A> property from the local time.</span></span>

<span data-ttu-id="b41ec-119">Zazwyczaj niejednoznaczny czas odbywa się przez wywołanie metody <xref:System.TimeZoneInfo.GetAmbiguousTimeOffsets%2A> metodę, która pobierze tablicę <xref:System.TimeSpan> obiektów, które zawierają niejednoznaczny czas UTC możliwe przesunięcia.</span><span class="sxs-lookup"><span data-stu-id="b41ec-119">Ordinarily, an ambiguous time is handled by calling the <xref:System.TimeZoneInfo.GetAmbiguousTimeOffsets%2A> method to retrieve an array of <xref:System.TimeSpan> objects that contain the ambiguous time's possible UTC offsets.</span></span> <span data-ttu-id="b41ec-120">Jednak w tym przykładzie sprawia, że dowolne założenie, że niejednoznaczny czas zawsze powinien być mapowany do strefy czasowej (czas standardowy).</span><span class="sxs-lookup"><span data-stu-id="b41ec-120">However, this example makes the arbitrary assumption that an ambiguous time should always be mapped to the time zone's standard time.</span></span> <span data-ttu-id="b41ec-121"><xref:System.TimeZoneInfo.BaseUtcOffset%2A> Właściwość zwraca przesunięcie między czasem UTC i strefy czasowej (czas standardowy).</span><span class="sxs-lookup"><span data-stu-id="b41ec-121">The <xref:System.TimeZoneInfo.BaseUtcOffset%2A> property returns the offset between UTC and a time zone's standard time.</span></span>

<span data-ttu-id="b41ec-122">W tym przykładzie wszystkie odwołania do lokalnej strefy czasowej są nawiązywane przy użyciu <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType> właściwości; czas lokalny strefy nigdy nie jest przypisany do zmiennej obiektu.</span><span class="sxs-lookup"><span data-stu-id="b41ec-122">In this example, all references to the local time zone are made through the <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType> property; the local time zone is never assigned to an object variable.</span></span> <span data-ttu-id="b41ec-123">Jest zalecanym rozwiązaniem, ponieważ wywołanie <xref:System.TimeZoneInfo.ClearCachedData%2A?displayProperty=nameWithType> metoda unieważnia żadnych obiektów przypisanych do lokalnej strefy czasowej.</span><span class="sxs-lookup"><span data-stu-id="b41ec-123">This is a recommended practice because a call to the <xref:System.TimeZoneInfo.ClearCachedData%2A?displayProperty=nameWithType> method invalidates any objects that the local time zone is assigned to.</span></span>

## <a name="compiling-the-code"></a><span data-ttu-id="b41ec-124">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="b41ec-124">Compiling the code</span></span>

<span data-ttu-id="b41ec-125">Ten przykład wymaga:</span><span class="sxs-lookup"><span data-stu-id="b41ec-125">This example requires:</span></span>

* <span data-ttu-id="b41ec-126">Czy <xref:System> zaimportowane wraz z przestrzeni nazw `using` — instrukcja (wymagane w kodzie języka C#).</span><span class="sxs-lookup"><span data-stu-id="b41ec-126">That the <xref:System> namespace be imported with the `using` statement (required in C# code).</span></span>

## <a name="see-also"></a><span data-ttu-id="b41ec-127">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b41ec-127">See also</span></span>

- [<span data-ttu-id="b41ec-128">Daty, godziny i strefy czasowe</span><span class="sxs-lookup"><span data-stu-id="b41ec-128">Dates, times, and time zones</span></span>](../../../docs/standard/datetime/index.md)
- [<span data-ttu-id="b41ec-129">Instrukcje: Zezwala użytkownikom na rozwiązywanie niejednoznacznych wartości czasu</span><span class="sxs-lookup"><span data-stu-id="b41ec-129">How to: Let users resolve ambiguous times</span></span>](../../../docs/standard/datetime/let-users-resolve-ambiguous-times.md)
