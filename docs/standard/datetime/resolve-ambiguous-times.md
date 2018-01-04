---
title: "Porady: Rozwiązywanie niejednoznacznych wartości czasu"
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
- time zones [.NET Framework], ambiguous time
- ambiguous time [.NET Framework]
ms.assetid: 2cf5fb25-492c-4875-9245-98cac8348e97
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 251f1914b131c5deed194ad7f3fb068c1d9b27c5
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/23/2017
---
# <a name="how-to-resolve-ambiguous-times"></a><span data-ttu-id="a0a4d-102">Porady: Rozwiązywanie niejednoznacznych wartości czasu</span><span class="sxs-lookup"><span data-stu-id="a0a4d-102">How to: Resolve ambiguous times</span></span>

<span data-ttu-id="a0a4d-103">Niejednoznaczny czas to czas, który mapuje do więcej niż jeden uniwersalny czas koordynowany (UTC).</span><span class="sxs-lookup"><span data-stu-id="a0a4d-103">An ambiguous time is a time that maps to more than one Coordinated Universal Time (UTC).</span></span> <span data-ttu-id="a0a4d-104">Nastąpi to po czas zegara jest uwzględniany w czasie, takie jak podczas przejścia z czasu letniego strefę czasową na jego czas standardowy.</span><span class="sxs-lookup"><span data-stu-id="a0a4d-104">It occurs when the clock time is adjusted back in time, such as during the transition from a time zone's daylight saving time to its standard time.</span></span> <span data-ttu-id="a0a4d-105">Podczas obsługi niejednoznaczny czas, możesz wybrać jedną z następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="a0a4d-105">When handling an ambiguous time, you can do one of the following:</span></span>

* <span data-ttu-id="a0a4d-106">Należy założeń dotyczących sposób mapowania czas UTC.</span><span class="sxs-lookup"><span data-stu-id="a0a4d-106">Make an assumption about how the time maps to UTC.</span></span> <span data-ttu-id="a0a4d-107">Na przykład można założyć, że który niejednoznaczny czas jest zawsze wyrażona w strefie czasowej (czas standardowy).</span><span class="sxs-lookup"><span data-stu-id="a0a4d-107">For example, you can assume that an ambiguous time is always expressed in the time zone's standard time.</span></span>

* <span data-ttu-id="a0a4d-108">Niejednoznaczny czas w przypadku elementu danych wprowadzonych przez użytkownika, można pozostawić go do użytkownika w celu rozwiązania niejednoznaczności.</span><span class="sxs-lookup"><span data-stu-id="a0a4d-108">If the ambiguous time is an item of data entered by the user, you can leave it to the user to resolve the ambiguity.</span></span>

<span data-ttu-id="a0a4d-109">W tym temacie pokazano, jak rozwiązać niejednoznaczny czas przez przy założeniu, że reprezentuje strefy czasowej (czas standardowy).</span><span class="sxs-lookup"><span data-stu-id="a0a4d-109">This topic shows how to resolve an ambiguous time by assuming that it represents the time zone's standard time.</span></span>

### <a name="to-map-an-ambiguous-time-to-a-time-zones-standard-time"></a><span data-ttu-id="a0a4d-110">Aby zamapować niejednoznaczny czas na strefę czasową (czas standardowy)</span><span class="sxs-lookup"><span data-stu-id="a0a4d-110">To map an ambiguous time to a time zone's standard time</span></span>

1. <span data-ttu-id="a0a4d-111">Wywołanie <xref:System.TimeZoneInfo.IsAmbiguousTime%2A> metodę, aby określić, czy czas jest niejednoznaczna.</span><span class="sxs-lookup"><span data-stu-id="a0a4d-111">Call the <xref:System.TimeZoneInfo.IsAmbiguousTime%2A> method to determine whether the time is ambiguous.</span></span>

2. <span data-ttu-id="a0a4d-112">Jeśli czas jest niejednoznaczny, odejmuje wartość czasu od <xref:System.TimeSpan> obiektu zwróconego przez strefę czasową <xref:System.TimeZoneInfo.BaseUtcOffset%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="a0a4d-112">If the time is ambiguous, subtract the time from the <xref:System.TimeSpan> object returned by the time zone's <xref:System.TimeZoneInfo.BaseUtcOffset%2A> property.</span></span>

3. <span data-ttu-id="a0a4d-113">Wywołanie `static` (`Shared` w języku Visual Basic .NET) <xref:System.DateTime.SpecifyKind%2A> metodę, aby ustawić czas UTC daty i godziny wartości <xref:System.DateTime.Kind%2A> właściwości <xref:System.DateTimeKind.Utc?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="a0a4d-113">Call the `static` (`Shared` in Visual Basic .NET) <xref:System.DateTime.SpecifyKind%2A> method to set the UTC date and time value's <xref:System.DateTime.Kind%2A> property to <xref:System.DateTimeKind.Utc?displayProperty=nameWithType>.</span></span>

## <a name="example"></a><span data-ttu-id="a0a4d-114">Przykład</span><span class="sxs-lookup"><span data-stu-id="a0a4d-114">Example</span></span>

<span data-ttu-id="a0a4d-115">Poniższy przykład przedstawia sposób konwertowania niejednoznaczny czas UTC przez przy założeniu, że reprezentuje czas standardowy strefy czasu lokalnego.</span><span class="sxs-lookup"><span data-stu-id="a0a4d-115">The following example illustrates how to convert an ambiguous time to UTC by assuming that it represents the local time zone's standard time.</span></span>

[!code-csharp[System.TimeZone2.Concepts#10](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Concepts/CS/TimeZone2Concepts.cs#10)]
[!code-vb[System.TimeZone2.Concepts#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Concepts/VB/TimeZone2Concepts.vb#10)]

<span data-ttu-id="a0a4d-116">Przykład zawiera metodę o nazwie `ResolveAmbiguousTime` Określa, czy <xref:System.DateTime> wartości przekazywane do niego jest niejednoznaczna.</span><span class="sxs-lookup"><span data-stu-id="a0a4d-116">The example consists of a method named `ResolveAmbiguousTime` that determines whether the <xref:System.DateTime> value passed to it is ambiguous.</span></span> <span data-ttu-id="a0a4d-117">Jeśli wartość jest niejednoznaczny, metoda zwraca <xref:System.DateTime> wartość, która reprezentuje odpowiedni czas UTC.</span><span class="sxs-lookup"><span data-stu-id="a0a4d-117">If the value is ambiguous, the method returns a <xref:System.DateTime> value that represents the corresponding UTC time.</span></span> <span data-ttu-id="a0a4d-118">Metoda obsługi konwersji przez odjęcie wartości lokalnej strefy czasowej <xref:System.TimeZoneInfo.BaseUtcOffset%2A> właściwość z czasem lokalnym.</span><span class="sxs-lookup"><span data-stu-id="a0a4d-118">The method handles this conversion by subtracting the value of the local time zone's <xref:System.TimeZoneInfo.BaseUtcOffset%2A> property from the local time.</span></span>

<span data-ttu-id="a0a4d-119">Zwykle niejednoznaczny czas jest obsługiwany przez wywołanie metody <xref:System.TimeZoneInfo.GetAmbiguousTimeOffsets%2A> metoda pobierania tablicę <xref:System.TimeSpan> obiektów zawierających niejednoznaczny czas UTC możliwe przesunięcia.</span><span class="sxs-lookup"><span data-stu-id="a0a4d-119">Ordinarily, an ambiguous time is handled by calling the <xref:System.TimeZoneInfo.GetAmbiguousTimeOffsets%2A> method to retrieve an array of <xref:System.TimeSpan> objects that contain the ambiguous time's possible UTC offsets.</span></span> <span data-ttu-id="a0a4d-120">Jednak w tym przykładzie powoduje, że dowolnego założenie, że niejednoznaczny czas powinien zawsze być zamapowany na strefie czasowej (czas standardowy).</span><span class="sxs-lookup"><span data-stu-id="a0a4d-120">However, this example makes the arbitrary assumption that an ambiguous time should always be mapped to the time zone's standard time.</span></span> <span data-ttu-id="a0a4d-121"><xref:System.TimeZoneInfo.BaseUtcOffset%2A> Właściwość zwraca przesunięcie UTC i strefy czasowej (czas standardowy).</span><span class="sxs-lookup"><span data-stu-id="a0a4d-121">The <xref:System.TimeZoneInfo.BaseUtcOffset%2A> property returns the offset between UTC and a time zone's standard time.</span></span>

<span data-ttu-id="a0a4d-122">W tym przykładzie wszystkie odwołania do lokalnej strefy czasowej są nawiązywane przy użyciu <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType> właściwości; czasu lokalnego strefy nigdy nie jest przypisany do zmiennej obiektu.</span><span class="sxs-lookup"><span data-stu-id="a0a4d-122">In this example, all references to the local time zone are made through the <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType> property; the local time zone is never assigned to an object variable.</span></span> <span data-ttu-id="a0a4d-123">To jest zalecanym rozwiązaniem, ponieważ wywołanie <xref:System.TimeZoneInfo.ClearCachedData%2A?displayProperty=nameWithType> metody unieważnia żadnych obiektów przypisanych do strefy czasu lokalnego.</span><span class="sxs-lookup"><span data-stu-id="a0a4d-123">This is a recommended practice because a call to the <xref:System.TimeZoneInfo.ClearCachedData%2A?displayProperty=nameWithType> method invalidates any objects that the local time zone is assigned to.</span></span>

## <a name="compiling-the-code"></a><span data-ttu-id="a0a4d-124">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="a0a4d-124">Compiling the code</span></span>

<span data-ttu-id="a0a4d-125">Ten przykład wymaga:</span><span class="sxs-lookup"><span data-stu-id="a0a4d-125">This example requires:</span></span>

* <span data-ttu-id="a0a4d-126">Odwołania do System.Core.dll dodania do projektu.</span><span class="sxs-lookup"><span data-stu-id="a0a4d-126">That a reference to System.Core.dll be added to the project.</span></span>

* <span data-ttu-id="a0a4d-127">Czy <xref:System> przestrzeni nazw można zaimportować z `using` instrukcji (wymagane w kodzie języka C#).</span><span class="sxs-lookup"><span data-stu-id="a0a4d-127">That the <xref:System> namespace be imported with the `using` statement (required in C# code).</span></span>

## <a name="see-also"></a><span data-ttu-id="a0a4d-128">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a0a4d-128">See also</span></span>

<span data-ttu-id="a0a4d-129">[Daty, godziny i strefy czasowe](../../../docs/standard/datetime/index.md)
[porady: zezwala użytkownikom na rozwiązywanie niejednoznacznych wartości czasu](../../../docs/standard/datetime/let-users-resolve-ambiguous-times.md)</span><span class="sxs-lookup"><span data-stu-id="a0a4d-129">[Dates, times, and time zones](../../../docs/standard/datetime/index.md)
[How to: Let users resolve ambiguous times](../../../docs/standard/datetime/let-users-resolve-ambiguous-times.md)</span></span>
