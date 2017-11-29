---
title: "Klasa połączenia"
ms.date: 05/01/2017
ms.prod: .net-framework
ms.technology: 
ms.topic: reference
topic_type: apiref
api_name: System.Net.Connection
api_location: System.dll
api_type: Assembly
ms.assetid: 6f0b8902-f31c-4ab9-a8c9-de43228995ec
author: guardrex
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 910c7e50eb87091cbf1cab6b8f8de2e10ac0a38e
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="connection-class"></a><span data-ttu-id="76abd-102">Klasa połączenia</span><span class="sxs-lookup"><span data-stu-id="76abd-102">Connection Class</span></span>

<span data-ttu-id="76abd-103">`Connection` Odpowiedzi serwera po analizie klasy, kolejki żądań i żądania potoku.</span><span class="sxs-lookup"><span data-stu-id="76abd-103">The `Connection` class parses server responses, queue requests, and pipeline requests.</span></span>

## <a name="syntax"></a><span data-ttu-id="76abd-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="76abd-104">Syntax</span></span>
  
```csharp  
internal class Connection : PooledStream
```

> [!WARNING]
> <span data-ttu-id="76abd-105">`Connection` Klasa jest wewnętrzna i nie są one przeznaczone do użycia bezpośrednio w kodzie.</span><span class="sxs-lookup"><span data-stu-id="76abd-105">The `Connection` class is internal and not meant to be used directly in your code.</span></span>
> 
> <span data-ttu-id="76abd-106">Microsoft w aplikacji produkcyjnej, w żadnym przypadku nie obsługuje korzystanie z tej klasy.</span><span class="sxs-lookup"><span data-stu-id="76abd-106">Microsoft does not support the use of this class in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="76abd-107">Wymagania</span><span class="sxs-lookup"><span data-stu-id="76abd-107">Requirements</span></span>

<span data-ttu-id="76abd-108">**Namespace:**<xref:System.Net></span><span class="sxs-lookup"><span data-stu-id="76abd-108">**Namespace:** <xref:System.Net></span></span>

<span data-ttu-id="76abd-109">**Zestaw:** System (w System.dll)</span><span class="sxs-lookup"><span data-stu-id="76abd-109">**Assembly:** System (in System.dll)</span></span>

<span data-ttu-id="76abd-110">**Wersje programu .NET framework:** dostępne od wersji 2.0.</span><span class="sxs-lookup"><span data-stu-id="76abd-110">**.NET Framework versions:** Available since 2.0.</span></span>
