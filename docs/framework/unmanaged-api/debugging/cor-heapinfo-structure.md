---
title: COR_HEAPINFO — Struktura
ms.date: 03/30/2017
api_name:
- COR_HEAPINFO
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- COR_HEAPINFO
helpviewer_keywords:
- COR_HEAPINFO structure [.NET Framework debugging]
ms.assetid: bfb2cd39-3e0b-4d51-ba0c-f009755c1456
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f7b340a73aa9eaebca9c0d78563ae298557039b8
ms.sourcegitcommit: 3caa92cb97e9f6c31f21769c7a3f7c4304024b39
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/25/2019
ms.locfileid: "71274188"
---
# <a name="cor_heapinfo-structure"></a>COR_HEAPINFO — Struktura
Zawiera ogólne informacje o stercie wyrzucania elementów bezużytecznych, w tym o tym, czy są wyliczalne  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
typedef struct _COR_HEAPINFO {  
    BOOL areGCStructuresValid;   
    DWORD pointerSize;   
    DWORD numHeaps;  
    BOOL concurrent;   
    CorDebugGCType gcType;   
} COR_HEAPINFO;  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
|Element członkowski|Opis|  
|------------|-----------------|  
|`areGCStructuresValid`|`true`Jeśli struktury wyrzucania elementów bezużytecznych są prawidłowe i sterta może zostać wyliczona; w przeciwnym razie. `false`|  
|`pointerSize`|Rozmiar (w bajtach) wskaźników na architekturze docelowej.|  
|`numHeaps`|Liczba sterty logicznego wyrzucania elementów bezużytecznych w procesie.|  
|`concurrent`|`TRUE`Jeśli włączono współbieżne (w tle) odzyskiwanie pamięci; w przeciwnym razie. `FALSE`|  
|`gcType`|Element członkowski wyliczenia [CorDebugGCType —](cordebuggctype-enumeration.md) , który wskazuje, czy moduł wyrzucania elementów bezużytecznych jest uruchomiony na stacji roboczej lub na serwerze.|  
  
## <a name="remarks"></a>Uwagi  
 Wystąpienie `COR_HEAPINFO` struktury jest zwracane przez wywołanie metody [ICorDebugProcess5:: GetGCHeapInformation —](icordebugprocess5-getgcheapinformation-method.md) .  
  
 Przed wyliczeniem obiektów na stercie wyrzucania elementów bezużytecznych należy `areGCStructuresValid` zawsze zaznaczyć pole, aby upewnić się, że sterta jest w stanie wyliczalnym. Aby uzyskać więcej informacji, zobacz metodę [ICorDebugProcess5:: GetGCHeapInformation —](icordebugprocess5-getgcheapinformation-method.md) .  
  
## <a name="requirements"></a>Wymagania  
 **Poszczególnych** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówki** CorDebug.idl, CorDebug.h  
  
 **Biblioteki** CorGuids.lib  
  
 **.NET Framework wersje:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Struktury debugowania](debugging-structures.md)
- [Debugowanie](index.md)
