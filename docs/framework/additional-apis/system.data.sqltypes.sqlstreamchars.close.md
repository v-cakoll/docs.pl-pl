---
title: SqlStreamChars. Close — Metoda (System. Data. SqlTypes)
author: stevestein
ms.author: sstein
ms.date: 12/20/2018
ms.technology: dotnet-data
topic_type:
- apiref
api_name:
- System.Data.SqlTypes.SqlStreamChars.Close
api_location:
- System.Data.dll
api_type:
- Assembly
ms.openlocfilehash: c33c60842d181be7011528ca7550f3d09f291f43
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/16/2019
ms.locfileid: "72395635"
---
# <a name="sqlstreamcharsclose-method"></a><span data-ttu-id="a15fb-102">SqlStreamChars. Close — Metoda</span><span class="sxs-lookup"><span data-stu-id="a15fb-102">SqlStreamChars.Close Method</span></span>

<span data-ttu-id="a15fb-103">Zamyka bieżący strumień i zwalnia wszystkie zasoby systemowe skojarzone ze strumieniem.</span><span class="sxs-lookup"><span data-stu-id="a15fb-103">Closes the current stream and releases any system resources associated with the stream.</span></span> <span data-ttu-id="a15fb-104">Zestaw, który zawiera tę metodę, ma relację zaprzyjaźnioną z obiektem sqlaccess. dll.</span><span class="sxs-lookup"><span data-stu-id="a15fb-104">The assembly that contains this method has a friend relationship with SQLAccess.dll.</span></span> <span data-ttu-id="a15fb-105">Jest on przeznaczony do użycia przez SQL Server.</span><span class="sxs-lookup"><span data-stu-id="a15fb-105">It's intended for use by SQL Server.</span></span><span data-ttu-id="a15fb-106"> W przypadku innych baz danych Użyj mechanizmu hostingu dostarczonego przez tę bazę danych.</span><span class="sxs-lookup"><span data-stu-id="a15fb-106"> For other databases, use the hosting mechanism provided by that database.</span></span>

```csharp
public virtual void Close ();
```

## <a name="remarks"></a><span data-ttu-id="a15fb-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="a15fb-107">Remarks</span></span>

> [!WARNING]
> <span data-ttu-id="a15fb-108">Metoda `SqlStreamChars.Close` jest prywatna i nie jest przeznaczona do użycia bezpośrednio w kodzie.</span><span class="sxs-lookup"><span data-stu-id="a15fb-108">The `SqlStreamChars.Close` method is private and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="a15fb-109">Firma Microsoft nie obsługuje korzystania z tej metody w aplikacji produkcyjnej w żadnej sytuacji.</span><span class="sxs-lookup"><span data-stu-id="a15fb-109">Microsoft does not support the use of this method in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="a15fb-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="a15fb-110">Requirements</span></span>

<span data-ttu-id="a15fb-111">**Przestrzeń nazw:** <xref:System.Data.SqlTypes></span><span class="sxs-lookup"><span data-stu-id="a15fb-111">**Namespace:** <xref:System.Data.SqlTypes></span></span>

<span data-ttu-id="a15fb-112">**Zestaw:** System. Data (w pliku System. Data. dll)</span><span class="sxs-lookup"><span data-stu-id="a15fb-112">**Assembly:** System.Data (in System.Data.dll)</span></span>

<span data-ttu-id="a15fb-113">**.NET Framework wersje:** Dostępne od 2,0.</span><span class="sxs-lookup"><span data-stu-id="a15fb-113">**.NET Framework versions:** Available since 2.0.</span></span>
