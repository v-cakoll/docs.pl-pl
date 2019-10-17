---
title: SqlStreamChars. Read (Char [], Int32, Int32) Metoda (System. Data. SqlTypes)
author: stevestein
ms.author: sstein
ms.date: 12/20/2018
ms.technology: dotnet-data
topic_type:
- apiref
api_name:
- System.Data.SqlTypes.SqlStreamChars.Read
api_location:
- System.Data.dll
api_type:
- Assembly
ms.openlocfilehash: 9c8a1526e75fdc304022e74a7cc52506762489ea
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/16/2019
ms.locfileid: "72395753"
---
# <a name="sqlstreamcharsreadchar-int32-int32-method"></a><span data-ttu-id="1c279-102">SqlStreamChars. Read (Char [], Int32, Int32) — Metoda</span><span class="sxs-lookup"><span data-stu-id="1c279-102">SqlStreamChars.Read(Char[], Int32, Int32) Method</span></span>

<span data-ttu-id="1c279-103">Gdy jest zastępowany w klasie pochodnej, odczytuje następny zestaw znaków ze strumienia wejściowego.</span><span class="sxs-lookup"><span data-stu-id="1c279-103">When overridden in a derived class, reads the next set of characters from the input stream.</span></span> <span data-ttu-id="1c279-104">Zestaw, który zawiera tę metodę, ma relację zaprzyjaźnioną z obiektem sqlaccess. dll.</span><span class="sxs-lookup"><span data-stu-id="1c279-104">The assembly that contains this method has a friend relationship with SQLAccess.dll.</span></span> <span data-ttu-id="1c279-105">Jest on przeznaczony do użycia przez SQL Server.</span><span class="sxs-lookup"><span data-stu-id="1c279-105">It's intended for use by SQL Server.</span></span> <span data-ttu-id="1c279-106">W przypadku innych baz danych Użyj mechanizmu hostingu dostarczonego przez tę bazę danych.</span><span class="sxs-lookup"><span data-stu-id="1c279-106">For other databases, use the hosting mechanism provided by that database.</span></span>

```csharp
public abstract int Read (char[] buffer, int offset, int count);
```

## <a name="parameters"></a><span data-ttu-id="1c279-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="1c279-107">Parameters</span></span>

`buffer`\
<span data-ttu-id="1c279-108">Tablica znaków do odczytania.</span><span class="sxs-lookup"><span data-stu-id="1c279-108">A char array to read.</span></span>

`offset`\
<span data-ttu-id="1c279-109">Przesunięcie względem pochodzenia.</span><span class="sxs-lookup"><span data-stu-id="1c279-109">An offset relative to origin.</span></span>

`count`\
<span data-ttu-id="1c279-110">Liczba znaków, które mają być odczytane z bieżącego strumienia.</span><span class="sxs-lookup"><span data-stu-id="1c279-110">The number of characters to be read from the current stream.</span></span>

## <a name="returns"></a><span data-ttu-id="1c279-111">Zwraca</span><span class="sxs-lookup"><span data-stu-id="1c279-111">Returns</span></span>

<xref:System.Int32>\
<span data-ttu-id="1c279-112">Całkowita liczba znaków odczytywanych w buforze.</span><span class="sxs-lookup"><span data-stu-id="1c279-112">The total number of characters read into the buffer.</span></span>

## <a name="remarks"></a><span data-ttu-id="1c279-113">Uwagi</span><span class="sxs-lookup"><span data-stu-id="1c279-113">Remarks</span></span>

> [!WARNING]
> <span data-ttu-id="1c279-114">Metoda `SqlStreamChars.Read` jest prywatna i nie jest przeznaczona do użycia bezpośrednio w kodzie.</span><span class="sxs-lookup"><span data-stu-id="1c279-114">The `SqlStreamChars.Read` method is private and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="1c279-115">Firma Microsoft nie obsługuje korzystania z tej metody w aplikacji produkcyjnej w żadnej sytuacji.</span><span class="sxs-lookup"><span data-stu-id="1c279-115">Microsoft does not support the use of this method in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="1c279-116">Wymagania</span><span class="sxs-lookup"><span data-stu-id="1c279-116">Requirements</span></span>

<span data-ttu-id="1c279-117">**Przestrzeń nazw:** <xref:System.Data.SqlTypes></span><span class="sxs-lookup"><span data-stu-id="1c279-117">**Namespace:** <xref:System.Data.SqlTypes></span></span>

<span data-ttu-id="1c279-118">**Zestaw:** System. Data (w pliku System. Data. dll)</span><span class="sxs-lookup"><span data-stu-id="1c279-118">**Assembly:** System.Data (in System.Data.dll)</span></span>

<span data-ttu-id="1c279-119">**.NET Framework wersje:** Dostępne od 2,0.</span><span class="sxs-lookup"><span data-stu-id="1c279-119">**.NET Framework versions:** Available since 2.0.</span></span>
