---
title: Pole servicepoint.m_ConnectionGroupList
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
ms.openlocfilehash: 2b1b46085ed035b67fd01447727b406fe3895980
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79155898"
---
# <a name="servicepointm_connectiongrouplist-field"></a>Pole Lista\_połączeń servicepoint.m

`ServicePoint.m_ConnectionGroupList`jest <xref:System.Collections.Hashtable> a grup połączeń, z których <xref:System.Net.ServicePoint>każda posiada połączenie dla identyfikatora URI.

## <a name="syntax"></a>Składnia
  
```csharp  
private Hashtable m_ConnectionGroupList
```

> [!WARNING]
> To `ServicePoint.m_ConnectionGroupList` pole jest prywatne i nie jest przeznaczone do użycia bezpośrednio w kodzie.
>
> Firma Microsoft w żadnym wypadku nie obsługuje używania tego pola w aplikacji produkcyjnej.

## <a name="requirements"></a>Wymagania

**Obszar nazw:**<xref:System.Net>

**Montaż:** System (w pliku System.dll)

**Wersje programu .NET Framework:** Dostępne od 2.0.
