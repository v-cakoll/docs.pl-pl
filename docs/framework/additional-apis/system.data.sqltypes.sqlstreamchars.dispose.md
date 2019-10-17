---
title: SqlStreamChars. Dispose (Boolean) — Metoda (System. Data. SqlTypes)
author: stevestein
ms.author: sstein
ms.date: 12/20/2018
ms.technology: dotnet-data
topic_type:
- apiref
api_name:
- System.Data.SqlTypes.SqlStreamChars.Dispose
api_location:
- System.Data.dll
api_type:
- Assembly
ms.openlocfilehash: 44dc97835b8a7141064e8de4d2d5325c40be5a34
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/16/2019
ms.locfileid: "72395763"
---
# <a name="sqlstreamcharsdisposeboolean-method"></a><span data-ttu-id="9aaf4-102">SqlStreamChars. Dispose (Boolean) — Metoda</span><span class="sxs-lookup"><span data-stu-id="9aaf4-102">SqlStreamChars.Dispose(Boolean) Method</span></span>

<span data-ttu-id="9aaf4-103">Gdy jest zastępowany w klasie pochodnej, zwalnia zasoby używane przez strumień.</span><span class="sxs-lookup"><span data-stu-id="9aaf4-103">When overridden in a derived class, releases the resources used by the stream.</span></span> <span data-ttu-id="9aaf4-104">Zestaw, który zawiera tę metodę, ma relację zaprzyjaźnioną z obiektem sqlaccess. dll.</span><span class="sxs-lookup"><span data-stu-id="9aaf4-104">The assembly that contains this method has a friend relationship with SQLAccess.dll.</span></span> <span data-ttu-id="9aaf4-105">Jest on przeznaczony do użycia przez SQL Server.</span><span class="sxs-lookup"><span data-stu-id="9aaf4-105">It's intended for use by SQL Server.</span></span> <span data-ttu-id="9aaf4-106">W przypadku innych baz danych Użyj mechanizmu hostingu dostarczonego przez tę bazę danych.</span><span class="sxs-lookup"><span data-stu-id="9aaf4-106">For other databases, use the hosting mechanism provided by that database.</span></span>

```csharp
protected virtual void Dispose (bool disposing);
```

## <a name="parameters"></a><span data-ttu-id="9aaf4-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="9aaf4-107">Parameters</span></span>

`disposing`\
<span data-ttu-id="9aaf4-108">`true` w celu zwolnienia zasobów zarządzanych i niezarządzanych; `false` do zwolnienia tylko zasobów niezarządzanych.</span><span class="sxs-lookup"><span data-stu-id="9aaf4-108">`true` to release both managed and unmanaged resources; `false` to release only unmanaged resources.</span></span>

## <a name="remarks"></a><span data-ttu-id="9aaf4-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="9aaf4-109">Remarks</span></span>

> [!WARNING]
> <span data-ttu-id="9aaf4-110">Metoda `SqlStreamChars.Dispose` jest prywatna i nie jest przeznaczona do użycia bezpośrednio w kodzie.</span><span class="sxs-lookup"><span data-stu-id="9aaf4-110">The `SqlStreamChars.Dispose` method is private and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="9aaf4-111">Firma Microsoft nie obsługuje korzystania z tej metody w aplikacji produkcyjnej w żadnej sytuacji.</span><span class="sxs-lookup"><span data-stu-id="9aaf4-111">Microsoft does not support the use of this method in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="9aaf4-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="9aaf4-112">Requirements</span></span>

<span data-ttu-id="9aaf4-113">**Przestrzeń nazw:** <xref:System.Data.SqlTypes></span><span class="sxs-lookup"><span data-stu-id="9aaf4-113">**Namespace:** <xref:System.Data.SqlTypes></span></span>

<span data-ttu-id="9aaf4-114">**Zestaw:** System. Data (w pliku System. Data. dll)</span><span class="sxs-lookup"><span data-stu-id="9aaf4-114">**Assembly:** System.Data (in System.Data.dll)</span></span>

<span data-ttu-id="9aaf4-115">**.NET Framework wersje:** Dostępne od 2,0.</span><span class="sxs-lookup"><span data-stu-id="9aaf4-115">**.NET Framework versions:** Available since 2.0.</span></span>
