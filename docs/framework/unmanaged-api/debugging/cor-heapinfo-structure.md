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
ms.openlocfilehash: 37659262695b63a6dd6390c62c4bb7e04fdadca4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79179310"
---
# <a name="cor_heapinfo-structure"></a>COR_HEAPINFO — Struktura
Zawiera ogólne informacje na temat sterty wyrzucania elementów bezużytecznych, w tym, czy jest wyliczalny.  
  
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
  
|Członek|Opis|  
|------------|-----------------|  
|`areGCStructuresValid`|`true`jeśli struktury wyrzucania elementów bezużytecznych są prawidłowe i sterty mogą być wyliczone; w `false`przeciwnym razie , .|  
|`pointerSize`|Rozmiar w bajtach wskaźników na architekturze docelowej.|  
|`numHeaps`|Liczba logicznych sterty wyrzucania elementów bezużytecznych w procesie.|  
|`concurrent`|`TRUE`jeśli równoczesne (tło) wyrzucanie elementów bezużytecznych jest włączone; w `FALSE`przeciwnym razie , .|  
|`gcType`|Członek wyliczenia [CorDebugGCType,](cordebuggctype-enumeration.md) który wskazuje, czy moduł zbierający elementy bezużyteczne jest uruchomiony na stacji roboczej lub serwera.|  
  
## <a name="remarks"></a>Uwagi  
 Wystąpienie `COR_HEAPINFO` struktury jest zwracany przez wywołanie [ICorDebugProcess5::GetGCHeapInformation](icordebugprocess5-getgcheapinformation-method.md) metody.  
  
 Przed wyliczeniem obiektów na stercie wyrzucania `areGCStructuresValid` elementów bezużytecznych należy zawsze sprawdzić pole, aby upewnić się, że sterty jest w stanie wyliczalnym. Aby uzyskać więcej informacji, zobacz [ICorDebugProcess5::GetGCHeapInformation](icordebugprocess5-getgcheapinformation-method.md) metody.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [Wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET Framework:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też

- [Struktury debugowania](debugging-structures.md)
- [Debugging](index.md)
