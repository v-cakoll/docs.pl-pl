---
title: SqlStreamChars.CanSeek Property (System.Data.SqlTypes)
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
ms.openlocfilehash: b85e21c6bc89d2a00ff8d302f67a3d074d5e7b8f
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2019
ms.locfileid: "65634385"
---
# <a name="sqlstreamcharscanseek-property"></a><span data-ttu-id="50889-102">SqlStreamChars.CanSeek Property</span><span class="sxs-lookup"><span data-stu-id="50889-102">SqlStreamChars.CanSeek Property</span></span>

<span data-ttu-id="50889-103">W przypadku przesłonięcia w klasie pochodnej pobiera wartość wskazującą, czy bieżący strumień obsługuje operacji wyszukiwania.</span><span class="sxs-lookup"><span data-stu-id="50889-103">When overridden in a derived class, gets a value that indicates whether the current steam supports the seek operation.</span></span> <span data-ttu-id="50889-104">Zestaw, który zawiera właściwość ta ma relację zaprzyjaźniona z SQLAccess.dll.</span><span class="sxs-lookup"><span data-stu-id="50889-104">The assembly that contains this property has a friend relationship with SQLAccess.dll.</span></span> <span data-ttu-id="50889-105">Jest przeznaczony do użytku przez program SQL Server.</span><span class="sxs-lookup"><span data-stu-id="50889-105">It's intended for use by SQL Server.</span></span> <span data-ttu-id="50889-106">W przypadku innych baz danych użyj mechanizmu hostowania, pod warunkiem, że ta baza danych.</span><span class="sxs-lookup"><span data-stu-id="50889-106">For other databases, use the hosting mechanism provided by that database.</span></span>

```csharp
public abstract bool CanSeek { get; }
```

## <a name="property-value"></a><span data-ttu-id="50889-107">Wartość właściwości</span><span class="sxs-lookup"><span data-stu-id="50889-107">Property value</span></span>

<xref:System.Boolean>\
<span data-ttu-id="50889-108">`true` Jeśli bieżący strumień obsługuje operacji wyszukiwania; w przeciwnym razie `false`.</span><span class="sxs-lookup"><span data-stu-id="50889-108">`true` if the current steam supports the seek operation; otherwise, `false`.</span></span>

## <a name="remarks"></a><span data-ttu-id="50889-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="50889-109">Remarks</span></span>

> [!WARNING]
> <span data-ttu-id="50889-110">`SqlStreamChars.CanSeek` Właściwość jest prywatny i nie jest przeznaczona do użycia bezpośrednio w kodzie.</span><span class="sxs-lookup"><span data-stu-id="50889-110">The `SqlStreamChars.CanSeek` property is private and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="50889-111">Firma Microsoft obsługuje korzystanie z tego pola w aplikacji produkcyjnej w żadnym wypadku.</span><span class="sxs-lookup"><span data-stu-id="50889-111">Microsoft does not support the use of this field in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="50889-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="50889-112">Requirements</span></span>

<span data-ttu-id="50889-113">**Namespace:** <xref:System.Data.SqlTypes></span><span class="sxs-lookup"><span data-stu-id="50889-113">**Namespace:** <xref:System.Data.SqlTypes></span></span>

<span data-ttu-id="50889-114">**Zestaw:** Dane systemowe (w System.Data.dll)</span><span class="sxs-lookup"><span data-stu-id="50889-114">**Assembly:** System.Data (in System.Data.dll)</span></span>

<span data-ttu-id="50889-115">**Wersje programu .NET framework:** Dostępne od wersji 2.0.</span><span class="sxs-lookup"><span data-stu-id="50889-115">**.NET Framework versions:** Available since 2.0.</span></span>
