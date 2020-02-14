---
title: Connection. m_ConnectionList — pole
ms.date: 05/01/2017
topic_type:
- apiref
api_name:
- System.Net.ConnectionGroup.m_ConnectionList
api_location:
- System.dll
api_type:
- Assembly
ms.assetid: 186083cf-8dff-4600-a2ab-6fed4b4de6af
ms.openlocfilehash: d53eeb54d212adb011dae138e103ea5b30f7fb99
ms.sourcegitcommit: 9c54866bcbdc49dbb981dd55be9bbd0443837aa2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/14/2020
ms.locfileid: "77215548"
---
# <a name="connectiongroupm_connectionlist-field"></a>ConnectionList pole połączenia. m\_

`ConnectionGroup.m_ConnectionList` to <xref:System.Collections.ArrayList> obiektów połączeń, które obsługują ten sam identyfikator URI i mają te same wartości dla niektórych innych właściwości, takich jak wygaśnięcie i uwierzytelnianie.

## <a name="syntax"></a>Składnia
  
```csharp  
private ArrayList m_ConnectionList
```

> [!WARNING]
> Pole `ConnectionGroup.m_ConnectionList` jest prywatne i nie jest przeznaczone do użycia bezpośrednio w kodzie.
> 
> Firma Microsoft nie obsługuje korzystania z tego pola w aplikacji produkcyjnej w żadnej sytuacji.

## <a name="requirements"></a>Wymagania

**Przestrzeń nazw:** <xref:System.Net>

**Zestaw:** System (w pliku System. dll)

**.NET Framework wersje:** Dostępne od 2,0.
