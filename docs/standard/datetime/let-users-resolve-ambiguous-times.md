---
title: "Porady: zezwala użytkownikom na rozwiązywanie niejednoznacznych wartości czasu"
ms.custom: 
ms.date: 04/10/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- time zones [.NET Framework], ambiguous time
- ambiguous time [.NET Framework]
ms.assetid: bca874ee-5b68-4654-8bbd-3711220ef332
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 6409e676944f64931b197fda1a6a7b392c268c97
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-let-users-resolve-ambiguous-times"></a><span data-ttu-id="3be23-102">Porady: zezwala użytkownikom na rozwiązywanie niejednoznacznych wartości czasu</span><span class="sxs-lookup"><span data-stu-id="3be23-102">How to: Let users resolve ambiguous times</span></span>

<span data-ttu-id="3be23-103">Niejednoznaczny czas to czas, który mapuje do więcej niż jeden uniwersalny czas koordynowany (UTC).</span><span class="sxs-lookup"><span data-stu-id="3be23-103">An ambiguous time is a time that maps to more than one Coordinated Universal Time (UTC).</span></span> <span data-ttu-id="3be23-104">Nastąpi to po czas zegara jest uwzględniany w czasie, takie jak podczas przejścia z czasu letniego strefę czasową na jego czas standardowy.</span><span class="sxs-lookup"><span data-stu-id="3be23-104">It occurs when the clock time is adjusted back in time, such as during the transition from a time zone's daylight saving time to its standard time.</span></span> <span data-ttu-id="3be23-105">Podczas obsługi niejednoznaczny czas, możesz wybrać jedną z następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="3be23-105">When handling an ambiguous time, you can do one of the following:</span></span>

* <span data-ttu-id="3be23-106">Niejednoznaczny czas w przypadku elementu danych wprowadzonych przez użytkownika, można pozostawić go do użytkownika w celu rozwiązania niejednoznaczności.</span><span class="sxs-lookup"><span data-stu-id="3be23-106">If the ambiguous time is an item of data entered by the user, you can leave it to the user to resolve the ambiguity.</span></span>

* <span data-ttu-id="3be23-107">Należy założeń dotyczących sposób mapowania czas UTC.</span><span class="sxs-lookup"><span data-stu-id="3be23-107">Make an assumption about how the time maps to UTC.</span></span> <span data-ttu-id="3be23-108">Na przykład można założyć, że który niejednoznaczny czas jest zawsze wyrażona w strefie czasowej (czas standardowy).</span><span class="sxs-lookup"><span data-stu-id="3be23-108">For example, you can assume that an ambiguous time is always expressed in the time zone's standard time.</span></span>

<span data-ttu-id="3be23-109">W tym temacie przedstawiono sposób umożliwia użytkownikowi niejednoznaczny czas rozpoznania.</span><span class="sxs-lookup"><span data-stu-id="3be23-109">This topic shows how to let a user resolve an ambiguous time.</span></span>

### <a name="to-let-a-user-resolve-an-ambiguous-time"></a><span data-ttu-id="3be23-110">Aby umożliwić użytkownikowi rozwiązać niejednoznaczny czas</span><span class="sxs-lookup"><span data-stu-id="3be23-110">To let a user resolve an ambiguous time</span></span>

1. <span data-ttu-id="3be23-111">Pobierz datę i godzinę wejściowych przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="3be23-111">Get the date and time input by the user.</span></span>

2. <span data-ttu-id="3be23-112">Wywołanie <xref:System.TimeZoneInfo.IsAmbiguousTime%2A> metodę, aby określić, czy czas jest niejednoznaczna.</span><span class="sxs-lookup"><span data-stu-id="3be23-112">Call the <xref:System.TimeZoneInfo.IsAmbiguousTime%2A> method to determine whether the time is ambiguous.</span></span>

3. <span data-ttu-id="3be23-113">Jeśli czas jest niejednoznaczny, wywołanie <xref:System.TimeZoneInfo.GetAmbiguousTimeOffsets%2A> metoda pobierania tablicę <xref:System.TimeSpan> obiektów.</span><span class="sxs-lookup"><span data-stu-id="3be23-113">If the time is ambiguous, call the <xref:System.TimeZoneInfo.GetAmbiguousTimeOffsets%2A> method to retrieve an array of <xref:System.TimeSpan> objects.</span></span> <span data-ttu-id="3be23-114">Każdy element w tablicy zawiera przesunięcie czasu UTC, który można mapować niejednoznaczny czas.</span><span class="sxs-lookup"><span data-stu-id="3be23-114">Each element in the array contains a UTC offset that the ambiguous time can map to.</span></span>

4. <span data-ttu-id="3be23-115">Poinformuj użytkowników wybierz żądane przesunięcie.</span><span class="sxs-lookup"><span data-stu-id="3be23-115">Let the user select the desired offset.</span></span>

5. <span data-ttu-id="3be23-116">Pobierz Data i Godzina UTC przez odjęcie przesunięcie wybrane przez użytkownika z czasem lokalnym.</span><span class="sxs-lookup"><span data-stu-id="3be23-116">Get the UTC date and time by subtracting the offset selected by the user from the local time.</span></span>

6. <span data-ttu-id="3be23-117">Wywołanie `static` (`Shared` w języku Visual Basic .NET) <xref:System.DateTime.SpecifyKind%2A> metodę, aby ustawić czas UTC daty i godziny wartości <xref:System.DateTime.Kind%2A> właściwości <xref:System.DateTimeKind.Utc?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="3be23-117">Call the `static` (`Shared` in Visual Basic .NET) <xref:System.DateTime.SpecifyKind%2A> method to set the UTC date and time value's <xref:System.DateTime.Kind%2A> property to <xref:System.DateTimeKind.Utc?displayProperty=nameWithType>.</span></span>

## <a name="example"></a><span data-ttu-id="3be23-118">Przykład</span><span class="sxs-lookup"><span data-stu-id="3be23-118">Example</span></span>

<span data-ttu-id="3be23-119">W poniższym przykładzie monituje użytkownika o wprowadź datę i godzinę i, jeśli jest niejednoznaczny, umożliwia użytkownikowi wybieranie niejednoznaczny czas mapowana na czas UTC.</span><span class="sxs-lookup"><span data-stu-id="3be23-119">The following example prompts the user to enter a date and time and, if it is ambiguous, lets the user select the UTC time that the ambiguous time maps to.</span></span>

[!code-csharp[System.TimeZone2.Concepts#11](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Concepts/CS/TimeZone2Concepts.cs#11)]
[!code-vb[System.TimeZone2.Concepts#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Concepts/VB/TimeZone2Concepts.vb#11)]

<span data-ttu-id="3be23-120">Podstawowy przykład kodu wykorzystuje tablicę <xref:System.TimeSpan> obiektów, aby wskazać możliwe przesunięcia niejednoznaczny czas od czasu UTC.</span><span class="sxs-lookup"><span data-stu-id="3be23-120">The core of the example code uses an array of <xref:System.TimeSpan> objects to indicate possible offsets of the ambiguous time from UTC.</span></span> <span data-ttu-id="3be23-121">Jednak przesunięcia prawdopodobnie nie jest zrozumiały dla użytkownika.</span><span class="sxs-lookup"><span data-stu-id="3be23-121">However, these offsets are unlikely to be meaningful to the user.</span></span> <span data-ttu-id="3be23-122">Wyjaśnienie przesunięcia, kod uwagi również, czy przesunięcie reprezentuje strefy czasu lokalnego (czas standardowy) lub jego czasu letniego.</span><span class="sxs-lookup"><span data-stu-id="3be23-122">To clarify the meaning of the offsets, the code also notes whether an offset represents the local time zone's standard time or its daylight saving time.</span></span> <span data-ttu-id="3be23-123">Kod określa czas, który jest standardem, a które czas letni porównując przesunięcie z wartością <xref:System.TimeZoneInfo.BaseUtcOffset%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="3be23-123">The code determines which time is standard and which time is daylight by comparing the offset with the value of the <xref:System.TimeZoneInfo.BaseUtcOffset%2A> property.</span></span> <span data-ttu-id="3be23-124">Ta właściwość wskazuje różnicę między czasem UTC i strefy czasowej (czas standardowy).</span><span class="sxs-lookup"><span data-stu-id="3be23-124">This property indicates the difference between the UTC and the time zone's standard time.</span></span>

<span data-ttu-id="3be23-125">W tym przykładzie wszystkie odwołania do lokalnej strefy czasowej są nawiązywane przy użyciu <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType> właściwości; czasu lokalnego strefy nigdy nie jest przypisany do zmiennej obiektu.</span><span class="sxs-lookup"><span data-stu-id="3be23-125">In this example, all references to the local time zone are made through the <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType> property; the local time zone is never assigned to an object variable.</span></span> <span data-ttu-id="3be23-126">To jest zalecanym rozwiązaniem, ponieważ wywołanie <xref:System.TimeZoneInfo.ClearCachedData%2A?displayProperty=nameWithType> metody unieważnia żadnych obiektów przypisanych do strefy czasu lokalnego.</span><span class="sxs-lookup"><span data-stu-id="3be23-126">This is a recommended practice because a call to the <xref:System.TimeZoneInfo.ClearCachedData%2A?displayProperty=nameWithType> method invalidates any objects that the local time zone is assigned to.</span></span>

## <a name="compiling-the-code"></a><span data-ttu-id="3be23-127">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="3be23-127">Compiling the code</span></span>

<span data-ttu-id="3be23-128">Ten przykład wymaga:</span><span class="sxs-lookup"><span data-stu-id="3be23-128">This example requires:</span></span>

* <span data-ttu-id="3be23-129">Odwołania do System.Core.dll dodania do projektu.</span><span class="sxs-lookup"><span data-stu-id="3be23-129">That a reference to System.Core.dll be added to the project.</span></span>

* <span data-ttu-id="3be23-130">Czy <xref:System> przestrzeni nazw można zaimportować z `using` instrukcji (wymagane w kodzie języka C#).</span><span class="sxs-lookup"><span data-stu-id="3be23-130">That the <xref:System> namespace be imported with the `using` statement (required in C# code).</span></span>

## <a name="see-also"></a><span data-ttu-id="3be23-131">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="3be23-131">See also</span></span>

<span data-ttu-id="3be23-132">[Daty, godziny i strefy czasowe](../../../docs/standard/datetime/index.md)
[porady: Rozwiązywanie niejednoznacznych wartości czasu](../../../docs/standard/datetime/resolve-ambiguous-times.md)</span><span class="sxs-lookup"><span data-stu-id="3be23-132">[Dates, times, and time zones](../../../docs/standard/datetime/index.md)
[How to: Resolve ambiguous times](../../../docs/standard/datetime/resolve-ambiguous-times.md)</span></span>
