---
title: Pole ServicePointManager. s_ServicePointTable
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
ms.openlocfilehash: 272a0c113fd70d804c763ba0e7e6e9a4a4ee04ce
ms.sourcegitcommit: 9c54866bcbdc49dbb981dd55be9bbd0443837aa2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/14/2020
ms.locfileid: "77214917"
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
