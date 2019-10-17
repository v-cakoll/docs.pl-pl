---
title: SqlStreamChars. Length — właściwość (System. Data. SqlTypes)
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
ms.openlocfilehash: 2171b10d1c0eb7bcad894cc44c5103bdab18b0a5
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/16/2019
ms.locfileid: "72395607"
---
# <a name="sqlstreamcharslength-property"></a><span data-ttu-id="241ac-102">SqlStreamChars. Length — właściwość</span><span class="sxs-lookup"><span data-stu-id="241ac-102">SqlStreamChars.Length Property</span></span>

<span data-ttu-id="241ac-103">Gdy jest zastępowany w klasie pochodnej, pobiera długość bieżącego strumienia.</span><span class="sxs-lookup"><span data-stu-id="241ac-103">When overridden in a derived class, gets the length of the current stream.</span></span> <span data-ttu-id="241ac-104">Zestaw, który zawiera tę właściwość, ma relację zaprzyjaźnioną z obiektem sqlaccess. dll.</span><span class="sxs-lookup"><span data-stu-id="241ac-104">The assembly that contains this property has a friend relationship with SQLAccess.dll.</span></span> <span data-ttu-id="241ac-105">Jest on przeznaczony do użycia przez SQL Server.</span><span class="sxs-lookup"><span data-stu-id="241ac-105">It's intended for use by SQL Server.</span></span> <span data-ttu-id="241ac-106">W przypadku innych baz danych Użyj mechanizmu hostingu dostarczonego przez tę bazę danych.</span><span class="sxs-lookup"><span data-stu-id="241ac-106">For other databases, use the hosting mechanism provided by that database.</span></span>

## <a name="syntax"></a><span data-ttu-id="241ac-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="241ac-107">Syntax</span></span>

```csharp
public abstract long Length { get; }
```

## <a name="property-value"></a><span data-ttu-id="241ac-108">Wartość właściwości</span><span class="sxs-lookup"><span data-stu-id="241ac-108">Property value</span></span>

<xref:System.Int64>\
<span data-ttu-id="241ac-109">Długość strumienia.</span><span class="sxs-lookup"><span data-stu-id="241ac-109">The length of the stream.</span></span>

## <a name="remarks"></a><span data-ttu-id="241ac-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="241ac-110">Remarks</span></span>

> [!WARNING]
> <span data-ttu-id="241ac-111">Właściwość `SqlStreamChars.Length` jest prywatna i nie jest przeznaczona do użycia bezpośrednio w kodzie.</span><span class="sxs-lookup"><span data-stu-id="241ac-111">The `SqlStreamChars.Length` property is private and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="241ac-112">Firma Microsoft nie obsługuje użycia tej właściwości w aplikacji produkcyjnej w żadnym przypadku.</span><span class="sxs-lookup"><span data-stu-id="241ac-112">Microsoft does not support the use of this property in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="241ac-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="241ac-113">Requirements</span></span>

<span data-ttu-id="241ac-114">**Przestrzeń nazw:** <xref:System.Data.SqlTypes></span><span class="sxs-lookup"><span data-stu-id="241ac-114">**Namespace:** <xref:System.Data.SqlTypes></span></span>

<span data-ttu-id="241ac-115">**Zestaw:** System. Data (w pliku System. Data. dll)</span><span class="sxs-lookup"><span data-stu-id="241ac-115">**Assembly:** System.Data (in System.Data.dll)</span></span>

<span data-ttu-id="241ac-116">**.NET Framework wersje:** Dostępne od 2,0.</span><span class="sxs-lookup"><span data-stu-id="241ac-116">**.NET Framework versions:** Available since 2.0.</span></span>
