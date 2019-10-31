---
title: 'Instrukcje: uzyskiwanie dostępu do wstępnie zdefiniowanych obiektów czasu UTC i lokalnego strefy czasowej'
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
ms.openlocfilehash: ef22753d9934a52d955412a4493b608f265519aa
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73132606"
---
# <a name="how-to-access-the-predefined-utc-and-local-time-zone-objects"></a><span data-ttu-id="af899-102">Instrukcje: uzyskiwanie dostępu do wstępnie zdefiniowanych obiektów czasu UTC i lokalnego strefy czasowej</span><span class="sxs-lookup"><span data-stu-id="af899-102">How to: Access the predefined UTC and local time zone objects</span></span>

<span data-ttu-id="af899-103">Klasa <xref:System.TimeZoneInfo> udostępnia dwie właściwości, <xref:System.TimeZoneInfo.Utc%2A> i <xref:System.TimeZoneInfo.Local%2A>, które dają kod dostępu do wstępnie zdefiniowanych obiektów stref czasowych.</span><span class="sxs-lookup"><span data-stu-id="af899-103">The <xref:System.TimeZoneInfo> class provides two properties, <xref:System.TimeZoneInfo.Utc%2A> and <xref:System.TimeZoneInfo.Local%2A>, that give your code access to predefined time zone objects.</span></span> <span data-ttu-id="af899-104">W tym temacie omówiono sposób uzyskiwania dostępu do obiektów <xref:System.TimeZoneInfo> zwracanych przez te właściwości.</span><span class="sxs-lookup"><span data-stu-id="af899-104">This topic discusses how to access the <xref:System.TimeZoneInfo> objects returned by those properties.</span></span>

### <a name="to-access-the-coordinated-universal-time-utc-timezoneinfo-object"></a><span data-ttu-id="af899-105">Aby uzyskać dostęp do obiektu TimeZoneInfo skoordynowanego czasu uniwersalnego (UTC)</span><span class="sxs-lookup"><span data-stu-id="af899-105">To access the Coordinated Universal Time (UTC) TimeZoneInfo object</span></span>

1. <span data-ttu-id="af899-106">Użyj właściwości <xref:System.TimeZoneInfo.Utc%2A?displayProperty=nameWithType> `static` (`Shared` w Visual Basic), aby uzyskać dostęp do uniwersalnego czasu koordynowanego.</span><span class="sxs-lookup"><span data-stu-id="af899-106">Use the `static` (`Shared` in Visual Basic) <xref:System.TimeZoneInfo.Utc%2A?displayProperty=nameWithType> property to access Coordinated Universal Time.</span></span>

2. <span data-ttu-id="af899-107">Zamiast przypisywać obiekt <xref:System.TimeZoneInfo> zwracany przez właściwość do zmiennej obiektu, Kontynuuj dostęp do uniwersalnego czasu koordynowanego za pomocą właściwości <xref:System.TimeZoneInfo.Utc%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="af899-107">Rather than assigning the <xref:System.TimeZoneInfo> object returned by the property to an object variable, continue to access Coordinated Universal Time through the <xref:System.TimeZoneInfo.Utc%2A?displayProperty=nameWithType> property.</span></span>

### <a name="to-access-the-local-time-zone"></a><span data-ttu-id="af899-108">Aby uzyskać dostęp do lokalnej strefy czasowej</span><span class="sxs-lookup"><span data-stu-id="af899-108">To access the local time zone</span></span>

1. <span data-ttu-id="af899-109">Aby uzyskać dostęp do strefy czasowej systemu lokalnego, użyj właściwości <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType> `static` (`Shared` Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="af899-109">Use the `static` (`Shared` in Visual Basic) <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType> property to access the local system time zone.</span></span>

2. <span data-ttu-id="af899-110">Zamiast przypisywać obiekt <xref:System.TimeZoneInfo> zwracany przez właściwość do zmiennej obiektu, Kontynuuj dostęp do lokalnej strefy czasowej za pomocą właściwości <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="af899-110">Rather than assigning the <xref:System.TimeZoneInfo> object returned by the property to an object variable, continue to access the local time zone through the <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType> property.</span></span>

## <a name="example"></a><span data-ttu-id="af899-111">Przykład</span><span class="sxs-lookup"><span data-stu-id="af899-111">Example</span></span>

<span data-ttu-id="af899-112">Poniższy kod używa właściwości <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType> i <xref:System.TimeZoneInfo.Utc%2A?displayProperty=nameWithType> do przekonwertowania czasu z amerykańskiej i kanadyjskiej standardowej strefy czasowej, a także do wyświetlania nazwy strefy czasowej w konsoli programu.</span><span class="sxs-lookup"><span data-stu-id="af899-112">The following code uses the <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType> and <xref:System.TimeZoneInfo.Utc%2A?displayProperty=nameWithType> properties to convert a time from the U.S. and Canadian Eastern Standard time zone, as well as to display the time zone name to the console.</span></span>

[!code-csharp[System.TimeZone2.Concepts#13](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Concepts/CS/TimeZone2Concepts.cs#13)]
[!code-vb[System.TimeZone2.Concepts#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Concepts/VB/TimeZone2Concepts.vb#13)]

<span data-ttu-id="af899-113">Należy zawsze uzyskać dostęp do lokalnej strefy czasowej przy użyciu właściwości <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType> zamiast przypisywać lokalną strefę czasową do zmiennej obiektu <xref:System.TimeZoneInfo>.</span><span class="sxs-lookup"><span data-stu-id="af899-113">You should always access the local time zone through the <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType> property rather than assigning the local time zone to a <xref:System.TimeZoneInfo> object variable.</span></span> <span data-ttu-id="af899-114">Podobnie należy zawsze uzyskiwać dostęp do skoordynowanego uniwersalnego czasu za pomocą właściwości <xref:System.TimeZoneInfo.Utc%2A?displayProperty=nameWithType> zamiast przypisywania strefy UTC do zmiennej obiektu <xref:System.TimeZoneInfo>.</span><span class="sxs-lookup"><span data-stu-id="af899-114">Similarly, you should always access Coordinated Universal Time through the <xref:System.TimeZoneInfo.Utc%2A?displayProperty=nameWithType> property rather than assigning the UTC zone to a <xref:System.TimeZoneInfo> object variable.</span></span> <span data-ttu-id="af899-115">Zapobiega to unieważnieniu zmiennej obiektu <xref:System.TimeZoneInfo> przez wywołanie metody <xref:System.TimeZoneInfo.ClearCachedData%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="af899-115">This prevents the <xref:System.TimeZoneInfo> object variable from being invalidated by a call to the <xref:System.TimeZoneInfo.ClearCachedData%2A?displayProperty=nameWithType> method.</span></span>

## <a name="compiling-the-code"></a><span data-ttu-id="af899-116">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="af899-116">Compiling the code</span></span>

<span data-ttu-id="af899-117">Ten przykład wymaga:</span><span class="sxs-lookup"><span data-stu-id="af899-117">This example requires:</span></span>

- <span data-ttu-id="af899-118">Przestrzeń nazw <xref:System> zostać zaimportowana przy użyciu instrukcji `using` (wymagane C# w kodzie).</span><span class="sxs-lookup"><span data-stu-id="af899-118">That the <xref:System> namespace be imported with the `using` statement (required in C# code).</span></span>

## <a name="see-also"></a><span data-ttu-id="af899-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="af899-119">See also</span></span>

- [<span data-ttu-id="af899-120">Daty, godziny i strefy czasowe</span><span class="sxs-lookup"><span data-stu-id="af899-120">Dates, times, and time zones</span></span>](../../../docs/standard/datetime/index.md)
- [<span data-ttu-id="af899-121">Znajdowanie stref czasowych zdefiniowanych w systemie lokalnym</span><span class="sxs-lookup"><span data-stu-id="af899-121">Finding the time zones defined on a local system</span></span>](../../../docs/standard/datetime/finding-the-time-zones-on-local-system.md)
- [<span data-ttu-id="af899-122">Instrukcje: Tworzenie wystąpień obiektów TimeZoneInfo</span><span class="sxs-lookup"><span data-stu-id="af899-122">How to: Instantiate a TimeZoneInfo object</span></span>](../../../docs/standard/datetime/instantiate-time-zone-info.md)
