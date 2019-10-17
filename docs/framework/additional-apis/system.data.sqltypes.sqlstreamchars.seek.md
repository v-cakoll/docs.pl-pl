---
title: SqlStreamChars. seek (Int64, SeekOrigin) — Metoda (System. Data. sqltypees)
author: stevestein
ms.author: sstein
ms.date: 12/20/2018
ms.technology: dotnet-data
topic_type:
- apiref
api_name:
- System.Data.SqlTypes.SqlStreamChars.Seek
api_location:
- System.Data.dll
api_type:
- Assembly
ms.openlocfilehash: db8aba0a86c140ba62af8056011226532d415951
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/16/2019
ms.locfileid: "72395598"
---
# <a name="sqlstreamcharsseekint64-seekorigin-method"></a><span data-ttu-id="0a85c-102">SqlStreamChars. seek (Int64, SeekOrigin) — Metoda</span><span class="sxs-lookup"><span data-stu-id="0a85c-102">SqlStreamChars.Seek(Int64, SeekOrigin) Method</span></span>

<span data-ttu-id="0a85c-103">Gdy jest zastępowany w klasie pochodnej, ustawia pozycję w bieżącym strumieniu.</span><span class="sxs-lookup"><span data-stu-id="0a85c-103">When overridden in a derived class, sets the position within the current stream.</span></span> <span data-ttu-id="0a85c-104">Zestaw, który zawiera tę metodę, ma relację zaprzyjaźnioną z obiektem sqlaccess. dll.</span><span class="sxs-lookup"><span data-stu-id="0a85c-104">The assembly that contains this method has a friend relationship with SQLAccess.dll.</span></span> <span data-ttu-id="0a85c-105">Jest on przeznaczony do użycia przez SQL Server.</span><span class="sxs-lookup"><span data-stu-id="0a85c-105">It's intended for use by SQL Server.</span></span> <span data-ttu-id="0a85c-106">W przypadku innych baz danych Użyj mechanizmu hostingu dostarczonego przez tę bazę danych.</span><span class="sxs-lookup"><span data-stu-id="0a85c-106">For other databases, use the hosting mechanism provided by that database.</span></span>

```csharp
public abstract long Seek (long offset, System.IO.SeekOrigin origin);
```

## <a name="parameters"></a><span data-ttu-id="0a85c-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="0a85c-107">Parameters</span></span>

`offset`\
<span data-ttu-id="0a85c-108">Przesunięcie bajtów względem `origin`.</span><span class="sxs-lookup"><span data-stu-id="0a85c-108">A byte offset relative to `origin`.</span></span>

`origin`\
<span data-ttu-id="0a85c-109">Jedna z wartości wyliczenia, która wskazuje punkt odniesienia, z którego ma zostać uzyskana Nowa pozycja.</span><span class="sxs-lookup"><span data-stu-id="0a85c-109">One of the enumeration values that indicates the reference point from which to obtain the new position.</span></span>

## <a name="returns"></a><span data-ttu-id="0a85c-110">Zwraca</span><span class="sxs-lookup"><span data-stu-id="0a85c-110">Returns</span></span>

<xref:System.Int32>\
<span data-ttu-id="0a85c-111">Nowa pozycja w bieżącym strumieniu.</span><span class="sxs-lookup"><span data-stu-id="0a85c-111">The new position within the current stream.</span></span>

## <a name="remarks"></a><span data-ttu-id="0a85c-112">Uwagi</span><span class="sxs-lookup"><span data-stu-id="0a85c-112">Remarks</span></span>

> [!WARNING]
> <span data-ttu-id="0a85c-113">Metoda `SqlStreamChars.Seek` jest prywatna i nie jest przeznaczona do użycia bezpośrednio w kodzie.</span><span class="sxs-lookup"><span data-stu-id="0a85c-113">The `SqlStreamChars.Seek` method is private and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="0a85c-114">Firma Microsoft nie obsługuje korzystania z tej metody w aplikacji produkcyjnej w żadnej sytuacji.</span><span class="sxs-lookup"><span data-stu-id="0a85c-114">Microsoft does not support the use of this method in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="0a85c-115">Wymagania</span><span class="sxs-lookup"><span data-stu-id="0a85c-115">Requirements</span></span>

<span data-ttu-id="0a85c-116">**Przestrzeń nazw:** <xref:System.Data.SqlTypes></span><span class="sxs-lookup"><span data-stu-id="0a85c-116">**Namespace:** <xref:System.Data.SqlTypes></span></span>

<span data-ttu-id="0a85c-117">**Zestaw:** System. Data (w pliku System. Data. dll)</span><span class="sxs-lookup"><span data-stu-id="0a85c-117">**Assembly:** System.Data (in System.Data.dll)</span></span>

<span data-ttu-id="0a85c-118">**.NET Framework wersje:** Dostępne od 2,0.</span><span class="sxs-lookup"><span data-stu-id="0a85c-118">**.NET Framework versions:** Available since 2.0.</span></span>
