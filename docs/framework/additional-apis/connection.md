---
title: Klasa połączenia (System.Net)
description: Dowiedz się więcej o klasie Connection w programie .NET. Ta klasa analizuje odpowiedzi serwera, żądania kolejki i żądania potoku. Znajduje się w przestrzeni nazw System.NET.
ms.date: 05/01/2017
ms.technology: dotnet-networking
topic_type:
- apiref
api_name:
- System.Net.Connection
api_location:
- System.dll
api_type:
- Assembly
ms.assetid: 6f0b8902-f31c-4ab9-a8c9-de43228995ec
ms.openlocfilehash: cb28724ed782fc5395dc74e9c59249ebdea44ddf
ms.sourcegitcommit: 45c8eed045779b70a47b23169897459d0323dc89
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/18/2020
ms.locfileid: "84989830"
---
# <a name="connection-class"></a><span data-ttu-id="209c3-105">Connection, klasa</span><span class="sxs-lookup"><span data-stu-id="209c3-105">Connection Class</span></span>

<span data-ttu-id="209c3-106">`Connection`Klasa analizuje odpowiedzi serwera, żądania kolejki i żądania potoku.</span><span class="sxs-lookup"><span data-stu-id="209c3-106">The `Connection` class parses server responses, queue requests, and pipeline requests.</span></span>

## <a name="syntax"></a><span data-ttu-id="209c3-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="209c3-107">Syntax</span></span>
  
```csharp  
internal class Connection : PooledStream
```

> [!WARNING]
> <span data-ttu-id="209c3-108">`Connection`Klasa jest wewnętrzna i nie jest przeznaczona do użycia bezpośrednio w kodzie.</span><span class="sxs-lookup"><span data-stu-id="209c3-108">The `Connection` class is internal and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="209c3-109">Firma Microsoft nie obsługuje korzystania z tej klasy w aplikacji produkcyjnej w żadnej sytuacji.</span><span class="sxs-lookup"><span data-stu-id="209c3-109">Microsoft does not support the use of this class in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="209c3-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="209c3-110">Requirements</span></span>

<span data-ttu-id="209c3-111">**Przestrzeń nazw:**<xref:System.Net></span><span class="sxs-lookup"><span data-stu-id="209c3-111">**Namespace:** <xref:System.Net></span></span>

<span data-ttu-id="209c3-112">**Zestaw:** System (w System.dll)</span><span class="sxs-lookup"><span data-stu-id="209c3-112">**Assembly:** System (in System.dll)</span></span>

<span data-ttu-id="209c3-113">**.NET Framework wersje:** Dostępne od 2,0.</span><span class="sxs-lookup"><span data-stu-id="209c3-113">**.NET Framework versions:** Available since 2.0.</span></span>
