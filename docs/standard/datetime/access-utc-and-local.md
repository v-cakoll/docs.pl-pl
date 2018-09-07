---
title: 'Porady: uzyskiwanie dostępu do wstępnie zdefiniowanych obiektów stref UTC i czasem lokalnym'
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
ms.openlocfilehash: f074e6f6d9b11cc7d7405adced3a4523a31676fa
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2018
ms.locfileid: "44086916"
---
# <a name="how-to-access-the-predefined-utc-and-local-time-zone-objects"></a><span data-ttu-id="fdc8a-102">Porady: uzyskiwanie dostępu do wstępnie zdefiniowanych obiektów stref UTC i czasem lokalnym</span><span class="sxs-lookup"><span data-stu-id="fdc8a-102">How to: Access the predefined UTC and local time zone objects</span></span>

<span data-ttu-id="fdc8a-103"><xref:System.TimeZoneInfo> Klasa udostępnia dwie właściwości <xref:System.TimeZoneInfo.Utc%2A> i <xref:System.TimeZoneInfo.Local%2A>, które podają kodu dostępu do obiektów wstępnie zdefiniowane strefy czasowej.</span><span class="sxs-lookup"><span data-stu-id="fdc8a-103">The <xref:System.TimeZoneInfo> class provides two properties, <xref:System.TimeZoneInfo.Utc%2A> and <xref:System.TimeZoneInfo.Local%2A>, that give your code access to predefined time zone objects.</span></span> <span data-ttu-id="fdc8a-104">W tym temacie omówiono sposób uzyskiwania dostępu do <xref:System.TimeZoneInfo> obiekty zwrócone przez te właściwości.</span><span class="sxs-lookup"><span data-stu-id="fdc8a-104">This topic discusses how to access the <xref:System.TimeZoneInfo> objects returned by those properties.</span></span>

### <a name="to-access-the-coordinated-universal-time-utc-timezoneinfo-object"></a><span data-ttu-id="fdc8a-105">Dostępu do obiektu TimeZoneInfo uniwersalnego czasu koordynowanego (UTC)</span><span class="sxs-lookup"><span data-stu-id="fdc8a-105">To access the Coordinated Universal Time (UTC) TimeZoneInfo object</span></span>

1. <span data-ttu-id="fdc8a-106">Użyj `static` (`Shared` w języku Visual Basic) <xref:System.TimeZoneInfo.Utc%2A?displayProperty=nameWithType> właściwość dostęp do uniwersalnego czasu koordynowanego.</span><span class="sxs-lookup"><span data-stu-id="fdc8a-106">Use the `static` (`Shared` in Visual Basic) <xref:System.TimeZoneInfo.Utc%2A?displayProperty=nameWithType> property to access Coordinated Universal Time.</span></span>

2. <span data-ttu-id="fdc8a-107">Zamiast przypisywać <xref:System.TimeZoneInfo> obiekt zwracany przez właściwość zmienną obiektu w dalszym ciągu uzyskać dostęp za pośrednictwem uniwersalny czas koordynowany <xref:System.TimeZoneInfo.Utc%2A?displayProperty=nameWithType> właściwości.</span><span class="sxs-lookup"><span data-stu-id="fdc8a-107">Rather than assigning the <xref:System.TimeZoneInfo> object returned by the property to an object variable, continue to access Coordinated Universal Time through the <xref:System.TimeZoneInfo.Utc%2A?displayProperty=nameWithType> property.</span></span>

### <a name="to-access-the-local-time-zone"></a><span data-ttu-id="fdc8a-108">Aby uzyskać dostęp do strefy czasu lokalnego</span><span class="sxs-lookup"><span data-stu-id="fdc8a-108">To access the local time zone</span></span>

1. <span data-ttu-id="fdc8a-109">Użyj `static` (`Shared` w języku Visual Basic) <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType> właściwość, aby uzyskać dostęp do strefy czasu lokalnego.</span><span class="sxs-lookup"><span data-stu-id="fdc8a-109">Use the `static` (`Shared` in Visual Basic) <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType> property to access the local system time zone.</span></span>

2. <span data-ttu-id="fdc8a-110">Zamiast przypisywać <xref:System.TimeZoneInfo> obiekt zwracany przez właściwość zmienną obiektu w dalszym ciągu uzyskać dostęp do strefy czasu lokalnego za pośrednictwem <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType> właściwości.</span><span class="sxs-lookup"><span data-stu-id="fdc8a-110">Rather than assigning the <xref:System.TimeZoneInfo> object returned by the property to an object variable, continue to access the local time zone through the <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType> property.</span></span>

## <a name="example"></a><span data-ttu-id="fdc8a-111">Przykład</span><span class="sxs-lookup"><span data-stu-id="fdc8a-111">Example</span></span>

<span data-ttu-id="fdc8a-112">Poniższy kod używa <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType> i <xref:System.TimeZoneInfo.Utc%2A?displayProperty=nameWithType> właściwości można skonwertować godzinę strefy czasowej USA i Kanady Eastern Standard, jak również do wyświetlania nazwy strefy czasowej do konsoli.</span><span class="sxs-lookup"><span data-stu-id="fdc8a-112">The following code uses the <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType> and <xref:System.TimeZoneInfo.Utc%2A?displayProperty=nameWithType> properties to convert a time from the U.S. and Canadian Eastern Standard time zone, as well as to display the time zone name to the console.</span></span>

[!code-csharp[System.TimeZone2.Concepts#13](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Concepts/CS/TimeZone2Concepts.cs#13)]
[!code-vb[System.TimeZone2.Concepts#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Concepts/VB/TimeZone2Concepts.vb#13)]

<span data-ttu-id="fdc8a-113">Należy zawsze dostęp do lokalnej strefy czasowej przy użyciu <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType> właściwości, a nie czas lokalny przypisywanie strefy do <xref:System.TimeZoneInfo> zmiennej obiektu.</span><span class="sxs-lookup"><span data-stu-id="fdc8a-113">You should always access the local time zone through the <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType> property rather than assigning the local time zone to a <xref:System.TimeZoneInfo> object variable.</span></span> <span data-ttu-id="fdc8a-114">Podobnie, należy zawsze dostęp uniwersalny czas koordynowany za pośrednictwem <xref:System.TimeZoneInfo.Utc%2A?displayProperty=nameWithType> właściwość niż przypisywanie UTC strefy do <xref:System.TimeZoneInfo> zmiennej obiektu.</span><span class="sxs-lookup"><span data-stu-id="fdc8a-114">Similarly, you should always access Coordinated Universal Time through the <xref:System.TimeZoneInfo.Utc%2A?displayProperty=nameWithType> property rather than assigning the UTC zone to a <xref:System.TimeZoneInfo> object variable.</span></span> <span data-ttu-id="fdc8a-115">Zapobiega to <xref:System.TimeZoneInfo> zmiennej obiektu z trwa unieważniony przez wywołanie <xref:System.TimeZoneInfo.ClearCachedData%2A?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="fdc8a-115">This prevents the <xref:System.TimeZoneInfo> object variable from being invalidated by a call to the <xref:System.TimeZoneInfo.ClearCachedData%2A?displayProperty=nameWithType> method.</span></span>

## <a name="compiling-the-code"></a><span data-ttu-id="fdc8a-116">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="fdc8a-116">Compiling the code</span></span>

<span data-ttu-id="fdc8a-117">Ten przykład wymaga:</span><span class="sxs-lookup"><span data-stu-id="fdc8a-117">This example requires:</span></span>

* <span data-ttu-id="fdc8a-118">Odwołania do System.Core.dll dodania do projektu.</span><span class="sxs-lookup"><span data-stu-id="fdc8a-118">That a reference to System.Core.dll be added to the project.</span></span>

* <span data-ttu-id="fdc8a-119">Czy <xref:System> zaimportowane wraz z przestrzeni nazw `using` — instrukcja (wymagane w kodzie języka C#).</span><span class="sxs-lookup"><span data-stu-id="fdc8a-119">That the <xref:System> namespace be imported with the `using` statement (required in C# code).</span></span>

## <a name="see-also"></a><span data-ttu-id="fdc8a-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="fdc8a-120">See also</span></span>

* [<span data-ttu-id="fdc8a-121">Daty, godziny i strefy czasowe</span><span class="sxs-lookup"><span data-stu-id="fdc8a-121">Dates, times, and time zones</span></span>](../../../docs/standard/datetime/index.md)
* [<span data-ttu-id="fdc8a-122">Znajdowanie stref czasowych zdefiniowanych w systemie lokalnym</span><span class="sxs-lookup"><span data-stu-id="fdc8a-122">Finding the time zones defined on a local system</span></span>](../../../docs/standard/datetime/finding-the-time-zones-on-local-system.md)
* [<span data-ttu-id="fdc8a-123">Instrukcje: Tworzenie wystąpień obiektów TimeZoneInfo</span><span class="sxs-lookup"><span data-stu-id="fdc8a-123">How to: Instantiate a TimeZoneInfo object</span></span>](../../../docs/standard/datetime/instantiate-time-zone-info.md)
