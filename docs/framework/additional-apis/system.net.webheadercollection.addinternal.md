---
title: WebHeaderCollection. addinternal — Metoda (System.Net)
ms.date: 06/12/2020
ms.technology: dotnet-networking
topic_type:
- apiref
api_name:
- System.Net.WebHeaderCollection.AddInternal
api_location:
- System.dll
api_type:
- Assembly
ms.openlocfilehash: fd7b13ccd1baad48ab99a85d80ccd6154651c608
ms.sourcegitcommit: 45c8eed045779b70a47b23169897459d0323dc89
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/18/2020
ms.locfileid: "84990355"
---
# <a name="webheadercollectionaddinternal-method"></a><span data-ttu-id="2a241-102">WebHeaderCollection. Add— Metoda wewnętrzna</span><span class="sxs-lookup"><span data-stu-id="2a241-102">WebHeaderCollection.AddInternal method</span></span>

<span data-ttu-id="2a241-103">Dodaje nowy nagłówek z określoną nazwą i wartością do kolekcji, pomijając sprawdzanie.</span><span class="sxs-lookup"><span data-stu-id="2a241-103">Adds a new header with the specified name and value to the collection, bypassing checks.</span></span>

```csharp
internal void AddInternal(string name, string value)
```

> [!WARNING]
> <span data-ttu-id="2a241-104">Ta metoda jest wewnętrzna i nie jest przeznaczona do użycia bezpośrednio w kodzie.</span><span class="sxs-lookup"><span data-stu-id="2a241-104">This method is internal and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="2a241-105">Firma Microsoft nie obsługuje korzystania z tej metody w aplikacji produkcyjnej w żadnej sytuacji.</span><span class="sxs-lookup"><span data-stu-id="2a241-105">Microsoft does not support the use of this method in a production application under any circumstance.</span></span>

## <a name="parameters"></a><span data-ttu-id="2a241-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="2a241-106">Parameters</span></span>

- <span data-ttu-id="2a241-107">`name` <xref:System.String></span><span class="sxs-lookup"><span data-stu-id="2a241-107">`name` <xref:System.String></span></span>

  <span data-ttu-id="2a241-108">Nazwa nagłówka.</span><span class="sxs-lookup"><span data-stu-id="2a241-108">The name of the header.</span></span>

- <span data-ttu-id="2a241-109">`value` <xref:System.String></span><span class="sxs-lookup"><span data-stu-id="2a241-109">`value` <xref:System.String></span></span>

  <span data-ttu-id="2a241-110">Wartość nagłówka.</span><span class="sxs-lookup"><span data-stu-id="2a241-110">The value of the header.</span></span>

## <a name="requirements"></a><span data-ttu-id="2a241-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="2a241-111">Requirements</span></span>

<span data-ttu-id="2a241-112">**Przestrzeń nazw:**<xref:System.Net></span><span class="sxs-lookup"><span data-stu-id="2a241-112">**Namespace:** <xref:System.Net></span></span>

<span data-ttu-id="2a241-113">**Zestaw:** System (w System.dll)</span><span class="sxs-lookup"><span data-stu-id="2a241-113">**Assembly:** System (in System.dll)</span></span>
