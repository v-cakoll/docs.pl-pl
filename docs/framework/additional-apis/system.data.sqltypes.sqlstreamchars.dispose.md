---
title: Metoda SqlStreamChars.Dispose(Boolean) (System.Data.SqlTypes)
author: douglaslMS
ms.author: douglasl
ms.date: 12/20/2018
ms.technology:
- dotnet-data
api_name:
- System.Data.SqlTypes.SqlStreamChars.Dispose
api_location:
- System.Data.dll
api_type:
- Assembly
ms.openlocfilehash: 3f2180d9a1893e651f174fff6d0f073df651e712
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/09/2019
ms.locfileid: "54152189"
---
# <a name="sqlstreamcharsdisposeboolean-method"></a><span data-ttu-id="39106-102">Metoda SqlStreamChars.Dispose(Boolean)</span><span class="sxs-lookup"><span data-stu-id="39106-102">SqlStreamChars.Dispose(Boolean) Method</span></span>

<span data-ttu-id="39106-103">W przypadku przesłonięcia w klasie pochodnej, zwalnia zasoby używane przez strumień.</span><span class="sxs-lookup"><span data-stu-id="39106-103">When overridden in a derived class, releases the resources used by the stream.</span></span> <span data-ttu-id="39106-104">Zestaw, który zawiera tę metodę ma relację zaprzyjaźniona z SQLAccess.dll.</span><span class="sxs-lookup"><span data-stu-id="39106-104">The assembly that contains this method has a friend relationship with SQLAccess.dll.</span></span> <span data-ttu-id="39106-105">Jest przeznaczony do użytku przez program SQL Server.</span><span class="sxs-lookup"><span data-stu-id="39106-105">It's intended for use by SQL Server.</span></span> <span data-ttu-id="39106-106">W przypadku innych baz danych użyj mechanizmu hostowania, pod warunkiem, że ta baza danych.</span><span class="sxs-lookup"><span data-stu-id="39106-106">For other databases, use the hosting mechanism provided by that database.</span></span>

```csharp
protected virtual void Dispose (bool disposing);
```

## <a name="parameters"></a><span data-ttu-id="39106-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="39106-107">Parameters</span></span>

`disposing`\
<span data-ttu-id="39106-108">`true` Aby zwolnić zasoby zarządzane i niezarządzane; `false` aby zwolnić tylko niezarządzane zasoby.</span><span class="sxs-lookup"><span data-stu-id="39106-108">`true` to release both managed and unmanaged resources; `false` to release only unmanaged resources.</span></span>

## <a name="remarks"></a><span data-ttu-id="39106-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="39106-109">Remarks</span></span>

> [!WARNING]
> <span data-ttu-id="39106-110">`SqlStreamChars.Dispose` Metoda jest prywatny i nie jest przeznaczona do użycia bezpośrednio w kodzie.</span><span class="sxs-lookup"><span data-stu-id="39106-110">The `SqlStreamChars.Dispose` method is private and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="39106-111">Firma Microsoft obsługuje korzystanie z tego pola w aplikacji produkcyjnej w żadnym wypadku.</span><span class="sxs-lookup"><span data-stu-id="39106-111">Microsoft does not support the use of this field in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="39106-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="39106-112">Requirements</span></span>

<span data-ttu-id="39106-113">**Namespace:** <xref:System.Data.SqlTypes></span><span class="sxs-lookup"><span data-stu-id="39106-113">**Namespace:** <xref:System.Data.SqlTypes></span></span>

<span data-ttu-id="39106-114">**Zestaw:** Dane systemowe (w System.Data.dll)</span><span class="sxs-lookup"><span data-stu-id="39106-114">**Assembly:** System.Data (in System.Data.dll)</span></span>

<span data-ttu-id="39106-115">**Wersje programu .NET framework:** Dostępne od wersji 2.0.</span><span class="sxs-lookup"><span data-stu-id="39106-115">**.NET Framework versions:** Available since 2.0.</span></span>