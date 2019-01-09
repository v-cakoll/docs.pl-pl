---
title: Właściwość SqlChars.Stream (System.Data.SqlTypes)
author: douglaslMS
ms.author: douglasl
ms.date: 12/19/2018
ms.technology:
- dotnet-data
api_name:
- System.Data.SqlTypes.SqlChars.Stream
- System.Data.SqlTypes.SqlChars.get_Stream
- System.Data.SqlTypes.SqlChars.set_Stream
api_location:
- System.Data.dll
api_type:
- Assembly
ms.openlocfilehash: f8b6f4f3a92f1d78e434263c6a7897641867c412
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/09/2019
ms.locfileid: "54152201"
---
# <a name="sqlcharsstream-property"></a><span data-ttu-id="782b6-102">Właściwość SqlChars.Stream</span><span class="sxs-lookup"><span data-stu-id="782b6-102">SqlChars.Stream Property</span></span>

<span data-ttu-id="782b6-103">Pobiera lub ustawia strumienia znaków.</span><span class="sxs-lookup"><span data-stu-id="782b6-103">Gets or sets the character stream.</span></span> <span data-ttu-id="782b6-104">Zestaw, który zawiera właściwość ta ma relację zaprzyjaźniona z SQLAccess.dll.</span><span class="sxs-lookup"><span data-stu-id="782b6-104">The assembly that contains this property has a friend relationship with SQLAccess.dll.</span></span> <span data-ttu-id="782b6-105">Jest przeznaczony do użytku przez program SQL Server.</span><span class="sxs-lookup"><span data-stu-id="782b6-105">It's intended for use by SQL Server.</span></span> <span data-ttu-id="782b6-106">W przypadku innych baz danych użyj mechanizmu hostowania, pod warunkiem, że ta baza danych.</span><span class="sxs-lookup"><span data-stu-id="782b6-106">For other databases, use the hosting mechanism provided by that database.</span></span>

```csharp
internal SqlStreamChars Stream { get; set; }
```

## <a name="property-value"></a><span data-ttu-id="782b6-107">Wartość właściwości</span><span class="sxs-lookup"><span data-stu-id="782b6-107">Property value</span></span>

`System.Data.SqlTypes.SqlStreamChars`\
<span data-ttu-id="782b6-108">Strumień znaków.</span><span class="sxs-lookup"><span data-stu-id="782b6-108">The character stream.</span></span>

## <a name="remarks"></a><span data-ttu-id="782b6-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="782b6-109">Remarks</span></span>

> [!WARNING]
> <span data-ttu-id="782b6-110">`SqlChars.Stream` Właściwość jest wewnętrzna i nie jest przeznaczona do użycia bezpośrednio w kodzie.</span><span class="sxs-lookup"><span data-stu-id="782b6-110">The `SqlChars.Stream` property is internal and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="782b6-111">Firma Microsoft nie obsługuje użycie tej właściwości w aplikacji produkcyjnej w żadnym wypadku.</span><span class="sxs-lookup"><span data-stu-id="782b6-111">Microsoft does not support the use of this property in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="782b6-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="782b6-112">Requirements</span></span>

<span data-ttu-id="782b6-113">**Namespace:** <xref:System.Data.SqlTypes></span><span class="sxs-lookup"><span data-stu-id="782b6-113">**Namespace:** <xref:System.Data.SqlTypes></span></span>

<span data-ttu-id="782b6-114">**Zestaw:** Dane systemowe (w System.Data.dll)</span><span class="sxs-lookup"><span data-stu-id="782b6-114">**Assembly:** System.Data (in System.Data.dll)</span></span>

<span data-ttu-id="782b6-115">**Wersje programu .NET framework:** Dostępne od wersji 2.0.</span><span class="sxs-lookup"><span data-stu-id="782b6-115">**.NET Framework versions:** Available since 2.0.</span></span>