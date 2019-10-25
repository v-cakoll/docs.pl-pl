---
title: PooledStream. NetworkStream — Właściwość (System.Net)
ms.date: 10/21/2019
ms.technology: dotnet-networking
topic_type:
- apiref
api_name:
- System.Net.PooledStream.NetworkStream
- System.Net.PooledStream.get_NetworkStream
- System.Net.PooledStream.set_NetworkStream
api_location:
- System.dll
api_type:
- Assembly
ms.openlocfilehash: 541b8c94b30675c1286b48a2291c3bd3e4aeea0b
ms.sourcegitcommit: 337bdc5a463875daf2cc6883e5a2da97d56f5000
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2019
ms.locfileid: "72847179"
---
# <a name="pooledstreamnetworkstream-property"></a><span data-ttu-id="f2c5b-102">PooledStream. NetworkStream — Właściwość</span><span class="sxs-lookup"><span data-stu-id="f2c5b-102">PooledStream.NetworkStream Property</span></span>

<span data-ttu-id="f2c5b-103">Pobiera lub ustawia strumień sieciowy dla gniazda `PooledStream`.</span><span class="sxs-lookup"><span data-stu-id="f2c5b-103">Gets or sets the network stream for the `PooledStream` socket.</span></span>

## <a name="syntax"></a><span data-ttu-id="f2c5b-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="f2c5b-104">Syntax</span></span>

```csharp
internal NetworkStream NetworkStream { get; set; }
```

## <a name="property-value"></a><span data-ttu-id="f2c5b-105">Wartość właściwości</span><span class="sxs-lookup"><span data-stu-id="f2c5b-105">Property value</span></span>

<xref:System.Net.Sockets.NetworkStream>  
<span data-ttu-id="f2c5b-106">Strumień sieciowy dla gniazda `PooledStream`owego.</span><span class="sxs-lookup"><span data-stu-id="f2c5b-106">The network stream for the `PooledStream` socket.</span></span>

## <a name="remarks"></a><span data-ttu-id="f2c5b-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="f2c5b-107">Remarks</span></span>

> [!WARNING]
> <span data-ttu-id="f2c5b-108">Właściwość `PooledStream.NetworkStream` jest wewnętrzna i nie jest przeznaczona do użycia bezpośrednio w kodzie.</span><span class="sxs-lookup"><span data-stu-id="f2c5b-108">The `PooledStream.NetworkStream` property is internal and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="f2c5b-109">Firma Microsoft nie obsługuje użycia tej właściwości w aplikacji produkcyjnej w żadnym przypadku.</span><span class="sxs-lookup"><span data-stu-id="f2c5b-109">Microsoft does not support the use of this property in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="f2c5b-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="f2c5b-110">Requirements</span></span>

<span data-ttu-id="f2c5b-111">**Przestrzeń nazw:** <xref:System.Net></span><span class="sxs-lookup"><span data-stu-id="f2c5b-111">**Namespace:** <xref:System.Net></span></span>

<span data-ttu-id="f2c5b-112">**Zestaw:** System (w pliku System. dll)</span><span class="sxs-lookup"><span data-stu-id="f2c5b-112">**Assembly:** System (in System.dll)</span></span>

<span data-ttu-id="f2c5b-113">**.NET Framework wersje:** Dostępne od 2,0.</span><span class="sxs-lookup"><span data-stu-id="f2c5b-113">**.NET Framework versions:** Available since 2.0.</span></span>
