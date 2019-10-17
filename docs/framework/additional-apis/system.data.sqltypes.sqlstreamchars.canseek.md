---
title: SqlStreamChars. CanSeek — Właściwość (System. Data. SqlTypes)
author: stevestein
ms.author: sstein
ms.date: 12/19/2018
ms.technology: dotnet-data
topic_type:
- apiref
api_name:
- System.Data.SqlTypes.SqlStreamChars.CanSeek
- System.Data.SqlTypes.SqlStreamChars.get_CanSeek
api_location:
- System.Data.dll
api_type:
- Assembly
ms.openlocfilehash: eb32978f62b7d46f0abf715e2bca347592c0fda8
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/16/2019
ms.locfileid: "72395779"
---
# <a name="sqlstreamcharscanseek-property"></a><span data-ttu-id="7a524-102">SqlStreamChars. CanSeek — Właściwość</span><span class="sxs-lookup"><span data-stu-id="7a524-102">SqlStreamChars.CanSeek Property</span></span>

<span data-ttu-id="7a524-103">Gdy jest zastępowany w klasie pochodnej, pobiera wartość wskazującą, czy bieżąca para obsługuje operację wyszukiwania.</span><span class="sxs-lookup"><span data-stu-id="7a524-103">When overridden in a derived class, gets a value that indicates whether the current steam supports the seek operation.</span></span> <span data-ttu-id="7a524-104">Zestaw, który zawiera tę właściwość, ma relację zaprzyjaźnioną z obiektem sqlaccess. dll.</span><span class="sxs-lookup"><span data-stu-id="7a524-104">The assembly that contains this property has a friend relationship with SQLAccess.dll.</span></span> <span data-ttu-id="7a524-105">Jest on przeznaczony do użycia przez SQL Server.</span><span class="sxs-lookup"><span data-stu-id="7a524-105">It's intended for use by SQL Server.</span></span> <span data-ttu-id="7a524-106">W przypadku innych baz danych Użyj mechanizmu hostingu dostarczonego przez tę bazę danych.</span><span class="sxs-lookup"><span data-stu-id="7a524-106">For other databases, use the hosting mechanism provided by that database.</span></span>

```csharp
public abstract bool CanSeek { get; }
```

## <a name="property-value"></a><span data-ttu-id="7a524-107">Wartość właściwości</span><span class="sxs-lookup"><span data-stu-id="7a524-107">Property value</span></span>

<xref:System.Boolean>\
<span data-ttu-id="7a524-108">`true`, jeśli bieżąca para obsługuje operację wyszukiwania; w przeciwnym razie `false`.</span><span class="sxs-lookup"><span data-stu-id="7a524-108">`true` if the current steam supports the seek operation; otherwise, `false`.</span></span>

## <a name="remarks"></a><span data-ttu-id="7a524-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="7a524-109">Remarks</span></span>

> [!WARNING]
> <span data-ttu-id="7a524-110">Właściwość `SqlStreamChars.CanSeek` jest prywatna i nie jest przeznaczona do użycia bezpośrednio w kodzie.</span><span class="sxs-lookup"><span data-stu-id="7a524-110">The `SqlStreamChars.CanSeek` property is private and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="7a524-111">Firma Microsoft nie obsługuje użycia tej właściwości w aplikacji produkcyjnej w żadnym przypadku.</span><span class="sxs-lookup"><span data-stu-id="7a524-111">Microsoft does not support the use of this property in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="7a524-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="7a524-112">Requirements</span></span>

<span data-ttu-id="7a524-113">**Przestrzeń nazw:** <xref:System.Data.SqlTypes></span><span class="sxs-lookup"><span data-stu-id="7a524-113">**Namespace:** <xref:System.Data.SqlTypes></span></span>

<span data-ttu-id="7a524-114">**Zestaw:** System. Data (w pliku System. Data. dll)</span><span class="sxs-lookup"><span data-stu-id="7a524-114">**Assembly:** System.Data (in System.Data.dll)</span></span>

<span data-ttu-id="7a524-115">**.NET Framework wersje:** Dostępne od 2,0.</span><span class="sxs-lookup"><span data-stu-id="7a524-115">**.NET Framework versions:** Available since 2.0.</span></span>
