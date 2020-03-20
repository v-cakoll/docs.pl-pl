---
title: Pole Connection.m_WriteList
ms.date: 05/01/2017
topic_type:
- apiref
api_name:
- System.Net.Connection.m_WriteList
api_location:
- System.dll
api_type:
- Assembly
ms.assetid: 235503c1-1d01-4f59-895f-ae2cf15b3345
ms.openlocfilehash: 6c60831ddf23ce8ac9afcf244383d24732c3ef8b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79155840"
---
# <a name="connectionm_writelist-field"></a>Pole Lista\_zapisów Connection.m

`Connection.m_WriteList`jest <xref:System.Collections.ArrayList> obiektem, <xref:System.Net.HttpWebRequest> które są umieszczane w kolejce do wysłania za pośrednictwem protokołu HTTP.

## <a name="syntax"></a>Składnia
  
```csharp  
private ArrayList m_WriteList
```

> [!WARNING]
> To `Connection.m_WriteList` pole jest prywatne i nie jest przeznaczone do użycia bezpośrednio w kodzie.
>
> Firma Microsoft w żadnym wypadku nie obsługuje używania tego pola w aplikacji produkcyjnej.

## <a name="requirements"></a>Wymagania

**Obszar nazw:**<xref:System.Net>

**Montaż:** System (w pliku System.dll)

**Wersje programu .NET Framework:** Dostępne od 2.0.
