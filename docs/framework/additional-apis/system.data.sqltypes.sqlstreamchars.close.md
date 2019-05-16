---
title: Metoda SqlStreamChars.Close (System.Data.SqlTypes)
author: stevestein
ms.author: sstein
ms.date: 12/20/2018
ms.technology: dotnet-data
topic_type:
- apiref
api_name:
- System.Data.SqlTypes.SqlStreamChars.Close
api_location:
- System.Data.dll
api_type:
- Assembly
ms.openlocfilehash: 942ee987f1c56abe2cb1718347886dd397e7217e
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2019
ms.locfileid: "65634343"
---
# <a name="sqlstreamcharsclose-method"></a><span data-ttu-id="abd9a-102">Metoda SqlStreamChars.Close</span><span class="sxs-lookup"><span data-stu-id="abd9a-102">SqlStreamChars.Close Method</span></span>

<span data-ttu-id="abd9a-103">Powoduje zamknięcie bieżącego strumienia i zwalnia wszystkie zasoby systemu, skojarzone ze strumienia.</span><span class="sxs-lookup"><span data-stu-id="abd9a-103">Closes the current stream and releases any system resources associated with the stream.</span></span> <span data-ttu-id="abd9a-104">Zestaw, który zawiera tę metodę ma relację zaprzyjaźniona z SQLAccess.dll.</span><span class="sxs-lookup"><span data-stu-id="abd9a-104">The assembly that contains this method has a friend relationship with SQLAccess.dll.</span></span> <span data-ttu-id="abd9a-105">Jest przeznaczony do użytku przez program SQL Server.</span><span class="sxs-lookup"><span data-stu-id="abd9a-105">It's intended for use by SQL Server.</span></span><span data-ttu-id="abd9a-106"> W przypadku innych baz danych użyj mechanizmu hostowania, pod warunkiem, że ta baza danych.</span><span class="sxs-lookup"><span data-stu-id="abd9a-106"> For other databases, use the hosting mechanism provided by that database.</span></span>

```csharp
public virtual void Close ();
```

## <a name="remarks"></a><span data-ttu-id="abd9a-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="abd9a-107">Remarks</span></span>

> [!WARNING]
> <span data-ttu-id="abd9a-108">`SqlStreamChars.Close` Metoda jest prywatny i nie jest przeznaczona do użycia bezpośrednio w kodzie.</span><span class="sxs-lookup"><span data-stu-id="abd9a-108">The `SqlStreamChars.Close` method is private and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="abd9a-109">Firma Microsoft obsługuje korzystanie z tego pola w aplikacji produkcyjnej w żadnym wypadku.</span><span class="sxs-lookup"><span data-stu-id="abd9a-109">Microsoft does not support the use of this field in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="abd9a-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="abd9a-110">Requirements</span></span>

<span data-ttu-id="abd9a-111">**Namespace:** <xref:System.Data.SqlTypes></span><span class="sxs-lookup"><span data-stu-id="abd9a-111">**Namespace:** <xref:System.Data.SqlTypes></span></span>

<span data-ttu-id="abd9a-112">**Zestaw:** Dane systemowe (w System.Data.dll)</span><span class="sxs-lookup"><span data-stu-id="abd9a-112">**Assembly:** System.Data (in System.Data.dll)</span></span>

<span data-ttu-id="abd9a-113">**Wersje programu .NET framework:** Dostępne od wersji 2.0.</span><span class="sxs-lookup"><span data-stu-id="abd9a-113">**.NET Framework versions:** Available since 2.0.</span></span>
