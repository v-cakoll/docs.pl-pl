---
title: ServicePointManager. s_ServicePointTable, pole
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 68445f4a290b9f4fe2696e35cda391b6c0ee8f85
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73119999"
---
# <a name="servicepointmanagers_servicepointtable-field"></a>ServicePointManager. s\_pole ServicePoint

`ServicePointManager.s_ServicePointTable` to <xref:System.Collections.Hashtable>, która zawiera listę aktywnych połączeń HTTP (<xref:System.Net.ServicePoint>s) w <xref:System.AppDomain>.

## <a name="syntax"></a>Składnia
  
```csharp  
private static Hashtable s_ServicePointTable
```

> [!WARNING]
> Pole `ServicePointManager.s_ServicePointTable` jest prywatne i nie jest przeznaczone do użycia bezpośrednio w kodzie.
> 
> Firma Microsoft nie obsługuje korzystania z tego pola w aplikacji produkcyjnej w żadnej sytuacji.

## <a name="requirements"></a>Wymagania

**Przestrzeń nazw:** <xref:System.Net>

**Zestaw:** System (w pliku System. dll)

**.NET Framework wersje:** Dostępne od 2,0.
