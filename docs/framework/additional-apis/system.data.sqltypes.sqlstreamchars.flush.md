---
title: SqlStreamChars. Flush — Metoda (System. Data. SqlTypes)
author: stevestein
ms.author: sstein
ms.date: 12/20/2018
ms.technology: dotnet-data
topic_type:
- apiref
api_name:
- System.Data.SqlTypes.SqlStreamChars.Flush
api_location:
- System.Data.dll
api_type:
- Assembly
ms.openlocfilehash: 38ade5ce38cfe5003b2d06c0d8bb2db1a20bc05b
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/16/2019
ms.locfileid: "72395626"
---
# <a name="sqlstreamcharsflush-method"></a><span data-ttu-id="0933c-102">SqlStreamChars. Flush — Metoda</span><span class="sxs-lookup"><span data-stu-id="0933c-102">SqlStreamChars.Flush Method</span></span>

<span data-ttu-id="0933c-103">Gdy jest zastępowany w klasie pochodnej, czyści wszystkie bufory dla tego strumienia i powoduje, że wszystkie buforowane dane są zapisywane na podstawowym urządzeniu.</span><span class="sxs-lookup"><span data-stu-id="0933c-103">When overridden in a derived class, clears all buffers for this stream and causes any buffered data to be written to the underlying device.</span></span> <span data-ttu-id="0933c-104">Zestaw, który zawiera tę metodę, ma relację zaprzyjaźnioną z obiektem sqlaccess. dll.</span><span class="sxs-lookup"><span data-stu-id="0933c-104">The assembly that contains this method has a friend relationship with SQLAccess.dll.</span></span> <span data-ttu-id="0933c-105">Jest on przeznaczony do użycia przez SQL Server.</span><span class="sxs-lookup"><span data-stu-id="0933c-105">It's intended for use by SQL Server.</span></span> <span data-ttu-id="0933c-106">W przypadku innych baz danych Użyj mechanizmu hostingu dostarczonego przez tę bazę danych.</span><span class="sxs-lookup"><span data-stu-id="0933c-106">For other databases, use the hosting mechanism provided by that database.</span></span>

## <a name="syntax"></a><span data-ttu-id="0933c-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="0933c-107">Syntax</span></span>

```csharp
public abstract void Flush ();
```

## <a name="remarks"></a><span data-ttu-id="0933c-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="0933c-108">Remarks</span></span>

> [!WARNING]
> <span data-ttu-id="0933c-109">Metoda `SqlStreamChars.Flush` jest prywatna i nie jest przeznaczona do użycia bezpośrednio w kodzie.</span><span class="sxs-lookup"><span data-stu-id="0933c-109">The `SqlStreamChars.Flush` method is private and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="0933c-110">Firma Microsoft nie obsługuje korzystania z tej metody w aplikacji produkcyjnej w żadnej sytuacji.</span><span class="sxs-lookup"><span data-stu-id="0933c-110">Microsoft does not support the use of this method in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="0933c-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="0933c-111">Requirements</span></span>

<span data-ttu-id="0933c-112">**Przestrzeń nazw:** <xref:System.Data.SqlTypes></span><span class="sxs-lookup"><span data-stu-id="0933c-112">**Namespace:** <xref:System.Data.SqlTypes></span></span>

<span data-ttu-id="0933c-113">**Zestaw:** System. Data (w pliku System. Data. dll)</span><span class="sxs-lookup"><span data-stu-id="0933c-113">**Assembly:** System.Data (in System.Data.dll)</span></span>

<span data-ttu-id="0933c-114">**.NET Framework wersje:** Dostępne od 2,0.</span><span class="sxs-lookup"><span data-stu-id="0933c-114">**.NET Framework versions:** Available since 2.0.</span></span>
