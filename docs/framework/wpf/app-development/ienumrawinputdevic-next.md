---
title: IEnumRAWINPUTDEVIC:Next
ms.date: 03/30/2017
helpviewer_keywords:
- Next method [WPF]
ms.assetid: 3698b44d-510e-4d18-b32b-85f17188ee26
ms.openlocfilehash: c7450a9ababa9cf3cb02d572f5ed84f0791d74e4
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2019
ms.locfileid: "71053396"
---
# <a name="ienumrawinputdevicnext"></a>IEnumRAWINPUTDEVIC:Next
Wylicza następną `celt` strukturę [RAWINPUTDEVICE](/windows/desktop/api/winuser/ns-winuser-rawinputdevice) na liście modułu wyliczającego `rgelt` , zwracając ją wraz z rzeczywistą liczbę wyliczonych elementów w `pceltFetched`.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT Next(  
      [in] ULONG celt,  
      [out, size_is(celt), length_is(*pceltFetched)] RAWINPUTDEVICE *rgelt,  
      [out] ULONG *pceltFetched);  
```  
  
## <a name="parameters"></a>Parametry  
 `celt`  
  
 podczas Liczba zwróconych `rgelt`struktur [RAWINPUTDEVICE](/windows/desktop/api/winuser/ns-winuser-rawinputdevice) .  
  
 `rgelt`  
  
 określoną Tablica rozmiaru celt (lub większa) do odbierania wyliczonych struktur RAWINPUTDEVICE.  
  
 `pceltFetched`  
  
 określoną Wskaźnik do liczby elementów faktycznie dostarczonych w `rgelt`. Obiekt wywołujący może `NULL` być `rgelt` przekazywany w przypadku, gdy jest on.  
  
## <a name="property-valuereturn-value"></a>Wartość właściwości/Zwracana wartość  
 WYNIK S_OK, jeśli liczba dostarczonych elementów to `celt`; S_FALSE w inny sposób.
