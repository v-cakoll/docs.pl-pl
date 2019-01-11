---
title: Właściwość SqlStreamChars.IsNull (System.Data.SqlTypes)
author: douglaslMS
ms.author: douglasl
ms.date: 12/19/2018
ms.technology:
- dotnet-data
topic_type:
- apiref
api_name:
- System.Data.SqlTypes.SqlStreamChars.IsNull
- System.Data.SqlTypes.SqlStreamChars.get_IsNull
api_location:
- System.Data.dll
api_type:
- Assembly
ms.openlocfilehash: 7bef26119e31658b8495df402bbc07341cd84cf7
ms.sourcegitcommit: a36cfc9dbbfc04bd88971f96e8a3f8e283c15d42
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/11/2019
ms.locfileid: "54222561"
---
# <a name="sqlstreamcharsisnull-property"></a><span data-ttu-id="7b29c-102">Właściwość SqlStreamChars.IsNull</span><span class="sxs-lookup"><span data-stu-id="7b29c-102">SqlStreamChars.IsNull Property</span></span>

<span data-ttu-id="7b29c-103">W przypadku przesłonięcia w klasie pochodnej pobiera wartość wskazującą, czy strumień jest `null`.</span><span class="sxs-lookup"><span data-stu-id="7b29c-103">When overridden in a derived class, gets a value that indicates whether the stream is `null`.</span></span> <span data-ttu-id="7b29c-104">Zestaw, który zawiera właściwość ta ma relację zaprzyjaźniona z SQLAccess.dll.</span><span class="sxs-lookup"><span data-stu-id="7b29c-104">The assembly that contains this property has a friend relationship with SQLAccess.dll.</span></span> <span data-ttu-id="7b29c-105">Jest przeznaczony do użytku przez program SQL Server.</span><span class="sxs-lookup"><span data-stu-id="7b29c-105">It's intended for use by SQL Server.</span></span> <span data-ttu-id="7b29c-106">W przypadku innych baz danych użyj mechanizmu hostowania, pod warunkiem, że ta baza danych.</span><span class="sxs-lookup"><span data-stu-id="7b29c-106">For other databases, use the hosting mechanism provided by that database.</span></span>

## <a name="syntax"></a><span data-ttu-id="7b29c-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="7b29c-107">Syntax</span></span>

```csharp
public abstract bool IsNull { get; }
```

## <a name="property-value"></a><span data-ttu-id="7b29c-108">Wartość właściwości</span><span class="sxs-lookup"><span data-stu-id="7b29c-108">Property value</span></span>

<xref:System.Boolean>\
<span data-ttu-id="7b29c-109">`true` Jeśli strumień jest `null`; w przeciwnym razie `false`.</span><span class="sxs-lookup"><span data-stu-id="7b29c-109">`true` if the stream is `null`; otherwise, `false`.</span></span>

## <a name="remarks"></a><span data-ttu-id="7b29c-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="7b29c-110">Remarks</span></span>

> [!WARNING]
> <span data-ttu-id="7b29c-111">`SqlStreamChars.IsNull` Właściwość jest prywatny i nie jest przeznaczona do użycia bezpośrednio w kodzie.</span><span class="sxs-lookup"><span data-stu-id="7b29c-111">The `SqlStreamChars.IsNull` property is private and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="7b29c-112">Firma Microsoft obsługuje korzystanie z tego pola w aplikacji produkcyjnej w żadnym wypadku.</span><span class="sxs-lookup"><span data-stu-id="7b29c-112">Microsoft does not support the use of this field in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="7b29c-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="7b29c-113">Requirements</span></span>

<span data-ttu-id="7b29c-114">**Namespace:** <xref:System.Data.SqlTypes></span><span class="sxs-lookup"><span data-stu-id="7b29c-114">**Namespace:** <xref:System.Data.SqlTypes></span></span>

<span data-ttu-id="7b29c-115">**Zestaw:** Dane systemowe (w System.Data.dll)</span><span class="sxs-lookup"><span data-stu-id="7b29c-115">**Assembly:** System.Data (in System.Data.dll)</span></span>

<span data-ttu-id="7b29c-116">**Wersje programu .NET framework:** Dostępne od wersji 2.0.</span><span class="sxs-lookup"><span data-stu-id="7b29c-116">**.NET Framework versions:** Available since 2.0.</span></span>