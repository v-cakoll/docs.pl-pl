---
title: SmiOrderProperty.Item Property (Microsoft.SqlServer.Server)
author: stevestein
ms.author: sstein
ms.date: 12/20/2018
ms.technology:
- dotnet-data
topic_type:
- apiref
api_name:
- Microsoft.SqlServer.Server.SmiOrderProperty.Item
- Microsoft.SqlServer.Server.SmiOrderProperty.get_Item
api_location:
- System.Data.dll
api_type:
- Assembly
ms.openlocfilehash: cb2f6cb956f9571f9bd2ba7f86d79c5df6e72a15
ms.sourcegitcommit: 3500c4845f96a91a438a02ef2c6b4eef45a5e2af
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/07/2019
ms.locfileid: "55827737"
---
# <a name="smiorderpropertyitem-property"></a><span data-ttu-id="5427e-102">Właściwość SmiOrderProperty.Item</span><span class="sxs-lookup"><span data-stu-id="5427e-102">SmiOrderProperty.Item Property</span></span>

<span data-ttu-id="5427e-103">Pobiera kolejność kolumn dla tej jednostki.</span><span class="sxs-lookup"><span data-stu-id="5427e-103">Gets the column order for the entity.</span></span> <span data-ttu-id="5427e-104">Zestaw, który zawiera właściwość ta ma relację zaprzyjaźniona z SQLAccess.dll.</span><span class="sxs-lookup"><span data-stu-id="5427e-104">The assembly that contains this property has a friend relationship with SQLAccess.dll.</span></span> <span data-ttu-id="5427e-105">Jest przeznaczony do użytku przez program SQL Server.</span><span class="sxs-lookup"><span data-stu-id="5427e-105">It's intended for use by SQL Server.</span></span> <span data-ttu-id="5427e-106">W przypadku innych baz danych użyj mechanizmu hostowania, pod warunkiem, że ta baza danych.</span><span class="sxs-lookup"><span data-stu-id="5427e-106">For other databases, use the hosting mechanism provided by that database.</span></span>

## <a name="syntax"></a><span data-ttu-id="5427e-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="5427e-107">Syntax</span></span>

```csharp
internal SmiColumnOrder Item { get; }
```

## <a name="property-value"></a><span data-ttu-id="5427e-108">Wartość właściwości</span><span class="sxs-lookup"><span data-stu-id="5427e-108">Property value</span></span>

<span data-ttu-id="5427e-109">Kolejność kolumn.</span><span class="sxs-lookup"><span data-stu-id="5427e-109">The column order.</span></span>

## <a name="remarks"></a><span data-ttu-id="5427e-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="5427e-110">Remarks</span></span>

> [!WARNING]
> <span data-ttu-id="5427e-111">`SmiOrderProperty.Item` Właściwość jest wewnętrzna i nie jest przeznaczona do użycia bezpośrednio w kodzie.</span><span class="sxs-lookup"><span data-stu-id="5427e-111">The `SmiOrderProperty.Item` property is internal and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="5427e-112">Firma Microsoft nie obsługuje użycie tej właściwości w aplikacji produkcyjnej w żadnym wypadku.</span><span class="sxs-lookup"><span data-stu-id="5427e-112">Microsoft does not support the use of this property in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="5427e-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="5427e-113">Requirements</span></span>

<span data-ttu-id="5427e-114">**Namespace:** <xref:Microsoft.SqlServer.Server></span><span class="sxs-lookup"><span data-stu-id="5427e-114">**Namespace:** <xref:Microsoft.SqlServer.Server></span></span>

<span data-ttu-id="5427e-115">**Zestaw:** Dane systemowe (w System.Data.dll)</span><span class="sxs-lookup"><span data-stu-id="5427e-115">**Assembly:** System.Data (in System.Data.dll)</span></span>

<span data-ttu-id="5427e-116">**Wersje programu .NET framework:** Dostępne od wersji 2.0.</span><span class="sxs-lookup"><span data-stu-id="5427e-116">**.NET Framework versions:** Available since 2.0.</span></span>