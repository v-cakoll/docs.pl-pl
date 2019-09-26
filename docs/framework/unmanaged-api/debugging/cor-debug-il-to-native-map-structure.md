---
title: COR_DEBUG_IL_TO_NATIVE_MAP — Struktura
ms.date: 03/30/2017
api_name:
- COR_DEBUG_IL_TO_NATIVE_MAP
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- COR_DEBUG_IL_TO_NATIVE_MAP
helpviewer_keywords:
- COR_DEBUG_IL_TO_NATIVE_MAP structure [.NET Framework debugging]
ms.assetid: 06f3b504-085f-4142-934a-25381fe23d4c
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: babb1ace1385c241b782691f22bfb4fbb689e310
ms.sourcegitcommit: 3caa92cb97e9f6c31f21769c7a3f7c4304024b39
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/25/2019
ms.locfileid: "71274073"
---
# <a name="cor_debug_il_to_native_map-structure"></a>COR_DEBUG_IL_TO_NATIVE_MAP — Struktura
Zawiera przesunięcia, które są używane do mapowania kodu języka pośredniego firmy Microsoft (MSIL) na kod natywny.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
typedef struct COR_DEBUG_IL_TO_NATIVE_MAP {  
    ULONG32  ilOffset;  
    ULONG32  nativeStartOffset;  
    ULONG32  nativeEndOffset;  
} COR_DEBUG_IL_TO_NATIVE_MAP;  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
|Element członkowski|Opis|  
|------------|-----------------|  
|`ilOffset`|Przesunięcie kodu MSIL.|  
|`nativeStartOffset`|Przesunięcie początku kodu natywnego.|  
|`nativeEndOffset`|Przesunięcie końca kodu natywnego.|  
  
## <a name="requirements"></a>Wymagania  
 **Poszczególnych** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówki** CorProf.idl, CorDebug.idl  
  
 **Biblioteki** CorGuids.lib  
  
 **.NET Framework wersje:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [GetILToNativeMapping, metoda](../profiling/icorprofilerinfo-getiltonativemapping-method.md)
- [GetILToNativeMapping, metoda](icordebugcode-getiltonativemapping-method.md)
- [Struktury debugowania](debugging-structures.md)
- [Debugowanie](index.md)
