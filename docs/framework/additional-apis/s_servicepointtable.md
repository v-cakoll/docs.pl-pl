---
title: Pole ServicePointManager. s_ServicePointTable
description: Przeczytaj o polu ServicePointManager. s_ServicePointTable w programie .NET. To pole tabeli skrótów zawiera aktywne połączenia HTTP (servicepoints) w domenie aplikacji.
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
ms.openlocfilehash: 9462ae10125dd37706f786a1f2cef78e62fbabcc
ms.sourcegitcommit: 45c8eed045779b70a47b23169897459d0323dc89
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/18/2020
ms.locfileid: "84989542"
---
# <a name="servicepointmanagers_servicepointtable-field"></a>Pole ServicePointManager. s \_

`ServicePointManager.s_ServicePointTable`<xref:System.Collections.Hashtable>zawiera listę aktywnych połączeń HTTP <xref:System.Net.ServicePoint> w programie <xref:System.AppDomain> .

## <a name="syntax"></a>Składnia
  
```csharp  
private static Hashtable s_ServicePointTable
```

> [!WARNING]
> `ServicePointManager.s_ServicePointTable`Pole jest prywatne i nie jest przeznaczone do użycia bezpośrednio w kodzie.
>
> Firma Microsoft nie obsługuje korzystania z tego pola w aplikacji produkcyjnej w żadnej sytuacji.

## <a name="requirements"></a>Wymagania

**Przestrzeń nazw:**<xref:System.Net>

**Zestaw:** System (w System.dll)

**.NET Framework wersje:** Dostępne od 2,0.
