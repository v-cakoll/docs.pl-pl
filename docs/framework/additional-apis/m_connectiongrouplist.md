---
title: ServicePoint. m_ConnectionGroupList — pole
description: Zapoznaj się z polem ServicePoint. m_ConnectionGroupList, czyli tabelą skrótów grup połączeń, które każdy z nich utrzymuje połączenie dla identyfikatora URI ServicePoint w programie .NET.
ms.date: 05/01/2017
topic_type:
- apiref
api_name:
- System.Net.ServicePoint.m_ConnectionGroupList
api_location:
- System.dll
api_type:
- Assembly
ms.assetid: df8afb59-f0f6-4ddc-b3c1-839b9fc601d8
ms.openlocfilehash: 0ebfeb782147f21abfde536b8053fa15b1e1a602
ms.sourcegitcommit: 45c8eed045779b70a47b23169897459d0323dc89
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/18/2020
ms.locfileid: "84989718"
---
# <a name="servicepointm_connectiongrouplist-field"></a>ServicePoint. m \_ ConnectionGroupList pole

`ServicePoint.m_ConnectionGroupList`jest <xref:System.Collections.Hashtable> grupą połączeń, z których każde utrzymuje połączenie dla <xref:System.Net.ServicePoint> identyfikatora URI.

## <a name="syntax"></a>Składnia
  
```csharp  
private Hashtable m_ConnectionGroupList
```

> [!WARNING]
> `ServicePoint.m_ConnectionGroupList`Pole jest prywatne i nie jest przeznaczone do użycia bezpośrednio w kodzie.
>
> Firma Microsoft nie obsługuje korzystania z tego pola w aplikacji produkcyjnej w żadnej sytuacji.

## <a name="requirements"></a>Wymagania

**Przestrzeń nazw:**<xref:System.Net>

**Zestaw:** System (w System.dll)

**.NET Framework wersje:** Dostępne od 2,0.
