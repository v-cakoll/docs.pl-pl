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
# <a name="pooledstreamnetworkstream-property"></a>PooledStream. NetworkStream — Właściwość

Pobiera lub ustawia strumień sieciowy dla gniazda `PooledStream`.

## <a name="syntax"></a>Składnia

```csharp
internal NetworkStream NetworkStream { get; set; }
```

## <a name="property-value"></a>Wartość właściwości

<xref:System.Net.Sockets.NetworkStream>  
Strumień sieciowy dla gniazda `PooledStream`owego.

## <a name="remarks"></a>Uwagi

> [!WARNING]
> Właściwość `PooledStream.NetworkStream` jest wewnętrzna i nie jest przeznaczona do użycia bezpośrednio w kodzie.
>
> Firma Microsoft nie obsługuje użycia tej właściwości w aplikacji produkcyjnej w żadnym przypadku.

## <a name="requirements"></a>Wymagania

**Przestrzeń nazw:** <xref:System.Net>

**Zestaw:** System (w pliku System. dll)

**.NET Framework wersje:** Dostępne od 2,0.
