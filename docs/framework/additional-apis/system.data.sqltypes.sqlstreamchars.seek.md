---
title: Metoda SqlStreamChars.Seek (Int64, SeekOrigin) (System.Data.SqlTypes)
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
ms.openlocfilehash: 6f802428a73f229e948099788ec21f07efbfab76
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61705795"
---
# <a name="sqlstreamcharsseekint64-seekorigin-method"></a><span data-ttu-id="804f1-102">Metoda SqlStreamChars.Seek (Int64, SeekOrigin)</span><span class="sxs-lookup"><span data-stu-id="804f1-102">SqlStreamChars.Seek(Int64, SeekOrigin) Method</span></span>

<span data-ttu-id="804f1-103">W przypadku przesłonięcia w klasie pochodnej, Ustawia położenie w obrębie bieżącego strumienia.</span><span class="sxs-lookup"><span data-stu-id="804f1-103">When overridden in a derived class, sets the position within the current stream.</span></span> <span data-ttu-id="804f1-104">Zestaw, który zawiera tę metodę ma relację zaprzyjaźniona z SQLAccess.dll.</span><span class="sxs-lookup"><span data-stu-id="804f1-104">The assembly that contains this method has a friend relationship with SQLAccess.dll.</span></span> <span data-ttu-id="804f1-105">Jest przeznaczony do użytku przez program SQL Server.</span><span class="sxs-lookup"><span data-stu-id="804f1-105">It's intended for use by SQL Server.</span></span> <span data-ttu-id="804f1-106">W przypadku innych baz danych użyj mechanizmu hostowania, pod warunkiem, że ta baza danych.</span><span class="sxs-lookup"><span data-stu-id="804f1-106">For other databases, use the hosting mechanism provided by that database.</span></span>

```csharp
public abstract long Seek (long offset, System.IO.SeekOrigin origin);
```

## <a name="parameters"></a><span data-ttu-id="804f1-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="804f1-107">Parameters</span></span>

`offset`\
<span data-ttu-id="804f1-108">Przesunięcie bajtów, względem `origin`.</span><span class="sxs-lookup"><span data-stu-id="804f1-108">A byte offset relative to `origin`.</span></span>

`origin`\
<span data-ttu-id="804f1-109">Jedna z wartości wyliczenia, które wskazuje punkt odniesienia, z którego można uzyskać nowe miejsce.</span><span class="sxs-lookup"><span data-stu-id="804f1-109">One of the enumeration values that indicates the reference point from which to obtain the new position.</span></span>

## <a name="returns"></a><span data-ttu-id="804f1-110">Zwraca</span><span class="sxs-lookup"><span data-stu-id="804f1-110">Returns</span></span>

<xref:System.Int32>\
<span data-ttu-id="804f1-111">Nowa pozycja w ciągu bieżącego strumienia.</span><span class="sxs-lookup"><span data-stu-id="804f1-111">The new position within the current stream.</span></span>

## <a name="remarks"></a><span data-ttu-id="804f1-112">Uwagi</span><span class="sxs-lookup"><span data-stu-id="804f1-112">Remarks</span></span>

> [!WARNING]
> <span data-ttu-id="804f1-113">`SqlStreamChars.Seek` Metoda jest prywatny i nie jest przeznaczona do użycia bezpośrednio w kodzie.</span><span class="sxs-lookup"><span data-stu-id="804f1-113">The `SqlStreamChars.Seek` method is private and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="804f1-114">Firma Microsoft obsługuje korzystanie z tego pola w aplikacji produkcyjnej w żadnym wypadku.</span><span class="sxs-lookup"><span data-stu-id="804f1-114">Microsoft does not support the use of this field in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="804f1-115">Wymagania</span><span class="sxs-lookup"><span data-stu-id="804f1-115">Requirements</span></span>

<span data-ttu-id="804f1-116">**Namespace:** <xref:System.Data.SqlTypes></span><span class="sxs-lookup"><span data-stu-id="804f1-116">**Namespace:** <xref:System.Data.SqlTypes></span></span>

<span data-ttu-id="804f1-117">**Zestaw:** Dane systemowe (w System.Data.dll)</span><span class="sxs-lookup"><span data-stu-id="804f1-117">**Assembly:** System.Data (in System.Data.dll)</span></span>

<span data-ttu-id="804f1-118">**Wersje programu .NET framework:** Dostępne od wersji 2.0.</span><span class="sxs-lookup"><span data-stu-id="804f1-118">**.NET Framework versions:** Available since 2.0.</span></span>