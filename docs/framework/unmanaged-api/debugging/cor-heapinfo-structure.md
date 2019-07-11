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
ms.openlocfilehash: 3dd233643bd18b60b7d6176c34ee57e4061daf7c
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67740655"
---
# <a name="corheapinfo-structure"></a>COR_HEAPINFO — Struktura
Zawiera ogólne informacje o stercie wyrzucania elementów bezużytecznych, w tym, czy jest wyliczalna.  
  
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
|`areGCStructuresValid`|`true` Jeśli odzyskiwanie kolekcji struktury są prawidłowe i mogą być wyliczane sterty; w przeciwnym razie `false`.|  
|`pointerSize`|Rozmiar w bajtach, wskaźników na architektury docelowej.|  
|`numHeaps`|Liczba logicznych wyrzucania elementów bezużytecznych sterty procesu.|  
|`concurrent`|`TRUE` Jeśli jest to równoczesne (w tle) wyrzucanie elementów bezużytecznych jest włączony; w przeciwnym razie `FALSE`.|  
|`gcType`|Członek [cordebuggctype —](../../../../docs/framework/unmanaged-api/debugging/cordebuggctype-enumeration.md) wyliczenia, która wskazuje, czy moduł garbage collector jest uruchomiona na serwerze lub stacji roboczej.|  
  
## <a name="remarks"></a>Uwagi  
 Wystąpienie `COR_HEAPINFO` struktury jest zwracany przez wywołanie metody [ICorDebugProcess5::GetGCHeapInformation](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-getgcheapinformation-method.md) metody.  
  
 Przed wyliczania obiektów na stercie wyrzucania elementów bezużytecznych, należy zawsze sprawdzić `areGCStructuresValid` pola, aby upewnić się, że stos jest w stanie wyliczalny. Aby uzyskać więcej informacji, zobacz [ICorDebugProcess5::GetGCHeapInformation](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-getgcheapinformation-method.md) metody.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Struktury debugowania](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)
- [Debugowanie](../../../../docs/framework/unmanaged-api/debugging/index.md)
