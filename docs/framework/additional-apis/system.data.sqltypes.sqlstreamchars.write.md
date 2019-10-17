---
title: SqlStreamChars. Write (Char [], Int32, Int32) Metoda (System. Data. SqlTypes)
author: stevestein
ms.author: sstein
ms.date: 12/20/2018
ms.technology: dotnet-data
topic_type:
- apiref
api_name:
- System.Data.SqlTypes.SqlStreamChars.Write
api_location:
- System.Data.dll
api_type:
- Assembly
ms.openlocfilehash: 9d952041122ceb3824712bd81cab7ce4789c9db8
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/16/2019
ms.locfileid: "72395578"
---
# <a name="sqlstreamcharswritechar-int32-int32-method"></a><span data-ttu-id="03cde-102">SqlStreamChars. Write (Char [], Int32, Int32) — Metoda</span><span class="sxs-lookup"><span data-stu-id="03cde-102">SqlStreamChars.Write(Char[], Int32, Int32) Method</span></span>

<span data-ttu-id="03cde-103">Gdy jest zastępowany w klasie pochodnej, zapisuje sekwencję znaków w bieżącym strumieniu i przesuwa bieżącą pozycję w tym strumieniu o liczbę pisanych znaków.</span><span class="sxs-lookup"><span data-stu-id="03cde-103">When overridden in a derived class, writes a sequence of characters to the current stream and advances the current position within this stream by the number of characters written.</span></span> <span data-ttu-id="03cde-104">Zestaw, który zawiera tę metodę, ma relację zaprzyjaźnioną z obiektem sqlaccess. dll.</span><span class="sxs-lookup"><span data-stu-id="03cde-104">The assembly that contains this method has a friend relationship with SQLAccess.dll.</span></span> <span data-ttu-id="03cde-105">Jest on przeznaczony do użycia przez SQL Server.</span><span class="sxs-lookup"><span data-stu-id="03cde-105">It's intended for use by SQL Server.</span></span> <span data-ttu-id="03cde-106">W przypadku innych baz danych Użyj mechanizmu hostingu dostarczonego przez tę bazę danych.</span><span class="sxs-lookup"><span data-stu-id="03cde-106">For other databases, use the hosting mechanism provided by that database.</span></span>

```csharp
public abstract void Write (char[] buffer, int offset, int count);
```

## <a name="parameters"></a><span data-ttu-id="03cde-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="03cde-107">Parameters</span></span>

`buffer`  
<span data-ttu-id="03cde-108">Tablica znaków do zapisania.</span><span class="sxs-lookup"><span data-stu-id="03cde-108">A char array to write.</span></span>

`offset`  
<span data-ttu-id="03cde-109">Przesunięcie względem pochodzenia.</span><span class="sxs-lookup"><span data-stu-id="03cde-109">An offset relative to origin.</span></span>

`count`  
<span data-ttu-id="03cde-110">Liczba znaków, które mają być zapisywane w bieżącym strumieniu.</span><span class="sxs-lookup"><span data-stu-id="03cde-110">The number of characters to be written to the current stream.</span></span>

## <a name="remarks"></a><span data-ttu-id="03cde-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="03cde-111">Remarks</span></span>

> [!WARNING]
> <span data-ttu-id="03cde-112">Metoda `SqlStreamChars.Write` jest prywatna i nie jest przeznaczona do użycia bezpośrednio w kodzie.</span><span class="sxs-lookup"><span data-stu-id="03cde-112">The `SqlStreamChars.Write` method is private and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="03cde-113">Firma Microsoft nie obsługuje korzystania z tej metody zapisu w aplikacji produkcyjnej w żadnej sytuacji.</span><span class="sxs-lookup"><span data-stu-id="03cde-113">Microsoft does not support the use of this method write in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="03cde-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="03cde-114">Requirements</span></span>

<span data-ttu-id="03cde-115">**Przestrzeń nazw:** <xref:System.Data.SqlTypes></span><span class="sxs-lookup"><span data-stu-id="03cde-115">**Namespace:** <xref:System.Data.SqlTypes></span></span>

<span data-ttu-id="03cde-116">**Zestaw:** System. Data (w pliku System. Data. dll)</span><span class="sxs-lookup"><span data-stu-id="03cde-116">**Assembly:** System.Data (in System.Data.dll)</span></span>

<span data-ttu-id="03cde-117">**.NET Framework wersje:** Dostępne od 2,0.</span><span class="sxs-lookup"><span data-stu-id="03cde-117">**.NET Framework versions:** Available since 2.0.</span></span>
