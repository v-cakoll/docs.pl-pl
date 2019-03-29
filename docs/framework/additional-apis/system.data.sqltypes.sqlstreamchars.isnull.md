---
title: SqlStreamChars.IsNull Property (System.Data.SqlTypes)
author: stevestein
ms.author: sstein
ms.date: 12/19/2018
ms.technology: dotnet-data
topic_type:
- apiref
api_name:
- System.Data.SqlTypes.SqlStreamChars.IsNull
- System.Data.SqlTypes.SqlStreamChars.get_IsNull
api_location:
- System.Data.dll
api_type:
- Assembly
ms.openlocfilehash: ec00b0afa1597c3ae6488c12fe5a0667dad70e2d
ms.sourcegitcommit: d938c39afb9216db377d0f0ecdaa53936a851059
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/29/2019
ms.locfileid: "58634339"
---
# <a name="sqlstreamcharsisnull-property"></a><span data-ttu-id="6e462-102">SqlStreamChars.IsNull Property</span><span class="sxs-lookup"><span data-stu-id="6e462-102">SqlStreamChars.IsNull Property</span></span>

<span data-ttu-id="6e462-103">W przypadku przesłonięcia w klasie pochodnej pobiera wartość wskazującą, czy strumień jest `null`.</span><span class="sxs-lookup"><span data-stu-id="6e462-103">When overridden in a derived class, gets a value that indicates whether the stream is `null`.</span></span> <span data-ttu-id="6e462-104">Zestaw, który zawiera właściwość ta ma relację zaprzyjaźniona z SQLAccess.dll.</span><span class="sxs-lookup"><span data-stu-id="6e462-104">The assembly that contains this property has a friend relationship with SQLAccess.dll.</span></span> <span data-ttu-id="6e462-105">Jest przeznaczony do użytku przez program SQL Server.</span><span class="sxs-lookup"><span data-stu-id="6e462-105">It's intended for use by SQL Server.</span></span> <span data-ttu-id="6e462-106">W przypadku innych baz danych użyj mechanizmu hostowania, pod warunkiem, że ta baza danych.</span><span class="sxs-lookup"><span data-stu-id="6e462-106">For other databases, use the hosting mechanism provided by that database.</span></span>

## <a name="syntax"></a><span data-ttu-id="6e462-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="6e462-107">Syntax</span></span>

```csharp
public abstract bool IsNull { get; }
```

## <a name="property-value"></a><span data-ttu-id="6e462-108">Wartość właściwości</span><span class="sxs-lookup"><span data-stu-id="6e462-108">Property value</span></span>

<xref:System.Boolean>\
<span data-ttu-id="6e462-109">`true` Jeśli strumień jest `null`; w przeciwnym razie `false`.</span><span class="sxs-lookup"><span data-stu-id="6e462-109">`true` if the stream is `null`; otherwise, `false`.</span></span>

## <a name="remarks"></a><span data-ttu-id="6e462-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="6e462-110">Remarks</span></span>

> [!WARNING]
> <span data-ttu-id="6e462-111">`SqlStreamChars.IsNull` Właściwość jest prywatny i nie jest przeznaczona do użycia bezpośrednio w kodzie.</span><span class="sxs-lookup"><span data-stu-id="6e462-111">The `SqlStreamChars.IsNull` property is private and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="6e462-112">Firma Microsoft obsługuje korzystanie z tego pola w aplikacji produkcyjnej w żadnym wypadku.</span><span class="sxs-lookup"><span data-stu-id="6e462-112">Microsoft does not support the use of this field in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="6e462-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="6e462-113">Requirements</span></span>

<span data-ttu-id="6e462-114">**Namespace:** <xref:System.Data.SqlTypes></span><span class="sxs-lookup"><span data-stu-id="6e462-114">**Namespace:** <xref:System.Data.SqlTypes></span></span>

<span data-ttu-id="6e462-115">**Zestaw:** Dane systemowe (w System.Data.dll)</span><span class="sxs-lookup"><span data-stu-id="6e462-115">**Assembly:** System.Data (in System.Data.dll)</span></span>

<span data-ttu-id="6e462-116">**Wersje programu .NET framework:** Dostępne od wersji 2.0.</span><span class="sxs-lookup"><span data-stu-id="6e462-116">**.NET Framework versions:** Available since 2.0.</span></span>