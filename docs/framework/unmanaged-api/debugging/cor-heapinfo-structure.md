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
ms.openlocfilehash: b6fd3682290c9752125aed7b9663c6704ade25de
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73132334"
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
|`areGCStructuresValid`|`true`, jeśli struktury wyrzucania elementów bezużytecznych są prawidłowe i można wyliczyć stertę; w przeciwnym razie `false`.|  
|`pointerSize`|Rozmiar (w bajtach) wskaźników na architekturze docelowej.|  
|`numHeaps`|Liczba sterty logicznego wyrzucania elementów bezużytecznych w procesie.|  
|`concurrent`|`TRUE`, jeśli jest włączone współbieżne wyrzucanie elementów bezużytecznych (w tle); w przeciwnym razie `FALSE`.|  
|`gcType`|Element członkowski wyliczenia [CorDebugGCType —](cordebuggctype-enumeration.md) , który wskazuje, czy moduł wyrzucania elementów bezużytecznych jest uruchomiony na stacji roboczej lub na serwerze.|  
  
## <a name="remarks"></a>Uwagi  
 Wystąpienie struktury `COR_HEAPINFO` jest zwracane przez wywołanie metody [ICorDebugProcess5:: GetGCHeapInformation —](icordebugprocess5-getgcheapinformation-method.md) .  
  
 Przed wyliczeniem obiektów na stercie wyrzucania elementów bezużytecznych należy zawsze sprawdzić pole `areGCStructuresValid`, aby upewnić się, że sterta jest w stanie wyliczalnym. Aby uzyskać więcej informacji, zobacz metodę [ICorDebugProcess5:: GetGCHeapInformation —](icordebugprocess5-getgcheapinformation-method.md) .  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug. idl, CorDebug. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Struktury debugowania](debugging-structures.md)
- [Debugowanie](index.md)
