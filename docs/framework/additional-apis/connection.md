---
title: Klasa połączenia
ms.date: 05/01/2017
topic_type:
- apiref
api_name:
- System.Net.Connection
api_location:
- System.dll
api_type:
- Assembly
ms.assetid: 6f0b8902-f31c-4ab9-a8c9-de43228995ec
author: guardrex
ms.author: mairaw
ms.openlocfilehash: ed1fce1d16f9ddbe3a3ede91fecb1a3ca6b3d407
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/09/2019
ms.locfileid: "54146540"
---
# <a name="connection-class"></a><span data-ttu-id="e4953-102">Klasa połączenia</span><span class="sxs-lookup"><span data-stu-id="e4953-102">Connection Class</span></span>

<span data-ttu-id="e4953-103">`Connection` Odpowiedzi serwera analizuje klasy, kolejki żądań i żądania potoku.</span><span class="sxs-lookup"><span data-stu-id="e4953-103">The `Connection` class parses server responses, queue requests, and pipeline requests.</span></span>

## <a name="syntax"></a><span data-ttu-id="e4953-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="e4953-104">Syntax</span></span>
  
```csharp  
internal class Connection : PooledStream
```

> [!WARNING]
> <span data-ttu-id="e4953-105">`Connection` Klasy jest wewnętrzna i nie jest przeznaczona do użycia bezpośrednio w kodzie.</span><span class="sxs-lookup"><span data-stu-id="e4953-105">The `Connection` class is internal and is not meant to be used directly in your code.</span></span>
> 
> <span data-ttu-id="e4953-106">Firma Microsoft nie obsługuje użycia tej klasy w aplikacji produkcyjnej w żadnym wypadku.</span><span class="sxs-lookup"><span data-stu-id="e4953-106">Microsoft does not support the use of this class in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="e4953-107">Wymagania</span><span class="sxs-lookup"><span data-stu-id="e4953-107">Requirements</span></span>

<span data-ttu-id="e4953-108">**Namespace:** <xref:System.Net></span><span class="sxs-lookup"><span data-stu-id="e4953-108">**Namespace:** <xref:System.Net></span></span>

<span data-ttu-id="e4953-109">**Zestaw:** System (System.dll)</span><span class="sxs-lookup"><span data-stu-id="e4953-109">**Assembly:** System (in System.dll)</span></span>

<span data-ttu-id="e4953-110">**Wersje programu .NET framework:** Dostępne od wersji 2.0.</span><span class="sxs-lookup"><span data-stu-id="e4953-110">**.NET Framework versions:** Available since 2.0.</span></span>
