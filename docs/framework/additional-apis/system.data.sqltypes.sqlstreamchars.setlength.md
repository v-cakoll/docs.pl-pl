---
title: SqlStreamChars. SetLength (Int64) — Metoda (System. Data. SqlTypes)
author: stevestein
ms.author: sstein
ms.date: 12/20/2018
ms.technology: dotnet-data
topic_type:
- apiref
api_name:
- System.Data.SqlTypes.SqlStreamChars.SetLength
api_location:
- System.Data.dll
api_type:
- Assembly
ms.openlocfilehash: 291d6e9395581f2370dafc728521a314d54a686d
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/16/2019
ms.locfileid: "72395722"
---
# <a name="sqlstreamcharssetlengthint64-method"></a><span data-ttu-id="6a0ff-102">SqlStreamChars. SetLength (Int64) — Metoda</span><span class="sxs-lookup"><span data-stu-id="6a0ff-102">SqlStreamChars.SetLength(Int64) Method</span></span>

<span data-ttu-id="6a0ff-103">Gdy jest zastępowany w klasie pochodnej, zwalnia zasoby używane przez strumień.</span><span class="sxs-lookup"><span data-stu-id="6a0ff-103">When overridden in a derived class, releases the resources used by the stream.</span></span> <span data-ttu-id="6a0ff-104">Zestaw, który zawiera tę metodę, ma relację zaprzyjaźnioną z obiektem sqlaccess. dll.</span><span class="sxs-lookup"><span data-stu-id="6a0ff-104">The assembly that contains this method has a friend relationship with SQLAccess.dll.</span></span> <span data-ttu-id="6a0ff-105">Jest on przeznaczony do użycia przez SQL Server.</span><span class="sxs-lookup"><span data-stu-id="6a0ff-105">It's intended for use by SQL Server.</span></span> <span data-ttu-id="6a0ff-106">W przypadku innych baz danych Użyj mechanizmu hostingu dostarczonego przez tę bazę danych.</span><span class="sxs-lookup"><span data-stu-id="6a0ff-106">For other databases, use the hosting mechanism provided by that database.</span></span>

```csharp
public abstract void SetLength (long value);
```

## <a name="parameters"></a><span data-ttu-id="6a0ff-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="6a0ff-107">Parameters</span></span>

`value`\
<span data-ttu-id="6a0ff-108">Wymagana długość bieżącego strumienia w bajtach.</span><span class="sxs-lookup"><span data-stu-id="6a0ff-108">The desired length of the current stream in bytes.</span></span>

## <a name="remarks"></a><span data-ttu-id="6a0ff-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="6a0ff-109">Remarks</span></span>

> [!WARNING]
> <span data-ttu-id="6a0ff-110">Metoda `SqlStreamChars.SetLength` jest prywatna i nie jest przeznaczona do użycia bezpośrednio w kodzie.</span><span class="sxs-lookup"><span data-stu-id="6a0ff-110">The `SqlStreamChars.SetLength` method is private and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="6a0ff-111">Firma Microsoft nie obsługuje korzystania z tej metody w aplikacji produkcyjnej w żadnej sytuacji.</span><span class="sxs-lookup"><span data-stu-id="6a0ff-111">Microsoft does not support the use of this method in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="6a0ff-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="6a0ff-112">Requirements</span></span>

<span data-ttu-id="6a0ff-113">**Przestrzeń nazw:** <xref:System.Data.SqlTypes></span><span class="sxs-lookup"><span data-stu-id="6a0ff-113">**Namespace:** <xref:System.Data.SqlTypes></span></span>

<span data-ttu-id="6a0ff-114">**Zestaw:** System. Data (w pliku System. Data. dll)</span><span class="sxs-lookup"><span data-stu-id="6a0ff-114">**Assembly:** System.Data (in System.Data.dll)</span></span>

<span data-ttu-id="6a0ff-115">**.NET Framework wersje:** Dostępne od 2,0.</span><span class="sxs-lookup"><span data-stu-id="6a0ff-115">**.NET Framework versions:** Available since 2.0.</span></span>
