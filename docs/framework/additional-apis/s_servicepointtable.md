---
title: Pole ServicePointManager.s_ServicePointTable
ms.date: 05/01/2017
topic_type:
- apiref
api_name:
- System.Net.ServicePointManager.s_ServicePointTable
api_location:
- System.dll
api_type:
- Assembly
ms.assetid: 24459679-291c-401a-9def-e42b29466fcf
ms.openlocfilehash: 6a56ecd6fc85005f5987c3c2ad0d1680ca63c398
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79155820"
---
# <a name="servicepointmanagers_servicepointtable-field"></a>Pole ServicePointManager.s\_ServicePointTable

`ServicePointManager.s_ServicePointTable`jest <xref:System.Collections.Hashtable> to, która zawiera listę aktywnych połączeń HTTP (s)<xref:System.Net.ServicePoint>w pliku <xref:System.AppDomain>.

## <a name="syntax"></a>Składnia
  
```csharp  
private static Hashtable s_ServicePointTable
```

> [!WARNING]
> To `ServicePointManager.s_ServicePointTable` pole jest prywatne i nie jest przeznaczone do użycia bezpośrednio w kodzie.
>
> Firma Microsoft w żadnym wypadku nie obsługuje używania tego pola w aplikacji produkcyjnej.

## <a name="requirements"></a>Wymagania

**Obszar nazw:**<xref:System.Net>

**Montaż:** System (w pliku System.dll)

**Wersje programu .NET Framework:** Dostępne od 2.0.
