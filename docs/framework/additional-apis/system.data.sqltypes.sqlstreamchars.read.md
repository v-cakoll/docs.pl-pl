---
title: Metoda SqlStreamChars.Read (Char [], Int32, Int32) (System.Data.SqlTypes)
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
ms.openlocfilehash: df92acfd4050eb16d3a101b20b9b44560273f4d5
ms.sourcegitcommit: d938c39afb9216db377d0f0ecdaa53936a851059
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/29/2019
ms.locfileid: "58633650"
---
# <a name="sqlstreamcharsreadchar-int32-int32-method"></a><span data-ttu-id="1f559-102">Metoda SqlStreamChars.Read (Char [], Int32, Int32)</span><span class="sxs-lookup"><span data-stu-id="1f559-102">SqlStreamChars.Read(Char[], Int32, Int32) Method</span></span>

<span data-ttu-id="1f559-103">W przypadku przesłonięcia w klasie pochodnej, odczytuje następny zestaw znaków ze strumienia wejściowego.</span><span class="sxs-lookup"><span data-stu-id="1f559-103">When overridden in a derived class, reads the next set of characters from the input stream.</span></span> <span data-ttu-id="1f559-104">Zestaw, który zawiera tę metodę ma relację zaprzyjaźniona z SQLAccess.dll.</span><span class="sxs-lookup"><span data-stu-id="1f559-104">The assembly that contains this method has a friend relationship with SQLAccess.dll.</span></span> <span data-ttu-id="1f559-105">Jest przeznaczony do użytku przez program SQL Server.</span><span class="sxs-lookup"><span data-stu-id="1f559-105">It's intended for use by SQL Server.</span></span> <span data-ttu-id="1f559-106">W przypadku innych baz danych użyj mechanizmu hostowania, pod warunkiem, że ta baza danych.</span><span class="sxs-lookup"><span data-stu-id="1f559-106">For other databases, use the hosting mechanism provided by that database.</span></span>

```csharp
public abstract int Read (char[] buffer, int offset, int count);
```

## <a name="parameters"></a><span data-ttu-id="1f559-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="1f559-107">Parameters</span></span>

`buffer`\
<span data-ttu-id="1f559-108">Tablicy znaków do odczytania.</span><span class="sxs-lookup"><span data-stu-id="1f559-108">A char array to read.</span></span>

`offset`\
<span data-ttu-id="1f559-109">Przesunięcie względem źródła.</span><span class="sxs-lookup"><span data-stu-id="1f559-109">An offset relative to origin.</span></span>

`count`\
<span data-ttu-id="1f559-110">Liczba znaków, które mają być odczytywane z bieżącego strumienia.</span><span class="sxs-lookup"><span data-stu-id="1f559-110">The number of characters to be read from the current stream.</span></span>

## <a name="returns"></a><span data-ttu-id="1f559-111">Zwraca</span><span class="sxs-lookup"><span data-stu-id="1f559-111">Returns</span></span>

<xref:System.Int32>\
<span data-ttu-id="1f559-112">Całkowita liczba znaków czytanych w buforze.</span><span class="sxs-lookup"><span data-stu-id="1f559-112">The total number of characters read into the buffer.</span></span>

## <a name="remarks"></a><span data-ttu-id="1f559-113">Uwagi</span><span class="sxs-lookup"><span data-stu-id="1f559-113">Remarks</span></span>

> [!WARNING]
> <span data-ttu-id="1f559-114">`SqlStreamChars.Read` Metoda jest prywatny i nie jest przeznaczona do użycia bezpośrednio w kodzie.</span><span class="sxs-lookup"><span data-stu-id="1f559-114">The `SqlStreamChars.Read` method is private and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="1f559-115">Firma Microsoft obsługuje korzystanie z tego pola w aplikacji produkcyjnej w żadnym wypadku.</span><span class="sxs-lookup"><span data-stu-id="1f559-115">Microsoft does not support the use of this field in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="1f559-116">Wymagania</span><span class="sxs-lookup"><span data-stu-id="1f559-116">Requirements</span></span>

<span data-ttu-id="1f559-117">**Namespace:** <xref:System.Data.SqlTypes></span><span class="sxs-lookup"><span data-stu-id="1f559-117">**Namespace:** <xref:System.Data.SqlTypes></span></span>

<span data-ttu-id="1f559-118">**Zestaw:** Dane systemowe (w System.Data.dll)</span><span class="sxs-lookup"><span data-stu-id="1f559-118">**Assembly:** System.Data (in System.Data.dll)</span></span>

<span data-ttu-id="1f559-119">**Wersje programu .NET framework:** Dostępne od wersji 2.0.</span><span class="sxs-lookup"><span data-stu-id="1f559-119">**.NET Framework versions:** Available since 2.0.</span></span>