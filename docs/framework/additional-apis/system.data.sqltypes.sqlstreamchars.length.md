---
title: Właściwość SqlStreamChars.Length (System.Data.SqlTypes)
author: douglaslMS
ms.author: douglasl
ms.date: 12/19/2018
ms.technology:
- dotnet-data
topic_type:
- apiref
api_name:
- System.Data.SqlTypes.SqlStreamChars.Length
- System.Data.SqlTypes.SqlStreamChars.get_Length
api_location:
- System.Data.dll
api_type:
- Assembly
ms.openlocfilehash: ac6e6af9c9411ebc25039e0992133fae2b35ee23
ms.sourcegitcommit: a36cfc9dbbfc04bd88971f96e8a3f8e283c15d42
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/11/2019
ms.locfileid: "54221184"
---
# <a name="sqlstreamcharslength-property"></a><span data-ttu-id="f9df8-102">Właściwość SqlStreamChars.Length</span><span class="sxs-lookup"><span data-stu-id="f9df8-102">SqlStreamChars.Length Property</span></span>

<span data-ttu-id="f9df8-103">W przypadku przesłonięcia w klasie pochodnej pobiera długość strumienia bieżącego.</span><span class="sxs-lookup"><span data-stu-id="f9df8-103">When overridden in a derived class, gets the length of the current stream.</span></span> <span data-ttu-id="f9df8-104">Zestaw, który zawiera właściwość ta ma relację zaprzyjaźniona z SQLAccess.dll.</span><span class="sxs-lookup"><span data-stu-id="f9df8-104">The assembly that contains this property has a friend relationship with SQLAccess.dll.</span></span> <span data-ttu-id="f9df8-105">Jest przeznaczony do użytku przez program SQL Server.</span><span class="sxs-lookup"><span data-stu-id="f9df8-105">It's intended for use by SQL Server.</span></span> <span data-ttu-id="f9df8-106">W przypadku innych baz danych użyj mechanizmu hostowania, pod warunkiem, że ta baza danych.</span><span class="sxs-lookup"><span data-stu-id="f9df8-106">For other databases, use the hosting mechanism provided by that database.</span></span>

## <a name="syntax"></a><span data-ttu-id="f9df8-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="f9df8-107">Syntax</span></span>

```csharp
public abstract long Length { get; }
```

## <a name="property-value"></a><span data-ttu-id="f9df8-108">Wartość właściwości</span><span class="sxs-lookup"><span data-stu-id="f9df8-108">Property value</span></span>

<xref:System.Int64>\
<span data-ttu-id="f9df8-109">Długość strumienia.</span><span class="sxs-lookup"><span data-stu-id="f9df8-109">The length of the stream.</span></span>

## <a name="remarks"></a><span data-ttu-id="f9df8-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="f9df8-110">Remarks</span></span>

> [!WARNING]
> <span data-ttu-id="f9df8-111">`SqlStreamChars.Length` Właściwość jest prywatny i nie jest przeznaczona do użycia bezpośrednio w kodzie.</span><span class="sxs-lookup"><span data-stu-id="f9df8-111">The `SqlStreamChars.Length` property is private and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="f9df8-112">Firma Microsoft obsługuje korzystanie z tego pola w aplikacji produkcyjnej w żadnym wypadku.</span><span class="sxs-lookup"><span data-stu-id="f9df8-112">Microsoft does not support the use of this field in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="f9df8-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="f9df8-113">Requirements</span></span>

<span data-ttu-id="f9df8-114">**Namespace:** <xref:System.Data.SqlTypes></span><span class="sxs-lookup"><span data-stu-id="f9df8-114">**Namespace:** <xref:System.Data.SqlTypes></span></span>

<span data-ttu-id="f9df8-115">**Zestaw:** Dane systemowe (w System.Data.dll)</span><span class="sxs-lookup"><span data-stu-id="f9df8-115">**Assembly:** System.Data (in System.Data.dll)</span></span>

<span data-ttu-id="f9df8-116">**Wersje programu .NET framework:** Dostępne od wersji 2.0.</span><span class="sxs-lookup"><span data-stu-id="f9df8-116">**.NET Framework versions:** Available since 2.0.</span></span>