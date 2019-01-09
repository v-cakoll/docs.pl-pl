---
title: Właściwość SqlStreamChars.Length (System.Data.SqlTypes)
author: douglaslMS
ms.author: douglasl
ms.date: 12/19/2018
ms.technology:
- dotnet-data
api_name:
- System.Data.SqlTypes.SqlStreamChars.Length
- System.Data.SqlTypes.SqlStreamChars.get_Length
api_location:
- System.Data.dll
api_type:
- Assembly
ms.openlocfilehash: 1ee15641e697a9d5d146f921640c73ff84a5c335
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/09/2019
ms.locfileid: "54152234"
---
# <a name="sqlstreamcharslength-property"></a><span data-ttu-id="e748d-102">Właściwość SqlStreamChars.Length</span><span class="sxs-lookup"><span data-stu-id="e748d-102">SqlStreamChars.Length Property</span></span>

<span data-ttu-id="e748d-103">W przypadku przesłonięcia w klasie pochodnej pobiera długość strumienia bieżącego.</span><span class="sxs-lookup"><span data-stu-id="e748d-103">When overridden in a derived class, gets the length of the current stream.</span></span> <span data-ttu-id="e748d-104">Zestaw, który zawiera właściwość ta ma relację zaprzyjaźniona z SQLAccess.dll.</span><span class="sxs-lookup"><span data-stu-id="e748d-104">The assembly that contains this property has a friend relationship with SQLAccess.dll.</span></span> <span data-ttu-id="e748d-105">Jest przeznaczony do użytku przez program SQL Server.</span><span class="sxs-lookup"><span data-stu-id="e748d-105">It's intended for use by SQL Server.</span></span> <span data-ttu-id="e748d-106">W przypadku innych baz danych użyj mechanizmu hostowania, pod warunkiem, że ta baza danych.</span><span class="sxs-lookup"><span data-stu-id="e748d-106">For other databases, use the hosting mechanism provided by that database.</span></span>

## <a name="syntax"></a><span data-ttu-id="e748d-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="e748d-107">Syntax</span></span>

```csharp
public abstract long Length { get; }
```

## <a name="property-value"></a><span data-ttu-id="e748d-108">Wartość właściwości</span><span class="sxs-lookup"><span data-stu-id="e748d-108">Property value</span></span>

<xref:System.Int64>\
<span data-ttu-id="e748d-109">Długość strumienia.</span><span class="sxs-lookup"><span data-stu-id="e748d-109">The length of the stream.</span></span>

## <a name="remarks"></a><span data-ttu-id="e748d-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="e748d-110">Remarks</span></span>

> [!WARNING]
> <span data-ttu-id="e748d-111">`SqlStreamChars.Length` Właściwość jest prywatny i nie jest przeznaczona do użycia bezpośrednio w kodzie.</span><span class="sxs-lookup"><span data-stu-id="e748d-111">The `SqlStreamChars.Length` property is private and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="e748d-112">Firma Microsoft obsługuje korzystanie z tego pola w aplikacji produkcyjnej w żadnym wypadku.</span><span class="sxs-lookup"><span data-stu-id="e748d-112">Microsoft does not support the use of this field in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="e748d-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="e748d-113">Requirements</span></span>

<span data-ttu-id="e748d-114">**Namespace:** <xref:System.Data.SqlTypes></span><span class="sxs-lookup"><span data-stu-id="e748d-114">**Namespace:** <xref:System.Data.SqlTypes></span></span>

<span data-ttu-id="e748d-115">**Zestaw:** Dane systemowe (w System.Data.dll)</span><span class="sxs-lookup"><span data-stu-id="e748d-115">**Assembly:** System.Data (in System.Data.dll)</span></span>

<span data-ttu-id="e748d-116">**Wersje programu .NET framework:** Dostępne od wersji 2.0.</span><span class="sxs-lookup"><span data-stu-id="e748d-116">**.NET Framework versions:** Available since 2.0.</span></span>