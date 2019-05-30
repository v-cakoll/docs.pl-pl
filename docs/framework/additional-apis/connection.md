---
title: Connection, klasa
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
author: rpetrusha
ms.author: mairaw
ms.openlocfilehash: c50f673e77ef384ccf33803e14d60c322b6c0365
ms.sourcegitcommit: 621a5f6df00152006160987395b93b5b55f7ffcd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/29/2019
ms.locfileid: "66300973"
---
# <a name="connection-class"></a><span data-ttu-id="ce8dd-102">Connection, klasa</span><span class="sxs-lookup"><span data-stu-id="ce8dd-102">Connection Class</span></span>

<span data-ttu-id="ce8dd-103">`Connection` Odpowiedzi serwera analizuje klasy, kolejki żądań i żądania potoku.</span><span class="sxs-lookup"><span data-stu-id="ce8dd-103">The `Connection` class parses server responses, queue requests, and pipeline requests.</span></span>

## <a name="syntax"></a><span data-ttu-id="ce8dd-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="ce8dd-104">Syntax</span></span>
  
```csharp  
internal class Connection : PooledStream
```

> [!WARNING]
> <span data-ttu-id="ce8dd-105">`Connection` Klasy jest wewnętrzna i nie jest przeznaczona do użycia bezpośrednio w kodzie.</span><span class="sxs-lookup"><span data-stu-id="ce8dd-105">The `Connection` class is internal and is not meant to be used directly in your code.</span></span>
> 
> <span data-ttu-id="ce8dd-106">Firma Microsoft nie obsługuje użycia tej klasy w aplikacji produkcyjnej w żadnym wypadku.</span><span class="sxs-lookup"><span data-stu-id="ce8dd-106">Microsoft does not support the use of this class in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="ce8dd-107">Wymagania</span><span class="sxs-lookup"><span data-stu-id="ce8dd-107">Requirements</span></span>

<span data-ttu-id="ce8dd-108">**Namespace:** <xref:System.Net></span><span class="sxs-lookup"><span data-stu-id="ce8dd-108">**Namespace:** <xref:System.Net></span></span>

<span data-ttu-id="ce8dd-109">**Zestaw:** System (System.dll)</span><span class="sxs-lookup"><span data-stu-id="ce8dd-109">**Assembly:** System (in System.dll)</span></span>

<span data-ttu-id="ce8dd-110">**Wersje programu .NET framework:** Dostępne od wersji 2.0.</span><span class="sxs-lookup"><span data-stu-id="ce8dd-110">**.NET Framework versions:** Available since 2.0.</span></span>
