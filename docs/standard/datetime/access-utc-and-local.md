---
title: 'Instrukcje: Uzyskiwanie dostępu do wstępnie zdefiniowanych obiektów lokalnej strefy czasowej i strefy czasowej UTC'
ms.date: 04/10/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- time zones [.NET Framework], local
- predefined time zones
- UTC times, predefined
- local time zone access
- time zones [.NET Framework], retrieving
- time zones [.NET Framework], UTC
ms.assetid: 961fb70b-83f0-4dab-a042-cb5fcd817cf5
ms.openlocfilehash: ebb07800b2a35f4faf312dc55b8c5679079b4b68
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/02/2020
ms.locfileid: "84291412"
---
# <a name="how-to-access-the-predefined-utc-and-local-time-zone-objects"></a><span data-ttu-id="66c01-102">Instrukcje: Uzyskiwanie dostępu do wstępnie zdefiniowanych obiektów lokalnej strefy czasowej i strefy czasowej UTC</span><span class="sxs-lookup"><span data-stu-id="66c01-102">How to: Access the predefined UTC and local time zone objects</span></span>

<span data-ttu-id="66c01-103"><xref:System.TimeZoneInfo>Klasa zawiera dwie właściwości <xref:System.TimeZoneInfo.Utc%2A> i <xref:System.TimeZoneInfo.Local%2A> , które dają kod dostępu do wstępnie zdefiniowanych obiektów stref czasowych.</span><span class="sxs-lookup"><span data-stu-id="66c01-103">The <xref:System.TimeZoneInfo> class provides two properties, <xref:System.TimeZoneInfo.Utc%2A> and <xref:System.TimeZoneInfo.Local%2A>, that give your code access to predefined time zone objects.</span></span> <span data-ttu-id="66c01-104">W tym temacie omówiono sposób uzyskiwania dostępu do <xref:System.TimeZoneInfo> obiektów zwracanych przez te właściwości.</span><span class="sxs-lookup"><span data-stu-id="66c01-104">This topic discusses how to access the <xref:System.TimeZoneInfo> objects returned by those properties.</span></span>

### <a name="to-access-the-coordinated-universal-time-utc-timezoneinfo-object"></a><span data-ttu-id="66c01-105">Aby uzyskać dostęp do obiektu TimeZoneInfo skoordynowanego czasu uniwersalnego (UTC)</span><span class="sxs-lookup"><span data-stu-id="66c01-105">To access the Coordinated Universal Time (UTC) TimeZoneInfo object</span></span>

1. <span data-ttu-id="66c01-106">`static` `Shared` <xref:System.TimeZoneInfo.Utc%2A?displayProperty=nameWithType> Aby uzyskać dostęp do uniwersalnego czasu koordynowanego, użyj właściwości (w Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="66c01-106">Use the `static` (`Shared` in Visual Basic) <xref:System.TimeZoneInfo.Utc%2A?displayProperty=nameWithType> property to access Coordinated Universal Time.</span></span>

2. <span data-ttu-id="66c01-107">Zamiast przypisywać <xref:System.TimeZoneInfo> obiekt zwracany przez właściwość do zmiennej obiektu, Kontynuuj dostęp do uniwersalnego czasu koordynowanego za pomocą <xref:System.TimeZoneInfo.Utc%2A?displayProperty=nameWithType> właściwości.</span><span class="sxs-lookup"><span data-stu-id="66c01-107">Rather than assigning the <xref:System.TimeZoneInfo> object returned by the property to an object variable, continue to access Coordinated Universal Time through the <xref:System.TimeZoneInfo.Utc%2A?displayProperty=nameWithType> property.</span></span>

### <a name="to-access-the-local-time-zone"></a><span data-ttu-id="66c01-108">Aby uzyskać dostęp do lokalnej strefy czasowej</span><span class="sxs-lookup"><span data-stu-id="66c01-108">To access the local time zone</span></span>

1. <span data-ttu-id="66c01-109">Użyj `static` właściwości ( `Shared` w Visual Basic), <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType> Aby uzyskać dostęp do strefy czasowej systemu lokalnego.</span><span class="sxs-lookup"><span data-stu-id="66c01-109">Use the `static` (`Shared` in Visual Basic) <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType> property to access the local system time zone.</span></span>

2. <span data-ttu-id="66c01-110">Zamiast przypisywać <xref:System.TimeZoneInfo> obiekt zwracany przez właściwość do zmiennej obiektu, Kontynuuj dostęp do lokalnej strefy czasowej za pomocą <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType> właściwości.</span><span class="sxs-lookup"><span data-stu-id="66c01-110">Rather than assigning the <xref:System.TimeZoneInfo> object returned by the property to an object variable, continue to access the local time zone through the <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType> property.</span></span>

## <a name="example"></a><span data-ttu-id="66c01-111">Przykład</span><span class="sxs-lookup"><span data-stu-id="66c01-111">Example</span></span>

<span data-ttu-id="66c01-112">Poniższy kod używa <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType> właściwości i, <xref:System.TimeZoneInfo.Utc%2A?displayProperty=nameWithType> Aby przekonwertować godzinę z amerykańskiej i kanadyjskiej, standardowej strefy czasowej, a także do wyświetlania nazwy strefy czasowej w konsoli programu.</span><span class="sxs-lookup"><span data-stu-id="66c01-112">The following code uses the <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType> and <xref:System.TimeZoneInfo.Utc%2A?displayProperty=nameWithType> properties to convert a time from the U.S. and Canadian Eastern Standard time zone, as well as to display the time zone name to the console.</span></span>

[!code-csharp[System.TimeZone2.Concepts#13](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Concepts/CS/TimeZone2Concepts.cs#13)]
[!code-vb[System.TimeZone2.Concepts#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Concepts/VB/TimeZone2Concepts.vb#13)]

<span data-ttu-id="66c01-113">Należy zawsze uzyskać dostęp do lokalnej strefy czasowej przy użyciu <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType> Właściwości zamiast przypisywać lokalną strefę czasową do <xref:System.TimeZoneInfo> zmiennej obiektu.</span><span class="sxs-lookup"><span data-stu-id="66c01-113">You should always access the local time zone through the <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType> property rather than assigning the local time zone to a <xref:System.TimeZoneInfo> object variable.</span></span> <span data-ttu-id="66c01-114">Podobnie należy zawsze uzyskiwać dostęp do skoordynowanego uniwersalnego czasu za pomocą <xref:System.TimeZoneInfo.Utc%2A?displayProperty=nameWithType> Właściwości zamiast przypisywać strefy UTC do <xref:System.TimeZoneInfo> zmiennej obiektu.</span><span class="sxs-lookup"><span data-stu-id="66c01-114">Similarly, you should always access Coordinated Universal Time through the <xref:System.TimeZoneInfo.Utc%2A?displayProperty=nameWithType> property rather than assigning the UTC zone to a <xref:System.TimeZoneInfo> object variable.</span></span> <span data-ttu-id="66c01-115">Zapobiega to <xref:System.TimeZoneInfo> unieważnieniu zmiennej obiektu przez wywołanie <xref:System.TimeZoneInfo.ClearCachedData%2A?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="66c01-115">This prevents the <xref:System.TimeZoneInfo> object variable from being invalidated by a call to the <xref:System.TimeZoneInfo.ClearCachedData%2A?displayProperty=nameWithType> method.</span></span>

## <a name="compiling-the-code"></a><span data-ttu-id="66c01-116">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="66c01-116">Compiling the code</span></span>

<span data-ttu-id="66c01-117">Ten przykład wymaga:</span><span class="sxs-lookup"><span data-stu-id="66c01-117">This example requires:</span></span>

- <span data-ttu-id="66c01-118">Że <xref:System> przestrzeń nazw ma zostać zaimportowana przy użyciu `using` instrukcji (wymaganej w kodzie C#).</span><span class="sxs-lookup"><span data-stu-id="66c01-118">That the <xref:System> namespace be imported with the `using` statement (required in C# code).</span></span>

## <a name="see-also"></a><span data-ttu-id="66c01-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="66c01-119">See also</span></span>

- [<span data-ttu-id="66c01-120">Daty, godziny i strefy czasowe</span><span class="sxs-lookup"><span data-stu-id="66c01-120">Dates, times, and time zones</span></span>](index.md)
- [<span data-ttu-id="66c01-121">Znajdowanie stref czasowych zdefiniowanych w systemie lokalnym</span><span class="sxs-lookup"><span data-stu-id="66c01-121">Finding the time zones defined on a local system</span></span>](finding-the-time-zones-on-local-system.md)
- [<span data-ttu-id="66c01-122">Instrukcje: Tworzenie wystąpień obiektów TimeZoneInfo</span><span class="sxs-lookup"><span data-stu-id="66c01-122">How to: Instantiate a TimeZoneInfo object</span></span>](instantiate-time-zone-info.md)
