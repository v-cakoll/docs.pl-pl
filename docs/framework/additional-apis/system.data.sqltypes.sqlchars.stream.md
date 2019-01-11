---
title: Właściwość SqlChars.Stream (System.Data.SqlTypes)
author: douglaslMS
ms.author: douglasl
ms.date: 12/19/2018
ms.technology:
- dotnet-data
topic_type:
- apiref
api_name:
- System.Data.SqlTypes.SqlChars.Stream
- System.Data.SqlTypes.SqlChars.get_Stream
- System.Data.SqlTypes.SqlChars.set_Stream
api_location:
- System.Data.dll
api_type:
- Assembly
ms.openlocfilehash: d756b78a7cdbc12562e474ca3d2c9a1f3529f6bf
ms.sourcegitcommit: a36cfc9dbbfc04bd88971f96e8a3f8e283c15d42
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/11/2019
ms.locfileid: "54223055"
---
# <a name="sqlcharsstream-property"></a><span data-ttu-id="ed9eb-102">Właściwość SqlChars.Stream</span><span class="sxs-lookup"><span data-stu-id="ed9eb-102">SqlChars.Stream Property</span></span>

<span data-ttu-id="ed9eb-103">Pobiera lub ustawia strumienia znaków.</span><span class="sxs-lookup"><span data-stu-id="ed9eb-103">Gets or sets the character stream.</span></span> <span data-ttu-id="ed9eb-104">Zestaw, który zawiera właściwość ta ma relację zaprzyjaźniona z SQLAccess.dll.</span><span class="sxs-lookup"><span data-stu-id="ed9eb-104">The assembly that contains this property has a friend relationship with SQLAccess.dll.</span></span> <span data-ttu-id="ed9eb-105">Jest przeznaczony do użytku przez program SQL Server.</span><span class="sxs-lookup"><span data-stu-id="ed9eb-105">It's intended for use by SQL Server.</span></span> <span data-ttu-id="ed9eb-106">W przypadku innych baz danych użyj mechanizmu hostowania, pod warunkiem, że ta baza danych.</span><span class="sxs-lookup"><span data-stu-id="ed9eb-106">For other databases, use the hosting mechanism provided by that database.</span></span>

```csharp
internal SqlStreamChars Stream { get; set; }
```

## <a name="property-value"></a><span data-ttu-id="ed9eb-107">Wartość właściwości</span><span class="sxs-lookup"><span data-stu-id="ed9eb-107">Property value</span></span>

`System.Data.SqlTypes.SqlStreamChars`\
<span data-ttu-id="ed9eb-108">Strumień znaków.</span><span class="sxs-lookup"><span data-stu-id="ed9eb-108">The character stream.</span></span>

## <a name="remarks"></a><span data-ttu-id="ed9eb-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="ed9eb-109">Remarks</span></span>

> [!WARNING]
> <span data-ttu-id="ed9eb-110">`SqlChars.Stream` Właściwość jest wewnętrzna i nie jest przeznaczona do użycia bezpośrednio w kodzie.</span><span class="sxs-lookup"><span data-stu-id="ed9eb-110">The `SqlChars.Stream` property is internal and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="ed9eb-111">Firma Microsoft nie obsługuje użycie tej właściwości w aplikacji produkcyjnej w żadnym wypadku.</span><span class="sxs-lookup"><span data-stu-id="ed9eb-111">Microsoft does not support the use of this property in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="ed9eb-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="ed9eb-112">Requirements</span></span>

<span data-ttu-id="ed9eb-113">**Namespace:** <xref:System.Data.SqlTypes></span><span class="sxs-lookup"><span data-stu-id="ed9eb-113">**Namespace:** <xref:System.Data.SqlTypes></span></span>

<span data-ttu-id="ed9eb-114">**Zestaw:** Dane systemowe (w System.Data.dll)</span><span class="sxs-lookup"><span data-stu-id="ed9eb-114">**Assembly:** System.Data (in System.Data.dll)</span></span>

<span data-ttu-id="ed9eb-115">**Wersje programu .NET framework:** Dostępne od wersji 2.0.</span><span class="sxs-lookup"><span data-stu-id="ed9eb-115">**.NET Framework versions:** Available since 2.0.</span></span>