---
title: Metoda SqlStreamChars.Write (Char [], Int32, Int32) (System.Data.SqlTypes)
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
ms.openlocfilehash: 4084c7161eaa91d78eab32f1c14624e0032cdfcf
ms.sourcegitcommit: 0aca6c5d166d7961a1e354c248495645b97a1dc5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/30/2019
ms.locfileid: "58675760"
---
# <a name="sqlstreamcharswritechar-int32-int32-method"></a><span data-ttu-id="f68c7-102">Metoda SqlStreamChars.Write (Char [], Int32, Int32)</span><span class="sxs-lookup"><span data-stu-id="f68c7-102">SqlStreamChars.Write(Char[], Int32, Int32) Method</span></span>

<span data-ttu-id="f68c7-103">W przypadku przesłonięcia w klasie pochodnej, zapisuje sekwencji znaków do bieżącego strumienia i przesuwa bieżącą pozycję w tym strumieniu według liczby znaków zapisanych.</span><span class="sxs-lookup"><span data-stu-id="f68c7-103">When overridden in a derived class, writes a sequence of characters to the current stream and advances the current position within this stream by the number of characters written.</span></span> <span data-ttu-id="f68c7-104">Zestaw, który zawiera tę metodę ma relację zaprzyjaźniona z SQLAccess.dll.</span><span class="sxs-lookup"><span data-stu-id="f68c7-104">The assembly that contains this method has a friend relationship with SQLAccess.dll.</span></span> <span data-ttu-id="f68c7-105">Jest przeznaczony do użytku przez program SQL Server.</span><span class="sxs-lookup"><span data-stu-id="f68c7-105">It's intended for use by SQL Server.</span></span> <span data-ttu-id="f68c7-106">W przypadku innych baz danych użyj mechanizmu hostowania, pod warunkiem, że ta baza danych.</span><span class="sxs-lookup"><span data-stu-id="f68c7-106">For other databases, use the hosting mechanism provided by that database.</span></span>

```csharp
public abstract void Write (char[] buffer, int offset, int count);
```

## <a name="parameters"></a><span data-ttu-id="f68c7-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="f68c7-107">Parameters</span></span>

`buffer`  
<span data-ttu-id="f68c7-108">Tablicy znaków do zapisania.</span><span class="sxs-lookup"><span data-stu-id="f68c7-108">A char array to write.</span></span>

`offset`  
<span data-ttu-id="f68c7-109">Przesunięcie względem źródła.</span><span class="sxs-lookup"><span data-stu-id="f68c7-109">An offset relative to origin.</span></span>

`count`  
<span data-ttu-id="f68c7-110">Liczba znaków, które mają być zapisywane do strumienia bieżącego.</span><span class="sxs-lookup"><span data-stu-id="f68c7-110">The number of characters to be written to the current stream.</span></span>

## <a name="remarks"></a><span data-ttu-id="f68c7-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="f68c7-111">Remarks</span></span>

> [!WARNING]
> <span data-ttu-id="f68c7-112">`SqlStreamChars.Write` Metoda jest prywatny i nie jest przeznaczona do użycia bezpośrednio w kodzie.</span><span class="sxs-lookup"><span data-stu-id="f68c7-112">The `SqlStreamChars.Write` method is private and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="f68c7-113">Firma Microsoft obsługuje korzystanie z tego pola w aplikacji produkcyjnej w żadnym wypadku.</span><span class="sxs-lookup"><span data-stu-id="f68c7-113">Microsoft does not support the use of this field in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="f68c7-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="f68c7-114">Requirements</span></span>

<span data-ttu-id="f68c7-115">**Namespace:** <xref:System.Data.SqlTypes></span><span class="sxs-lookup"><span data-stu-id="f68c7-115">**Namespace:** <xref:System.Data.SqlTypes></span></span>

<span data-ttu-id="f68c7-116">**Zestaw:** Dane systemowe (w System.Data.dll)</span><span class="sxs-lookup"><span data-stu-id="f68c7-116">**Assembly:** System.Data (in System.Data.dll)</span></span>

<span data-ttu-id="f68c7-117">**Wersje programu .NET framework:** Dostępne od wersji 2.0.</span><span class="sxs-lookup"><span data-stu-id="f68c7-117">**.NET Framework versions:** Available since 2.0.</span></span>
