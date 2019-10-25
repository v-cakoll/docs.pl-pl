---
title: SslState. SslProtocol — Właściwość (System .NET. Security)
ms.date: 10/21/2019
ms.technology: dotnet-networking
topic_type:
- apiref
api_name:
- System.Net.Security.SslState.SslProtocol
- System.Net.Security.SslState.get_SslProtocol
api_location:
- System.dll
api_type:
- Assembly
ms.openlocfilehash: 6983ac071dad29b240308031ecd0a3562a6856e4
ms.sourcegitcommit: 337bdc5a463875daf2cc6883e5a2da97d56f5000
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2019
ms.locfileid: "72847200"
---
# <a name="sslstatesslprotocol-property"></a><span data-ttu-id="f16c0-102">SslState. SslProtocol — Właściwość</span><span class="sxs-lookup"><span data-stu-id="f16c0-102">SslState.SslProtocol Property</span></span>

<span data-ttu-id="f16c0-103">Pobiera wersje protokołu SSL.</span><span class="sxs-lookup"><span data-stu-id="f16c0-103">Gets the SSL protocol versions.</span></span>

## <a name="syntax"></a><span data-ttu-id="f16c0-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="f16c0-104">Syntax</span></span>

```csharp
internal SslProtocols SslProtocol { get; }
```

## <a name="property-value"></a><span data-ttu-id="f16c0-105">Wartość właściwości</span><span class="sxs-lookup"><span data-stu-id="f16c0-105">Property value</span></span>

<xref:System.Security.Authentication.SslProtocols>  
<span data-ttu-id="f16c0-106">Bitowa kombinacja wartości wyliczenia, które określają wersje protokołu SSL.</span><span class="sxs-lookup"><span data-stu-id="f16c0-106">A bitwise combination of the enumeration values that specify the SSL protocol versions.</span></span>

## <a name="remarks"></a><span data-ttu-id="f16c0-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="f16c0-107">Remarks</span></span>

> [!WARNING]
> <span data-ttu-id="f16c0-108">Właściwość `SslState.SslProtocol` jest wewnętrzna i nie jest przeznaczona do użycia bezpośrednio w kodzie.</span><span class="sxs-lookup"><span data-stu-id="f16c0-108">The `SslState.SslProtocol` property is internal and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="f16c0-109">Firma Microsoft nie obsługuje użycia tej właściwości w aplikacji produkcyjnej w żadnym przypadku.</span><span class="sxs-lookup"><span data-stu-id="f16c0-109">Microsoft does not support the use of this property in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="f16c0-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="f16c0-110">Requirements</span></span>

<span data-ttu-id="f16c0-111">**Przestrzeń nazw:** <xref:System.Net.Security></span><span class="sxs-lookup"><span data-stu-id="f16c0-111">**Namespace:** <xref:System.Net.Security></span></span>

<span data-ttu-id="f16c0-112">**Zestaw:** System (w pliku System. dll)</span><span class="sxs-lookup"><span data-stu-id="f16c0-112">**Assembly:** System (in System.dll)</span></span>

<span data-ttu-id="f16c0-113">**.NET Framework wersje:** Dostępne od 2,0.</span><span class="sxs-lookup"><span data-stu-id="f16c0-113">**.NET Framework versions:** Available since 2.0.</span></span>
