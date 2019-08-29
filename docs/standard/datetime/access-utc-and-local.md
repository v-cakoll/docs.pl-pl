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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8aa19118ce0837b9ce0eb523f3e086fcbcecb9e8
ms.sourcegitcommit: 6f28b709592503d27077b16fff2e2eacca569992
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/28/2019
ms.locfileid: "70106566"
---
# <a name="how-to-access-the-predefined-utc-and-local-time-zone-objects"></a><span data-ttu-id="1b8aa-102">Instrukcje: Uzyskiwanie dostępu do wstępnie zdefiniowanych obiektów lokalnej strefy czasowej i strefy czasowej UTC</span><span class="sxs-lookup"><span data-stu-id="1b8aa-102">How to: Access the predefined UTC and local time zone objects</span></span>

<span data-ttu-id="1b8aa-103">Klasa zawiera dwie <xref:System.TimeZoneInfo.Utc%2A> właściwości i <xref:System.TimeZoneInfo.Local%2A>, które dają kod dostępu do wstępnie zdefiniowanych obiektów stref czasowych. <xref:System.TimeZoneInfo></span><span class="sxs-lookup"><span data-stu-id="1b8aa-103">The <xref:System.TimeZoneInfo> class provides two properties, <xref:System.TimeZoneInfo.Utc%2A> and <xref:System.TimeZoneInfo.Local%2A>, that give your code access to predefined time zone objects.</span></span> <span data-ttu-id="1b8aa-104">W tym temacie omówiono sposób uzyskiwania dostępu <xref:System.TimeZoneInfo> do obiektów zwracanych przez te właściwości.</span><span class="sxs-lookup"><span data-stu-id="1b8aa-104">This topic discusses how to access the <xref:System.TimeZoneInfo> objects returned by those properties.</span></span>

### <a name="to-access-the-coordinated-universal-time-utc-timezoneinfo-object"></a><span data-ttu-id="1b8aa-105">Aby uzyskać dostęp do obiektu TimeZoneInfo skoordynowanego czasu uniwersalnego (UTC)</span><span class="sxs-lookup"><span data-stu-id="1b8aa-105">To access the Coordinated Universal Time (UTC) TimeZoneInfo object</span></span>

1. <span data-ttu-id="1b8aa-106">Aby uzyskać `static` dostęp`Shared` do uniwersalnego <xref:System.TimeZoneInfo.Utc%2A?displayProperty=nameWithType> czasu koordynowanego, użyj właściwości (w Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="1b8aa-106">Use the `static` (`Shared` in Visual Basic) <xref:System.TimeZoneInfo.Utc%2A?displayProperty=nameWithType> property to access Coordinated Universal Time.</span></span>

2. <span data-ttu-id="1b8aa-107">Zamiast przypisywać <xref:System.TimeZoneInfo> obiekt zwracany przez właściwość do zmiennej obiektu, Kontynuuj dostęp do uniwersalnego czasu koordynowanego <xref:System.TimeZoneInfo.Utc%2A?displayProperty=nameWithType> za pomocą właściwości.</span><span class="sxs-lookup"><span data-stu-id="1b8aa-107">Rather than assigning the <xref:System.TimeZoneInfo> object returned by the property to an object variable, continue to access Coordinated Universal Time through the <xref:System.TimeZoneInfo.Utc%2A?displayProperty=nameWithType> property.</span></span>

### <a name="to-access-the-local-time-zone"></a><span data-ttu-id="1b8aa-108">Aby uzyskać dostęp do lokalnej strefy czasowej</span><span class="sxs-lookup"><span data-stu-id="1b8aa-108">To access the local time zone</span></span>

1. <span data-ttu-id="1b8aa-109">Użyj właściwości`Shared` <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType> (w Visual Basic), aby uzyskać dostęp do strefy czasowej systemu lokalnego. `static`</span><span class="sxs-lookup"><span data-stu-id="1b8aa-109">Use the `static` (`Shared` in Visual Basic) <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType> property to access the local system time zone.</span></span>

2. <span data-ttu-id="1b8aa-110">Zamiast przypisywać <xref:System.TimeZoneInfo> obiekt zwracany przez właściwość do zmiennej obiektu, Kontynuuj dostęp do lokalnej strefy czasowej <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType> za pomocą właściwości.</span><span class="sxs-lookup"><span data-stu-id="1b8aa-110">Rather than assigning the <xref:System.TimeZoneInfo> object returned by the property to an object variable, continue to access the local time zone through the <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType> property.</span></span>

## <a name="example"></a><span data-ttu-id="1b8aa-111">Przykład</span><span class="sxs-lookup"><span data-stu-id="1b8aa-111">Example</span></span>

<span data-ttu-id="1b8aa-112">Poniższy kod używa <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType> właściwości i <xref:System.TimeZoneInfo.Utc%2A?displayProperty=nameWithType> , aby przekonwertować godzinę z amerykańskiej i kanadyjskiej, standardowej strefy czasowej, a także do wyświetlania nazwy strefy czasowej w konsoli programu.</span><span class="sxs-lookup"><span data-stu-id="1b8aa-112">The following code uses the <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType> and <xref:System.TimeZoneInfo.Utc%2A?displayProperty=nameWithType> properties to convert a time from the U.S. and Canadian Eastern Standard time zone, as well as to display the time zone name to the console.</span></span>

[!code-csharp[System.TimeZone2.Concepts#13](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Concepts/CS/TimeZone2Concepts.cs#13)]
[!code-vb[System.TimeZone2.Concepts#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Concepts/VB/TimeZone2Concepts.vb#13)]

<span data-ttu-id="1b8aa-113">Należy zawsze uzyskać dostęp do lokalnej strefy czasowej przy <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType> użyciu właściwości zamiast przypisywać lokalną strefę czasową <xref:System.TimeZoneInfo> do zmiennej obiektu.</span><span class="sxs-lookup"><span data-stu-id="1b8aa-113">You should always access the local time zone through the <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType> property rather than assigning the local time zone to a <xref:System.TimeZoneInfo> object variable.</span></span> <span data-ttu-id="1b8aa-114">Podobnie należy zawsze uzyskiwać dostęp do skoordynowanego uniwersalnego czasu <xref:System.TimeZoneInfo.Utc%2A?displayProperty=nameWithType> za pomocą właściwości zamiast przypisywać strefy UTC <xref:System.TimeZoneInfo> do zmiennej obiektu.</span><span class="sxs-lookup"><span data-stu-id="1b8aa-114">Similarly, you should always access Coordinated Universal Time through the <xref:System.TimeZoneInfo.Utc%2A?displayProperty=nameWithType> property rather than assigning the UTC zone to a <xref:System.TimeZoneInfo> object variable.</span></span> <span data-ttu-id="1b8aa-115">Zapobiega <xref:System.TimeZoneInfo> to unieważnieniu zmiennej obiektu przez wywołanie <xref:System.TimeZoneInfo.ClearCachedData%2A?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="1b8aa-115">This prevents the <xref:System.TimeZoneInfo> object variable from being invalidated by a call to the <xref:System.TimeZoneInfo.ClearCachedData%2A?displayProperty=nameWithType> method.</span></span>

## <a name="compiling-the-code"></a><span data-ttu-id="1b8aa-116">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="1b8aa-116">Compiling the code</span></span>

<span data-ttu-id="1b8aa-117">Ten przykład wymaga:</span><span class="sxs-lookup"><span data-stu-id="1b8aa-117">This example requires:</span></span>

- <span data-ttu-id="1b8aa-118">Że przestrzeń nazw ma zostać zaimportowana `using` przy użyciu instrukcji C# (wymaganej w kodzie). <xref:System></span><span class="sxs-lookup"><span data-stu-id="1b8aa-118">That the <xref:System> namespace be imported with the `using` statement (required in C# code).</span></span>

## <a name="see-also"></a><span data-ttu-id="1b8aa-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="1b8aa-119">See also</span></span>

- [<span data-ttu-id="1b8aa-120">Daty, godziny i strefy czasowe</span><span class="sxs-lookup"><span data-stu-id="1b8aa-120">Dates, times, and time zones</span></span>](../../../docs/standard/datetime/index.md)
- [<span data-ttu-id="1b8aa-121">Znajdowanie stref czasowych zdefiniowanych w systemie lokalnym</span><span class="sxs-lookup"><span data-stu-id="1b8aa-121">Finding the time zones defined on a local system</span></span>](../../../docs/standard/datetime/finding-the-time-zones-on-local-system.md)
- [<span data-ttu-id="1b8aa-122">Instrukcje: Tworzenie wystąpienia obiektu TimeZoneInfo</span><span class="sxs-lookup"><span data-stu-id="1b8aa-122">How to: Instantiate a TimeZoneInfo object</span></span>](../../../docs/standard/datetime/instantiate-time-zone-info.md)
