---
title: Właściwość SqlStreamChars.Length (System.Data.SqlTypes)
author: stevestein
ms.author: sstein
ms.date: 12/19/2018
ms.technology: dotnet-data
topic_type:
- apiref
api_name:
- System.Data.SqlTypes.SqlStreamChars.Length
- System.Data.SqlTypes.SqlStreamChars.get_Length
api_location:
- System.Data.dll
api_type:
- Assembly
ms.openlocfilehash: c2ef66fa493512e1fa062e22858ea251ced39453
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61705847"
---
# <a name="sqlstreamcharslength-property"></a><span data-ttu-id="f4b61-102">SqlStreamChars.Length Property</span><span class="sxs-lookup"><span data-stu-id="f4b61-102">SqlStreamChars.Length Property</span></span>

<span data-ttu-id="f4b61-103">W przypadku przesłonięcia w klasie pochodnej pobiera długość strumienia bieżącego.</span><span class="sxs-lookup"><span data-stu-id="f4b61-103">When overridden in a derived class, gets the length of the current stream.</span></span> <span data-ttu-id="f4b61-104">Zestaw, który zawiera właściwość ta ma relację zaprzyjaźniona z SQLAccess.dll.</span><span class="sxs-lookup"><span data-stu-id="f4b61-104">The assembly that contains this property has a friend relationship with SQLAccess.dll.</span></span> <span data-ttu-id="f4b61-105">Jest przeznaczony do użytku przez program SQL Server.</span><span class="sxs-lookup"><span data-stu-id="f4b61-105">It's intended for use by SQL Server.</span></span> <span data-ttu-id="f4b61-106">W przypadku innych baz danych użyj mechanizmu hostowania, pod warunkiem, że ta baza danych.</span><span class="sxs-lookup"><span data-stu-id="f4b61-106">For other databases, use the hosting mechanism provided by that database.</span></span>

## <a name="syntax"></a><span data-ttu-id="f4b61-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="f4b61-107">Syntax</span></span>

```csharp
public abstract long Length { get; }
```

## <a name="property-value"></a><span data-ttu-id="f4b61-108">Wartość właściwości</span><span class="sxs-lookup"><span data-stu-id="f4b61-108">Property value</span></span>

<xref:System.Int64>\
<span data-ttu-id="f4b61-109">Długość strumienia.</span><span class="sxs-lookup"><span data-stu-id="f4b61-109">The length of the stream.</span></span>

## <a name="remarks"></a><span data-ttu-id="f4b61-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="f4b61-110">Remarks</span></span>

> [!WARNING]
> <span data-ttu-id="f4b61-111">`SqlStreamChars.Length` Właściwość jest prywatny i nie jest przeznaczona do użycia bezpośrednio w kodzie.</span><span class="sxs-lookup"><span data-stu-id="f4b61-111">The `SqlStreamChars.Length` property is private and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="f4b61-112">Firma Microsoft obsługuje korzystanie z tego pola w aplikacji produkcyjnej w żadnym wypadku.</span><span class="sxs-lookup"><span data-stu-id="f4b61-112">Microsoft does not support the use of this field in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="f4b61-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="f4b61-113">Requirements</span></span>

<span data-ttu-id="f4b61-114">**Namespace:** <xref:System.Data.SqlTypes></span><span class="sxs-lookup"><span data-stu-id="f4b61-114">**Namespace:** <xref:System.Data.SqlTypes></span></span>

<span data-ttu-id="f4b61-115">**Zestaw:** Dane systemowe (w System.Data.dll)</span><span class="sxs-lookup"><span data-stu-id="f4b61-115">**Assembly:** System.Data (in System.Data.dll)</span></span>

<span data-ttu-id="f4b61-116">**Wersje programu .NET framework:** Dostępne od wersji 2.0.</span><span class="sxs-lookup"><span data-stu-id="f4b61-116">**.NET Framework versions:** Available since 2.0.</span></span>