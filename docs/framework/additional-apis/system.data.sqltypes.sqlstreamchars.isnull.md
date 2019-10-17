---
title: SqlStreamChars. IsNull — Właściwość (System. Data. SqlTypes)
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
ms.openlocfilehash: d80f653724b3ef0a1cadb69a5f72b1d9455597d6
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/16/2019
ms.locfileid: "72395733"
---
# <a name="sqlstreamcharsisnull-property"></a><span data-ttu-id="244b4-102">SqlStreamChars. IsNull — Właściwość</span><span class="sxs-lookup"><span data-stu-id="244b4-102">SqlStreamChars.IsNull Property</span></span>

<span data-ttu-id="244b4-103">Gdy jest zastępowany w klasie pochodnej, pobiera wartość wskazującą, czy strumień jest `null`.</span><span class="sxs-lookup"><span data-stu-id="244b4-103">When overridden in a derived class, gets a value that indicates whether the stream is `null`.</span></span> <span data-ttu-id="244b4-104">Zestaw, który zawiera tę właściwość, ma relację zaprzyjaźnioną z obiektem sqlaccess. dll.</span><span class="sxs-lookup"><span data-stu-id="244b4-104">The assembly that contains this property has a friend relationship with SQLAccess.dll.</span></span> <span data-ttu-id="244b4-105">Jest on przeznaczony do użycia przez SQL Server.</span><span class="sxs-lookup"><span data-stu-id="244b4-105">It's intended for use by SQL Server.</span></span> <span data-ttu-id="244b4-106">W przypadku innych baz danych Użyj mechanizmu hostingu dostarczonego przez tę bazę danych.</span><span class="sxs-lookup"><span data-stu-id="244b4-106">For other databases, use the hosting mechanism provided by that database.</span></span>

## <a name="syntax"></a><span data-ttu-id="244b4-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="244b4-107">Syntax</span></span>

```csharp
public abstract bool IsNull { get; }
```

## <a name="property-value"></a><span data-ttu-id="244b4-108">Wartość właściwości</span><span class="sxs-lookup"><span data-stu-id="244b4-108">Property value</span></span>

<xref:System.Boolean>\
<span data-ttu-id="244b4-109">`true`, jeśli strumień jest `null`; w przeciwnym razie `false`.</span><span class="sxs-lookup"><span data-stu-id="244b4-109">`true` if the stream is `null`; otherwise, `false`.</span></span>

## <a name="remarks"></a><span data-ttu-id="244b4-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="244b4-110">Remarks</span></span>

> [!WARNING]
> <span data-ttu-id="244b4-111">Właściwość `SqlStreamChars.IsNull` jest prywatna i nie jest przeznaczona do użycia bezpośrednio w kodzie.</span><span class="sxs-lookup"><span data-stu-id="244b4-111">The `SqlStreamChars.IsNull` property is private and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="244b4-112">Firma Microsoft nie obsługuje użycia tej właściwości w aplikacji produkcyjnej w żadnym przypadku.</span><span class="sxs-lookup"><span data-stu-id="244b4-112">Microsoft does not support the use of this property in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="244b4-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="244b4-113">Requirements</span></span>

<span data-ttu-id="244b4-114">**Przestrzeń nazw:** <xref:System.Data.SqlTypes></span><span class="sxs-lookup"><span data-stu-id="244b4-114">**Namespace:** <xref:System.Data.SqlTypes></span></span>

<span data-ttu-id="244b4-115">**Zestaw:** System. Data (w pliku System. Data. dll)</span><span class="sxs-lookup"><span data-stu-id="244b4-115">**Assembly:** System.Data (in System.Data.dll)</span></span>

<span data-ttu-id="244b4-116">**.NET Framework wersje:** Dostępne od 2,0.</span><span class="sxs-lookup"><span data-stu-id="244b4-116">**.NET Framework versions:** Available since 2.0.</span></span>
