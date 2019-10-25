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
# <a name="sslstatesslprotocol-property"></a>SslState. SslProtocol — Właściwość

Pobiera wersje protokołu SSL.

## <a name="syntax"></a>Składnia

```csharp
internal SslProtocols SslProtocol { get; }
```

## <a name="property-value"></a>Wartość właściwości

<xref:System.Security.Authentication.SslProtocols>  
Bitowa kombinacja wartości wyliczenia, które określają wersje protokołu SSL.

## <a name="remarks"></a>Uwagi

> [!WARNING]
> Właściwość `SslState.SslProtocol` jest wewnętrzna i nie jest przeznaczona do użycia bezpośrednio w kodzie.
>
> Firma Microsoft nie obsługuje użycia tej właściwości w aplikacji produkcyjnej w żadnym przypadku.

## <a name="requirements"></a>Wymagania

**Przestrzeń nazw:** <xref:System.Net.Security>

**Zestaw:** System (w pliku System. dll)

**.NET Framework wersje:** Dostępne od 2,0.
