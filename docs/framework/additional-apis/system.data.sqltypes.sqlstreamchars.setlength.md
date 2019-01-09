---
title: Metoda SqlStreamChars.SetLength(Int64) (System.Data.SqlTypes)
author: douglaslMS
ms.author: douglasl
ms.date: 12/20/2018
ms.technology:
- dotnet-data
api_name:
- System.Data.SqlTypes.SqlStreamChars.SetLength
api_location:
- System.Data.dll
api_type:
- Assembly
ms.openlocfilehash: 7eb2b1bfe0a3d180b54c41cbca1d645dfb402be7
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/09/2019
ms.locfileid: "54152249"
---
# <a name="sqlstreamcharssetlengthint64-method"></a><span data-ttu-id="7b8d8-102">Metoda SqlStreamChars.SetLength(Int64)</span><span class="sxs-lookup"><span data-stu-id="7b8d8-102">SqlStreamChars.SetLength(Int64) Method</span></span>

<span data-ttu-id="7b8d8-103">W przypadku przesłonięcia w klasie pochodnej, zwalnia zasoby używane przez strumień.</span><span class="sxs-lookup"><span data-stu-id="7b8d8-103">When overridden in a derived class, releases the resources used by the stream.</span></span> <span data-ttu-id="7b8d8-104">Zestaw, który zawiera tę metodę ma relację zaprzyjaźniona z SQLAccess.dll.</span><span class="sxs-lookup"><span data-stu-id="7b8d8-104">The assembly that contains this method has a friend relationship with SQLAccess.dll.</span></span> <span data-ttu-id="7b8d8-105">Jest przeznaczony do użytku przez program SQL Server.</span><span class="sxs-lookup"><span data-stu-id="7b8d8-105">It's intended for use by SQL Server.</span></span> <span data-ttu-id="7b8d8-106">W przypadku innych baz danych użyj mechanizmu hostowania, pod warunkiem, że ta baza danych.</span><span class="sxs-lookup"><span data-stu-id="7b8d8-106">For other databases, use the hosting mechanism provided by that database.</span></span>

```csharp
public abstract void SetLength (long value);
```

## <a name="parameters"></a><span data-ttu-id="7b8d8-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="7b8d8-107">Parameters</span></span>

`value`\
<span data-ttu-id="7b8d8-108">Wymagana długość bieżącego strumienia, w bajtach.</span><span class="sxs-lookup"><span data-stu-id="7b8d8-108">The desired length of the current stream in bytes.</span></span>

## <a name="remarks"></a><span data-ttu-id="7b8d8-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="7b8d8-109">Remarks</span></span>

> [!WARNING]
> <span data-ttu-id="7b8d8-110">`SqlStreamChars.SetLength` Metoda jest prywatny i nie jest przeznaczona do użycia bezpośrednio w kodzie.</span><span class="sxs-lookup"><span data-stu-id="7b8d8-110">The `SqlStreamChars.SetLength` method is private and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="7b8d8-111">Firma Microsoft obsługuje korzystanie z tego pola w aplikacji produkcyjnej w żadnym wypadku.</span><span class="sxs-lookup"><span data-stu-id="7b8d8-111">Microsoft does not support the use of this field in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="7b8d8-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="7b8d8-112">Requirements</span></span>

<span data-ttu-id="7b8d8-113">**Namespace:** <xref:System.Data.SqlTypes></span><span class="sxs-lookup"><span data-stu-id="7b8d8-113">**Namespace:** <xref:System.Data.SqlTypes></span></span>

<span data-ttu-id="7b8d8-114">**Zestaw:** Dane systemowe (w System.Data.dll)</span><span class="sxs-lookup"><span data-stu-id="7b8d8-114">**Assembly:** System.Data (in System.Data.dll)</span></span>

<span data-ttu-id="7b8d8-115">**Wersje programu .NET framework:** Dostępne od wersji 2.0.</span><span class="sxs-lookup"><span data-stu-id="7b8d8-115">**.NET Framework versions:** Available since 2.0.</span></span>